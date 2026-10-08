# Data pipeline delivery tracker

One page that brings together the tools a project manager usually juggles in separate places when running data pipeline projects alongside a tech lead: portfolio status, schedule, data flow map, kanban, backlog scoring, RAID log, source dependencies, incidents, pipeline health, stakeholder meeting minutes, and an AI tab that turns the current data into ready-to-use prompts.

> **Status: prototype.** A single static page with fictional data, built to explore the idea and to serve as a demo. It is not a production tool yet.

## Why

On data projects, delays rarely come from the code. They come from what data owners have not yet provided (access, extracts, schemas, definitions, agreements), and from data that arrives late or wrong once the pipeline runs. The two are usually tracked in different places, so the link between them is made by hand.

This page keeps them in one place and connected: a blocked source shows up in the schedule, on the board, in the risk log, on the data flow map and in the risk score at the same time.

## What is inside

| Tab | Purpose |
|---|---|
| **Portfolio** | Weekly view: status per project, variance, budget, alerts, next milestones and meetings |
| **Schedule (Gantt)** | Consolidated plan with milestones, slippage and data owner deliverables shown as circles |
| **Data flow map** | Each pipeline as stages from source to serving, with status, owner, and the downstream impact of a blocked stage |
| **Kanban** | Drag-and-drop board with a "Blocked by data owner" column and a work-in-progress limit |
| **RICE backlog** | Editable scoring (reach, impact, confidence, effort) with live ranking |
| **RAID log** | Risks, actions, issues and dependencies with owners and due dates |
| **Source dependencies** | What engineering needs from data owners, by when, and the impact if it is late |
| **Incidents** | Severity levels, incident flow, indicators, log and a timeline per incident |
| **Pipeline health** | Freshness SLA hit rate, run success rate, data quality test pass rate, recovery time and run duration, computed per pipeline from a run log |
| **Stakeholder meeting** | Agenda template and filled-in minutes example |
| **AI copilot** | Prompt builder, delay-risk radar, guardrails and a weekly routine |

### About the AI tab

- **Prompt builder.** Pick a task (weekly status report, data owner chase email, delay-risk scan, data delay note for consumers, meeting notes to actions, post-incident review, RICE check) and a scope. The prompt is filled with the current tracker data. Copy it into any AI assistant. No API key and no network call are involved.
- **Delay-risk radar.** A transparent, rule-based score computed from the other tabs, with the reasons displayed. It is not AI, on purpose.
- **Guardrails.** Never paste personal data or production records, read before sending, check numbers and dates, and leave technical decisions to the tech lead.

### About the pipeline health tab

All figures are computed in the page from a generated, fictional run log (224 runs over 8 weeks). Targets are illustrative and not an industry benchmark: agree real SLAs with each data owner. The DORA metrics (deployment frequency, lead time, change failure rate, recovery time) still apply to the pipeline code itself and are covered in the companion project tracker.

## Run it

No build step and no dependency. Open `index.html` in a browser. An internet connection is only needed to load the web font; the page falls back to system fonts offline.

## Publish

Any static host works (GitHub Pages, Netlify, Cloudflare Pages). Put `index.html` at the root of the project or drag the folder into the host's deploy page.

## Customise the data

Everything lives in `index.html`. The data is defined as plain JavaScript at the top of the `<script>` block: `P` (projects), `port` (portfolio cards), `G` (Gantt rows), `FLOW` (data flow stages), `K0` (kanban cards), `R` (RICE items), `RAID`, `AT` (source dependencies), `INC` (incidents) and `HP` (parameters that generate the run log).

The kanban board and the last opened tab are saved in the browser's `localStorage`. Use **Reset board** to restore the default cards.

## Roadmap

Nothing here exists yet.

- [ ] Real run history imported from the orchestrator and test results from the quality tooling, instead of a generated log
- [ ] Link failed runs to incidents and to the RAID log
- [ ] Editing every tab in the page, with real storage
- [ ] Explicit links between items (a late source linked to its tasks, cards, stages and incidents)
- [ ] Export: weekly status as PDF or Markdown, RAID and dependencies as CSV
- [ ] Optional direct AI calls behind a user-provided key, keeping copy-paste as the default

## Limits

- All data is fictional. Do not enter confidential or personal data in the public version.
- Scores, thresholds and severity targets are illustrative. Align them with your own SLAs and practices.
- The delay-risk radar is a simple heuristic, not a forecast.

## License

Choose a license before sharing widely. MIT is a common default for a small project like this.
