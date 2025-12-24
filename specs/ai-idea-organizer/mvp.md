# MVP Definition

## The Two-Platform MVP

> **Key Insight**: Mobile is for capture. Desktop is for organization.
> See `platform-strategy.md` for the full rationale.

### Goal
Validate that:
1. Users will capture ideas via voice when friction is near-zero
2. Users find value in AI-organized transcriptions and project plans
3. The two-platform model (capture on mobile, organize on desktop) works

### Success Criteria
- Users capture 5+ ideas in first week
- 70% of ideas captured are reviewed on desktop within 48 hours
- 50% of users generate at least one project plan
- User retention at day 7: >30%

---

## MVP = iPhone App + Web App

### iPhone App — "The Recorder"

**One purpose: Capture. That's all.**

| Feature | Details |
|---------|---------|
| Lock screen widget | Large tap target, starts recording immediately |
| One-tap record | App opens already recording |
| Auto-stop | Stops after 2s silence |
| Haptic feedback | Confirms recording started/stopped |
| Sync indicator | Shows "X ideas captured, all synced" |
| Background upload | Audio uploads even if app closed |

**That's the entire app.** No browsing. No editing. No organization.

#### iPhone App Screen (The ONLY Screen)
```
┌─────────────────────────────────────┐
│                                     │
│                                     │
│                                     │
│              ◉                      │   ← Tap = record
│                                     │     (or pulsing when recording)
│                                     │
│                                     │
│                                     │
│         12 ideas captured           │
│         ✓ All synced                │
└─────────────────────────────────────┘
```

---

### Web App — "The Studio"

**Full organization experience for desktop/tablet.**

| Feature | Details |
|---------|---------|
| Idea timeline | Chronological list with transcriptions |
| Audio playback | Listen to original recordings |
| Edit transcriptions | Fix errors with keyboard |
| Project organization | Manual + AI-suggested grouping |
| AI categorization | Auto-assigns ideas to projects |
| Project plan generation | Convert idea clusters to task lists |
| Search | Full-text across all ideas |
| Basic export | Markdown, plain text |

#### Web App Layout
```
┌─────────────────────────────────────────────────────────────────┐
│  Idea Studio                                                    │
├─────────────┬───────────────────────────────────────────────────┤
│ PROJECTS    │  Recent Ideas                                     │
│ ─────────── │  ─────────────────────────────────────────────    │
│ 📖 Novel    │  "The protagonist should discover..."    [▶][✎]  │
│ 🏠 House    │   → Novel Project                                 │
│ 💼 Startup  │                                                   │
│ 📋 Inbox    │  "Research Victorian mourning..."        [▶][✎]  │
│             │   → Novel Project                                 │
│             │                                                   │
│             │  [Generate Plan from Novel Project]               │
└─────────────┴───────────────────────────────────────────────────┘
```

---

### ❌ Out of Scope (Post-MVP)

| Feature | Why Deferred |
|---------|--------------|
| Offline transcription | Online-first; validate core loop |
| Mobile browsing | Desktop is for review |
| Mobile editing | Desktop is for editing |
| Apple Watch | Separate app development |
| Siri integration | Additional Apple review process |
| Collaboration | Single-user first |
| Third-party integrations | Manual export sufficient |
| Native Mac/iPad apps | Web app covers these initially |

---

## MVP Screens

### iPhone App: Just ONE Screen

The entire mobile app is one screen with two states:

#### State 1: Ready (Default)
```
┌─────────────────────────────┐
│                             │
│                             │
│                             │
│           ○                 │  ← Hollow circle
│                             │    Tap anywhere = record
│                             │
│                             │
│                             │
│      12 ideas · ✓ synced    │
└─────────────────────────────┘
```

#### State 2: Recording
```
┌─────────────────────────────┐
│                             │
│                             │
│                             │
│           ◉                 │  ← Solid red, pulsing
│                             │    Tap anywhere = stop
│                             │
│                             │
│                             │
│                             │
└─────────────────────────────┘
```

#### State 3: Captured (1 second, then back to Ready)
```
┌─────────────────────────────┐
│                             │
│                             │
│                             │
│           ✓                 │
│        Captured             │
│                             │
│                             │
│                             │
│                             │
└─────────────────────────────┘
```

**That's it. Three states, one screen, zero navigation.**

---

### Web App Screens

All browsing, editing, and organization happens here.

