# Core User Flows

> **UX Philosophy**: The Cassette Recorder
> See `ux-philosophy.md` for the full vision. Capture must feel like pressing
> record on a handheld recorder - one action, no feedback required, trust the machine.

## Flow 1: Idea Capture (Primary Flow) — "The Cassette Recorder"

This is the most critical flow. Every millisecond of friction is the enemy.

```
┌─────────────────────────────────────────────────────────────────┐
│                   THE CASSETTE RECORDER FLOW                     │
└─────────────────────────────────────────────────────────────────┘

User has idea
      │
      ▼
┌─────────────┐
│ Tap Widget  │ ◄── Lock screen widget, large target
│ (< 1 sec)   │     OR open app (opens ALREADY recording)
└──────┬──────┘
       │
       │ 🔴 IMMEDIATELY RECORDING
       │ Haptic: single firm tap
       ▼
┌─────────────┐
│             │
│      ◉      │ ◄── Just a red pulsing dot
│             │     Nothing else on screen
│             │
└──────┬──────┘
       │
       │ User speaks idea
       │
       ▼
┌─────────────┐
│  Auto-stop  │ ◄── 2 seconds of silence = done
│  (or tap)   │     Haptic: double light tap
└──────┬──────┘
       │
       ▼
┌─────────────┐
│      ✓      │ ◄── Brief flash (1 second)
│   Captured  │     Then screen fades / closes
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Phone back  │ ◄── NO review, NO confirmation
│ in pocket   │     NO decisions required
└─────────────┘

TOTAL INTERACTION: < 10 seconds (plus speaking time)
```

### What Happens in Background (User Never Sees):
- Audio uploaded
- Transcription processed
- AI categorizes into project
- Synced to cloud

### What Does NOT Happen:
- ❌ "Which project?" dialog
- ❌ Transcription review
- ❌ "Save" button
- ❌ Any confirmation
- ❌ Any choice whatsoever

---

## Flow 2: Browse & Organize Ideas

```
┌─────────────────────────────────────────────────────────────────┐
│                      BROWSE IDEAS                                │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────┐
│  Home Screen (Timeline View)        │
│  ─────────────────────────────────  │
│                                     │
│  🎤 [Record New Idea]               │
│                                     │
│  TODAY                              │
│  ├─ "Dark mode toggle..." → 📱 App  │
│  ├─ "User onboarding..." → 📱 App   │
│  └─ "Call dentist..." → 📋 Personal │
│                                     │
│  YESTERDAY                          │
│  ├─ "Blog post about..." → ✍️ Blog  │
│  └─ "API rate limiting" → 📱 App    │
│                                     │
│  [Timeline] [Projects] [Search]     │
└─────────────────────────────────────┘
       │
       │ Tap on project
       ▼
┌─────────────────────────────────────┐
│  📱 Mobile App Project              │
│  ─────────────────────────────────  │
│                                     │
│  12 ideas · Last updated 2h ago     │
│                                     │
│  [Generate Plan ✨]                 │
│                                     │
│  IDEAS                              │
│  ├─ Dark mode toggle...             │
│  ├─ User onboarding flow...         │
│  ├─ API rate limiting...            │
│  └─ Push notifications...           │
│                                     │
│  + Add idea to this project         │
└─────────────────────────────────────┘
```

---

## Flow 3: Generate Project Plan

```
┌─────────────────────────────────────────────────────────────────┐
│                    GENERATE PROJECT PLAN                         │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────┐
│  📱 Mobile App Project              │
│  ─────────────────────────────────  │
│  12 ideas                           │
│                                     │
│  [Generate Plan ✨] ◄── User taps   │
└──────────┬──────────────────────────┘
           │
           ▼
┌─────────────────────────────────────┐
│  🤖 Analyzing your ideas...         │
│                                     │
│  ████████████░░░░░░░░ 60%           │
│                                     │
│  • Identifying themes               │
│  • Grouping related items           │
│  • Suggesting order                 │
└──────────┬──────────────────────────┘
           │ (2-5 seconds)
           ▼
┌─────────────────────────────────────┐
│  📱 Mobile App - Project Plan       │
│  ─────────────────────────────────  │
│                                     │
│  PHASE 1: Core Features             │
│  ──────────────────────             │
│  □ Set up push notification service │
│    └─ From: "Push notifications..." │
│  □ Implement notification UI        │
│  □ Add user preferences             │
│                                     │
│  PHASE 2: User Experience           │
│  ──────────────────────             │
│  □ Design onboarding flow           │
│    └─ From: "User onboarding..."    │
│  □ Build onboarding screens         │
│  □ Add dark mode support            │
│    └─ From: "Dark mode toggle..."   │
│                                     │
│  PHASE 3: Polish                    │
│  ──────────────────────             │
│  □ API rate limiting                │
│  □ Error handling improvements      │
│                                     │
│  [Edit Plan] [Export] [Start →]     │
└─────────────────────────────────────┘
```

