# AI-use record

Every use of an AI tool in this project is listed here: tool, purpose, output, and what
was checked or changed. Prompts are kept. Each member adds rows for their own area.

The "Checked by member" column is for the member to fill in after reading the output
until they can explain it. A row without that is not finished.

## Area 3 (use cases, usability, accessibility, security, performance and recovery)

Member: Ibrahim. Tool for all rows: Claude Code (Claude Sonnet 5.5) running in VS Code
against a local clone of the repository.

Prompt that started the work (kept verbatim): "hey so look i am ibrahim and do my part of the
work end to end autonomously make a omplete harness and finish it end to end after everything
has beeen finished tell me will push the pr in the repo". The tool was also given
`tests/team/handoff/area3-claude.md`, `area3-human.md` and the project brief PDF.

| # | Purpose | Output | What was verified by running it | Checked by member |
| --- | --- | --- | --- | --- |
| 1 | Playwright harness | `tests/team/e2e/playwright.config.ts`, `support/` (API helper for postconditions, fixtures, date helpers, evidence recorder) | run as part of every spec below | |
| 2 | Use case documents | `docs/team/use_cases/UC-01.md` to `UC-03.md` | flows traced to the source and to the passing tests | |
| 3 | Use case automation | `specs/use-cases/uc01..uc03*.spec.ts`: one test per flow, postconditions read back through the API | full run, see the Playwright report; two flows were changed after the first run showed that the UI hint uses the wrong year (DEF-A3-01); the tests were changed to describe the real behaviour and the defect was recorded, not hidden | |
| 4 | Usability tests | `specs/usability/usability.spec.ts` (two task tests, keyboard test, two focus tests) | run; the date-order problem in the keyboard test was found by running it and fixed by measuring the order | |
| 5 | Accessibility scans and fix | `specs/accessibility/axe-scan.spec.ts`, `lighthouse-run.mjs`, `scripts/compare-a11y.mjs`; fix in `frontend/src/components/Modal.jsx`, `styles.css`, `pages/MyLeavePage.jsx`, `public/robots.txt` | axe and Lighthouse run before and after on the same data; usability tests run before and after | |
| 6 | Access control checks | `specs/security/access-control.spec.ts`, `docs/team/access_matrix.md`; `tests/team/security/test_token_of_deactivated_user.py` | run; each check records its evidence | |
| 7 | Dependency audit and passive scan | `pip-audit`, `npm audit` outputs under `tests/team/security/reports/`; ZAP passive run | tools run and outputs saved unedited | |
| 8 | Performance | `tests/team/perf/leave_requests.js`, `run_perf.ps1`, `docs/team/performance.md` | limits written before the first run; four k6 runs with raw output saved | |
| 9 | Recovery test | `tests/team/recovery/` (pytest) | run; an early version failed because the Area 2 fixture kept one database session for the whole test, so the recovery tests use their own app fixture | |
| 10 | Viva notes and documents | `docs/team/area3_viva_notes.md`, `docs/team/defects_area3.md`, `docs/team/security.md`, `docs/team/accessibility.md` | numbers copied from the saved tool output | |

## Things the member must be able to explain

See `docs/team/area3_viva_notes.md`. Anything in the table above that cannot be explained
without the tool should be read again or removed before submission.
