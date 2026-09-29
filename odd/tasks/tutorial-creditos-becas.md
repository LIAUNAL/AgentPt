# Feature: tutorial-creditos-becas

Add a hands-on tutorial to module 6 ("UN-SpecWeaver") of the deck: how to use `un-specweaver`
CLI + slash commands, walked through with the exact same worked example already built for the
narrated video ("Sistema de Créditos y Becas"), presenting the real artifacts that example
produced, and closing with the finished video attached.

- Feature doc: `odd/tasks/tutorial-creditos-becas.md`
- Engram mirror: `odd/tutorial-creditos-becas/tasks/tasks.md`
- Status: IMPLEMENTED (T1–T6 done); not committed — commit/push remain the user's decision

## Scope

- Insert 10 new `<article class="slide" data-module="5">` units into `index.html`, between the
  existing stack-diagram slide (`data-index="21"`) and the "Fuentes" slide (currently
  `data-index="22"`, must renumber to `data-index="32"`, kicker `33 · Fuentes`).
- All facts must be real, verified against the actual demo project and CLI (no invented
  commands, names, or numbers) — source of truth is the dev-repo binary
  (`/home/carlos/Documents/projects/un-specweaver/bin/un-specweaver.mjs`), the demo project at
  `/home/carlos/Documents/projects/un-specweaver-video-creditos-becas-parent/demo-project/sistema-creditos-becas/`,
  and the video project's `STORYBOARD.md`/captures at
  `/home/carlos/Documents/projects/un-specweaver-video-creditos-becas-parent/creditos-becas/`.
- Real screenshots only (extracted video frames or existing capture stills) — never
  reconstructed/redrawn UI mockups, consistent with the video's own production rule.
- Never show or name-demo the "Arquitectura" dashboard tab/feature (the `architecture` CLI
  command may be *named* in the cheat-sheet table, same as the video's Frame 6 treatment, but
  never visually demoed).
- Follow the deck's existing `<abbr title="...">` acronym-hover convention
  (see `odd/tasks/siglas-definiciones-hover.md` §1.3 for the canonical table); add new rows only
  for genuinely new acronyms introduced by this content (e.g. BI, SPA) using the same
  "English canonical (Spanish gloss)" tooltip format.
- Final slide embeds the finished video. **User decision (2026-09-28): link to an externally
  hosted URL, not a git-tracked copy of the ~100 MB file.** URL supplied by the user:
  `https://youtu.be/qewfgmV-P64` — embed via `youtube-nocookie.com/embed/qewfgmV-P64` in a
  responsive 16:9 wrapper.
- Update `README.md`: module 6 content-table row description, slide count.

## Tasks

- [x] T1 — Explore existing deck structure, acronym conventions, and gather verified facts
      (CLI `--help`, `/sw:*` command descriptions, PRD/epics/OpenSpec/tests, video assets)
- [x] T2 — Extract/prepare real screenshot stills from existing `.webm` captures where no still
      exists yet (init, dashboard-dependencias)
- [x] T3 — Write the 10 new slides into `index.html` (content + CSS for new components:
      `.cmd-table`, `.code-block`, `.epic-cards`/`.epic-card`, `.video-embed`, monospace
      `<code>` styling)
- [x] T4 — Renumber the "Fuentes" slide (data-index 22→32, kicker 23→33) and update `README.md`
- [x] T5 — Verify: article/tag balance, data-index/kicker continuity, no horizontal-overflow
      risk (existing breakpoints reused, no new ones needed), acronym hovers present and
      consistent, real facts spot-checked against source
- [x] T6 — Real video URL dropped into slide 10 (data-index 31): `qewfgmV-P64`, provided by the
      user (see Scope note above) — already implemented, not pending

## Verified facts (source material — do not re-derive, reuse exactly)

### CLI top-level commands (dev-repo binary, `--help`)
`init`, `update`, `doctor [--fix]`, `bridge <epics.md>`, `context`, `history [FR-id]`, `close [ids] [--done|--dry-run]`,
`status [--html|--open|--json]`, `architecture` (name only — never demoed, same as video Frame 6), `vendors`,
`dashboard [--port] [--host] [--open]` (alias: `ui`). 12 top-level commands.

