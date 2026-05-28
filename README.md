# vibe-tracker
Personal vibe coding project tracker — progress bars, daily logs &amp; agent prompts
# VibeTRACKER 🎯

> Personal vibe coding project OS — track ideas, progress, and daily updates in one place.

## What is this?

VibeTRACKER is a single-page dashboard for managing vibe coding projects. Built for people who have too many ideas scattered everywhere and need one place to organise, track, and share their coding journey.

**Live demo:** `https://DoloresHua.github.io/vibe-tracker`

---

## Features

### 📊 Overview Dashboard
- Stats summary (total projects, active, ideas, average progress)
- Progress snapshot — all projects in one bar chart
- Recent activity feed

### ◫ Project Management
- Add / edit / delete projects
- Status tags: Active, Paused, Idea, Done
- Color themes per project (purple, green, cyan, amber, pink)
- Tech stack tags
- Per-project progress percentage

### ✅ Goals & Milestones
- Checklist per project
- Toggle done/undone
- Add new goals inline from the detail panel

### 📝 Daily Update Log
- Date + project + update text + progress delta
- Full log table with delete support
- Recent updates shown on Overview page

### ⌘ Agent Prompts
- 3 standard Claude Code prompt templates:
  - **Progress Update** — structured daily update → returns JSON
  - **Project Kickoff** — idea → milestone breakdown
  - **Blocker Debug** — stuck? get unstuck
- One-click copy to clipboard

---

## Architecture

```
vibe-tracker/
└── index.html        ← entire app (single file)
```

Everything runs in one HTML file — no build step, no server, no dependencies.

### Tech Stack
- **HTML / CSS / JavaScript** — vanilla, no frameworks
- **localStorage** — all data persists in the browser
- **Google Fonts** — JetBrains Mono + Syne

### Data Structure

```javascript
// Stored in localStorage as JSON
{
  projects: [
    {
      id: "p_1234567890",
      name: "VibeTRACKER",
      desc: "Project description",
      status: "active",          // active | paused | idea | done
      color: "purple",           // purple | green | cyan | amber | pink
      progress: 40,              // 0-100
      tech: ["HTML", "CSS", "JavaScript"],
      goals: [
        { text: "Build overview dashboard", done: true },
        { text: "Deploy to GitHub Pages", done: false }
      ],
      createdAt: "2026-05-28T..."
    }
  ],
  logs: [
    {
      id: "l_1234567890",
      projectId: "p_1234567890",
      date: "2026-05-28",
      text: "Completed v1 features, verified all functions",
      progress: 40,
      next: "Deploy to GitHub Pages"
    }
  ]
}
```

### Page Structure

| Page | Route | Description |
|------|-------|-------------|
| Overview | `#overview` | Dashboard with stats + progress bars |
| Projects | `#projects` | All project cards + detail panel |
| Update Log | `#log` | Full log table |
| Agent Prompt | `#prompt` | Claude Code prompt templates |

---

## How to Use with Claude Code

1. Go to the **Agent Prompt** page
2. Copy the **Progress Update Prompt**
3. Paste into Claude Code or claude.ai
4. Fill in your project info
5. Get back a JSON response
6. Go to **+ Log Update** and fill in the details

### Standard Update Prompt

```
PROJECT_NAME: [your project]
TODAY_UPDATE: [what you did today]
BLOCKERS: [what's blocking you, or "none"]
NEXT_STEP: [what's next]
PROGRESS_PCT: [0-100]
GOALS_COMPLETED: [milestones done today]
```

---

## Roadmap

- [x] Project management (add / edit / delete)
- [x] Progress bars + milestone checklist
- [x] Daily update log
- [x] Agent prompt templates
- [x] Overview dashboard
- [ ] Tag system (tech tags + vibe tags)
- [ ] Blocker log
- [ ] JSON paste import from Claude Code
- [ ] Export to shareable static page
- [ ] Public profile toggle

---

## Deploy Your Own

1. Fork this repo
2. Go to **Settings → Pages**
3. Set source to **Deploy from branch → main**
4. Done — your tracker is live at `https://yourusername.github.io/vibe-tracker`

---

*Built with vibe. Tracked with VibeTRACKER.*
