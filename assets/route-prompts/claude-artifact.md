# BUILD-PROMPT: <dashboard name> (route 2, Claude Code artifact)

<Fill every <placeholder> from PRD.md, CONNECTORS.md, and DESIGN.md, then the operator opens Claude Code (or Codex, or Cowork) in the folder where the dashboard should live and pastes this whole file as the first message. Delete this line.>

Build me a dashboard as **one self-contained HTML file** at `dashboard/index.html` in this folder. No framework, no build step, no server, no account. The file has three parts: a documented JSON data block (`<script id="dashboard-data" type="application/json">`), the page markup, and the script that renders the markup from the data. From now on, **when I ask you to refresh the dashboard you edit only the JSON block, in place**, never the markup or the script, and you set `"updatedAt"` to now. The kit this comes from is in `dashboard-kit/` beside this message if you want the long version; the short version is below. Do not re-ask anything answered here.

## What it is for
<The job, from PRD.md.>

## The numbers
<Paste the numbers table from PRD.md.>

## Where the data comes from, and how you reach it
<Paste the connectors table from CONNECTORS.md. The reach methods you can use from here: MCP servers already connected to this session, connectors, official APIs with the keys listed in CONNECTORS.md (read them from a .env file in this folder, never from the HTML), or exports I drop into `dashboard/data/`. For each source, say what you will call, and run the two-minute test from CONNECTORS.md before you rely on it.>

## The data block
Design the JSON so that a refresh is a targeted edit: one object per number with `value`, `goal`, `threshold`, `direction`, `unit`, `asOf`, and a short `series` for the trend; one array for the breakdown; one array for the detail table; `updatedAt` at the top; `"sample": true` until the data is mine. Put a comment above the block that documents every key so a future session can refresh it without reading the script.

## Refresh
<From PRD.md and CONNECTORS.md: the freshness per number and who refreshes. For "the AI when asked": tell me the exact phrase to say. Default to "when asked": a scheduled refresh only works if this folder is a GitHub repo a cloud routine can check out; if it is a local folder, say so and give me the phrase instead. Say when it runs and what to do when a source fails: the page must show the source as broken with the last good time, never a silent zero.>

## Design brief
<Paste DESIGN.md in full: layout, tile anatomy, chart per number, color (accent hex, three status colors), type, states, the ten-second test. Render charts with inline SVG you write yourself or a single small library from a CDN (Chart.js is fine); no readable text in images; light and dark via `prefers-color-scheme`. Phone first if the device is a phone. Tabular figures for every number.>

## Done means
<Paste the definition of done checks from PRD.md.> Walk through each one with me on real data before you call it finished.

## How to work
1. Build the file with sample data first so I can see the design in my browser. Stop and show me.
2. Then wire the sources one at a time, in the order they work today, replacing sample data with real data and flipping `"sample"` to false. After each source, tell me what to open and what I should see.
3. Then set up the refresh and tell me the phrase or the schedule.
4. Then run the done checks with me.
Keep the file under 100 KB. Keep every key. If something in this brief cannot be done, say so and propose the smallest change, do not silently drop it.
