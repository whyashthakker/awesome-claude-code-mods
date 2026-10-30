# Existing mods and design choices

This repository was inspired by the [Claude Code Mods guide on ExplainX.ai](https://www.explainx.ai/blog/claude-code-mods-typescript-plugins-guide-2026).

Research checked on October 3, 2026. Links below are primary author repositories or Anthropic documentation. Their descriptions are based on those pages, not evidence that we installed or tested them. Their implementations and assets are not copied into this collection.

| Existing project | Use case observed | What it suggested for this collection |
| --- | --- | --- |
| [Anthropic built-in mods](https://github.com/anthropics/claude-code/tree/main/mods) | Diff panes, instruction loading, managed policy, telemetry | Use the native middleware and test-kit conventions |
| [Anthropic sample mods](https://code.claude.com/docs/en/plugins/mods/overview#try-a-sample-mod) | Context forecasts, risky command questions, edit replay | Give each mod a narrow command and observable behavior |
| [terminal-browser](https://github.com/zenbu-labs/terminal-browser) | Browse websites and previews beside a coding session | Small local viewers can reduce context switching |
| [cctop](https://github.com/tomstagl/cctop) | A broad live dashboard for session internals | Offer independent diagnostics users can select individually |
| [claude-flightdeck](https://github.com/scasella/claude-flightdeck) | Agent and permission activity dashboard | Include a read-only agent board and turn timeline |
| [cc-pr-tracker](https://github.com/sezaakgun/cc-pr-tracker) | Watch pull-request state and checks | Prefer local Git inspection in this first release, without GitHub auth |
| [claude-games](https://github.com/mohi-devhub/claude-games) | Games that respond to real coding activity | Include a small ASCII flipbook and focus tools rather than a game pack |
| [Storybloq](https://github.com/Storybloq/storybloq) | Project stories, plans, handovers, review evidence | Include explicit user-maintained decisions and handoff notes |
| [claude-mods / Mermaid and Queue](https://github.com/galElmalah/claude-mods) | Inline diagram rendering and queued follow-up prompts | Describe the diagram renderer and the queue's automatic submission behavior separately |
| [Claude Image View](https://github.com/jarrodwatts/claude-image-view) | Numbered thumbnails of pasted images above the prompt in terminals supporting the kitty graphics protocol | Link the author's marketplace installation and explain terminal requirements in the README's Community mods section |
| [prismantis](https://github.com/NahumLitvin/prismantis) | Themed reply tables, highlighted code, diagrams, charts and copy controls | List formatting alongside its optional model-context hints |
| [aside](https://github.com/JayDoubleu/aside) | Tool-less side chat over the session transcript | Explain additional model usage and the last-completed-turn snapshot |
| [secret-redactor](https://github.com/ray-amjad/awesome-claude-code-function-hooks/tree/main/plugins/secret-redactor) | Reversible masking of detected secrets, emails and IPs | State session-memory lifetime, restoration into tool inputs and detection limits |
| [pixelband](https://github.com/furqan-khan07/pixelband) | Reactive pixel scenes and user image/GIF banners | Include local-file and image-converter prerequisites |
| [Mindful Claude](https://github.com/halluton/Mindful-Claude) | A breathing animation while Claude works | Describe controls without repeating health-benefit claims |
| [Intermission](https://github.com/jarrodwatts/intermission) | Doom deathmatch during a running turn, with focus returned for completion or user input | State macOS/graphics prerequisites, game download, native process and multiplayer networking |
| [claude-doom](https://github.com/ChaseWNorton/claude-doom) | Local Doom/Freedoom gameplay in a Claude Code pane | Label the Apple Silicon alpha, pinned older runtime and separate GPL/BSD licenses |
| [karanb192/claude-code-mods](https://github.com/karanb192/claude-code-mods) | Mod building and cache/model customization | Inventory every engine call with the native validator |
| [Community mod catalogue](https://github.com/karanb192/awesome-claude-code-mods) | Discover mods with reported access footprints | Describe access per mod and distinguish validation from safety or runtime proof |

The ASCII video viewer mentioned in the request was not uniquely identified by the searches. We do not attribute it to an unverified author. **ASCII Flipbook** here is an original text-frame player, not an MP4 decoder. It uses form-feed-separated frames and a 2 fps clock; it does not download a video engine or invoke ffmpeg.

## Community listing follow-up

The [community list](COMMUNITY_MODS.md) now covers 15 external mods, including Claude Image View, 11 initial additions and two Doom projects. Discovery used GitHub searches and community directories; installation and behavior descriptions were checked against the linked authors' READMEs. Directory star counts and scanner results are not used as runtime or security evidence.

The added use cases include live web previews, PR review/check monitoring, transcript diagrams, ordered follow-ups, reply formatting, combined session diagnostics, subagent/permission timelines, side questions, reversible redaction, reactive artwork and breathing animations. These complement the bundled viewers and workflow tools without copying third-party code or changing the 50-plugin marketplace.

Some author READMEs still target the early-access function-hooks API. The listings label that status and use the current official version/enablement guidance; compatibility, native layout and security testing of external mods remain unverified. `docs/COMMUNITY_MODS.md` is included by the README generator so the source and rendered list stay in sync.

## Walkthrough-thread leads

The user supplied Lydia Hallie's walkthrough post and replies mentioning Doom gameplay and viewing suggested Magic: The Gathering cards. Searches found the two documented Doom projects above, but did not establish either as the implementation by `@original_ngv`. Their listings credit their repository authors without attributing them to that reply.

No public source or installation instructions were identified for `@full_kelly_`'s MTG-card viewer. The reply suggests a use case for showing domain-specific image references beside recommendations, but it remains an unverified project lead. MTG skills and MCP servers found in search were not treated as that mod. `@JustinPerea`'s reply provides no project name or use case to verify.

Related official documentation also identifies [You should know](https://code.claude.com/docs/en/plugins/mods/overview#mods-built-into-claude-code), an optional built-in side agent that surfaces overlooked information. It is listed separately with its enable command and organization-availability limit; it is not attributed to the walkthrough's video.

## Selection

The collection covers 8 session diagnostics, 8 Git inspectors, 10 repository viewers, 8 workspace tools, 10 utilities, and 6 workflow controls. The goals were immediate everyday use, independent installation, no paid services or external model calls, and a useful pane for every mod.

Some use cases overlap with existing projects. These are original implementations, not claims of novel invention. A full browser, external-service monitoring, advanced regex execution, or a game engine would need different dependencies and more validation, so those are left to the linked projects.

## API baseline

- [Overview](https://code.claude.com/docs/en/plugins/mods/overview): installation, version requirement, surfaces, and access model.
- [Create a mod](https://code.claude.com/docs/en/plugins/mods/create): manifests, module layout, static-analysis rules.
- [Draw in the interface](https://code.claude.com/docs/en/plugins/mods/interface): panes, controls, redrawing, persistence.
- [Test a mod](https://code.claude.com/docs/en/plugins/mods/test): stubs, timers, and native drawing tests.
- [Reference](https://code.claude.com/docs/en/plugins/mods/reference): engine methods, render sites, limits.
- [Marketplace reference](https://code.claude.com/docs/en/plugins/marketplace-reference): independent local plugin sources and distribution.

Documentation says mods require 2.1.287 or later and are enabled by default. This repository was validated using 2.1.288. Historical community pages mentioning `CLAUDE_CODE_ENABLE_FUNCTION_HOOKS` reflect early access; this repository does not require that flag.
