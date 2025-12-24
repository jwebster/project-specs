# AI Idea Organizer

> A voice-first iPhone app that captures ideas and uses AI to organize them into actionable project plans.

## Status: Discovery

## Name Candidates

| Name | Vibe |
|------|------|
| **Murmur** | Intimate, talking to yourself, muttering ideas |
| **Spoke** | Past tense - it's already captured, no friction |
| **Spark** | The flash of inspiration you're trying to catch |
| **Dictate** | Classic, professional, the act itself |
| **Vox** | Voice, Latin, timeless |

---

## Vision

Capture fleeting ideas effortlessly through voice, and let AI transform scattered thoughts into structured, actionable project plans.

## Core Concepts

### Voice-First Idea Capture
- **Quick capture**: Speak your idea anytime, anywhere
- **Natural language**: No rigid format required - just talk
- **Context preservation**: Capture the full thought, not just keywords

### AI-Powered Organization
- **Automatic categorization**: Ideas grouped by theme/project
- **Structure extraction**: Convert rambling thoughts into clear items
- **Project plan generation**: Transform related ideas into actionable plans

### Project Plan Output
- **Task breakdown**: Ideas become tasks with clear scope
- **Logical ordering**: AI suggests task sequences and dependencies
- **Priority suggestions**: What to tackle first based on impact/effort

---

## Open Questions

### Voice & Capture Experience

1. **Activation method**: Tap-to-record, always listening, or widget/Siri integration?
2. **Recording length**: Quick snippets (< 1 min) or extended brainstorming sessions?
3. **Offline support**: Should voice capture work without internet? (affects technology choices)
4. **Multi-language**: English only, or multiple languages?

### AI Organization

5. **Organization scope**:
   - Simple grouping (like folders)?
   - Full project plans with tasks, milestones, timelines?
   - Mind maps or visual hierarchies?

6. **AI interaction style**:
   - Fully automatic (AI decides everything)?
   - Collaborative (AI suggests, you confirm)?
   - AI asks clarifying questions to refine understanding?

7. **Learning**: Should AI learn your patterns and preferences over time?

### Project Types & Domain

8. **Target use cases**:
   - Software/product development?
   - Creative projects (writing, art, music)?
   - Business planning?
   - Personal goals and life organization?
   - All of the above?

9. **Project methodology**: Free-form, or support specific methods (Agile, GTD, etc.)?

### Data & Privacy

10. **Processing location**:
    - Cloud AI (more powerful, requires internet)?
    - On-device AI (private, works offline, less capable)?
    - Hybrid approach?

11. **Data storage**: Local only, or cloud sync across devices?

12. **Collaboration**: Single user only, or share projects with others?

### Integrations

13. **Export/sync with other tools**:
    - Project management (Jira, Asana, Trello, Linear)?
    - Notes apps (Apple Notes, Notion, Obsidian)?
    - Calendar apps?

14. **Apple ecosystem**: Deep integration with Siri, Shortcuts, Widgets, Apple Watch?

### Business Model

15. **Monetization approach**:
    - Free with premium features?
    - One-time purchase?
    - Subscription for AI features?

---

## Technical Considerations

### Voice Recognition Options
| Approach | Pros | Cons |
|----------|------|------|
| Apple Speech Framework | Free, on-device, private | Less accurate for complex speech |
| Whisper (on-device) | Accurate, private, offline | Battery/processing intensive |
| Cloud API (OpenAI, Deepgram) | Most accurate | Requires internet, ongoing costs |

### AI Processing Options
| Approach | Pros | Cons |
|----------|------|------|
| On-device (Core ML) | Private, offline, fast | Limited capability |
| Cloud LLM (GPT-4, Claude) | Powerful, flexible | Latency, cost, privacy concerns |
| Hybrid | Best of both worlds | Complex to implement |

### Key Technical Decisions Needed
- Native Swift vs React Native/Flutter
- Local-first vs cloud-first architecture
- Real-time processing vs batch organization

---

## Competitive Landscape

### Voice Note Apps
- **Otter.ai**: Transcription focused, less organization
- **Voice Memos**: Simple recording, no AI
- **Whisper Memos**: Transcription + basic summary

### Idea/Note Organization
- **Notion AI**: Powerful but complex, not voice-first
- **Mem.ai**: AI organization, but text-focused
- **Napkin.ai**: Visual idea connection

### Gap in Market
No app currently combines **voice-first capture** with **AI project plan generation**. Most are either:
- Voice → Text transcription only
- Text → AI organization (not voice-first)

---

## Initial Feature Ideas

### MVP (Phase 1)
- [ ] Voice capture with transcription
- [ ] Automatic idea tagging/categorization
- [ ] View and edit transcribed ideas
- [ ] Basic project grouping

### Enhanced AI (Phase 2)
- [ ] Generate project plans from idea clusters
- [ ] Task breakdown with suggested order
- [ ] AI-generated summaries of projects

### Power Features (Phase 3)
- [ ] Integrations with external tools
- [ ] Collaboration features
- [ ] Apple Watch quick capture
- [ ] Siri Shortcuts integration

---

## Next Steps

1. Answer the open questions above to refine scope
2. Define target user persona
3. Create detailed user stories
4. Design core user flows
5. Technical architecture decisions

