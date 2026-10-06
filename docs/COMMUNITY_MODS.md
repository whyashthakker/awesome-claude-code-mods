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