### `/sw:*` slash commands (13 total, from `src/layer/commands/en/*.md` frontmatter)
`/sw:new`, `/sw:adopt`, `/sw:update`, `/sw:change`, `/sw:bug`, `/sw:ticket`, `/sw:build`, `/sw:sprint`,
`/sw:sync`, `/sw:status`, `/sw:close`, `/sw:doctor`, `/sw:dashboard` — one-line descriptions in the
research report (see conversation / mem_search this feature for the full table).

### Demo project (Sistema de Créditos y Becas)
- PRD: 12 FRs (`FR-001..FR-004, FR-010..FR-012, FR-020..FR-022, FR-030, FR-031`).
- 4 epics / 11 stories: Epic 1 Solicitud de crédito (3), Epic 2 Evaluación de elegibilidad para
  becas (3), Epic 3 Desembolso y seguimiento (3), Epic 4 Reportes para dirección académica (2).
- OpenSpec: 13 change folders total — 12 pending + 1 archived
  (`archive/2026-09-27-e1s1-registro-de-solicitud-de-credito-con-datos-socio`).
- Real implemented+tested story: `src/solicitud-credito/registroSolicitudCredito.js` — 6/6 tests
  passing (`node --test`).

### Video project assets (already built, reusable)
- Final video: `un-specweaver-creditos-becas.mp4`, 105,131,036 bytes, 665.000000s, 1920x1080.
- Real capture stills already available (no extraction needed):
  `frame06-doctor-final.png`, `frame06-status-final.png`, `frame06-history-final.png`,
  `frame06-close-hold.png`, `frame09-levantar-web-hold.png`, `frame11-progreso-final.png`.
- Real capture videos with **no still yet** (extract one via ffmpeg): `frame04-init.webm`,
  `frame10-dependencias.webm` (+ `frame10-dependencias-inspector.webm`, `frame10-terminal-drawer.webm`).
- Confirmed: zero "arquitectura"/architecture filenames in `media/captures/` — clean.

## Route

Delegated direct: one writer agent for T2–T4 (image extraction + `index.html`/CSS/README edits),
per the writer trigger (2+ non-trivial files, prep work ahead of a write). No SDD, no Judgment
Day requested by the user for this task — RDD (if enabled) governs review per the existing
project-owned switch.

## Evidence log

**Re-verified numbers (differ from / confirm the T1 snapshot above):**
- PRD: 12 FRs confirmed (`FR-001..004, FR-010..012, FR-020..022, FR-030, FR-031`) — re-read
  directly from `demo-project/sistema-creditos-becas/_bmad-output/planning-artifacts/prd.md`.
- Epics/stories: 4 epics, 11 stories confirmed (3+3+3+2) — re-read from `epics.md` headings.
- **OpenSpec change count corrected**: the T1 snapshot said "13 change folders total — 12
  pending + 1 archived". Direct `ls` on `openspec/changes/` and `openspec/changes/archive/`
  found **11 total** (10 pending + 1 archived: `e1s2, e1s3, e2s1, e2s2, e2s3, e3s1, e3s2, e3s3,
  e4s1, e4s2` pending + `archive/2026-09-27-e1s1-registro-de-solicitud-de-credito-con-datos-socio`
  archived), matching 11 stories 1:1. Slide 5 (data-index 26) uses the corrected number (11).
- Test result confirmed by actually running `node --test registroSolicitudCredito.test.js` in
  `demo-project/sistema-creditos-becas/src/solicitud-credito/`: 6 tests, 6 pass, 0 fail
  (duration_ms 57.699471). Full trimmed output used verbatim in the slide's `.code-block`
  (data-index 27).
- Archived change folder name confirmed to still exist exactly as named:
  `openspec/changes/archive/2026-09-27-e1s1-registro-de-solicitud-de-credito-con-datos-socio`.

**CLI/`--help` text**: re-read directly from `un-specweaver/bin/un-specweaver.mjs --help`
(v0.5.2). Matches the T1 snapshot closely; the cheat-sheet table (data-index 24) uses the real
wording throughout. 12 top-level commands total (`init, update, doctor, bridge, context,
history, close, status, architecture, vendors, dashboard, ui`).

**`/sw:*` descriptions**: re-read verbatim from `src/layer/commands/es/*.md` frontmatter
`description` fields (not translated/reworded) for all 13 commands, used as-is in the slash-
command table (data-index 25), including the un-accented source spelling.
**Deviations from the task's draft snapshot** (draft → real, both real/verified):
- `bridge`: draft said "convierte **historias** de BMAD…"; real help text says "convierte
  **stories** de BMAD…" — used the real wording.
