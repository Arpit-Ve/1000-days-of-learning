# ⚡ GitHub Activity Generator — Autonomous Agent

> **Zero-effort, fully automated GitHub contribution graph maintenance.**
> This agent ensures your GitHub profile has green squares every single day of the year — no manual work needed.

---

## 🎯 What Does This Agent Do?

This is a **background agent** that runs silently on your PC. Every day, it automatically:

- Creates **5 to 10 commits** with randomized timing
- Pushes real, meaningful content to your GitHub repository
- Keeps your **contribution graph green** — 365 days a year

You don't open any app, click any button, or even think about it. It just works.

---

## 🔄 How It Works — The Daily Cycle

### Step 1: Midnight — Planning Phase

```
🕛 12:00 AM → Agent wakes up
   ↓
   Picks a random number between 5 and 10 (e.g., 7)
   ↓
   Generates 7 random times during your active hours (9 AM - 11 PM)
   Example: 9:12 AM, 10:45 AM, 1:30 PM, 3:15 PM, 5:50 PM, 7:22 PM, 9:48 PM
   ↓
   Sets timers for each commit → Goes back to sleep
```

### Step 2: Throughout the Day — Execution Phase

```
⏰ Timer fires (e.g., 9:12 AM)
   ↓
   Picks a random file to update (learning journal, dev log, etc.)
   ↓
   Generates realistic developer content
   ↓
   Commits with a natural message like "docs: update learning journal"
   ↓
   Pushes to GitHub → 🟩 Green Square!
   ↓
   Goes back to sleep until next timer
```

### Step 3: Before Midnight — Safety Net

```
🚨 11:00 PM → "Did I commit at least once today?"
                 Yes → All good ✅
                 No  → EMERGENCY COMMIT NOW!

🚨 11:30 PM → Second safety check

🚨 11:50 PM → FINAL check — last chance before midnight
```

**Triple-check system makes it impossible to miss a day.**

### Step 4: If Something Goes Wrong

```
❌ Commit fails (no internet, GitHub down, etc.)
   ↓
   Wait 30 seconds → Retry
   ↓
   Still failing? Wait 60 seconds → Retry again
   ↓
   Up to 5 retries per commit
   ↓
   Emergency checks at 11 PM will catch any missed day
```

---

## 📁 What Content Does It Create?

The agent creates and updates **7 different types of files** in your repository:

| File | Content |
|------|---------|
| `docs/learning-journal.md` | Notes on tech topics (APIs, Docker, databases, etc.) |
| `docs/dev-log.md` | Daily development activity logs |
| `docs/productivity-insights.md` | Developer productivity tips |
| `docs/progress-tracker.md` | Skill progress bars with percentages |
| `docs/project-ideas.md` | Brainstorming log with feature lists |
| `docs/tech-stack.md` | Technology evaluations and reviews |
| `docs/weekly-summary.md` | Weekly activity recaps |
| `stats.json` | Auto-generated project statistics |

All content looks like a **real developer's documentation** — not spam or empty commits.

---

## 🕵️ Anti-Detection — Looks Like a Real Human

| What's Randomized | Why |
|-------------------|-----|
| Commit count (5–10/day) | No fixed daily pattern |
| Commit times | Not at the same time every day |
| Seconds offset | Doesn't commit at exact minutes (e.g., 9:12:34 AM) |
| File selection | Doesn't modify the same file repeatedly |
| Commit messages | 25+ templates, avoids recent duplicates |
| Content topics | 40+ topics, varied each time |

---

## 💻 Running in Background

The agent uses **PM2** (a process manager) to run silently:

- ✅ **No terminal window needed** — runs completely in the background
- ✅ **Survives PC restarts** — auto-starts when you log in
- ✅ **Auto-recovers from crashes** — PM2 restarts it immediately
- ✅ **Zero CPU usage** — sleeps between commits, uses <1% CPU

### PC Restart Flow:

```
PC shuts down → Agent stops
   ↓
PC turns back on → You log in
   ↓
PM2 auto-resurrects → Agent starts
   ↓
Schedules today's commits → Business as usual ✅
```

---

## ⚙️ Configuration

All settings are in the `.env` file:

| Setting | Value | Meaning |
|---------|-------|---------|
| Repository | `1000-days-of-learning` | Only this repo gets commits |
| Branch | `main` | Commits go to main branch |
| Timezone | `Asia/Kolkata` | IST timezone |
| Active Hours | 9:00 AM - 11:00 PM | Commits only during waking hours |
| Min Commits | 5 | At least 5 commits per day |
| Max Commits | 10 | At most 10 commits per day |
| Emergency Hour | 11:00 PM | Safety check time |
| Retries | 5 | Retry failed commits up to 5 times |

---

## 📊 Monitoring

### Check Status (Terminal):
```bash
npm run status
```

Shows your current streak, total commits, and recent 7-day activity.

### Check PM2 (Terminal):
```bash
pm2 status              # Is agent running?
pm2 logs github-activity  # See live logs
```

### Dashboard (Browser):
```bash
npm run dashboard
# Opens at http://localhost:3456
```

Visual dashboard with contribution grid, stats, and live logs.

---

## 🟩 GitHub Contribution Graph

**How GitHub counts contributions:**

- GitHub's green chart on your profile = commits across **ALL your repos**
- This agent adds commits to `1000-days-of-learning` only
- Your manual work on other repos **also counts**
- Everything adds up together into one green chart

**Result:** Every day has at least 5–10 green squares from the agent, plus whatever you do manually.

---

## ⚠️ Important Notes

1. **PC must be turned on** at least once per day — the agent runs on your local machine
2. **Internet required** — needs to push commits to GitHub
3. **Don't delete the `repo/` folder** — that's the local clone the agent works with
4. **Regenerate your GitHub token** periodically for security

---

## 🛠️ Useful Commands

| Command | What It Does |
|---------|-------------|
| `pm2 status` | Check if agent is running |
| `pm2 logs github-activity` | View real-time logs |
| `pm2 restart github-activity` | Restart the agent |
| `pm2 stop github-activity` | Stop the agent |
| `pm2 start github-activity` | Start the agent |
| `npm run status` | View streak and stats |
| `npm test` | Make a single test commit |
| `npm run dashboard` | Open monitoring dashboard |

---

## 📋 Project Structure

```
github commits/
├── .env                 ← Your configuration (token, repo, etc.)
├── .env.example         ← Template for new setups
├── package.json         ← Dependencies and scripts
├── start-agent.bat      ← Windows auto-start script
├── README.md            ← This file
├── src/
│   ├── index.js         ← Main entry point
│   ├── config.js        ← Loads .env settings
│   ├── scheduler.js     ← Schedules daily commits
│   ├── commit-engine.js ← Git clone, commit, push logic
│   ├── content-generator.js ← Creates file content
│   ├── history.js       ← Tracks commit history
│   ├── logger.js        ← Logging system
│   ├── setup.js         ← Setup wizard
│   ├── test-run.js      ← Test commit script
│   ├── status.js        ← CLI status reporter
│   └── dashboard/       ← Monitoring web dashboard
├── repo/                ← Local clone of your GitHub repo
├── data/                ← Commit history JSON
└── logs/                ← Daily log files
```

---

**Built with ❤️ — Set it once, green squares forever.**