### AI Plan Generation Logic:
1. Extract actionable items from each idea
2. Identify dependencies (X must come before Y)
3. Group into logical phases
4. Order by priority within phases
5. Link tasks back to source ideas

---

## Flow 4: Expand & Refine an Idea

```
┌─────────────────────────────────────────────────────────────────┐
│                      REFINE IDEA                                 │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────┐
│  Idea Details                       │
│  ─────────────────────────────────  │
│                                     │
│  "Add dark mode toggle to the       │
│   settings page with system         │
│   preference detection"             │
│                                     │
│  🔊 [Play original audio]           │
│                                     │
│  📁 Project: Mobile App             │
│  📅 Captured: Today, 2:34 PM        │
│                                     │
│  ─────────────────────────────────  │
│  🤖 AI INSIGHTS                     │
│                                     │
│  This idea involves:                │
│  • UI component (toggle switch)     │
│  • System integration (OS prefs)    │
│  • State persistence                │
│                                     │
│  Related ideas in this project:     │
│  • "User preferences screen..."     │
│  • "Theming system for..."          │
│                                     │
│  [Break into tasks] [Edit] [Delete] │
└─────────────────────────────────────┘
           │
           │ User taps "Break into tasks"
           ▼
┌─────────────────────────────────────┐
│  Tasks from this idea:              │
│                                     │
│  □ Create DarkModeToggle component  │
│  □ Add toggle to Settings screen    │
│  □ Detect system dark mode pref     │
│  □ Persist user preference locally  │
│  □ Apply theme across app           │
│                                     │
│  [Add to plan] [Edit tasks]         │
└─────────────────────────────────────┘
```

---

## Flow 5: First-Time User Onboarding

```
┌─────────────────────────────────────────────────────────────────┐
│                      ONBOARDING                                  │
└─────────────────────────────────────────────────────────────────┘

Screen 1: Welcome
┌─────────────────────────────────────┐
│                                     │
│         🎤                          │
│                                     │
│    Capture ideas instantly          │
│    with your voice                  │
│                                     │
│    AI organizes them into           │
│    actionable project plans         │
│                                     │
│         [Get Started]               │
│                                     │
└─────────────────────────────────────┘

Screen 2: Permissions
┌─────────────────────────────────────┐
│                                     │
│    We need microphone access        │
│    to capture your ideas            │
│                                     │
│    🎤 Microphone                    │
│    Required for voice capture       │
│                                     │
│    🔔 Notifications (optional)      │
│    Get reminders to review ideas    │
│                                     │
│         [Allow Microphone]          │
│                                     │
└─────────────────────────────────────┘

Screen 3: Try It
┌─────────────────────────────────────┐
│                                     │
│    Let's capture your first idea!   │
│                                     │
│    Tap and speak any idea           │
│    you've been thinking about       │
│                                     │
│         🎤                          │
│      [Tap to record]                │
│                                     │
│         Skip for now →              │
│                                     │
└─────────────────────────────────────┘

Screen 4: Success
┌─────────────────────────────────────┐
│                                     │
│         ✓                           │
│                                     │
│    Perfect! Your idea is saved      │
│                                     │
│    "Build an app that..."           │
│                                     │
│    As you add more ideas, AI will   │
│    organize them into projects      │
│                                     │
│         [Start Using App]           │
│                                     │
└─────────────────────────────────────┘
```

---

## State Diagram: Idea Lifecycle

```
                    ┌──────────┐
                    │ Captured │
                    └────┬─────┘
                         │
                         ▼
                  ┌──────────────┐
                  │ Transcribed  │
                  └──────┬───────┘
                         │
            ┌────────────┼────────────┐
            │            │            │
            ▼            ▼            ▼
      ┌──────────┐ ┌──────────┐ ┌──────────┐
      │ Orphaned │ │ Assigned │ │  Merged  │
      │ (no proj)│ │(in proj) │ │(combined)│
      └────┬─────┘ └────┬─────┘ └──────────┘
           │            │
           │            ▼
           │      ┌──────────┐
           └─────►│ In Plan  │
                  └────┬─────┘
                       │
                       ▼
                  ┌──────────┐
                  │ Completed│
                  └──────────┘
```