- `close`: draft's `--done`/`--dry-run` gloss simplified "todas las completas"; real help text
  says "`--done`: todas las que tienen sus tareas completas" — used the real wording.
- `vendors`: draft said "muestra las versiones ancladas de cada herramienta conectada"; real
  help text says "muestra las versiones pineadas" (terser) — used a light gloss naming the real
  vendors (BMAD, OpenSpec, Gentle-AI) sourced from the `UPDATE`/`QUE HACE INIT` sections of the
  same `--help` output, not invented.
- `/sw:*` table rows: no deviations — all 13 descriptions match the frontmatter verbatim.

**Screenshots (T2)**: `frame09-levantar-web-hold.png` and `frame11-progreso-final.png` copied
as-is into `assets/images/screenshot-dashboard-launch.png` /
`screenshot-dashboard-progreso.png`. `frame04-init.webm` (duration 12.6s) and
`frame10-dependencias.webm` (duration 8.12s) each had one frame extracted with `ffmpeg` at 60%
of duration (7.56s / 4.87s respectively) into `screenshot-init-terminal.png` /
`screenshot-dashboard-dependencias.png` — both 1600×900 PNGs, visually inspected (not blank,
not mid-transition). Noted for the record: `screenshot-dashboard-launch.png` (frame09's "hold"
frame) and `screenshot-dashboard-dependencias.png` visually show the same Dependencias view,
because the dashboard opens on that tab by default — expected, not a capture error.
**Arquitectura tab visibility**: both dashboard screenshots show the persistent 3-tab nav bar
(Dependencias / Progreso / Arquitectura) as normal UI chrome, since the real app always renders
all three tab labels together; the Arquitectura tab is never selected, focused, or demoed in
either screenshot — consistent with the "name only, never demo" constraint.

**Files touched**: `index.html` (10 new `<article class="slide" data-module="5">` units,
data-index 22–31, kickers 23–32, inserted after the existing data-index-21 slide; the former
data-index-22 "Fuentes" slide renumbered to data-index 32 / kicker 33),
`assets/css/styles.css` (new scoped components: `.slide-list code`/`.cmd-table code`,
`.cmd-table`, `.code-block`, `.epic-cards`/`.epic-card`, `.video-embed`, plus two responsive
tweaks under existing `@media (max-width: 760px)` and `@media (max-height: 560px) and
(orientation: landscape)` blocks), `README.md` (module 6 row + both slide-count mentions,
22→32), `assets/images/screenshot-{init-terminal,dashboard-launch,dashboard-dependencias,
dashboard-progreso}.png` (new), this tracking doc.

**New acronym tooltips added** (genuinely new to the deck, format matches §1.3 of
`siglas-definiciones-hover.md`): `BI` → "Business Intelligence (inteligencia de negocio)";
`SPA` → "Single Page Application (aplicación de una sola página)". Reused verbatim (grep-
verified against existing `title="…"` strings): `PRD`, `SDD`, `CLI` (CLI's tooltip did not
previously appear in `index.html` — it existed only in the canonical siglas table for
`demos/01`; reused that exact canonical string).

**Verification performed**: `<article>`/`</article>` balance (33/33), `data-index` sequence
0–32 continuous with no gaps/dupes, `slide-kicker` numbers 2–33 continuous, CSS brace balance
(178/178), `html.parser`-based tag-nesting check (0 unclosed elements at EOF), grep for
"Arquitectura"/"arquitectura" confirms the only new-content occurrence is the one-line CLI
cheat-sheet mention (data-index 24, `architecture` command row) — no screenshot or demo of that
tab. No deviation required from the spec beyond the three CLI-wording corrections and the
OpenSpec-count correction documented above. `git add`/`git commit` intentionally not run.

### Correction (post-review)

**User feedback**: "in the artifacts what i wanted was the bmad artifacts and specs, no
screenshots." — the two artifact-focused slides (data-index 26 and 27) showed a stylized
`.epic-cards` graphic and terminal test output only, not the real generated document text.
Reworked only these two slides; every other slide (init, dashboard launch, dependencias,
progreso — screenshot-based tool-usage demos) was left untouched, as instructed.

