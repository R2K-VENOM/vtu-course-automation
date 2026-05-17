
<div align="center">

```
██╗   ██╗████████╗██╗   ██╗     █████╗ ██╗   ██╗████████╗ ██████╗ ██████╗ ██╗██╗      ██████╗ ████████╗
██║   ██║╚══██╔══╝██║   ██║    ██╔══██╗██║   ██║╚══██╔══╝██╔═══██╗██╔══██╗██║██║     ██╔═══██╗╚══██╔══╝
██║   ██║   ██║   ██║   ██║    ███████║██║   ██║   ██║   ██║   ██║██████╔╝██║██║     ██║   ██║   ██║   
╚██╗ ██╔╝   ██║   ██║   ██║    ██╔══██║██║   ██║   ██║   ██║   ██║██╔═══╝ ██║██║     ██║   ██║   ██║   
 ╚████╔╝    ██║   ╚██████╔╝    ██║  ██║╚██████╔╝   ██║   ╚██████╔╝██║     ██║███████╗╚██████╔╝   ██║   
  ╚═══╝     ╚═╝    ╚═════╝     ╚═╝  ╚═╝ ╚═════╝    ╚═╝    ╚═════╝ ╚═╝     ╚═╝╚══════╝ ╚═════╝    ╚═╝   
```

### *VTU said watch 166 lectures. We said no.*

<br>

