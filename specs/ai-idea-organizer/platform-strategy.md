# Platform Strategy

## The Two-Mode Model

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   CAPTURE                              ORGANIZE                     │
│   (Mobile)                             (Desktop/Tablet)             │
│                                                                     │
│   ┌─────────────┐                     ┌─────────────────────────┐  │
│   │             │                     │                         │  │
│   │    📱       │      ───────►       │    💻  🖥️  📱(iPad)     │  │
│   │   iPhone    │       Sync          │    Mac / Web / Tablet   │  │
│   │             │                     │                         │  │
│   └─────────────┘                     └─────────────────────────┘  │
│                                                                     │
│   • One button                        • Full keyboard              │
│   • Voice only                        • Mouse/trackpad             │
│   • Zero decisions                    • Deep organization          │
│   • In the moment                     • Thoughtful review          │
│   • 10 seconds                        • 10 minutes                 │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Mobile App (iPhone) — "The Recorder"

### Single Purpose
Capture ideas. That's it.

### What It Does
- Record voice
- Confirm capture happened
- Background sync to cloud

### What It Does NOT Do
- ❌ Show transcriptions
- ❌ Browse ideas
- ❌ Organize projects
- ❌ Generate plans
- ❌ Edit anything
- ❌ Any complex UI

### The Entire Mobile App
```
┌─────────────────────────────────────┐
│                                     │
│                                     │
│                                     │
│              ◉                      │   ← Tap anywhere = record
│                                     │
│                                     │
│                                     │
│                                     │
│         12 ideas captured           │   ← Optional: count since last sync
│         ✓ All synced                │
└─────────────────────────────────────┘
```

That's it. One screen. One function. Pure capture.

### Optional: Minimal Review
If user *really* wants to check recent captures on mobile:
- Swipe up to see last 5 ideas (text only)
- Read-only, no editing
- Clear path back to record mode

But this is secondary. The phone is for capture.

---

## Desktop/Tablet App — "The Studio"

### Purpose
Review, organize, plan, and work with captured ideas.

### Where Organization Happens
- Full keyboard for editing
- Large screen for seeing connections
- Mouse/trackpad for drag-and-drop
- Time and focus for deep work

### Features (Desktop/Tablet Only)
| Feature | Why Desktop |
|---------|-------------|
| Browse all ideas | Need screen real estate |
| Edit transcriptions | Keyboard is faster |
| Organize into projects | Drag and drop |
| Generate project plans | Review and refine |
| Visual connections | Mind maps, graphs |
| Export to other tools | Complex workflows |

### The Experience
```
┌────────────────────────────────────────────────────────────────────────┐
│  Ideas Studio                                           [Capture 🎤]  │
├──────────────────┬─────────────────────────────────────────────────────┤
│                  │                                                     │
│  PROJECTS        │  Novel Project                                      │
│  ─────────       │  ──────────────────────────────────────────────    │
│  📖 Novel     12 │                                                     │
│  🏠 House      8 │  NEW IDEAS (3)                    [Generate Plan]   │
│  💼 Startup    5 │  ┌─────────────────────────────────────────────┐   │
│  📋 Unsorted   3 │  │ "The protagonist should discover the letter │   │
│                  │  │  in chapter 3, not chapter 5 — builds more  │   │
│                  │  │  tension before the confrontation"          │   │
│  + New Project   │  │                                     [▶ 0:12] │   │
│                  │  │  Yesterday 3:42 PM            [Edit] [Move]  │   │
│                  │  └─────────────────────────────────────────────┘   │
│                  │                                                     │
│                  │  ┌─────────────────────────────────────────────┐   │
│                  │  │ "Research Victorian mourning customs —      │   │
│                  │  │  could inform the aunt's behavior..."       │   │
│                  │  └─────────────────────────────────────────────┘   │
│                  │                                                     │
│                  │  PROJECT PLAN                                       │
│                  │  ─────────────                                      │
│                  │  □ Restructure chapter 3-5 arc                      │
│                  │  □ Research Victorian mourning customs              │
│                  │  □ Write the letter discovery scene                 │
│                  │                                                     │
└──────────────────┴─────────────────────────────────────────────────────┘
```

---

## Platform Rollout

### Phase 1: iPhone + Web
| Platform | Purpose | Priority |
|----------|---------|----------|
| iPhone | Capture | MVP |
| Web app | Organize | MVP |

Web app works on any device with a browser. Covers Mac, Windows, iPad, even Android for organization.

### Phase 2: Native Expansion
| Platform | Purpose | Priority |
|----------|---------|----------|
| iPad | Organize (optimized) | Post-MVP |
| Mac (native) | Organize (optimized) | Post-MVP |
| Apple Watch | Capture (wrist) | Post-MVP |

### Future Consideration
| Platform | Notes |
|----------|-------|
| Android | Capture app, if market demands |
| Android tablet | Could use web app |

---

## Sync Architecture

```
       iPhone                    Cloud                    Desktop/Web
    (Capture Only)              (Sync)                   (Full Features)
         │                        │                            │
         │  Upload audio ───────► │                            │
         │                        │ ◄─────── Fetch new ideas   │
         │                        │                            │
         │                        │  Transcribe ──────►        │
         │                        │                            │
         │                        │  AI Categorize ───►        │
         │                        │                            │
         │  Get sync status ◄──── │                            │
         │  (count, last sync)    │                            │
         │                        │                            │
         │                        │ ◄─── Edit, organize, plan  │
         │                        │                            │
```

Mobile only needs to:
1. Upload audio
2. Get confirmation it synced
3. Optionally get idea count

All the heavy lifting happens in the cloud and is consumed by the desktop experience.

---

## Why This Split Works

### For the User
- **Mobile**: Zero friction capture, like a cassette recorder
- **Desktop**: Full power when they're ready to think deeply

### For Development
- **Mobile**: Extremely simple app, fast to build
- **Desktop**: Web-first, works everywhere, iterate quickly

### For the Product
- **Focus**: Each platform does one thing brilliantly
- **No compromise**: Mobile isn't a bad desktop, desktop isn't a bad mobile

---

## Updated MVP Scope

### MVP = iPhone App + Web App

**iPhone App (Capture)**
- One-tap record from widget or app
- Audio upload
- "Captured" confirmation
- Sync status indicator
- That's ALL

**Web App (Organize)**
- View all ideas with transcriptions
- Play original audio
- Edit transcriptions
- Organize into projects (manual + AI suggested)
- Generate project plans
- Basic export (markdown, text)

**Both**
- Auth (Apple Sign-In)
- Real-time sync between platforms