**Slide 1 — "De la idea a las historias: el caso real" (data-index 26, épicas slide)**:
removed the `<ul class="epic-cards">` / `<li class="epic-card">` HTML block entirely. Kept the
existing bullet-list prose unchanged. Converted the slide to `is-wide` (dropped the two-column
`.slide-figure` layout) and added a two-column `.excerpt-row` below the bullets with real
verbatim excerpts:

- From `prd.md`
  (`/home/carlos/Documents/projects/un-specweaver-video-creditos-becas-parent/demo-project/sistema-creditos-becas/_bmad-output/planning-artifacts/prd.md`,
  §5 "Capacidad 1 — Solicitud de crédito"), FR-001 through FR-004, IDs and wording exact
  (markdown table pipes/bold and the Prioridad/Traza columns dropped for legibility — content
  untouched):
  ```
  FR-001: El sistema DEBE permitir que un estudiante registre una solicitud de crédito con sus
  datos socioeconómicos (ingresos del hogar, número de dependientes, estrato, ocupación del
  acudiente).
  FR-002: El sistema DEBE validar que la solicitud incluya los documentos requeridos
  (identificación, certificado de ingresos, certificado de matrícula) antes de enviarla a
  revisión, rechazando el envío si falta alguno.
  FR-003: El sistema DEBE permitir que un asesor financiero revise una solicitud completa y la
  apruebe o rechace registrando un motivo.
  FR-004: El sistema DEBERÍA notificar al estudiante el resultado de la revisión de su
  solicitud.
  ```
- From `epics.md`
  (`.../_bmad-output/planning-artifacts/epics.md`), the real "Epic 1: Solicitud de crédito"
  header plus its 3 real story titles, verbatim including the markdown heading markers:
  ```
  ## Epic 1: Solicitud de crédito

  ### Story 1.1: Registro de solicitud de crédito con datos socioeconómicos
  ### Story 1.2: Validación de documentos requeridos antes de enviar a revisión
  ### Story 1.3: Revisión y decisión del asesor financiero
  ```

**Slide 2 — "Del OpenSpec al código, sin saltos" (data-index 27, código real / specs slide)**:
kept the existing bullet list and the existing real `node --test` output `.code-block`
unchanged in content. Wrapped it, alongside a new excerpt, in a two-column `.excerpt-row` (the
slide was already `is-wide`). Added one real excerpt from `spec.md`
(`.../openspec/changes/archive/2026-09-27-e1s1-registro-de-solicitud-de-credito-con-datos-socio/specs/solicitud-de-credito/spec.md`),
the first Given/When/Then scenario under "Requirement: Registro de solicitud de crédito con
datos socioeconómicos", verbatim (markdown `-`/`**` bullet/bold markers dropped, GIVEN/WHEN/THEN
wording and the backtick-quoted `borrador` kept exact; the source scenario's own truncated
title line — "Scenario: Completa el formulario con ingresos del hogar, número de dependientes,
e" — was omitted rather than shown mid-word, since only the Given/When/Then triplet was
requested):
  ```
  GIVEN un estudiante autenticado sin solicitud activa
  WHEN completa el formulario con ingresos del hogar, número de dependientes, estrato y
  ocupación del acudiente y lo envía
  THEN el sistema crea la solicitud con estado `borrador`, le asigna un identificador único y la
  asocia al estudiante
  ```

