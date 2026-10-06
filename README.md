# Awesome Claude Code Mods

**70 useful mods: 50 general tools + 20 Desktop mods, plus community picks. Pick one. Install it. Keep working.**

This repository was inspired by the [Claude Code Mods guide on ExplainX.ai](https://www.explainx.ai/blog/claude-code-mods-typescript-plugins-guide-2026).

70 independent, MIT-licensed bundled plugins for Git inspection, session diagnostics, local file viewers, workspace notes, text utilities, and workflow controls, including 20 additions for the Claude Desktop Code tab. Each comes with working source, native Claude Code tests, install instructions, an access description, and a screenshot. The community section adds external projects with their own installation and requirements.

![Six mod previews](assets/screenshots/collection.png)

*Screenshots show actual mod render trees captured by Claude Code's test kit with fixture data, painted in a browser preview. They are not native Claude Code app captures. [Screenshot provenance](docs/SCREENSHOTS.md).*

[Searchable gallery (open locally)](gallery.html) · [20 Desktop mods and setup](docs/DESKTOP.md) · [Community mods](#community-mods) · [Research and existing mods](docs/RESEARCH.md) · [Validation](docs/VALIDATION.md) · [Contribute](CONTRIBUTING.md)

## Start in under a minute

Requires Claude Code **2.1.287+**. Tested with **2.1.288**. Mods are enabled by default; no early-access environment flag is needed. Works in the CLI and the Desktop **Code** tab. The VS Code chat panel and `claude -p` run hooks but do not show mod panes. [Official overview](https://code.claude.com/docs/en/plugins/mods/overview).

```sh
claude plugin marketplace add whyashthakker/awesome-claude-code-mods
claude plugin install task-board@awesome-claude-code-mods
```

In Claude Code, run `/reload-plugins` if your session is already open, then `/task-board`. Type a task, press Enter to save, and use the task button to mark it done. Tab moves between controls; Esc closes a pane. Ctrl+X then Tab returns keyboard focus to a pane.

Try a mod directly from source:

```sh
git clone https://github.com/whyashthakker/awesome-claude-code-mods.git
cd awesome-claude-code-mods
claude --plugin-dir ./mods/context-meter
```

Then run `/context-meter`. Replace `context-meter` with any folder below. You can install several independently; each command uses its mod's name. No runtime dependencies or build step. Git tools require Git on PATH; package viewers expect a package.json in your project or a path you choose.

These are executable mods, not a list of prompts or skills. Research links document the ecosystem; the 70 implementations here are original, and some use cases overlap with existing mods.

## Desktop quick start

The new Desktop set includes an image-inspired usage strip, SVG charts, document and review panes, drafting tools, and a workflow board. These 20 additions target the **Claude Desktop Code tab**. [Choose a Desktop mod and see setup details](docs/DESKTOP.md).

![Six Desktop mod fixture previews](assets/screenshots/desktop-collection.png)

```sh
claude plugin marketplace add whyashthakker/awesome-claude-code-mods
claude plugin install desktop-usage-strip@awesome-claude-code-mods
```

Open a local Code session in Claude Desktop, run `/reload-plugins` if needed, then `/desktop-usage-strip`. If the marketplace is already registered, update it first with `claude plugin marketplace update awesome-claude-code-mods`. The strip shows quota/reset, context, observed token totals, and reported session USD. Its pane includes a hide/show control. Missing figures are labeled; costs are not subscription bills.

## Choose a mod

The screenshot in every row opens at full resolution. Each name links to its README, usage, access details, and source.

### Session · 8 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [Context Meter](mods/context-meter/README.md) | See the current context window fill and remaining tokens. | [![Context Meter preview](assets/screenshots/context-meter.png)](assets/screenshots/context-meter.png) |
| [Quota Watch](mods/quota-watch/README.md) | Inspect reported plan windows and their reset times. | [![Quota Watch preview](assets/screenshots/quota-watch.png)](assets/screenshots/quota-watch.png) |
| [Cache Inspector](mods/cache-inspector/README.md) | Track API cache reads, writes, and uncached input by request. | [![Cache Inspector preview](assets/screenshots/cache-inspector.png)](assets/screenshots/cache-inspector.png) |
| [Tool Timing](mods/tool-timing/README.md) | Measure observed tool latency, call counts, and failures. | [![Tool Timing preview](assets/screenshots/tool-timing.png)](assets/screenshots/tool-timing.png) |
| [Error Inbox](mods/error-inbox/README.md) | Keep the last 30 failed or refused tool calls in one pane. | [![Error Inbox preview](assets/screenshots/error-inbox.png)](assets/screenshots/error-inbox.png) |
| [Edit Heatmap](mods/edit-heatmap/README.md) | Count successful Edit and Write calls by path. | [![Edit Heatmap preview](assets/screenshots/edit-heatmap.png)](assets/screenshots/edit-heatmap.png) |
| [Turn Timeline](mods/turn-timeline/README.md) | Show duration, token totals, and interruption state per turn. | [![Turn Timeline preview](assets/screenshots/turn-timeline.png)](assets/screenshots/turn-timeline.png) |
| [Agent Board](mods/agent-board/README.md) | Inspect the subagents reported by the session. | [![Agent Board preview](assets/screenshots/agent-board.png)](assets/screenshots/agent-board.png) |

### Git · 8 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [Branch Board](mods/branch-board/README.md) | Inspect local branches, upstreams, and dirty files. | [![Branch Board preview](assets/screenshots/branch-board.png)](assets/screenshots/branch-board.png) |
| [Staged Review](mods/staged-review/README.md) | Review the staged diff before committing. | [![Staged Review preview](assets/screenshots/staged-review.png)](assets/screenshots/staged-review.png) |
| [Commit Browser](mods/commit-browser/README.md) | Browse the latest 20 commits with author and subject. | [![Commit Browser preview](assets/screenshots/commit-browser.png)](assets/screenshots/commit-browser.png) |
| [Stash Browser](mods/stash-browser/README.md) | List stashes and inspect a selected stash diff. | [![Stash Browser preview](assets/screenshots/stash-browser.png)](assets/screenshots/stash-browser.png) |
| [Worktree Map](mods/worktree-map/README.md) | List worktree paths, branches, and locked states. | [![Worktree Map preview](assets/screenshots/worktree-map.png)](assets/screenshots/worktree-map.png) |
| [Conflict Radar](mods/conflict-radar/README.md) | List unresolved paths and count conflict markers in tracked files. | [![Conflict Radar preview](assets/screenshots/conflict-radar.png)](assets/screenshots/conflict-radar.png) |
| [Blame View](mods/blame-view/README.md) | Read authorship for the first 80 lines of a chosen tracked file. | [![Blame View preview](assets/screenshots/blame-view.png)](assets/screenshots/blame-view.png) |
| [Ignore Check](mods/ignore-check/README.md) | Explain which Git ignore rule matches a path. | [![Ignore Check preview](assets/screenshots/ignore-check.png)](assets/screenshots/ignore-check.png) |

### Repository · 10 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [File Tree](mods/file-tree/README.md) | Browse one directory at a time with clickable folders. | [![File Tree preview](assets/screenshots/file-tree.png)](assets/screenshots/file-tree.png) |
| [Package Scripts](mods/package-scripts/README.md) | List npm scripts and package identity without running them. | [![Package Scripts preview](assets/screenshots/package-scripts.png)](assets/screenshots/package-scripts.png) |
| [Dependency Table](mods/dependency-table/README.md) | Inspect dependency groups from a package manifest. | [![Dependency Table preview](assets/screenshots/dependency-table.png)](assets/screenshots/dependency-table.png) |
| [TODO Finder](mods/todo-finder/README.md) | Find TODO, FIXME, and HACK notes in tracked files. | [![TODO Finder preview](assets/screenshots/todo-finder.png)](assets/screenshots/todo-finder.png) |
| [Markdown Map](mods/markdown-map/README.md) | Build a heading outline with source line numbers. | [![Markdown Map preview](assets/screenshots/markdown-map.png)](assets/screenshots/markdown-map.png) |
| [JSON Browser](mods/json-browser/README.md) | Summarize top-level JSON keys with types and a formatted preview. | [![JSON Browser preview](assets/screenshots/json-browser.png)](assets/screenshots/json-browser.png) |
| [CSV Table](mods/csv-table/README.md) | Preview quoted CSV fields, row counts, and column headers. | [![CSV Table preview](assets/screenshots/csv-table.png)](assets/screenshots/csv-table.png) |
| [Log Viewer](mods/log-viewer/README.md) | Show the last 60 lines of a small local log with an optional filter. | [![Log Viewer preview](assets/screenshots/log-viewer.png)](assets/screenshots/log-viewer.png) |
| [Env Example](mods/env-example/README.md) | List variable names and missing placeholders in an example env file. | [![Env Example preview](assets/screenshots/env-example.png)](assets/screenshots/env-example.png) |
| [File Compare](mods/file-compare/README.md) | Compare two small text files by line without editing either. | [![File Compare preview](assets/screenshots/file-compare.png)](assets/screenshots/file-compare.png) |

### Workspace · 8 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [Scratchpad](mods/scratchpad/README.md) | Save short notes beside your conversation. | [![Scratchpad preview](assets/screenshots/scratchpad.png)](assets/screenshots/scratchpad.png) |
| [Task Board](mods/task-board/README.md) | Add tasks and toggle done status. | [![Task Board preview](assets/screenshots/task-board.png)](assets/screenshots/task-board.png) |
| [Decision Log](mods/decision-log/README.md) | Record dated engineering decisions. | [![Decision Log preview](assets/screenshots/decision-log.png)](assets/screenshots/decision-log.png) |
| [Snippet Shelf](mods/snippet-shelf/README.md) | Save and copy short code or command snippets. | [![Snippet Shelf preview](assets/screenshots/snippet-shelf.png)](assets/screenshots/snippet-shelf.png) |
| [Link Shelf](mods/link-shelf/README.md) | Save labeled HTTP and HTTPS reference links. | [![Link Shelf preview](assets/screenshots/link-shelf.png)](assets/screenshots/link-shelf.png) |
| [Prompt Shelf](mods/prompt-shelf/README.md) | Save reusable prompts and put one into the composer as a draft. | [![Prompt Shelf preview](assets/screenshots/prompt-shelf.png)](assets/screenshots/prompt-shelf.png) |
| [Release Checklist](mods/release-checklist/README.md) | Keep a persistent checklist for a release. | [![Release Checklist preview](assets/screenshots/release-checklist.png)](assets/screenshots/release-checklist.png) |
| [Handoff Notes](mods/handoff-notes/README.md) | Keep a dated list of progress and next steps, then copy it. | [![Handoff Notes preview](assets/screenshots/handoff-notes.png)](assets/screenshots/handoff-notes.png) |

### Utilities · 10 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [Regex Lab](mods/regex-lab/README.md) | Test a regular expression against text and see matched ranges. | [![Regex Lab preview](assets/screenshots/regex-lab.png)](assets/screenshots/regex-lab.png) |
| [JSON Format](mods/json-format/README.md) | Validate and pretty-print JSON without touching a file. | [![JSON Format preview](assets/screenshots/json-format.png)](assets/screenshots/json-format.png) |
| [URL Lab](mods/url-lab/README.md) | Inspect URL components and decoded query parameters locally. | [![URL Lab preview](assets/screenshots/url-lab.png)](assets/screenshots/url-lab.png) |
| [Base64 Lab](mods/base64-lab/README.md) | Encode UTF-8 text or decode strict Base64. | [![Base64 Lab preview](assets/screenshots/base64-lab.png)](assets/screenshots/base64-lab.png) |
| [Time Lab](mods/time-lab/README.md) | Convert Unix seconds, milliseconds, or an ISO date to UTC. | [![Time Lab preview](assets/screenshots/time-lab.png)](assets/screenshots/time-lab.png) |
| [Hash Lab](mods/hash-lab/README.md) | Calculate SHA-256, SHA-384, or SHA-512 for UTF-8 text. | [![Hash Lab preview](assets/screenshots/hash-lab.png)](assets/screenshots/hash-lab.png) |
| [Color Lab](mods/color-lab/README.md) | Convert hex colors and measure contrast against a background. | [![Color Lab preview](assets/screenshots/color-lab.png)](assets/screenshots/color-lab.png) |
| [UUID Lab](mods/uuid-lab/README.md) | Generate up to 20 random UUID v4 values locally. | [![UUID Lab preview](assets/screenshots/uuid-lab.png)](assets/screenshots/uuid-lab.png) |
| [Text Counter](mods/text-counter/README.md) | Count words, lines, Unicode code points, and UTF-8 bytes. | [![Text Counter preview](assets/screenshots/text-counter.png)](assets/screenshots/text-counter.png) |
| [ASCII Flipbook](mods/ascii-flipbook/README.md) | Play a local text animation whose frames are separated by a form feed. | [![ASCII Flipbook preview](assets/screenshots/ascii-flipbook.png)](assets/screenshots/ascii-flipbook.png) |

### Workflow · 6 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [Focus Clock](mods/focus-clock/README.md) | Run a 25-minute focus countdown with pause, reset, and a toast. | [![Focus Clock preview](assets/screenshots/focus-clock.png)](assets/screenshots/focus-clock.png) |
| [Stopwatch](mods/stopwatch/README.md) | Time a task with start, pause, and lap markers. | [![Stopwatch preview](assets/screenshots/stopwatch.png)](assets/screenshots/stopwatch.png) |
| [Test Ledger](mods/test-ledger/README.md) | Record likely test, lint, and build commands and their tool status. | [![Test Ledger preview](assets/screenshots/test-ledger.png)](assets/screenshots/test-ledger.png) |
| [Command History](mods/command-history/README.md) | Keep the last 40 Bash command strings and copy one for reuse. | [![Command History preview](assets/screenshots/command-history.png)](assets/screenshots/command-history.png) |
| [Scope Watch](mods/scope-watch/README.md) | Warn when observed file edits leave a chosen path prefix. | [![Scope Watch preview](assets/screenshots/scope-watch.png)](assets/screenshots/scope-watch.png) |
| [Read-only Mode](mods/read-only-mode/README.md) | Toggle a reminder guard that refuses built-in mutating tools and Bash. | [![Read-only Mode preview](assets/screenshots/read-only-mode.png)](assets/screenshots/read-only-mode.png) |

### Desktop · 20 mods

| Mod | Use case | Preview |
| --- | --- | --- |
| [Desktop Usage Strip](mods/desktop-usage-strip/README.md) | Show quota, reset countdowns, tokens, and cost in a composer strip. | [![Desktop Usage Strip preview](assets/screenshots/desktop-usage-strip.png)](assets/screenshots/desktop-usage-strip.png) |
| [Desktop Context Map](mods/desktop-context-map/README.md) | Chart context headroom and sampled window growth. | [![Desktop Context Map preview](assets/screenshots/desktop-context-map.png)](assets/screenshots/desktop-context-map.png) |
| [Desktop Quota Clock](mods/desktop-quota-clock/README.md) | Chart reported plan windows with live reset countdowns. | [![Desktop Quota Clock preview](assets/screenshots/desktop-quota-clock.png)](assets/screenshots/desktop-quota-clock.png) |
| [Desktop Cost Watch](mods/desktop-cost-watch/README.md) | Set a local budget reminder against reported session USD. | [![Desktop Cost Watch preview](assets/screenshots/desktop-cost-watch.png)](assets/screenshots/desktop-cost-watch.png) |
| [Desktop Token Flow](mods/desktop-token-flow/README.md) | Chart uncached input, output, cache reads, and cache writes. | [![Desktop Token Flow preview](assets/screenshots/desktop-token-flow.png)](assets/screenshots/desktop-token-flow.png) |
| [Desktop Tool Pulse](mods/desktop-tool-pulse/README.md) | Chart completed tool latency and failures by tool. | [![Desktop Tool Pulse preview](assets/screenshots/desktop-tool-pulse.png)](assets/screenshots/desktop-tool-pulse.png) |
| [Desktop Turn Chart](mods/desktop-turn-chart/README.md) | Chart turn durations with interruption labels. | [![Desktop Turn Chart preview](assets/screenshots/desktop-turn-chart.png)](assets/screenshots/desktop-turn-chart.png) |
| [Desktop Edit Map](mods/desktop-edit-map/README.md) | Chart successful built-in edits grouped by file path. | [![Desktop Edit Map preview](assets/screenshots/desktop-edit-map.png)](assets/screenshots/desktop-edit-map.png) |
| [Desktop Agent Desk](mods/desktop-agent-desk/README.md) | Filter reported agents and copy a status snapshot. | [![Desktop Agent Desk preview](assets/screenshots/desktop-agent-desk.png)](assets/screenshots/desktop-agent-desk.png) |
| [Desktop Review Desk](mods/desktop-review-desk/README.md) | Switch between Git status, staged diff, and unstaged diff. | [![Desktop Review Desk preview](assets/screenshots/desktop-review-desk.png)](assets/screenshots/desktop-review-desk.png) |
| [Desktop File Desk](mods/desktop-file-desk/README.md) | Read a bounded text file with line filtering and path drafting. | [![Desktop File Desk preview](assets/screenshots/desktop-file-desk.png)](assets/screenshots/desktop-file-desk.png) |
| [Desktop Markdown Reader](mods/desktop-markdown-reader/README.md) | Render a local Markdown document with a source tab. | [![Desktop Markdown Reader preview](assets/screenshots/desktop-markdown-reader.png)](assets/screenshots/desktop-markdown-reader.png) |
| [Desktop Compare Desk](mods/desktop-compare-desk/README.md) | Compare two local text files in responsive side-by-side columns. | [![Desktop Compare Desk preview](assets/screenshots/desktop-compare-desk.png)](assets/screenshots/desktop-compare-desk.png) |
| [Desktop Prompt Builder](mods/desktop-prompt-builder/README.md) | Build a saved prompt from goal, constraints, and acceptance criteria. | [![Desktop Prompt Builder preview](assets/screenshots/desktop-prompt-builder.png)](assets/screenshots/desktop-prompt-builder.png) |
| [Desktop Session Brief](mods/desktop-session-brief/README.md) | Combine observed tool and turn counts with a manual handoff note. | [![Desktop Session Brief preview](assets/screenshots/desktop-session-brief.png)](assets/screenshots/desktop-session-brief.png) |
| [Desktop Bookmark Dock](mods/desktop-bookmark-dock/README.md) | Keep labeled web references with copy and delete controls. | [![Desktop Bookmark Dock preview](assets/screenshots/desktop-bookmark-dock.png)](assets/screenshots/desktop-bookmark-dock.png) |
| [Desktop Checklist Desk](mods/desktop-checklist-desk/README.md) | Move saved work items through To do, Doing, and Done columns. | [![Desktop Checklist Desk preview](assets/screenshots/desktop-checklist-desk.png)](assets/screenshots/desktop-checklist-desk.png) |
| [Desktop Workspace Home](mods/desktop-workspace-home/README.md) | Show the current workspace, Git state, and session usage together. | [![Desktop Workspace Home preview](assets/screenshots/desktop-workspace-home.png)](assets/screenshots/desktop-workspace-home.png) |
| [Desktop Break Bell](mods/desktop-break-bell/README.md) | Set an adjustable countdown with a visual progress chart and toast. | [![Desktop Break Bell preview](assets/screenshots/desktop-break-bell.png)](assets/screenshots/desktop-break-bell.png) |
| [Desktop JSON Desk](mods/desktop-json-desk/README.md) | Validate pasted JSON with a searchable key summary and formatted preview. | [![Desktop JSON Desk preview](assets/screenshots/desktop-json-desk.png)](assets/screenshots/desktop-json-desk.png) |

## Community mods

15 independently published mods. The original 14 entries were checked against author documentation on **October 3, 2026**; Spinlings was added from a maker-affiliated source and documentation review on **October 6, 2026**. Install these from their authors' marketplaces. The descriptions and commands below are documentation reviews; Spinlings' entry separately identifies maker-supplied CLI/SDK checks and static captures. These do not establish independent native testing or security audits. The collection's 70 bundled plugins and their test results are separate.

Use Claude Code **2.1.287+**. [Anthropic's current documentation](https://code.claude.com/docs/en/plugins/mods/overview#turn-mods-on-or-off) says mods are enabled by default and the old `CLAUDE_CODE_ENABLE_FUNCTION_HOOKS` flag is ignored. Entries marked **early-access documentation** describe older builds; their compatibility with the current API remains unverified. Run `/reload-plugins` after installing into an open session.

| Need | Community mod | Setup or behavior to know |
| --- | --- | --- |
| See which image you pasted | [Claude Image View](https://github.com/jarrodwatts/claude-image-view) | Kitty graphics terminal; macOS or Linux |
| Preview a web app beside your conversation | [terminal-browser](https://github.com/zenbu-labs/terminal-browser/blob/main/claude-code-plugin/README.md) | Browser binary, kitty graphics and Unicode placeholders |
| Follow PR checks and reviews while coding | [cc-pr-tracker](https://github.com/sezaakgun/cc-pr-tracker) | Authenticated GitHub CLI; polls GitHub |
| Read diagrams inside the transcript | [claude-mermaid](https://github.com/galElmalah/claude-mods) | Replaces Mermaid fences with box-art diagrams |
| Keep follow-up prompts in order | [claude-queue](https://github.com/galElmalah/claude-mods/tree/main/claude-queue) | Automatically submits queued text after turns end |
| Make tables, code and charts easier to scan | [prismantis](https://github.com/NahumLitvin/prismantis) | Reply themes, copy controls and optional diagram hints |
| Inspect cost, cache and tool latency together | [cctop](https://github.com/tomstagl/cctop) | Separate cctop binary; some readings are estimates |
| Follow subagents and permission decisions | [Flightdeck](https://github.com/scasella/claude-flightdeck) | Observes session events; does not decide permissions |
| Ask a side question about the current session | [aside](https://github.com/JayDoubleu/aside) | Makes additional model calls with token costs |
| Redact detected sensitive values before model input | [secret-redactor](https://github.com/ray-amjad/awesome-claude-code-function-hooks/tree/main/plugins/secret-redactor) | Reversible, session-memory placeholders; detection has limits |
| Personalize the prompt with reactive artwork | [pixelband](https://github.com/furqan-khan07/pixelband) | Local images/GIFs; some formats need an OS converter |
| Use waiting time for a breathing animation | [Mindful Claude](https://github.com/halluton/Mindful-Claude) | Configurable breathing band while a turn runs |
| Play Doom deathmatch while waiting | [Intermission](https://github.com/jarrodwatts/intermission) | macOS 15+, Ghostty/kitty, game download and shared-server connection |
| Play Doom locally inside a pane | [claude-doom](https://github.com/ChaseWNorton/claude-doom) | Apple Silicon alpha; pinned older Claude runtime and native engine |
| Collect creatures, trade cards and duel other players | [Spinlings](https://github.com/416rehman/spinlings) | Claude Code 2.1.287+; online world or a separate offline collection |

### [Claude Image View](https://github.com/jarrodwatts/claude-image-view) · jarrodwatts

Shows numbered thumbnails of pasted images above the prompt. They preserve aspect ratios, fit the available space, and clear when you send the prompt or remove the tags.

```text
/plugin marketplace add jarrodwatts/claude-image-view
/plugin install image-view
```

Requires macOS or Linux and a terminal with the kitty graphics protocol, such as Ghostty or kitty. Other terminals show image tags in tiles. Claude Desktop already has previews, so this mod draws nothing there. The author documents prompt/cache reads, no network requests or file writes, and a one-time `id -u` call if `CLAUDE_CODE_TMPDIR` is unset. **MIT.**

### [terminal-browser](https://github.com/zenbu-labs/terminal-browser/blob/main/claude-code-plugin/README.md) · zenbu-labs

Open `/browser localhost:3000` to keep a live web preview beside the conversation, or view a local HTML plan. The browser also offers CLI actions for agent interaction.

Install the browser binary first, for example with `brew install terminal-browser`, then install the mod:

```text
/plugin marketplace add zenbu-labs/terminal-browser
/plugin install terminal-browser@terminal-browser
```

Requires a terminal supporting kitty graphics **and Unicode placeholders**. The plugin communicates with the browser through a local HTTP server; visited websites make network requests. Upstream documents mouse-position and multiplexer limitations. **MIT; early-access documentation.**

### [cc-pr-tracker](https://github.com/sezaakgun/cc-pr-tracker) · sezaakgun

Paste a PR URL as the whole prompt to watch its merge state, review decision and required checks above the input. The mod consumes that prompt without a model turn, refreshes every minute, and alerts on changes. Paste the URL again to stop watching.

```text
/plugin marketplace add sezaakgun/cc-pr-tracker
/plugin install cc-pr-tracker@cc-pr-tracker
```

Requires `gh` authenticated for the repositories you watch. GitHub reads use your CLI access; sound and cmux notifications are optional. Upstream reports testing on 2.1.269. **MIT; early-access documentation.**

### [claude-mermaid](https://github.com/galElmalah/claude-mods) · galElmalah

Draws Mermaid blocks Claude writes as box-art diagrams where the code fence would appear in the transcript. Useful for following architecture and flow explanations inside a terminal.

```text
/plugin marketplace add galElmalah/claude-mods
/plugin install claude-mermaid@claude-mods
```

This is the diagram renderer from the author's two-mod marketplace. **MIT; early-access documentation.**

### [claude-queue](https://github.com/galElmalah/claude-mods/tree/main/claude-queue) · galElmalah

Use `/q <text>` while Claude works to hold a follow-up for a later turn. Reorder, edit or remove entries in the band, or use `/q clear`. The mod automatically submits queued prompts when the current turn and tracked background work finish; it can also run queued slash commands.

```text
/plugin marketplace add galElmalah/claude-mods
/plugin install claude-queue@claude-mods
```

Interactive terminal only; text only. Upstream documents plugin-prompt rate limits and warns that interrupting a turn with Esc can still drain the queue. **MIT; early-access documentation.**

### [prismantis](https://github.com/NahumLitvin/prismantis) · NahumLitvin

Restyles replies with themed tables, highlighted code, diagrams, charts and copy buttons. Try `/prismantis theme nord` to switch palettes.

```text
/plugin marketplace add NahumLitvin/prismantis
/plugin install prismantis@prismantis
```

Requires 2.1.287+. Its parser is not full CommonMark. The `diagramHints` option adds a model-only prompt note encouraging diagrams, so the default behavior also changes model context. **MIT**, with bundled-code notices in the upstream repository.

### [cctop](https://github.com/tomstagl/cctop) · tomstagl

Use `/cctop` for a dashboard of context, cost, cache activity, rate limits, tool latency and subagents. This is **tomstagl's cctop**; other unrelated projects use the same name.

Install the binary with `brew install tomstagl/tap/cctop` or `cargo install cctop`, then:

```text
/plugin marketplace add tomstagl/cctop
/plugin install cctop
```

Upstream describes an in-app panel with a terminal-split fallback; the latter needs a supported multiplexer or terminal. It reads local session data, and some forecasts and token calculations are explicitly estimates. **MIT.**

### [Flightdeck](https://github.com/scasella/claude-flightdeck) · scasella

Use `/flightdeck` to see subagent cards or swimlanes, permission verdicts, context/cost readings and turn receipts. Useful when delegated work is hard to follow from the transcript alone.

```text
/plugin marketplace add scasella/claude-flightdeck
/plugin install flightdeck@claude-flightdeck
```

Requires 2.1.287+. The author documents observing prompts, tool inputs and session events, with no file access, subprocesses, network requests or model calls. It shows permission outcomes without approving or blocking calls. Some advisor moments are labelled as inferred. **MIT.**

### [aside](https://github.com/JayDoubleu/aside) · JayDoubleu

Use `/aside what has changed so far?` for a side conversation about the session. A tool-less model fork answers without inserting the question or answer into the main thread.

```text
/plugin marketplace add JayDoubleu/aside
/plugin install aside@aside
```

Side answers incur model usage. During later running turns, a fork sees the last completed turn; before the first completion, the default fallback sends transcript text to a model. A side-by-side pane needs 110 columns, otherwise it opens inline. Upstream reports testing on 2.1.270. **MIT; early-access documentation.**

### [secret-redactor](https://github.com/ray-amjad/awesome-claude-code-function-hooks/tree/main/plugins/secret-redactor) · ray-amjad

Replaces detected secrets, emails and IPs in prompts, context and tool results with stable placeholders. By default, real values are restored in tool inputs so commands can still use them.

```text
/plugin marketplace add ray-amjad/awesome-claude-code-function-hooks
/plugin install secret-redactor@awesome-claude-code-function-hooks
```

The mapping stays in session memory and disappears on restart. Detection uses patterns and entropy heuristics, with configurable exceptions; it does not promise to catch every sensitive value or redact secrets the model generates. **MIT; early-access documentation.**

### [pixelband](https://github.com/furqan-khan07/pixelband) · furqan-khan07

Put an animated scene, your own image or a GIF above the prompt. Scenes react to working, completed and error states. Try `/pixelband scene city` or open `/pixelband` for controls.

```text
/plugin marketplace add furqan-khan07/pixelband
/plugin install pixelband@pixelband
```

Requires 2.1.287+. Upstream documents terminal and Desktop Code support, local image reads and saved settings. PNG/GIF decoding is built in; other image formats use macOS `sips` or ImageMagick on Linux. **MIT.**

### [Mindful Claude](https://github.com/halluton/Mindful-Claude) · halluton

Displays a breathing animation while Claude works and removes it when the reply arrives. `/breathe box` selects a four-phase exercise; `/breathe off` hides the band.

```text
/plugin marketplace add halluton/Mindful-Claude
/plugin install mindful-claude@mindful-claude
```

Settings persist across sessions. **MIT; early-access documentation.**

### [Intermission](https://github.com/jarrodwatts/intermission) · jarrodwatts

Opens a Doom deathmatch pane while Claude works, using Odamex and Freedoom. The game returns focus when Claude finishes or needs input, such as a permission response. Enable it with `/intermission`; disable it with `/intermission off`.

The author documents this installation command:

```text
/plugin install intermission --marketplace jarrodwatts/intermission
```

Requires Claude Code 2.1.287+, macOS 15+ on Apple Silicon or Intel, and Ghostty or kitty. First activation downloads about 20 MB of game files and starts a native engine. Multiplayer connects over UDP to a shared server. The author says session/project data is not sent. **Mod: MIT; Odamex and engine changes: GPL-2.0; Freedoom: BSD-3-Clause.**

### [claude-doom](https://github.com/ChaseWNorton/claude-doom) · ChaseWNorton

Runs the original Doom engine with Freedoom game data in a local `/doom` pane. Playing makes no model calls. The published alpha targets **Apple Silicon Macs, macOS 14+, Node.js 22+ and an authenticated Claude session**.

```text
/plugin marketplace add ChaseWNorton/claude-doom
/plugin install doom@faros-labs
```

The author tests on **Claude Code 2.1.278** with early-access and fullscreen-rendering flags. Its release launcher, `bash scripts/play.sh`, checks the included engine and uses or installs that pinned runtime. Compatibility with 2.1.287+ is unverified. Requires true color and mouse reporting; the recommended terminal is at least 110 columns × 50 rows. A local Node bridge starts the native engine. The alpha has no audio and discards saves/settings on close. **Mod/engine: GPL-2.0-or-later; Freedoom data: permissive BSD license.**

### [Spinlings](https://github.com/416rehman/spinlings) · 416rehman

Collect pixel creatures while Claude works, choose a team of three, trade cards and duel other players' saved teams. Duels are asynchronous, so the other player does not need to be online at the same time.

```text
/plugin marketplace add 416rehman/spinlings
/plugin install spinlings@spinlings
```

Requires **Claude Code 2.1.287+**. Restart Claude and start a new session after installing, then run `/spin`. The terminal and compatible Claude Desktop Code sessions are supported. Fresh installs start in the online world at `spinlings.dev`; `/spin world offline` uses a separate local collection. Online play sends game actions and a coarse model family to the game server. The author documents no prompt, reply, project-file or Claude-credential reads, and no model calls by the game. **Mod and server: MIT.** [Installation and source](https://github.com/416rehman/spinlings#install) · [Privacy](https://spinlings.dev/privacy).

**Review: October 6, 2026.** Maker-affiliated source and documentation review. The maintainer's strict CLI validation and 243 SDK tests passed on Claude Code **2.1.288**. Those checks are separate from this collection's 390 bundled tests and do not establish independent native layout acceptance. The original game was built with Claude; Codex assisted later UI and test iterations and this contribution.

Owner-supplied static Claude Desktop captures show a player duel and its win/streak reward. They have no visible version footer and do not establish animation behavior or independent native acceptance of v0.2.16.

![A player duel with an optional special-hit cue in Claude Desktop](https://spinlings.dev/media/desktop-player-duel-2026-10-06.png)

![A duel win and streak reward above the prompt in Claude Desktop](https://spinlings.dev/media/desktop-duel-win-2026-10-06.png)

## Built-in option: You should know

[Anthropic documents `cc-plugin-you-should-know`](https://code.claude.com/docs/en/plugins/mods/overview#mods-built-into-claude-code) as a side agent that observes longer-running work and puts potentially overlooked information above the prompt. It is disabled by default and may depend on organization availability. Check `/plugin` → Installed → Show disabled, then enable it if present:

```text
/plugin enable cc-plugin-you-should-know@builtin
```

This is an Anthropic built-in, separate from the 15 external community projects and the 70 plugins bundled here. We have not enabled or measured its model usage or runtime behavior.

## How the bundled collection behaves

- Panes open when you run a command. Refresh and input controls act on your request.
- Git inspectors run read-only argv commands. File viewers read bounded, user-chosen paths. They do not edit your repository.
- Workspace tools save user-entered items in each plugin's local store, partitioned by working directory. Clipboard and composer-draft actions require a button press.
- Session diagnostics observe activity from the moment they load. They do not reconstruct earlier turns, and their history resets on reload.
- None of the bundled mods makes network requests, calls a model, auto-submits a prompt, messages a session, or approves permission prompts. No paid service is needed for the bundled collection.

Mods run with your user permissions. Tool error text, command arguments, and notes may be sensitive; inspect what you share. `read-only-mode` and `scope-watch` are convenience guards with explicit limits, not security boundaries. [Access and security](SECURITY.md).

## Verify and develop

```sh
claude plugin validate mods/task-board --strict
claude plugin test mods/task-board
python3 scripts/check.py
python3 scripts/audit.py
```

The collection passed **70 strict plugin validations and 390 native tests** on Claude Code 2.1.288, including the original 50 mods on both Terminal and Desktop surfaces, and 20 Desktop mods at two pane widths with unsupported-surface handling. The marketplace also passed strict validation. Browser checks cover the gallery's search, filtering, and mobile width. [Check output and limits](docs/VALIDATION.md).

The test kit verifies behavior and valid element trees. Interactive native pixel/layout acceptance for all 70 mods remains open. Screenshot regeneration uses development-only Python tooling; see [Contributing](CONTRIBUTING.md).

Disable or uninstall an installed mod in `/plugin` → **Installed**. Develop against `--plugin-dir`, since installed plugin versions are cached. When publishing a change, bump its version and the marketplace entry together.

## License

[MIT](LICENSE), including a copy in every plugin folder. This is a community project and is not affiliated with Anthropic.