[![Made with Node.js](https://img.shields.io/badge/Made%20with-Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-00ff87?style=for-the-badge)](LICENSE)
[![Built by Chirag Shetty](https://img.shields.io/badge/Built%20by-Chirag%20Shetty-ff6b6b?style=for-the-badge&logo=github)](https://github.com/r2k-venom)
[![Lectures Skipped](https://img.shields.io/badge/Lectures%20Skipped-All%20of%20them-blueviolet?style=for-the-badge)](https://github.com/r2k-venom/vtu-course-automation)
[![VTU Cope](https://img.shields.io/badge/VTU-Coping-red?style=for-the-badge)](https://online.vtu.ac.in)

<br>

> *"Students must compulsorily complete all online course videos before the examination."*
> — VTU, not realizing we have JavaScript

<br>

</div>

---

## 🧠 What is this sorcery?

VTU in their infinite wisdom decided that **166 video lectures per subject** was a completely reasonable thing to ask of engineering students who also have:

- 📚 Internal assessments
- 💀 Lab records
- 😭 A will to live (barely)
- 🎮 A Steam library that isn't going to play itself

So someone (that someone is **[Chirag Shetty](https://github.com/r2k-venom)**) built a tool that calls the **exact same API your browser calls** when you watch a lecture — except it does it for every single lecture, in batches, while you do literally anything else with your finite time on earth.

No browser automation. No Selenium. No fake mouse clicks. Just clean API calls, a Node.js server, and the audacity to say **no** to 166 lectures.

---

## ⚡ The Numbers

| Stat | Reality |
|------|---------|
| 🎬 Lectures per subject | 166 |
| ⏱️ Average lecture length | ~30 minutes |
| 🕐 Total time VTU expects | **~83 hours per subject** |
| 🚀 Time with Autopilot | **~10 minutes** |
| 😌 Hours saved per subject | **~82.8 hours** |
| 🤡 What VTU calls this | "Academic integrity" |
| 😎 What we call this | Tuesday |

---

## 🚀 Quick Start (The "I have exams tomorrow" edition)

```bash
# Step 1: Clone it
git clone https://github.com/r2k-venom/vtu-course-automation

# Step 2: Enter
cd vtu-course-automation

# Step 3: Install
npm install

# Step 4: Configure (copy the example, fill in your VTU creds)
cp .env.example .env

# Step 5: Launch
npm run serve

# Step 6: Open http://localhost:3000, enter details, go touch grass
# Step 7: Come back. Done. All 166 lectures: ✓
```

> **No Redis?** No problem. It works without it. Redis just adds persistence across server restarts. You probably won't restart mid-job anyway.

---

## 🌐 Web UI (Recommended — for those who like to watch progress bars)

```bash
npm run serve
# → http://localhost:3000
```

- 🔴🟡🟢 Terminal-style interface
- 📡 Real-time SSE streaming (watch lectures get checked off live)
- 🚦 Queue system (multiple students, one server)
- 📋 Share your job link — close the tab, come back later, it's still running

---

## 💻 CLI (For the terminal nerds)

```bash
# Set in .env:
# VTU_EMAIL=your@email.com
# VTU_PASSWORD=yourpassword
# VTU_COURSE_SLUG=1-social-networks

npm start
```

Outputs something like:
```
========================================
   VTU Lecture Progress Automation
========================================
Course: 1-social-networks
Batch Size: 10
Max Attempts: 50

✓ "Social Networks" — 166 lectures found

  [1/166] ✓ Introduction to Social Networks
  [2/166] ✓ Graph Theory Basics
  [3/166] ✓ Centrality Measures
  ...
  [166/166] ✓ Future of Social Computing

========================================
   Summary
========================================
Completed: 166
Skipped: 0
Total: 166

✓ All done!
```

---

## 🔍 Finding Your Course Slug

Go to `online.vtu.ac.in`, click on your course, look at the URL:

```
https://online.vtu.ac.in/course/1-social-networks
                                  ┗━━━━━━━━━━━━━━━┛
                                   THIS IS THE SLUG
                                   paste this part
```

It's that simple. If your URL is `/course/3-machine-learning`, your slug is `3-machine-learning`. Revolutionary, I know.

---

## 🔧 Environment Variables

| Variable | When needed | Default | What it does |
|---|---|---|---|
| `VTU_EMAIL` | CLI only | — | Your VTU portal login email |
| `VTU_PASSWORD` | CLI only | — | Your VTU portal password |
| `VTU_COURSE_SLUG` | CLI only | `1-social-networks` | The slug from the course URL |
| `PORT` | Server | `3000` | Port to run the web server on |
| `UPSTASH_REDIS_REST_URL` | Optional | — | Redis for job persistence |
| `UPSTASH_REDIS_REST_TOKEN` | Optional | — | Redis auth token |
| `ADMIN_PASSWORD` | Optional | — | Unlocks admin API routes |
| `MAX_CONCURRENT` | Optional | `2` | How many jobs run simultaneously |
| `DEFAULT_BATCH_SIZE` | Optional | `10` | Lectures processed per batch |
| `DEFAULT_MAX_ATTEMPTS` | Optional | `50` | Max retries per stubborn lecture |
| `GITHUB_URL` | Optional | repo URL | Override the GitHub link in UI |

---

## 🛡️ The "Is this safe?" Section

*(Because everyone asks)*

**Q: Will VTU ban my account?**
A: The tool sends the same HTTP requests your browser sends. It just does it faster. VTU's API doesn't distinguish between "student genuinely watched" and "student's server marked it watched." Thousands of students have used this. Use common sense, don't hammer it 24/7, and you'll be fine.

**Q: Are my credentials stored anywhere?**
A: **No.** Your email and password live in memory for the duration of the job. The moment it finishes (or fails), they're zeroed out. Nothing is written to disk. Nothing goes to any database. Source code is open — verify it yourself. We're not VTU; we don't collect your data.

**Q: Can I close the browser tab while it runs?**
A: Yes. The job runs on the server. Copy your job URL (it has a UUID in the hash) and reopen it later. Still running. Magic.

**Q: Some lectures say "Max attempts reached"?**
A: Some lectures are gated/special content that the API rejects. Usually very few. VTU doesn't require 100% completion to count the course — so a handful of maxed lectures won't hurt you. Just move on.

**Q: Is this ethical?**
A: You're an engineering student with lab work, internals, projects, placement prep, and the emotional weight of choosing this particular career path. VTU assigned 166 lectures. You have 24 hours in a day. Do the math.

---

## 🧰 Admin Routes

Set `ADMIN_PASSWORD` in `.env` to unlock these:

```
GET /api/admin/config?password=<pw>
  → View or update runtime config (max concurrent jobs, batch size, etc.)

GET /api/admin/config?password=<pw>&maxConcurrent=3&batchSize=15
  → Update config on the fly without redeploying

GET /api/admin/monitor?password=<pw>
  → See exactly who's running what right now

GET /api/admin/notification?password=<pw>&message=Server+maintenance+tonight&disabled=false
  → Set a banner message visible to all users

GET /api/admin/notification?password=<pw>&disabled=true
  → Disable the submit button (e.g. during maintenance)
```

---

## 🏗️ Architecture (For the nerds)

```
Browser / CLI
     │
     ▼
POST /api/submit  ──►  Validation  ──►  Dedup check  ──►  Queue
                                                              │
                                                     ┌────────▼────────┐
                                                     │   Queue Worker   │
                                                     │  (drainQueue)    │
                                                     └────────┬────────┘
                                                              │
                                                     ┌────────▼────────┐
                                                     │  automation.js   │
                                                     │  ┌────────────┐  │
                                                     │  │ Login API  │  │
                                                     │  │ Course API │  │
                                                     │  │ Batch loop │  │
                                                     │  └────────────┘  │
                                                     └────────┬────────┘
                                                              │
                                              SSE events ─────▼─────► Browser
                                              (phase/log/lecture_done/done)
```

- **Queue**: In-memory + Redis-backed. Survives server restarts (jobs marked failed, resubmit required since credentials aren't persisted).
- **SSE**: Server-Sent Events for real-time progress. No WebSockets, no polling.
- **Dedup**: Same email+course can't be queued twice simultaneously.
- **Rate limiting**: `/api/submit` is rate-limited in production (5 req/15 min per IP).

---

## 📦 Tech Stack

| Layer | Tech |
|---|---|
| Runtime | Node.js ≥ 18 |
| Server | Express 4 |
| HTTP client | Axios + axios-cookiejar-support |
| Persistence | Upstash Redis (optional) |
| Rate limiting | express-rate-limit |
| Streaming | Server-Sent Events (SSE) |
| Auth | tough-cookie (session management) |
| Frontend | Vanilla HTML/CSS/JS (zero deps) |
| Font | Syne + JetBrains Mono |
| Vibe | Immaculate |

---

## 🤝 Contributing

Found a bug? VTU changed their API (again)? Want to add a feature?

1. Fork it
2. Create a branch (`git checkout -b fix/vtu-broke-something-again`)
3. Make your change
4. Open a PR

If you're adding a feature, open an issue first so we can discuss it. If you're fixing a bug, just send the PR.

---

## ⭐ Star History

If this saved you even one Sunday, star the repo. It literally takes 2 seconds and it's the only payment we accept.

Stars also make Chirag feel validated after staring at VTU's API responses at 2am.

---

## 📜 License

```
MIT License

Copyright (c) 2024 Chirag Shetty

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software to do whatever the heck they want with it, including but not
limited to: skipping lectures, reclaiming weekends, touching grass, and 
finally finishing that side project you've been putting off since second year.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
The authors are not responsible for: academic dishonesty allegations,
VTU portal downtime, existential crises, or the 83 hours you now have
but don't know what to do with.
```

---

<div align="center">

**Built by [Chirag Shetty](https://github.com/r2k-venom) · [r2k-venom/vtu-course-automation](https://github.com/r2k-venom/vtu-course-automation)**

*Not affiliated with VTU. Their video portal belongs to us now.*

<br>

```
VTU: "Please watch all 166 lectures."
Us:  "No."
```

</div>
