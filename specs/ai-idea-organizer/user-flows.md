# Core User Flows

## Flow 1: Quick Idea Capture (Primary Flow)

This is the most critical flow - must be optimized for speed.

```
┌─────────────────────────────────────────────────────────────────┐
│                        QUICK CAPTURE                             │
└─────────────────────────────────────────────────────────────────┘

User has idea
      │
      ▼
┌─────────────┐
│ Open App /  │ ◄── Target: < 1 second
│ Tap Widget  │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Recording  │ ◄── Visual: pulsing mic, waveform
│   Active    │     Audio: subtle start chime
└──────┬──────┘
       │
       │ User speaks idea
       │
       ▼
┌─────────────┐
│ Stop (tap   │ ◄── Auto-stop after 2s silence OR manual tap
│ or silence) │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Transcribing│ ◄── Show progress (< 2 seconds)
│     ...     │
└──────┬──────┘
       │
       ▼
┌─────────────────────────────────────┐
│         Idea Captured!              │
│  ┌───────────────────────────────┐  │
│  │ "Add dark mode toggle to the │  │
│  │  settings page with system   │  │
│  │  preference detection"       │  │
│  └───────────────────────────────┘  │
│                                     │
│  📁 Auto-filed to: Mobile App       │
│                                     │
│  [Edit] [Change Project] [Done ✓]   │
└─────────────────────────────────────┘
       │
       │ User taps Done or swipes away
       │
       ▼
    ┌──────┐
    │ Done │ ◄── Total time: < 15 seconds
    └──────┘
```

### Key Optimizations:
- App remembers last state - opens ready to record
- No confirmation dialogs
- AI categorization happens async (shown after capture)
- "Done" is the default - user doesn't need to take action

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
