# BUILD-PROMPT: <dashboard name> (route 1, spreadsheet)

<Fill every <placeholder> from PRD.md, CONNECTORS.md, and DESIGN.md, then the operator pastes this whole file as one message into the AI that helps them in Google Sheets or Excel. Delete this line.>

You are building a dashboard in <Google Sheets / Excel> for <operator>, <business>. The requirements are below; do not re-ask anything they answer. Work tab by tab, and after each tab tell me exactly what to click or paste. I am not a developer.

## What it is for
<The job, from PRD.md. One paragraph.>

## The numbers
<Paste the numbers table from PRD.md: name, unit, direction, "oh no" line, freshness, source.>

## Where the data comes from
<Paste the connectors table from CONNECTORS.md. For a spreadsheet the reach methods are: a scheduled import (IMPORTRANGE from another sheet, a CSV the operator drops in, a Zapier/Make/Composio zap that appends rows, or a connector add-on such as Coefficient or the tool's own Sheets export), or manual entry.>

## Build it like this
1. **One tab per source**, named after the source (`Stripe`, `GoHighLevel`, `Manual`). Row 1 is headers, one row per record, dates in a real date column. Never type numbers into these tabs by hand except in `Manual`.
2. **A `Calc` tab** that turns raw rows into the numbers above with formulas (SUMIFS, COUNTIFS, AVERAGEIFS, QUERY where it is clearer). One named cell per number, with its goal and its "oh no" line beside it. Everything the dashboard shows comes from this tab.
3. **A `Dashboard` tab** that is the only tab anyone looks at. Follow the design brief below exactly. Freeze the header row, hide gridlines, set the print area so it fits one page.
4. **A `Refresh` note** at the top of `Dashboard`: what refreshes each source, how often, and the date it last ran (a cell that the import writes or the operator updates).
5. **Conditional formatting** for the "oh no" lines: good / watch / act in the three status colors, applied to the tile cells only.
6. Charts: build them on `Calc` ranges, place them on `Dashboard`, no 3D, no pies with more than five slices, one accent color.

## Design brief
<Paste the layout, tile anatomy, chart-per-number table, color, and states from DESIGN.md. For a sheet: tiles are merged-cell blocks (label small caps in gray, number large, delta beside it), the trend is a line chart against a goal series, the breakdown is a bar chart, the table is a sorted range with the action column first.>

## Done means
<Paste the definition of done checks from PRD.md.>

Start with the `Stripe` tab (or whichever source works today) and the import method for it. Tell me what to click. After every tab, stop and let me confirm before the next one.
