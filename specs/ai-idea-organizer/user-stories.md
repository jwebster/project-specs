# User Stories

## Epic 1: Voice Capture

### US-1.1: Quick Voice Capture
**As a** user with a fleeting idea
**I want to** capture it with my voice in under 3 seconds
**So that** I don't lose the idea while fumbling with my phone

**Acceptance Criteria:**
- App opens to record-ready state
- Single tap starts recording
- Recording auto-stops after pause in speech (or manual stop)
- Transcription appears within 2 seconds of stopping
- Works from lock screen widget

---

### US-1.2: Extended Voice Capture
**As a** user brainstorming
**I want to** record longer thoughts (2-5 minutes)
**So that** I can fully explore an idea without interruption

**Acceptance Criteria:**
- No arbitrary time limit on recording
- Visual indicator shows recording is active
- Transcription handles long-form speech accurately
- AI extracts multiple distinct ideas from single recording

---

### US-1.3: Offline Capture
**As a** user without internet connection
**I want to** still capture voice ideas
**So that** I never miss an idea due to connectivity

**Acceptance Criteria:**
- Voice recording works offline
- Basic transcription available offline (Apple Speech)
- Full AI processing queued for when online
- Clear indication of pending sync status

---

## Epic 2: AI Organization

### US-2.1: Automatic Categorization
**As a** user with many ideas
**I want** AI to automatically group related ideas
**So that** I can see patterns without manual organization

**Acceptance Criteria:**
- New ideas auto-assigned to existing or new project
- User can see why AI chose categorization
- Easy to re-categorize if AI got it wrong
- Categories/projects created dynamically based on content

---

### US-2.2: Idea Refinement
**As a** user with a rough idea
**I want** AI to help clarify and structure my thought
**So that** vague ideas become actionable

**Acceptance Criteria:**
- AI extracts key points from rambling speech
- Suggests clearer phrasing of the core idea
- Identifies implicit sub-tasks or components
- Preserves original voice recording for reference

---

### US-2.3: Project Plan Generation
**As a** user with a collection of related ideas
**I want** AI to generate a project plan
**So that** I know what to do first

**Acceptance Criteria:**
- One-tap to generate plan from idea cluster
- Plan includes ordered tasks
- Tasks have suggested priorities (high/medium/low)
- Dependencies identified where logical
- Plan is editable after generation

---

### US-2.4: AI Suggestions
**As a** user working on a project
**I want** AI to proactively suggest connections
**So that** I notice relationships I might have missed

**Acceptance Criteria:**
- "Related ideas" shown when viewing an idea
- AI suggests merging similar ideas
- AI identifies gaps ("You might also want to think about...")
- Suggestions are non-intrusive (not constant notifications)

---

## Epic 3: Viewing & Editing

### US-3.1: Idea Timeline
**As a** user
**I want to** see my ideas in chronological order
**So that** I can browse recent thoughts

**Acceptance Criteria:**
- Default view shows recent ideas
- Grouped by day/week
- Search across all ideas
- Filter by project/category

---

### US-3.2: Project View
**As a** user working on a specific project
**I want to** see all related ideas and the generated plan
**So that** I can focus on one initiative

**Acceptance Criteria:**
- Project dashboard shows all linked ideas
- Generated plan prominently displayed
- Progress tracking on tasks
- Add new ideas directly to project

---

### US-3.3: Edit Transcriptions
**As a** user
**I want to** correct transcription errors
**So that** the text accurately reflects my idea

**Acceptance Criteria:**
- Tap to edit any transcription
- Original audio always preserved
- Edits don't break AI categorization
- Playback audio while editing

---

## Epic 4: Quick Access

### US-4.1: Lock Screen Widget
**As a** user with a sudden idea
**I want to** start recording from lock screen
**So that** capture is truly instant

**Acceptance Criteria:**
- iOS widget available for lock screen
- Tap widget → immediately recording
- No unlock required for capture
- Transcription visible after unlock

---

### US-4.2: Siri Integration
**As a** user
**I want to** say "Hey Siri, capture idea"
**So that** I can record hands-free

**Acceptance Criteria:**
- Siri Shortcut for idea capture
- Works while driving (CarPlay compatible)
- Confirmation that idea was captured
- Idea appears in app with full AI processing

---

### US-4.3: Apple Watch Capture
**As a** user on the go
**I want to** capture ideas from my watch
**So that** I don't need to pull out my phone

**Acceptance Criteria:**
- Watch app with one-tap record
- Syncs to iPhone for AI processing
- Complications for quick access
- Voice recording stored locally until sync

---

## Epic 5: Data Management

### US-5.1: Export to Other Tools
**As a** user with existing workflows
**I want to** export project plans
**So that** I can use my preferred tools for execution

**Acceptance Criteria:**
- Export as markdown/text
- Export to Reminders app
- Share sheet integration
- (Future) Direct integration with Notion, Things, etc.

---

### US-5.2: Backup & Sync
**As a** user with multiple devices
**I want** my ideas synced via iCloud
**So that** I can access them anywhere

**Acceptance Criteria:**
- Automatic iCloud sync
- Works on iPhone and iPad
- Conflict resolution for simultaneous edits
- Export all data for backup

---

## User Story Priority (MVP)

### Must Have (MVP)
- US-1.1: Quick Voice Capture
- US-2.1: Automatic Categorization
- US-2.3: Project Plan Generation
- US-3.1: Idea Timeline
- US-3.2: Project View

### Should Have (v1.1)
- US-1.3: Offline Capture
- US-2.2: Idea Refinement
- US-3.3: Edit Transcriptions
- US-4.1: Lock Screen Widget

### Could Have (v1.2+)
- US-1.2: Extended Voice Capture
- US-2.4: AI Suggestions
- US-4.2: Siri Integration
- US-4.3: Apple Watch Capture
- US-5.1: Export to Other Tools
- US-5.2: Backup & Sync