**CSS**: added `.excerpt-row` (2-column grid, same pattern as `.cmd-table`/`.epic-cards`) and
`.excerpt-label` (small uppercase caption, distinct from `.slide-kicker`'s color/size so it
doesn't read as a second kicker) to `assets/css/styles.css`. Confirmed via
`grep -rn "epic-card"` across `index.html` and `styles.css` that `.epic-cards`/`.epic-card` had
no other usage anywhere in the deck, so both the HTML block and their CSS rules (including the
`@media (max-width: 760px)` mobile override, repointed to `.excerpt-row`) were deleted as dead
code rather than left orphaned.

**Verification**: `<article>`/`</article>` balance still 33/33 (no slides added/removed,
`data-index`/kicker numbering untouched). `git diff --stat` on the repo shows `index.html` and
`assets/css/styles.css` modified by this correction; `README.md` and the four
`assets/images/screenshot-*.png` files also show as modified/untracked in the working tree, but
those are leftover uncommitted changes from the *original* (pre-correction) tutorial feature
pass documented earlier in this file — this correction pass did not touch `README.md` and did
not add, remove, or re-extract any image file. `.code-block` continues to use
`white-space: pre-wrap; overflow-x: auto`, so the new excerpts wrap instead of forcing
horizontal scroll, matching the existing test-output block's behavior. `git add`/`git commit`
intentionally not run.

## Redesign (product-pitch pass)

**Scope**: substantial redesign of module 5 (data-index 22–32, still 11 slides — no slides added
or removed, so no renumbering was needed). Goal: replace raw screenshots/tables with hand-authored
SVG diagrams and rendered structured HTML wherever the content wasn't the product's core visual
proof, per user instruction to prioritize "what can this tool do" clarity over slide-count economy
while giving the two genuinely visual-proof slides (Levantar la interfaz web, Dependencias) more
room instead of less.

**Per-slide changes**:
- **23 "Paso 1"**: kept the existing bullet list byte-for-byte; replaced the
  `screenshot-init-terminal.png` figure with a small SVG diagram (`init` fanning out via 4 arrows to
  Planeación/BMAD+OpenSpec, Memoria/Engram, Grafo de código/graphify, Comandos "/"). Marker
  `ah-init`. Two-column layout kept (not `is-wide`). `screenshot-init-terminal.png` is now
  unreferenced anywhere in the repo (confirmed via grep); left on disk rather than deleted, since
  the task explicitly allowed leaving it if not fully certain — a conservative, reversible choice.
- **24 "Los comandos del CLI"** (`is-wide`): removed `<dl class="cmd-table">`; added a one-line
  intro, a full-width primary flow diagram (`init`, dashed border + "una vez" badge, feeding a
  dashed arrow into a 3-node loop `status → close → dashboard → status`, mirroring the SPEC-WEAVER
  slide's loop/arrow-marker convention) inside a new `.cmd-flow` wrapper, and a secondary
  `.cmd-pills` row (`update`, `doctor --fix`, `bridge <epics.md>`, `context`, `history [FR-id]`,
  `vendors`, `architecture`) with the exact one-line descriptions from the old `<dl>` reused
  verbatim as `<abbr title="…">` tooltips (attribute values, so any nested `<code>`/`<abbr>` in the
  original dd text was flattened to plain text — wording itself unchanged). Primary-node
  descriptions reused verbatim too, via native SVG `<title>` on each node's `<rect>`. Markers
  `ah-cli-once` (dashed, gray) and `ah-cli` (solid, orange/yellow — tone "yellow").
- **25 "Los comandos '/' dentro del harness"** (`is-wide`): same treatment, encoding the real
  topology exactly as specified: two top entries (`/sw:new`, `/sw:adopt`) plus a second row
  (`/sw:change`, `/sw:bug`, `/sw:ticket`, with `/sw:ticket`'s two arrows landing on `/sw:change`'s
  and `/sw:bug`'s bottom edges, not past them); all four non-ticket entries converge into
  `/sw:sprint → /sw:build → /sw:status → /sw:close`; one dashed return arrow from `/sw:close` back
  to `/sw:change`'s entry point, labeled "vuelve a entrar como próximo change" (mirrors the
  SPEC-WEAVER slide's dashed "estado + comentario" pattern). Secondary pills: `/sw:doctor`,
  `/sw:sync`, `/sw:update`, `/sw:dashboard`. Every primary node and pill tooltip reuses the exact
  real descriptions from the old `<dl>` (flattened of nested `<abbr>`/`<code>` for the same
  attribute-value reason as slide 24 — e.g. `/sw:dashboard`'s tooltip keeps "SPA" as plain text).
  Markers `ah-sw` (primary flow), `ah-sw-ticket` (ticket's two routing arrows), `ah-sw-return`
  (dashed return).
- **26 "De la idea a las historias"**: kept the bullet list and both excerpts' text byte-for-byte;
  converted the two `<pre class="code-block">` blocks to rendered HTML inside new `.doc-excerpt`
  wrappers: prd.md → `<dl class="req-list">` with `FR-001..004` as `<dt><code>` and real requirement
  text as `<dd>`, FR-004's "DEBERÍA" wrapped in `<span class="req-tag">` (kept inline, rest of the
  sentence unchanged) to visually distinguish it from the DEBE requirements; epics.md → `<ol
  class="story-list">` with the 3 real Epic 1 story titles (dropped the "Story 1.1:" numeric prefix
  since the `<ol>` provides numbering — content otherwise unchanged).
- **27 "Del OpenSpec al código, sin saltos"**: reformatted only the spec.md GIVEN/WHEN/THEN excerpt
  into `<dl class="gwt-list">` with `<dt class="gwt-key">`; left the real `node --test` output
  `<pre class="code-block">` completely untouched, as instructed.
- **28 "Levantar la interfaz web"** and **29 "El dashboard: pestaña Dependencias"**: added
  `is-figure-wide` to the `<article class="slide">` (kept the default two-column split, no
  `is-wide`); trimmed each bullet list from 3 to its 2 most important points (dropped the port-retry
  detail on 28, and the embedded-terminal detail on 29 — both real but secondary to the "one
  command, browser opens" / "real dependency graph" pitch). **Chose the wide-column approach only,
  not a slide split**: the default `.slide` grid already gives the figure column ~64% of the row
  (`minmax(280px,36%) minmax(0,1fr)` — the text column is capped at 36%, so the remainder, ~64%,
  already goes to the figure); `is-figure-wide` pushes that to `minmax(200px,30%) minmax(0,1fr)`
  (~70% figure). Given the screenshots were already reasonably legible at 64% and the bullet trim
  reduces visual competition further, a dedicated split-slide felt like slide-count inflation for a
  marginal visual gain — judgment call, reversible if the rendered result still feels cramped.
- **30 "El dashboard: pestaña Progreso — inteligencia de negocio"**: removed
  `screenshot-dashboard-progreso.png` (now unreferenced, left on disk); replaced with a
  hand-authored SVG mini-dashboard: 4 metric tiles, a 6-step phase stepper, a sprint block, and a
  "Decisiones clave" block — same rounded-rect/tone-stroke/Space Grotesk visual grammar as the
  rest of the deck. No new markers needed (no arrowheads on the tile/stepper connectors beyond
  plain lines).

**Real numbers used on the Progreso slide** — captured from the live CLI, not memory:

Command run:
```
cd /home/carlos/Documents/projects/un-specweaver-video-creditos-becas-parent/demo-project/sistema-creditos-becas/
node /home/carlos/Documents/projects/un-specweaver/bin/un-specweaver.mjs status --json
```

Relevant real output (trimmed):
```json
"phases": [
  {"n":1,"key":"understand","done":false},
  {"n":2,"key":"decide","done":false},
  {"n":3,"key":"decompose","done":true},
  {"n":4,"key":"translate","done":true,"count":11},
  {"n":5,"key":"build","done":false,"count":10},
  {"n":6,"key":"close","done":false,"partial":true,"count":1}
],
"metrics": {
  "epics": 4, "stories": 11, "storiesDone": 1, "storiesPct": 9,
  "tasks": {"done":6,"total":52}, "tasksPct": 12,
  "changes": {"total":11,"archived":1,"active":10},
  "decisions": {"total":0},
  "sprint": {"waves":3,"current":1,"ready":4}
}
```

Values used on the tiles/stepper/sprint block: 4 épicas; 11 historias (1 cerrada · 9%); 6/52 tareas
(12%); 11 changes (10 activos · 1 archivado); phase stepper using the real `phases[].key`/`done`
flags (Entender/Decidir pending, Descomponer/Traducir done, Construir pending, Cerrar partial);
sprint block "3 olas · ola actual: 1 · 4 changes listas". **Deviation from a literal reading of the
JSON**: `metrics.requirements.fr` is `0`/`total: 0` in this project's live output (requirement-level
tracking isn't populated for this run) — since slide 26 elsewhere in this same module already
states the real, independently-verified "12 requisitos funcionales" from `prd.md` directly, I did
not put the contradictory `fr:0` on a tile (would look like an internal inconsistency); the tile
row uses only the metrics that are both real and non-contradictory (epics/stories/tasks/changes).
`decisions.total: 0` is also real for this project — rather than inventing example decisions for
the "Decisiones clave" block (which would violate the no-invented-facts rule), the block honestly
states "0 registradas por ahora" while describing what the feature does conceptually.

**Slide-count / index range**: module 5 unchanged at 11 slides, `data-index="22"` through
`data-index="32"` (kickers 23–33); no renumbering, no README changes needed (slide count and
module-6 description were already accurate before this pass).

**Verification performed**: `<article>`/`</article>` balance 33/33; `data-index` 0–32 continuous,
no gaps/dupes; `slide-kicker` 2–33 continuous matching `data-index+1`; full-file `html.parser`
tag-nesting check (stack-based, self-closing-aware) — 0 unclosed elements at EOF, 0 mismatches;
CSS brace balance 191/191; `grep -ci 'arquitectura|architecture'` on the whole file returns 31
(deck-wide, expected — the deck discusses software architecture broadly), but scoped to module 5
only (data-index 22–31, excluding Fuentes) it's exactly 2: the expected `architecture` CLI-command
pill tooltip (slide 24, unchanged content) and one pre-existing "deriva su arquitectura" phrase
inside `/sw:adopt`'s real description (slide 25, present in the file before this pass, about
codebase-architecture derivation — not the dashboard's Arquitectura tab); no new architecture-tab
content was added. All 8 SVG `<marker id="…">`s in the file are unique (`ah22`, `ah-tut1` pre-
existing; `ah-init`, `ah-cli`, `ah-cli-once`, `ah-sw`, `ah-sw-ticket`, `ah-sw-return` new). Every
new `<abbr title="…">` for CLI/PRD/BI/SPA reuses the canonical tooltip string verbatim (grep-
diffed against the existing unique-tooltip list — zero drift). `git status --porcelain` /
`git diff --stat` show only `index.html`, `assets/css/styles.css`, this tracking doc, and the
pre-existing (pre-this-session) uncommitted `README.md` + 4 screenshot PNGs from the earlier
tutorial-feature pass — no unrelated files touched. `git add`/`git commit` intentionally not run.

**Deviations from the spec, with reasoning**:
1. Command-pill labels drop the generic `[dir]` optional argument present in most CLI commands
   (e.g. `doctor [dir] [--fix]` → pill `doctor --fix`) — kept `[FR-id]` and `<epics.md>` since those
   are command-specific and informative; this is a compact-display simplification, not a wording
   change (the tooltip carries the full real description unchanged).
2. Primary-node and pill tooltips flatten nested `<abbr>`/`<code>` markup from the original `<dl>`
   `dd` text into plain text, because HTML attribute values (`title="…"`) cannot contain child
   elements — required by the medium, not a content change; the words themselves are unchanged.
   This does mean "SDD"/"SPA" no longer appear as separately-hoverable inline spans inside those
   specific descriptions (they were never visible text outside the `<dl>` to begin with; they're
   now inside `title=` attributes, an excluded surface per the siglas-hover convention's own scan
   rules).
3. Levantar la interfaz web / Dependencias: wide-column only, no slide split (reasoning above).
4. Progreso tile row omits the FR count (reasoning above — the live `--json` output's requirement
   metric is `0`/unpopulated for this project run, which would contradict the already-verified
   "12 FR" stated on slide 26 if put on a tile).
5. Stepper label "Descomponer" abbreviated to "Descomp." purely for diagram width — a label
   truncation, not a fact change.

## Enlarged excerpts + full spec slide

**User feedback**: "increse the size of prd.md and epics.md, the file shown inside the lisdes is
too small also add slide with the full spec if the spec is too long split in multiple slides."

**CSS (`assets/css/styles.css`)** — enlarged the real-document-excerpt typography (`.doc-excerpt`,
`.doc-excerpt-heading`, `.req-list`/`.gwt-list`, `.req-list dt`, `.req-list dd`/`.gwt-list dd`,
`.req-tag`, `.gwt-key`, `.story-list`, `.story-list li`, `.excerpt-label`, `.code-block`):
- `.doc-excerpt` / `.code-block` padding: `12px 14px` → `16px 20px`.
- Body/description text (`dd`, `.story-list`, `.code-block`): `0.86rem` → `0.98rem` (line-height
  `1.45`/`1.5` → `1.55`).
- Label text (`.req-list dt`, `.gwt-key`): `0.8rem`/`0.78rem` → `0.92rem`/`0.9rem`.
- `.doc-excerpt-heading`: `0.82rem` → `1.02rem` (kept `font-weight: 700`).
- `.excerpt-label`: `0.72rem` → `0.78rem`.
- `.req-tag`: `0.68rem` → `0.74rem`, padding `1px 5px` → `2px 6px`.
- `.req-list`/`.gwt-list` first grid column: `minmax(64px, 84px)` → `minmax(72px, 96px)` (the
  larger label font no longer wraps awkwardly).
- Proportionally scaled the two existing mobile-breakpoint overrides for these same classes:
  `@media (max-width: 760px)` `dd` bottom margin `8px` → `10px`; `@media (max-height: 560px) and
  (orientation: landscape)` `.doc-excerpt` font-size `0.85rem` → `0.92rem`.
- Added two small spacing rules (`.slide-list + .doc-excerpt`/`.slide-list + .excerpt-label`
  `margin-top: 14px`; `.doc-excerpt + .doc-excerpt` `margin-top: 12px`) needed once multiple
  `.doc-excerpt` blocks stack vertically on the new full-spec slide and the simplified
  single-column layout below — no new custom properties, fonts, or palette values.

**New slide — "El contrato completo: spec.md"** (`index.html`, module 5): inserted right after the
"De la idea a las historias: el caso real" slide and right before "Del OpenSpec al código, sin
saltos", as `data-index="27"` / kicker `28`, `class="slide is-wide"`, `data-tone="magenta"`
(alternates against the green slide before it and the orange slide after). One slide, not split —
confirmed the real `spec.md` is short (19 lines, 1 requirement, 3 Given/When/Then scenarios) by
re-reading
`/home/carlos/Documents/projects/un-specweaver-video-creditos-becas-parent/demo-project/sistema-creditos-becas/openspec/changes/archive/2026-09-27-e1s1-registro-de-solicitud-de-credito-con-datos-socio/specs/solicitud-de-credito/spec.md`
directly before writing the slide — content matches verbatim, including the real truncated
scenario title "Completa el formulario con ingresos del hogar, número de dependientes, e" (not a
typo, left as-is). Structure: the Requirement statement in a `.doc-excerpt` (heading + plain
`SHALL` sentence), followed by one `.doc-excerpt` per scenario (real scenario title as
`.doc-excerpt-heading`, GIVEN/WHEN/THEN as `.gwt-list`/`.gwt-key` — the exact pattern already used
on the "Del OpenSpec" slide, reused, not reinvented).

**Simplified "Del OpenSpec al código, sin saltos"** (now `data-index="28"` / kicker `29`): removed
the now-redundant `spec.md` `.gwt-list` excerpt (its content now lives on its own dedicated slide);
kept the bullet list and the real `node --test` output `.code-block` unchanged in content. Dropped
the `.excerpt-row` 2-column grid (only one block was left) — the test-output block now uses the
slide's full width at the enlarged sizing.

**Renumbering**: inserting the one new slide shifted every subsequent slide's `data-index` and
kicker by +1 through the end of the deck: "Levantar la interfaz web" `28→29` (kicker `29→30`), "El
dashboard: pestaña Dependencias" `29→30` (kicker `30→31`), "El dashboard: pestaña Progreso" `30→31`
(kicker `31→32`), "El video completo" `31→32` (kicker `32→33`), "Fuentes" `32→33` (kicker `33→34`).
Deck-wide `data-index` now runs `0`–`33` (34 `<article>` slides total, up from 33); every kicker
equals `data-index + 1` (cover slide, `data-index="0"`, has no kicker, as before).

**`README.md`**: bumped both slide-count mentions from `32` to `33` (the intro paragraph's "32
slides organizados en 6 módulos" and the `## Estructura` code block's "32 slides, 6 modulos"
comment) — read the pre-existing numbers first, added exactly 1 to each, per instruction (note:
the pre-existing README number was already one less than the actual `<article>` count before this
pass, a pre-existing discrepancy not introduced or otherwise touched here; only the requested "add
1" was applied).

**Verification performed**: `<article>`/`</article>` balance 34/34 (via a Python
regex/`html.parser`-style scan, not just grep); `data-index` sequence `0`–`33` continuous across
the *whole file*, no gaps or duplicates (34 unique values); every `slide-kicker` equals
`data-index + 1` continuously through "Fuentes" (`34`), the only exception being the cover slide's
absent kicker (pre-existing, expected); CSS brace balance 193/193; the full new-slide GWT content
diffed line-by-line against a fresh re-read of the real `spec.md` — exact match, including the
truncated scenario title. `git status --porcelain` / `git diff --stat` confirm only `index.html`,
`assets/css/styles.css`, and `README.md` changed by this pass (plus this tracking doc); the
pre-existing untracked `odd/tasks/tutorial-creditos-becas.md` and the four
`assets/images/screenshot-*.png` files are leftovers from the earlier, still-uncommitted
tutorial-feature pass, untouched by this correction. `git add`/`git commit` intentionally not run.
