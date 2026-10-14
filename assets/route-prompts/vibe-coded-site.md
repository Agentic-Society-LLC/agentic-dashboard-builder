# BUILD-PROMPT: <dashboard name> (route 3, vibe-coded site)

<Fill every <placeholder> from PRD.md, CONNECTORS.md, and DESIGN.md, then the operator starts a new project in Lovable (or Bolt, v0, Replit) and pastes this whole file as the first message. Delete this line.>

Build a web app: a dashboard for <operator>, <business>, used by <my team / my clients> on <laptop / phone>. Requirements are below; do not re-ask anything they answer. Build it in stages and stop after each one so I can look.

## What it is for
<The job, from PRD.md.>

## Who can see it
<From PRD.md, audience section. For a team: email + password login, one role. For clients: a login per client and each client sees only their own rows; say which field scopes the data (a client id on every row). Nothing is public.>

## The numbers
<Paste the numbers table from PRD.md.>

## Where the data comes from
<Paste the connectors table from CONNECTORS.md. For this route the methods are: the app's own database (Supabase or the builder's built-in one) filled by scheduled syncs, direct API calls from the server side with keys stored as environment secrets (never in the browser), a webhook the source tool posts to, or a CSV upload page. List the env secret names from CONNECTORS.md; I will paste the values into the project's secrets, not into chat.>

## Pages
1. **Login.**
2. **Dashboard** (the only page most people see): follow the design brief below exactly.
3. **Data** (admin only): one card per source with its last sync time, a Sync now button, and the last error in plain words.
4. **Settings** (admin only): the goals and "oh no" lines for each number, editable, so I never ask you to change a threshold.

## Syncs and freshness
<From PRD.md and CONNECTORS.md, per source: how often it syncs and how. Every sync writes a `last_synced_at` and a `last_error`. A number older than its freshness rule shows its age on the dashboard; a failed sync shows "Stripe did not answer, showing data from Tue 7:02am", never a zero.>

## Design brief
<Paste DESIGN.md in full: layout, tile anatomy, chart per number, color (accent hex, three status colors), type, states, the ten-second test. Phone layout is one column, tiles first. Light and dark following the system setting. Tabular figures on every number. No pies over five slices, no 3D, no gauges.>

## Done means
<Paste the definition of done checks from PRD.md.>

## Stages
1. The dashboard page with sample data, exactly to the design brief. Stop; I will review on my phone and laptop.
2. The database and the login. Stop.
3. One source synced for real (<the one that works today>). Stop; I will check the number against the source.
4. The remaining sources, then the Data and Settings pages.
5. Walk me through the done checks.
If something here cannot be done in this builder, say so and propose the smallest change. Do not add features that are not here.