#### 1. Inbox / Timeline
```
┌────────────────────────────────────────────────────────────────────┐
│  Idea Studio                                    jordan@email.com ▼ │
├──────────────────┬─────────────────────────────────────────────────┤
│                  │                                                 │
│  📥 Inbox    (3) │  Inbox                              [Search 🔍] │
│                  │  ────────────────────────────────────────────   │
│  PROJECTS        │                                                 │
│  ─────────       │  ┌────────────────────────────────────────────┐ │
│  📖 Novel    12  │  │ "The protagonist should discover the..."  │ │
│  🏠 House     8  │  │                                            │ │
│  💼 Startup   5  │  │ ▶ 0:23  ·  Today 3:42 PM                   │ │
│                  │  │                                            │ │
│                  │  │ [Move to: Novel ▼]              [✎ Edit]   │ │
│  + New Project   │  └────────────────────────────────────────────┘ │
│                  │                                                 │
│                  │  ┌────────────────────────────────────────────┐ │
│                  │  │ "Call the electrician about the..."       │ │
│                  │  │                                            │ │
│                  │  │ ▶ 0:08  ·  Today 2:15 PM                   │ │
│                  │  │                                            │ │
│                  │  │ AI suggests: 🏠 House                      │ │
│                  │  │ [Accept] [Move to: ▼]            [✎ Edit]  │ │
│                  │  └────────────────────────────────────────────┘ │
│                  │                                                 │
└──────────────────┴─────────────────────────────────────────────────┘
```

#### 2. Project View
```
┌────────────────────────────────────────────────────────────────────┐
│  Idea Studio                                    jordan@email.com ▼ │
├──────────────────┬─────────────────────────────────────────────────┤
│                  │                                                 │
│  📥 Inbox    (3) │  📖 Novel                    [✨ Generate Plan] │
│                  │  ────────────────────────────────────────────   │
│  PROJECTS        │  12 ideas                                       │
│  ─────────       │                                                 │
│  📖 Novel  ← 12  │  IDEAS                                          │
│  🏠 House     8  │  ┌────────────────────────────────────────────┐ │
│  💼 Startup   5  │  │ "The protagonist should discover..."  ▶ ✎ │ │
│                  │  ├────────────────────────────────────────────┤ │
│                  │  │ "Research Victorian mourning..."      ▶ ✎ │ │
│  + New Project   │  ├────────────────────────────────────────────┤ │
│                  │  │ "Chapter 3 pacing feels slow..."      ▶ ✎ │ │
│                  │  └────────────────────────────────────────────┘ │
│                  │                                                 │
│                  │  GENERATED PLAN                                 │
│                  │  ─────────────                                  │
│                  │  No plan yet. Click "Generate Plan" above.      │
│                  │                                                 │
└──────────────────┴─────────────────────────────────────────────────┘
```

#### 3. Generated Plan View
```
┌────────────────────────────────────────────────────────────────────┐
│  Idea Studio                                    jordan@email.com ▼ │
├──────────────────┬─────────────────────────────────────────────────┤
│                  │                                                 │
│  📥 Inbox    (0) │  📖 Novel — Project Plan           [Regenerate] │
│                  │  ────────────────────────────────────────────   │
│  PROJECTS        │                                                 │
│  ─────────       │  PHASE 1: Story Structure                       │
│  📖 Novel    12  │  □ Restructure discovery scene to chapter 3     │
│  🏠 House     8  │    └─ from: "The protagonist should discover.." │
│  💼 Startup   5  │  □ Adjust pacing in chapters 3-5                │
│                  │    └─ from: "Chapter 3 pacing feels slow..."    │
│                  │                                                 │
│  + New Project   │  PHASE 2: Research                              │
│                  │  □ Research Victorian mourning customs          │
│                  │    └─ from: "Research Victorian mourning..."    │
│                  │  □ Find primary sources for period details      │
│                  │                                                 │
│                  │  PHASE 3: Writing                               │
│                  │  □ Draft new chapter 3 discovery scene          │
│                  │  □ Revise aunt character based on research      │
│                  │                                                 │
│                  │  [Export as Markdown]  [Copy to Clipboard]      │
│                  │                                                 │
└──────────────────┴─────────────────────────────────────────────────┘
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

### v1.1
- Offline voice capture
- iCloud sync across devices

### v1.2
- Siri Shortcuts integration
- Export to Reminders
- AI refinement suggestions

### v2.0
- Apple Watch capture
- Collaboration (share projects)
- Third-party integrations (Notion, Linear, etc.)
