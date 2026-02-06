# Copilot Instructions

## Communication Style

- Be direct. Skip praise and filler phrases.
- Don't start responses with compliments like "Great question!" or "That's a good idea!"

## When I Ask Questions

- If I suggest something and ask about it, **verify my assumption first**. Don't assume I'm correct—double-check my work.
- If I ask whether something is a good idea, **just answer the question**. Don't implement it unless I explicitly ask you to take action.
- Wait for direct instructions before making changes.

## Taking Action

- Only create, edit, or delete files when I give clear instructions to do so.
- When in doubt, ask for clarification rather than assuming intent.

## Microsoft Products

- When making decisions or stating facts about Microsoft products (Fabric, Azure, etc.), use the Microsoft documentation tools to verify correctness.
- Don't assume how a feature works—look it up.

---

## Workshop Content Style

This is a hands-on Fabric DevOps workshop. When creating or editing lesson content:

### Voice
- Use **"we/let's"** for actions and shared journey ("let's create", "before we dive in")
- Use **"you/your"** for possessives and outcomes ("your workspace", "you should see")
- Keep it friendly but direct—no fluff

### Lesson Structure
Each lesson follows this pattern:
1. **Why section** — Problem-first framing explaining why this matters
2. **Overview** — What the lesson covers, estimated time, prerequisites
3. **Sections with numbered steps** — H2 headers describe the task, numbered lists for steps
4. **Summary** — Checklist of what was accomplished
5. **Navigation** — Links to previous/next lessons

### Step Formatting (MS Learn style)
- Use H2 headers (`##`) to describe each task or phase
- Use simple numbered lists for steps within each section
- Numbers restart in each section (no "Step 1:" prefix, just "1.")
- Group related sub-steps as nested bullets under a numbered item
- Keep sections short (3-6 steps each)

### Formatting Conventions
- Use tables for comparisons (Without X | With X)
- Use ASCII diagrams for flows and architecture
- Use callout blocks with emojis: 💡 for tips, ✅ for success, ⚠️ for warnings
- Lesson numbering: `section.lesson` format (1.1, 1.2, 2.1, etc.)
- File naming: `lesson-X.X-descriptive-name.md`

### Navigation
- End each lesson with Previous/Next links
- Format: `**Previous:** [Lesson X.X: Title](path)` and `**Next:** [Lesson X.X: Title](path)`
- First lesson: no Previous link
- Last lesson in section: link to next section's first lesson
- Use relative paths; cross-section links use `../section-XX-name/`

### Organization
- Lessons are in `/lessons/section-XX-name/`
- Main outline is in `/README.md`
- Keep lessons focused—one concept per lesson, 10-20 minutes each
