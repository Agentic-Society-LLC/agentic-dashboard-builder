# agentic-dashboard-builder

The PRD build kit for an agentic dashboard. An interview, not a template: your AI asks the right questions in rounds (each with its own recommended answer), then writes a kit the next AI session can build from without asking anything twice.

**You come out with `dashboard-kit/`:**

- `PRD.md`: the job the dashboard does (the decisions it serves), the three to seven numbers with an "oh no" line each, the scope ladder, the definition of done.
- `STACK.md`: the build route and why, scored against the four routes, with what moves it up or down a rung and the honest cost and maintenance line.
- `CONNECTORS.md`: every data source, how the AI reaches it (MCP, connector, API, export, or manual), whether it works today or what two-minute test proves it, and what writes back.
- `DESIGN.md`: the design brief, so it looks great and passes the ten-second test: layout, tile anatomy, the right chart per number, one accent color, light and dark, empty and broken states.
- `BUILD-PROMPT.md`: the copy-paste message that starts the build in the tool the route chose.

**The four routes** it decides between: a spreadsheet, a Claude Code artifact (one HTML file your AI keeps current), a vibe-coded site (Lovable and friends), or a full agentic harness (GitHub + Vercel + Cloudflare + a database, with agent jobs that pull, alert, and write back). Rule: when in doubt, one rung down, ship, promote later.

It plans and does not build. Say "build it" after the kit exists and it builds in the route the kit chose.

## Install

**One click:** [agenticsociety.com/downloads/mike-chu](https://agenticsociety.com/downloads/mike-chu) downloads the zip (SKILL.md + the templates) and shows the install for each tool.

**Claude Code** (paste into your terminal)
```bash
mkdir -p ~/.claude/skills/agentic-dashboard-builder/assets/route-prompts && cd ~/.claude/skills/agentic-dashboard-builder && for f in SKILL.md assets/PRD-TEMPLATE.md assets/STACK-TEMPLATE.md assets/CONNECTORS-TEMPLATE.md assets/DESIGN-TEMPLATE.md assets/route-prompts/spreadsheet.md assets/route-prompts/claude-artifact.md assets/route-prompts/vibe-coded-site.md assets/route-prompts/agentic-harness.md; do curl -sL "https://raw.githubusercontent.com/Agentic-Society-LLC/agentic-dashboard-builder/main/$f" -o "$f"; done
```
Then type `/agentic-dashboard-builder` in any session. Running it inside your company brain folder is best, because it can check what you already have connected.

**Codex** (paste into your terminal)
```bash
mkdir -p ~/.codex/skills/agentic-dashboard-builder/assets/route-prompts && cd ~/.codex/skills/agentic-dashboard-builder && for f in SKILL.md assets/PRD-TEMPLATE.md assets/STACK-TEMPLATE.md assets/CONNECTORS-TEMPLATE.md assets/DESIGN-TEMPLATE.md assets/route-prompts/spreadsheet.md assets/route-prompts/claude-artifact.md assets/route-prompts/vibe-coded-site.md assets/route-prompts/agentic-harness.md; do curl -sL "https://raw.githubusercontent.com/Agentic-Society-LLC/agentic-dashboard-builder/main/$f" -o "$f"; done
```
Then restart Codex and ask "run the agentic-dashboard-builder skill".

**Claude.ai / Cowork**
Download the zip from the link above and upload it as-is in Settings > Customize > Skills. Then say "plan my dashboard".

**Anything else (ChatGPT, Hermes, etc.)**
Open [SKILL.md](https://raw.githubusercontent.com/Agentic-Society-LLC/agentic-dashboard-builder/main/SKILL.md), copy all of it, paste it as your first message, then say "start".

## Three ways it runs

- **Interview:** no kit yet. The full interview, 20 to 30 minutes, 4 to 6 rounds.
- **Route check:** you already have a sheet, a half-built app, or a PRD. It reads what you have, scores it against the four routes, asks only about what fails.
- **Kit refresh:** something changed. It updates the one file that changed and tells you whether the route moved.

## Inspiration

- Matt Pocock's `grill-me` / `grilling` skill (github.com/mattpocock/skills): the relentless interview, the rounds of numbered questions each with a recommended answer, and the split where the agent looks up facts and the human makes decisions.
- Lauren Tan's (poteto) `pstack` (github.com/cursor/plugins/tree/main/pstack): definition of done as a checkable test, settling facts by running something instead of asking, candor over agreement, and planning without building.
- The Agentic Society `hackathon-plan` skill (github.com/Agentic-Society-LLC/hackathon-plan), which this one is shaped after.

## License

MIT. Use it, adapt it, share it. See [LICENSE](LICENSE).
