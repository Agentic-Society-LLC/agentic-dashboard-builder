# Design brief: <dashboard name>

**Device first:** <laptop / phone / wall screen>
**The ten-second test:** a person who has never seen this opens it and, within ten seconds, knows whether **<number 1>** is on track. Everything below serves that.

## Layout, top to bottom

1. **Header tiles:** <3 to 5 numbers, in this order; the first is highlighted>
2. **The trend:** <number N over time against goal, as a line; the time window>
3. **The breakdown:** <by source / stage / client; the chart type>
4. **The detail table:** <what rows, which column comes first (the action), how it sorts>

Phone: one column, tiles first, the trend second, the table collapses to the three most important columns. Wall screen: tiles and the trend only, type at least twice the laptop size, auto-refresh visible.

## Tile anatomy

Label in small caps · the number large, in tabular figures · the delta beside it in plain words ("+12% vs goal", "3 below target") · a tiny sparkline when there is a trend · the status color on the tile edge, not the whole tile. Highlighted tile: **<number 1>**.

## Chart per number

| Number | Question it answers | Chart |
|---|---|---|
| <cash collected> | <are we on pace this month> | <line vs goal line, month to date> |
| <clients won by source> | <where do wins come from> | <horizontal bars, sorted> |
| <clients at risk> | <who do I call> | <table, action column first> |

Never: a pie with more than five slices, a 3D chart, a gauge, a chart with two y-axes, a legend that is needed to read the chart.

## Color

- **Accent:** <hex, from the brand or chosen> used for the highlighted tile, the main trend line, and buttons. Nothing else is this color.
- **Neutrals:** grays for text, borders, and backgrounds.
- **Status, exactly three:** good <hex>, watch <hex>, act <hex>. Used only to say good / watch / act.
- Light and dark, following the system setting. Both must pass the ten-second test.

## Type

<One typeface (brand font or Inter / Geist). Numbers in tabular figures. Sizes: tile number, tile label, body, table.>

## States

- **Empty:** <what a source with no rows yet shows, in words>
- **Loading:** <skeleton tiles, no spinners that hide the layout>
- **Stale:** <a number older than its freshness rule shows its age: "as of Tue 7:02am">
- **Broken:** <"Stripe did not answer. Showing yesterday's numbers." Never a silent zero.>

## Brand references

<Links or files: the site, a logo, a style guide, screenshots the operator likes. Or "none; use the defaults above.">
