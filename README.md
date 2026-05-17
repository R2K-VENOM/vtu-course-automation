# VTU Autopilot

> Auto-complete VTU online courses. Because 166 lectures per subject is not it.

[![MIT License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Node.js](https://img.shields.io/badge/node-%3E%3D18-brightgreen)](https://nodejs.org)

---

## What is this?

VTU Autopilot is a tool that auto-completes VTU online course lectures on your behalf. It calls the same API your browser uses — no scraping, no emulation, no drama. You enter your credentials, pick a course slug, and the server marks every lecture as complete.

A web UI with real-time SSE streaming and a queue system is included. You can also run it as a CLI tool.

---

## Quick Start

### Web Server (recommended)

```bash
git clone https://github.com/r2k-venom/vtu-course-automation && cd vtu-course-automation && npm install
cp .env.example .env   # edit Redis credentials if you want persistence
npm run serve
```

Open `http://localhost:3000`.

### CLI

```bash
cp .env.example .env
# set VTU_EMAIL, VTU_PASSWORD, VTU_COURSE_SLUG in .env
npm start
```

---

## Environment Variables

Copy `.env.example` to `.env` and fill in the values.

| Variable | Required | Default | Description |
|---|---|---|---|
| `VTU_EMAIL` | CLI only | — | Your VTU portal email |
| `VTU_PASSWORD` | CLI only | — | Your VTU portal password |
| `VTU_COURSE_SLUG` | CLI only | `1-social-networks` | Course slug from URL |
| `PORT` | No | `3000` | Server port |
| `UPSTASH_REDIS_REST_URL` | No | — | Redis URL for persistence |
| `UPSTASH_REDIS_REST_TOKEN` | No | — | Redis auth token |
| `ADMIN_PASSWORD` | No | — | Enables admin API routes |
| `GITHUB_URL` | No | see server.js | Overrides the GitHub link shown in UI |
| `MAX_CONCURRENT` | No | `2` | Max simultaneous jobs |
| `DEFAULT_BATCH_SIZE` | No | `10` | Lectures per batch |
| `DEFAULT_MAX_ATTEMPTS` | No | `50` | Max retries per lecture |

---

## Finding the Course Slug

Go to `online.vtu.ac.in`, open your course, and look at the URL:

```
https://online.vtu.ac.in/course/1-social-networks
                                  ─────────────────
                                  this is the slug
```

---

## FAQ

**Will my account get banned?**
The tool uses VTU's official API — the same one your browser calls. Thousands of students have used it without issues.

**Are credentials stored?**
No. Email and password are held in memory only for the duration of the job, then zeroed out.

**Can I close the browser tab?**
Yes. Jobs run server-side. Copy the URL (it contains your job ID) to reconnect.

**Some lectures say "Max attempts reached"?**
Certain lectures (usually gated/special content) don't accept API progress. These can be ignored — VTU doesn't require 100% completion to mark a course complete.

---

## Admin Routes

Set `ADMIN_PASSWORD` in your `.env`, then:

| Route | Description |
|---|---|
| `GET /api/admin/config?password=<pw>` | View / update runtime config |
| `GET /api/admin/monitor?password=<pw>` | Live queue inspector |
| `GET /api/admin/notification?password=<pw>&message=<msg>&disabled=true` | Set notification banner |

---

## License

MIT © Chirag Shetty

**GitHub**: [r2k-venom/vtu-course-automation](https://github.com/r2k-venom/vtu-course-automation)

---

## Self-host in 60 seconds

```bash
git clone https://github.com/r2k-venom/vtu-course-automation && cd vtu-course-automation && npm install
```
