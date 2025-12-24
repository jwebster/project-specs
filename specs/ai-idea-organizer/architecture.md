# Technical Architecture

## System Overview

```
┌─────────────────────────────────────────────────────────────────────┐
│                           iPhone App                                 │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ │
│  │   Voice     │  │   Ideas     │  │  Projects   │  │   Plans     │ │
│  │   Capture   │  │   Manager   │  │   Manager   │  │   Manager   │ │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘ │
│         │                │                │                │        │
│         └────────────────┴────────────────┴────────────────┘        │
│                                   │                                  │
│                          ┌───────┴───────┐                          │
│                          │  Local Store  │                          │
│                          │  (Core Data)  │                          │
│                          └───────┬───────┘                          │
└──────────────────────────────────┼──────────────────────────────────┘
                                   │
                                   │ HTTPS
                                   ▼
┌──────────────────────────────────────────────────────────────────────┐
│                            Backend                                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐               │
│  │   Auth       │  │   API        │  │   Storage    │               │
│  │   Service    │  │   Gateway    │  │   Service    │               │
│  └──────────────┘  └──────┬───────┘  └──────────────┘               │
│                           │                                          │
└───────────────────────────┼──────────────────────────────────────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
       ┌───────────┐ ┌───────────┐ ┌───────────┐
       │  Whisper  │ │  Claude   │ │  Database │
       │   API     │ │   API     │ │ (Postgres)│
       └───────────┘ └───────────┘ └───────────┘

> **AI Decision**: Claude is the AI provider for all categorization and
> plan generation. Chosen for strong reasoning and natural language understanding.
```

---

## Component Details

### iOS App Architecture

```
┌─────────────────────────────────────────────────┐
│                    App Layer                     │
│  ┌───────────────────────────────────────────┐  │
│  │              SwiftUI Views                 │  │
│  │  HomeView | RecordView | ProjectView | ... │  │
│  └───────────────────────────────────────────┘  │
│                        │                         │
│  ┌───────────────────────────────────────────┐  │
│  │             ViewModels                     │  │
│  │  HomeVM | RecordVM | ProjectVM | PlanVM   │  │
│  └───────────────────────────────────────────┘  │
│                        │                         │
│  ┌───────────────────────────────────────────┐  │
│  │              Services                      │  │
│  │  AudioService | TranscriptionService |    │  │
│  │  AIService | SyncService                  │  │
│  └───────────────────────────────────────────┘  │
│                        │                         │
│  ┌───────────────────────────────────────────┐  │
│  │            Data Layer                      │  │
│  │  CoreData | FileManager | Keychain        │  │
│  └───────────────────────────────────────────┘  │
└─────────────────────────────────────────────────┘
```

#### Key Services

**AudioService**
```swift
protocol AudioService {
    func startRecording() async throws
    func stopRecording() async throws -> URL  // Returns audio file URL
    func playAudio(url: URL) async throws
    var isRecording: Bool { get }
    var recordingDuration: TimeInterval { get }
}
```

**TranscriptionService**
```swift
protocol TranscriptionService {
    func transcribe(audioURL: URL) async throws -> String
    func transcribeStream(audioURL: URL) -> AsyncStream<String>  // Real-time
}
```

**AIService**
```swift
protocol AIService {
    func categorize(idea: Idea, existingProjects: [Project]) async throws -> Project
    func generatePlan(project: Project) async throws -> Plan
    func suggestTasks(idea: Idea) async throws -> [Task]
}
```

---

### Data Models

```swift
// Core entities

struct User {
    let id: UUID
    let email: String
    let createdAt: Date
}

struct Idea {
    let id: UUID
    let userId: UUID
    let transcription: String
    let audioURL: URL?
    let projectId: UUID?
    let createdAt: Date
    let updatedAt: Date
    var status: IdeaStatus  // .captured, .categorized, .inPlan, .completed
}

struct Project {
    let id: UUID
    let userId: UUID
    let name: String
    let emoji: String?
    let createdAt: Date
    let updatedAt: Date
    var ideas: [Idea]
    var plan: Plan?
}

struct Plan {
    let id: UUID
    let projectId: UUID
    let phases: [Phase]
    let generatedAt: Date
    var status: PlanStatus  // .draft, .active, .completed
}

struct Phase {
    let id: UUID
    let name: String
    let order: Int
    var tasks: [Task]
}

struct Task {
    let id: UUID
    let title: String
    let sourceIdeaId: UUID?
    let priority: Priority  // .high, .medium, .low
    var isCompleted: Bool
    let order: Int
}
```

---

### API Design

#### Endpoints

```
POST   /auth/login
POST   /auth/register
POST   /auth/apple

POST   /ideas                    # Create new idea
GET    /ideas                    # List user's ideas
GET    /ideas/:id                # Get single idea
PATCH  /ideas/:id                # Update idea
DELETE /ideas/:id                # Delete idea

POST   /ideas/:id/transcribe     # Upload audio, get transcription
POST   /ideas/:id/categorize     # AI categorization

GET    /projects                 # List user's projects
POST   /projects                 # Create project
GET    /projects/:id             # Get project with ideas
PATCH  /projects/:id             # Update project
DELETE /projects/:id             # Delete project

POST   /projects/:id/plan        # Generate plan from ideas
GET    /projects/:id/plan        # Get current plan
PATCH  /projects/:id/plan        # Update plan
```

