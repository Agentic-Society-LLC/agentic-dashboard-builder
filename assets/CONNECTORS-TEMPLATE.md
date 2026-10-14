# Connectors: <dashboard name>

One row per source. The building AI reads this before it writes anything; the operator does the prep tasks before the build starts. Reach methods, in order of preference: **MCP** (the AI uses the tool directly), **Connector** (a pre-built plug in Claude, Zapier, or Composio), **API** (a key from the tool's settings), **Export** (a file downloaded on a schedule), **Manual** (a number someone types in).

| Source | Object | Feeds numbers | Reach method | Works today? | Writes back? | Freshness | Refresh owner |
|---|---|---|---|---|---|---|---|
| <GoHighLevel> | <opportunities, Sales pipeline> | <2, 3> | <MCP> | <yes, tested 2026-10-14> | <no> | <daily> | <AI, scheduled 7am> |
| <Stripe> | <charges, last 90 days> | <1> | <API key, read-only> | <prep task C-1> | <no> | <daily> | <AI, scheduled 7am> |
| <Google Sheet "Weekly Numbers"> | <tab "NPS"> | <5> | <Manual> | <yes> | <no> | <weekly> | <operator, Fridays> |

## Prep tasks (do these before building)

Each one is a two-minute test. When it passes, change the row above to "yes" with today's date.

- [ ] **C-1 Stripe:** In Stripe → Developers → API keys, create a restricted key with read access to Charges and Customers. Then ask your AI: "List my five most recent Stripe charges." If it answers with real amounts, this works today.
- [ ] **C-2 <source>:** <the test>

## Secrets the build will need

<Names only, never values. Where each one goes depends on the route: a sheet's import settings, the artifact's refresh job, the builder's environment settings, or the repo's Vercel env.>

- `STRIPE_RESTRICTED_KEY`
- `<...>`

## Human checkpoints

<For every "writes back: yes" row: who approves, and how (a draft to review, a tag the operator clears, a Slack message with a button).>
