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
- Color themes per project (purple, green, blue, amber, pink)
- Tech stack tags
- Per-project progress percentage

### ✅ Goals & Milestones
- Checklist per project
- Toggle done/undone
- Add new goals inline from the detail panel

### 🗂 Task Board (per project)
- Lightweight Trello-style kanban inside each project
- Three columns: To Do / In Progress / Done
- Add and delete tasks inline

### 📝 Notes (per project)
- Free-form notes area inside each project detail panel
- Save anytime — technical decisions, ideas, references, anything
- Persists in localStorage

### 🔗 Links & Resources (per project)
- Add labeled links (GitHub repo, demo URL, references)
- Opens in new tab
- Delete links inline

### 📋 Daily Update Log
- Date + project + update text + progress delta
- Full log table with delete support
- Recent updates shown on Overview page

### ⌘ Agent Prompts
- 3 standard Claude Code prompt templates:
  - **Progress Update** — structured daily update → returns JSON
  - **Project Kickoff** — idea → milestone breakdown
  - **Blocker Debug** — stuck? get unstuck
- **Per-project prompt button** in each project detail panel — auto-fills project name and remaining goals, ready to paste into Claude Code

### 💾 Export / Import
- Export all data as a dated JSON backup file
- Import a backup to restore or sync data across devices
- Prevents data loss if browser cache is cleared
- Use to sync between local file and GitHub Pages

---

## Architecture

```
vibe-tracker/
├── index.html    ← entire app (single file)
└── README.md
```

Everything runs in one HTML file — no build step, no server, no dependencies.

### Tech Stack
- **HTML / CSS / JavaScript** — vanilla, no frameworks
- **localStorage** — all data persists in the browser
- **Google Fonts** — Inter

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
      color: "cyan",             // purple | green | cyan | amber | pink
      progress: 40,              // 0-100
      tech: ["HTML", "CSS", "JavaScript"],
      goals: [
        { text: "Build overview dashboard", done: true },
        { text: "Deploy to GitHub Pages", done: false }
      ],
      notes: "Free-form project notes...",
      links: [
        { label: "GitHub", url: "https://github.com/..." },
        { label: "Demo", url: "https://..." }
      ],
      kanban: {
        todo: ["Set up auth", "Design landing page"],
        doing: ["Build dashboard"],
        done: ["Project setup"]
      },
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

| Page | Description |
|------|-------------|
| Overview | Dashboard with stats + progress bars |
| Projects | All project cards + detail panel |
| Update Log | Full log table |
| Agent Prompt | Claude Code prompt templates |

---

## How to Use with Claude Code

### Option A — Quick update (claude.ai)
1. Open the project detail panel
2. Click **"Copy Update Prompt"** — auto-fills project name + remaining goals
3. Paste into claude.ai, fill in your update
4. Get back a JSON response
5. Go to **+ Log Update** and fill in the details

### Option B — From terminal (Claude Code)
Run Claude Code in your project folder and use the same prompt format. Paste the returned JSON into the Log Update form.

### Standard Update Prompt Format

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
- [x] Task board (kanban: To Do / In Progress / Done)
- [x] Notes per project
- [x] Links & resources per project
- [x] Daily update log
- [x] Agent prompt templates
- [x] Per-project prompt button (auto-fills project context)
- [x] Overview dashboard
- [x] Export / Import JSON backup
- [ ] Tag system (tech tags + vibe tags)
- [ ] Blocker log
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