#### Request/Response Examples

**Create Idea**
```json
// POST /ideas
// Request
{
  "audioUploadId": "abc123",  // Pre-uploaded audio file
  "transcription": "Add dark mode toggle..."  // Optional, if client-transcribed
}

// Response
{
  "id": "idea-uuid",
  "transcription": "Add dark mode toggle to the settings page",
  "audioUrl": "https://storage.../abc123.m4a",
  "projectId": "project-uuid",
  "projectName": "Mobile App",
  "createdAt": "2024-01-15T10:30:00Z"
}
```

**Generate Plan**
```json
// POST /projects/:id/plan
// Request
{
  "ideaIds": ["id1", "id2", "id3"]  // Optional, defaults to all
}

// Response
{
  "id": "plan-uuid",
  "phases": [
    {
      "name": "Phase 1: Core Features",
      "tasks": [
        {
          "title": "Set up authentication service",
          "sourceIdeaId": "id1",
          "priority": "high"
        }
      ]
    }
  ],
  "generatedAt": "2024-01-15T10:35:00Z"
}
```

---

### AI Prompts

#### Categorization Prompt

```
You are organizing ideas into projects. Given a new idea and existing projects,
decide which project it belongs to, or suggest creating a new one.

EXISTING PROJECTS:
{{#each projects}}
- {{name}}: {{description}}
{{/each}}

NEW IDEA:
"{{transcription}}"

Respond with JSON:
{
  "projectId": "existing-id or null",
  "newProjectName": "Name if new project needed",
  "confidence": 0.0-1.0,
  "reasoning": "Brief explanation"
}
```

#### Plan Generation Prompt

```
You are a project planning assistant. Convert these ideas into an actionable
project plan with phases and tasks.

PROJECT: {{projectName}}

IDEAS:
{{#each ideas}}
{{@index}}. "{{transcription}}"
{{/each}}

Create a structured plan with:
1. Logical phases (2-4 phases typically)
2. Specific, actionable tasks
3. Priority levels (high/medium/low)
4. Task ordering within phases
5. Link tasks to source ideas where applicable

Respond with JSON:
{
  "phases": [
    {
      "name": "Phase name",
      "tasks": [
        {
          "title": "Task title",
          "sourceIdeaIndex": 0,
          "priority": "high",
          "order": 1
        }
      ]
    }
  ]
}
```

---

### Backend Stack Options

#### Option A: Supabase (Recommended for MVP)

```
┌─────────────────────────────────────────┐
│              Supabase                    │
│  ┌─────────────┐  ┌─────────────────┐   │
│  │  Auth       │  │  PostgreSQL     │   │
│  │  (built-in) │  │  + Row Security │   │
│  └─────────────┘  └─────────────────┘   │
│  ┌─────────────┐  ┌─────────────────┐   │
│  │  Storage    │  │  Edge Functions │   │
│  │  (S3-like)  │  │  (for AI calls) │   │
│  └─────────────┘  └─────────────────┘   │
└─────────────────────────────────────────┘
```

**Pros**: Fast setup, built-in auth, real-time, generous free tier
**Cons**: Less control, Edge Functions have limits

#### Option B: Custom Backend

```
┌─────────────────────────────────────────┐
│           Cloud Run / Railway           │
│  ┌─────────────────────────────────┐    │
│  │  Node.js / Python API           │    │
│  │  (Express / FastAPI)            │    │
│  └─────────────────────────────────┘    │
└───────────────────┬─────────────────────┘
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
   ┌────────┐  ┌────────┐  ┌────────┐
   │ Auth0  │  │ Neon   │  │  S3    │
   │        │  │(Postgres)│ │        │
   └────────┘  └────────┘  └────────┘
```

**Pros**: Full control, no limits
**Cons**: More setup time, more to maintain

---

### Security Considerations

| Concern | Mitigation |
|---------|------------|
| Audio data privacy | Encrypt at rest, delete after transcription option |
| API key exposure | Server-side AI calls only, never in client |
| User data isolation | Row-level security in Postgres |
| Auth tokens | Secure storage in iOS Keychain |
| API abuse | Rate limiting, usage quotas |

---

### Performance Targets

| Metric | Target | Measurement |
|--------|--------|-------------|
| App launch to record | < 1s | Cold start time |
| Transcription latency | < 3s | For 30s audio |
| AI categorization | < 2s | Time to assign project |
| Plan generation | < 5s | For 10 ideas |
| Idea list load | < 500ms | 100 ideas |

---

### Infrastructure Costs (Estimated)

| Service | Monthly Cost (1K users) |
|---------|------------------------|
| Supabase (Pro) | $25 |
| Whisper API | $50 (10K min audio) |
| Claude API | $100 (categorization + plans) |
| Audio Storage | $20 |
| **Total** | **~$200/month** |

Scales roughly linearly with users until optimization needed.
