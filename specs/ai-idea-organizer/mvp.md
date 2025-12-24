# MVP Definition

## MVP Scope

### Goal
Validate that users will consistently capture ideas via voice and find value in AI-generated project organization.

### Success Criteria
- Users capture 5+ ideas in first week
- 60% of users generate at least one project plan
- User retention at day 7: >30%

---

## MVP Features

### ✅ In Scope

#### Voice Capture
| Feature | Details |
|---------|---------|
| One-tap recording | App opens to record-ready state |
| Transcription | Real-time using cloud API (Whisper/Deepgram) |
| Audio storage | Keep original audio linked to transcription |
| Edit transcription | Fix errors in transcribed text |

#### AI Organization
| Feature | Details |
|---------|---------|
| Auto-categorization | AI assigns ideas to projects automatically |
| Project creation | AI creates new projects when needed |
| Project plan generation | Convert idea cluster → ordered task list |
| Task priorities | High/Medium/Low suggested by AI |

#### Viewing & Navigation
| Feature | Details |
|---------|---------|
| Timeline view | Chronological list of all ideas |
| Project view | Ideas grouped by project |
| Search | Full-text search across ideas |
| Idea detail | View/edit individual idea with audio playback |

#### Basic Settings
| Feature | Details |
|---------|---------|
| Account | Email/Apple sign-in |
| Theme | Light/dark mode |
| Feedback | In-app feedback mechanism |

---

### ❌ Out of Scope (Post-MVP)

| Feature | Why Deferred |
|---------|--------------|
| Offline mode | Adds complexity; validate online-first |
| Lock screen widget | Requires iOS 16+ specific work |
| Apple Watch | Separate app development |
| Siri integration | Requires additional Apple review |
| Collaboration | Single-user validation first |
| Export integrations | Manual export sufficient for MVP |
| iCloud sync | Single device validation first |
| Extended recordings | Focus on quick capture pattern |

---

## MVP Screens

### 1. Home (Timeline)
```
┌─────────────────────────────┐
│ [≡]  Ideas         [👤]    │
├─────────────────────────────┤
│                             │
│     🎤                      │
│  Tap to capture idea        │
│                             │
├─────────────────────────────┤
│ Today                       │
│ ├─ Idea 1... → Project A    │
│ └─ Idea 2... → Project B    │
│                             │
│ Yesterday                   │
│ └─ Idea 3... → Project A    │
│                             │
├─────────────────────────────┤
│ [Timeline] [Projects] [🔍]  │
└─────────────────────────────┘
```

### 2. Recording
```
┌─────────────────────────────┐
│                             │
│                             │
│         ◉                   │
│    ∿∿∿∿∿∿∿∿∿∿              │
│                             │
│     Recording...            │
│        0:04                 │
│                             │
│       [Stop]                │
│                             │
└─────────────────────────────┘
```

### 3. Post-Capture
```
┌─────────────────────────────┐
│      ✓ Idea Captured        │
├─────────────────────────────┤
│                             │
│ "Add user authentication    │
│  with social login options  │
│  like Google and Apple"     │
│                             │
│ 📁 → Mobile App Project     │
│      [Change]               │
│                             │
│ [Edit] [🔊]       [Done ✓]  │
│                             │
└─────────────────────────────┘
```

### 4. Projects List
```
┌─────────────────────────────┐
│ [←]  Projects               │
├─────────────────────────────┤
│                             │
│ 📱 Mobile App          (12) │
│    Last: 2 hours ago        │
│                             │
│ ✍️ Blog                 (5) │
│    Last: Yesterday          │
│                             │
│ 🏠 Home Renovation      (8) │
│    Last: 3 days ago         │
│                             │
│ + Create Project            │
│                             │
└─────────────────────────────┘
```

### 5. Project Detail
```
┌─────────────────────────────┐
│ [←]  📱 Mobile App          │
├─────────────────────────────┤
│ 12 ideas                    │
│                             │
│ [✨ Generate Plan]          │
│                             │
│ Ideas ──────────────────    │
│ • Add user auth with...     │
│ • Dark mode toggle...       │
│ • Push notifications...     │
│ • Onboarding flow...        │
│                             │
│ + Add idea                  │
└─────────────────────────────┘
```

### 6. Generated Plan
```
┌─────────────────────────────┐
│ [←]  📱 Mobile App Plan     │
├─────────────────────────────┤
│ Generated from 12 ideas     │
│                             │
│ PHASE 1 ────────────────    │
│ □ Set up auth service   [H] │
│ □ Build login screens   [H] │
│ □ Add social providers  [M] │
│                             │
│ PHASE 2 ────────────────    │
│ □ Design onboarding     [M] │
│ □ Build onboard screens [M] │
│                             │
│ [Regenerate] [Edit] [Share] │
└─────────────────────────────┘
```

### 7. Idea Detail
```
┌─────────────────────────────┐
│ [←]  Idea                   │
├─────────────────────────────┤
│                             │
│ "Add user authentication    │
│  with social login options  │
│  like Google and Apple"     │
│                             │
│ [🔊 Play Audio]             │
│                             │
│ Project: Mobile App [Edit]  │
│ Captured: Today, 2:34 PM    │
│                             │
│ [Edit Text]      [Delete]   │
│                             │
└─────────────────────────────┘
```

---

## MVP Tech Stack (Recommended)

| Layer | Technology | Rationale |
|-------|------------|-----------|
| Platform | Native iOS (Swift/SwiftUI) | Best voice/performance |
| Voice | OpenAI Whisper API | Best accuracy |
| AI | Claude API | Strong reasoning for organization |
| Backend | Supabase or Firebase | Fast to implement |
| Auth | Apple Sign-In + Email | Required for App Store |
| Storage | Supabase Storage / S3 | Audio file storage |

---

## MVP Timeline Estimate

| Phase | Duration | Deliverable |
|-------|----------|-------------|
| Design | 2 weeks | Figma mockups, user flows |
| Core Capture | 2 weeks | Voice recording + transcription |
| AI Integration | 2 weeks | Categorization + plan generation |
| Polish & Testing | 2 weeks | Bug fixes, TestFlight |
| **Total** | **8 weeks** | TestFlight Beta |

---

## MVP Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|------------|
| Transcription accuracy | Users frustrated by errors | Use Whisper (best accuracy), allow easy edits |
| AI categorization wrong | Users lose trust | Easy re-categorization, explain AI decisions |
| Plan quality low | Core value prop fails | Iterate on prompts, get user feedback |
| Voice capture too slow | Users won't use it | Optimize cold start, pre-warm recording |
| App Store rejection | Delays launch | Follow guidelines, prepare appeal |

---

## Post-MVP Roadmap

### v1.1 (Month 2)
- Offline voice capture
- Lock screen widget
- iCloud sync

### v1.2 (Month 3)
- Siri Shortcuts
- Export to Reminders
- AI refinement suggestions

### v2.0 (Month 4-5)
- Apple Watch app
- Collaboration (share projects)
- Third-party integrations
