# BUILD-PROMPT: <dashboard name> (route 4, agentic harness)

<Fill every <placeholder> from PRD.md, CONNECTORS.md, and DESIGN.md, then the operator creates an empty GitHub repo, opens Claude Code (or Codex) in a clone of it, and pastes this whole file as the first message. Delete this line.>

Build an agentic dashboard for <operator>, <business>, as a real codebase in this repo, deployed on Vercel with Cloudflare in front, with agent jobs that pull the data, compute the numbers, alert when a line is crossed, and (with a human checkpoint) write back. Requirements are below; `dashboard-kit/` beside this message has the long version. Do not re-ask anything answered here. Work in small pull requests I can read; I review, you merge.

## What it is for
<The job, from PRD.md.>

## Who can see it and act on it
<From PRD.md: audience and device. Logins: <team / per client>. What an agent is allowed to do without asking, and what needs a person: paste the human checkpoints from PRD.md and CONNECTORS.md.>

## The numbers
<Paste the numbers table from PRD.md.>

## Sources
<Paste the connectors table from CONNECTORS.md. For this route every source is reached server-side: an official API with a key in Vercel env, an MCP server the agent job can call, or a webhook. The secret names are in CONNECTORS.md; I will set the values in Vercel, you never see them. Each source gets a sync job with a schedule from the freshness column.>

## Architecture (keep it this simple unless a requirement forces more)
- **Site:** a static front end (Astro or Next, your call, static output) that renders the dashboard from a JSON the jobs write. No server-rendered pages; the dashboard must still load if every job is down.
- **Jobs:** serverless functions on Vercel, run by Vercel cron on the schedule per source. Each job: pull, normalize, write rows to Postgres, recompute the numbers, write `latest.json`, record `last_synced_at` and `last_error`.
- **Database:** Postgres (Neon or Vercel Postgres). One table per source's raw rows, one `numbers` table with history so the trend is real, one `events` table for alerts and write-backs with who approved them.
- **Alerts:** when a number crosses its "oh no" line, post to <Slack channel / email / SMS> with the number, the threshold, and a link. Once per crossing, not every run.
- **Write-backs:** <from CONNECTORS.md, every "writes back: yes" row>. Each one is proposed into `events` first and executed only after <the checkpoint: a Slack button, a tag the operator clears, an approval in the dashboard>. Log every execution.
- **Cloudflare:** DNS, caching for the static site, and a rule that keeps `/api/*` uncached. Nothing else until something needs it.
- **Secrets:** Vercel env only. Fail loudly with a named `not_configured` error when one is missing; never a silent zero.

## Design brief
<Paste DESIGN.md in full: layout, tile anatomy, chart per number, color (accent hex, three status colors), type, states, the ten-second test. Light and dark following the system setting. Phone first if the device is a phone. Tabular figures on every number. The stale and broken states come from `last_synced_at` and `last_error`, shown in plain words.>

## Done means
<Paste the definition of done checks from PRD.md.> Plus, for this route: every job has a log line I can read in Vercel, a failed job alerts me once, and `git log` tells the story.

## Order of work
1. Repo skeleton, the static dashboard with sample data to the design brief, deployed to a Vercel preview URL. Stop; I review on my phone.
2. Postgres schema and the first sync job for <the source that works today>, on its schedule. Stop; I check the number against the source.
3. The remaining sync jobs, then the numbers computation and the trend history.
4. Alerts.
5. Write-backs with their checkpoints, one at a time.
6. Cloudflare in front, custom domain, then the done checks with me.
Keep a `README.md` that a future AI session can read to pick this up: what runs when, where secrets live, how to add a source. If a requirement cannot be met as written, say so and propose the smallest change. Do not add what is not here.
