# OpenClaw Ecosystem Digest 2026-04-30

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-04-30 06:31 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [TinyClaw](https://github.com/TinyAGI/tinyagi)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw Deep Dive

# OpenClaw Project Digest: 2026-04-30

## 1. Today's Overview
The OpenClaw ecosystem is experiencing a period of intense activity and architectural expansion, evidenced by 500 issues and 500 PRs updated in the last 24 hours. The project is currently balancing a major feature release (desktop control and new model providers) with significant stability challenges in its core memory and session management layers. While community engagement is exceptionally high, the large ratio of open to closed items (487/13 issues) suggests a growing triage backlog.

## 2. Releases: v2026.4.27
The latest release, **v2026.4.27**, focuses on expanding OpenClaw’s operational reach:
*   **Codex Computer Use:** A major leap into desktop control, shipping with status/install commands, marketplace discovery, and "fail-closed" MCP checks to ensure safety during autonomous desktop interaction.
*   **DeepInfra Bundling:** DeepInfra is now a first-class provider, bringing built-in model discovery, media generation, TTS, and embedding support.
*   **Safety Improvements:** Refined fail-closed logic for Codex-mode to prevent unauthorized system actions.

## 3. Project Progress
Today saw the merging or movement of 37 PRs, with a focus on cross-platform performance and session reliability:
*   **Windows Performance:** PR [#74173](https://github.com/openclaw/openclaw/pull/74173) addresses a massive 39-second startup delay on Windows caused by Jiti's transform pipeline, a critical fix for 100% of Windows users.
*   **Connectivity:** PR [#44996](https://github.com/openclaw/openclaw/pull/44996) adds NetBird VPN support with auto-TLS, solving "SubtleCrypto" identity issues over VPNs.
*   **UI/UX Stability:** Fixes for malformed chat blocks ([#45017](https://github.com/openclaw/openclaw/pull/45017)) and TUI reconnection hints ([#43793](https://github.com/openclaw/openclaw/pull/43793)) improve the developer experience.
*   **Skill Optimization:** Documentation and prompt engineering for skills were improved to include "trigger phrases" following 2026 Anthropic guidelines ([#44329](https://github.com/openclaw/openclaw/pull/44329)).

## 4. Community Hot Topics
*   **Cross-Platform Parity:** Issue [#75](https://github.com/openclaw/openclaw/issues/75) (101 comments) remains the top priority, with users demanding Linux and Windows desktop apps equivalent to the macOS version.
*   **The Skill Ecosystem:** Issue [#50090](https://github.com/openclaw/openclaw/issues/50090) highlights the "gap between promise and practice" for ClawHub, indicating a need for better skill-sharing primitives.
*   **Constraint Enforcement:** Users are pushing for "Hard Gates" ([#13583](https://github.com/openclaw/openclaw/issues/13583))—mechanically preventing agents from responding until specific tool-call policies are met, showing a shift toward high-stakes enterprise use.

## 5. Bugs & Stability
Stability issues are currently concentrated in memory consistency and subagent orchestration:
*   **Critical - Session Data Loss:** PR [#45044](https://github.com/openclaw/openclaw/pull/45044) is tracking a fix for session files being wiped during gateway restarts mid-turn.
*   **High - Memory Logic:** `memoryFlush` is reportedly firing unreliably ([#12590](https://github.com/openclaw/openclaw/issues/12590)), and users report "memory management chaos" ([#43747](https://github.com/openclaw/openclaw/issues/43747)) where data is stored inconsistently across different installs.
*   **Security - Prompt Injection:** The `gh-issues` skill has a reported vulnerability where untrusted issue bodies are injected into prompts without sanitization ([#45740](https://github.com/openclaw/openclaw/issues/45740)).
*   **Regression:** Windows `openclaw update` commands are failing with EBUSY errors ([#40540](https://github.com/openclaw/openclaw/issues/40540)).

## 6. Feature Requests & Roadmap Signals
*   **Progressive Context:** Tiered bootstrap loading ([#22438](https://github.com/openclaw/openclaw/issues/22438)) is gaining traction to save tokens in large workspaces.
*   **Distributed Hardware:** Support for "Brabble" as a voice-wake node ([#147](https://github.com/openclaw/openclaw/issues/147)) suggests a future roadmap into "Star Trek-style" ambient computing.
*   **Rich Messaging:** Slack Block Kit support ([#12602](https://github.com/openclaw/openclaw/issues/12602)) and MathJax/LaTeX for Control UI ([#42840](https://github.com/openclaw/openclaw/issues/42840)) indicate a push for more professional UI outputs.

## 7. User Feedback Summary
The general sentiment reflects a powerful but "leaky" platform. Power users (e.g., [#65824](https://github.com/openclaw/openclaw/issues/65824)) have identified numerous "platform gaps" after intensive daily use. The most common pain points include **silent failures** (e.g., lost Slack connections or subagent results) and **token waste** due to inefficient tool schema loading ([#14785](https://github.com/openclaw/openclaw/issues/14785)). However, the rapid adoption of "Computer Use" features shows high satisfaction with the project's cutting-edge capabilities.

## 8. Backlog Watch
*   **Onboarding Debt:** The setup wizard still doesn't include mandatory configuration for Memory/Embeddings ([#16670](https://github.com/openclaw/openclaw/issues/16670)), leading to "broken" memory features for new users.
*   **Admin Permissions:** The Feishu plugin still requires overly broad "read-only" access to the entire organization contact directory ([#13751](https://github.com/openclaw/openclaw/issues/13751)), a blocker for security-conscious corporate users that has remained open since February.
*   **Stale Backups:** There is still no standardized backup/restore utility for configuration and session history ([#13616](https://github.com/openclaw/openclaw/issues/13616)).

---

## Cross-Ecosystem Comparison

# AI Agent & Personal Assistant Open-Source Ecosystem Report: 2026-04-30

## 1. Ecosystem Overview
The open-source AI agent landscape is currently undergoing a massive architectural shift from simple chat interfaces to "autonomous operating systems" capable of desktop control, complex multi-agent delegation, and cross-platform enterprise integration. The ecosystem is bifurcated between high-resource, feature-rich platforms (OpenClaw, IronClaw) and specialized, "low-footprint" alternatives (NullClaw, NanoBot). Stability remains the primary challenge as projects struggle to keep pace with rapid LLM API evolutions, specifically regarding "thinking" modes and long-context management.

## 2. Activity Comparison

| Project | Issues (24h) | PRs (24h) | Recent Release | Health Score* |
| :--- | :---: | :---: | :--- | :---: |
| **OpenClaw** | 500 | 500 | v2026.4.27 | 7/10 |
| **NanoBot** | 10 | 30 | v0.1.5.post3 | 8/10 |
| **Hermes Agent** | 50 | 50 | v0.11.0 branch | 6/10 |
| **PicoClaw** | 12 | 22 | v0.2.7-nightly | 8/10 |
| **NanoClaw** | N/A | 50 | Opus 4.7 Update | 7/10 |
| **NullClaw** | 2 | 0 | None | 9/10 |
| **IronClaw** | 50** | 50 | v0.27.0 | 9/10 |
| **LobsterAI** | 2 | 14 | v2026.4.29 | 7/10 |
| **Moltis** | 6 | 8 | 20260429.02 | 8/10 |
| **CoPaw** | 50 | 16 | v1.1.5 | 7/10 |
| **ZeroClaw** | 39 | 50 | DeepSeek-V4 | 7/10 |

*\*Health Score based on Issue/PR ratio, triage speed, and documentation status.*
*\*\*Primarily architectural Epics related to V2 "Reborn" transition.*

## 3. OpenClaw’s Position
OpenClaw remains the undisputed **ecosystem anchor** in terms of community size and feature breadth. Its main advantage lies in its "desktop-first" philosophy—shipping functional "Computer Use" capabilities that competitors are only beginning to draft. 
*   **Technical Approach:** Unlike competitors focusing on server-side automation, OpenClaw prioritizes the "Human-in-the-loop" desktop experience via Codex and Marketplace discovery.
*   **Community Size:** With 1,000 active items in 24 hours, it operates at a scale 10x larger than most peers, though this has led to a significant triage backlog (487 open issues).
*   **Differentiation:** It acts as the "Standard Bearer" for MCP (Model Context Protocol) checks and safety logic.

## 4. Shared Technical Focus Areas
*   **Context Management & Compaction:** Almost every major project (**OpenClaw, NanoClaw, Hermes, CoPaw**) is struggling with "token waste." Projects are moving toward "Progressive Context" or tiered loading to handle the massive context windows of models like Opus 4.7 and Gemini.
*   **Reasoning/Thinking Mode Integration:** **ZeroClaw, Moltis, and IronClaw** are all racing to implement "Chain-of-Thought" (CoT) trace captures, reflecting a shift toward more transparent AI reasoning.
*   **Enterprise Channel Stability:** **CoPaw, NanoBot, and ZeroClaw** are heavily focused on stabilizing Feishu (Lark) and WeChat/WeCom integrations, highlighting a strong push toward professional/corporate utility.
*   **Sandbox Security:** **Moltis, NullClaw, and NanoBot** all reported or fixed sandbox escape vulnerabilities this cycle, showing that "Agentic Safety" is no longer theoretical but a production requirement.

## 5. Differentiation Analysis
*   **Target Users:** **NullClaw** and **PicoClaw** target hobbyists with low-resource hardware (Raspberry Pi), while **IronClaw** and **CoPaw** target enterprise developers needing robust CI/CD and multi-user configurations.
*   **Feature Focus:** **Moltis** is pivoting toward "Voice/Telephony" agents; **OpenClaw** is focusing on "Computer Use" (desktop control); **LobsterAI** is specializing in "Education/Study" via YoudaoNote skills.
*   **Architecture:** **IronClaw** is undergoing a "Reborn" rewrite to move toward a WASM-based substrate, whereas **NanoClaw** and **ZeroClaw** are leaning into containerized "Runner" models for isolation.

## 6. Community Momentum & Maturity
*   **Rapid Iteration (High Momentum):** **IronClaw** and **OpenClaw** are in "High Velocity" phases. IronClaw is particularly mature in its infrastructure, moving toward "GitHub Merge Queues" and sophisticated CI/CD pipelines.
*   **Emerging (High Growth):** **Moltis** and **ZeroClaw** are seeing a surge in "Power User" feedback, rapidly expanding into new protocols like Twilio and WukongIM.
*   **Stabilizing/Maintenance:** **LobsterAI** and **NullClaw** are in a "Refinement" phase, focusing on documentation and bug fixes rather than radical architectural changes.
*   **Stagnant:** **TinyClaw** and **ZeptoClaw** showed zero activity, suggesting potential project stasis or transition.

## 7. Trend Signals
*   **From "Chatbot" to "Worker":** The shift toward "Agent Delegation" (**PicoClaw**) and "Cron/Scheduled Tasks" (**ZeroClaw**) indicates that users want agents to work in the background, not just respond to prompts.
*   **Local-First vs. API Friction:** Community frustration with Brave/OpenAI 403 errors in **NullClaw** and **LobsterAI** suggests a growing demand for local-first search (scrapers/DuckDuckGo) and decentralized model hosting to bypass regional gates.
*   **Monetization Readiness:** The introduction of "AgentCash" in **NanoClaw** for micropayments signals the early stages of a "Pay-per-task" agent economy.
*   **UI/UX Professionalization:** Demand for "Markdown-aware splitting" and "Wide-screen table modes" shows that agents are being used for complex data analysis, necessitating more professional UI outputs than simple chat bubbles.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest – 2026-04-30

## Today's Overview
The NanoBot project remains highly active with significant churn in both development and community feedback. Today saw the release of **v0.1.5.post3**, accompanied by 30 updated PRs and 10 updated issues, reflecting a period of intense refinement for platform-specific behaviors. The activity is characterized by a strong focus on enterprise chat integration (Feishu/Lark) and the architectural transition toward more structured agent workflows.

## Releases
### v0.1.5.post3
This patch release focuses on making conversations "first-class citizens" through enhanced threading support.
*   **Key Feature:** Feishu group topics now receive isolated sessions via `reply_in_thread`.
*   **Stats:** 57 PRs merged, 12 new contributors.
*   **Breaking Changes/Notes:** Users have noted that the forced threading in Feishu may disrupt established workflows where flat replies were preferred (see Community Hot Topics).

## Project Progress
The development team successfully merged several critical PRs today, focusing on configuration flexibility and stability:
*   **Platform Refinement:** Fixed the forced `reply_in_thread` behavior in Feishu to respect user configuration ([#3547](https://github.com/HKUDS/nanobot/pull/3547)).
*   **Subagent Control:** Subagents now correctly inherit `max_iterations` from the parent agent instead of using a hardcoded limit of 15 ([#3532](https://github.com/HKUDS/nanobot/pull/3532)).
*   **Feature Modularization:** Introduced a `HookCenter` for plugin discovery and named hook points, allowing for easier external contributions ([#3541](https://github.com/HKUDS/nanobot/pull/3541)).
*   **Performance & Safety:** Implemented atomic writes for `history.jsonl` to prevent data corruption during crashes ([#3508](https://github.com/HKUDS/nanobot/pull/3508)).

## Community Hot Topics
*   **The "Bloat" Debate ([#660](https://github.com/HKUDS/nanobot/issues/660)):** With 10 comments and 5 upvotes, users are challenging the "ultra-lightweight" claim due to the inclusion of both Python and Node.js in the Dockerfile. This indicates a growing demand for a leaner, specialized image.
*   **Feishu Threading UX ([#3546](https://github.com/HKUDS/nanobot/issues/3546)):** Users are reporting "memory loss" when threading is disabled and expressing frustration over the lack of choice regarding threaded vs. flat replies.
*   **AI Agent Security ([#979](https://github.com/HKUDS/nanobot/issues/979)):** A discussion on the difficulty of preventing AI agents from executing dangerous commands like `rm -rf`, highlighting the inherent risks of interactive agent modes.

## Bugs & Stability
1.  **High Severity: Matrix Windows OS Error ([#3506](https://github.com/HKUDS/nanobot/issues/3506)):** The Matrix channel fails on Windows due to invalid characters (colons) in file paths. This prevents all outbound messaging for Windows users.
2.  **Medium Severity: Subagent Timeouts ([#970](https://github.com/HKUDS/nanobot/issues/970)):** Hardcoded limits caused long-running tasks to fail silently. *Fix merged in [#3532](https://github.com/HKUDS/nanobot/pull/3532).*
3.  **Low Severity: WebFetch Privacy ([#2341](https://github.com/HKUDS/nanobot/issues/2341)):** A privacy concern where all URLs are proxied through Jina Reader even without an API key.

## Feature Requests & Roadmap Signals
*   **Multi-Account Support:** A pending PR ([#3542](https://github.com/HKUDS/nanobot/pull/3542)) seeks to allow multiple personal WeChat accounts on one instance.
*   **Model Presets:** PR [#3358](https://github.com/HKUDS/nanobot/pull/3358) suggests adding "Model Presets" for quick switching between different LLM parameter sets (temperature, context window, etc.).
*   **6-Stage Workflow:** Experimental work is underway ([#3531](https://github.com/HKUDS/nanobot/pull/3531), [#3535](https://github.com/HKUDS/nanobot/pull/3535)) to implement a structured "Classify-Plan-Execute-Compress-Verify-Report" loop, signaling a move toward more sophisticated autonomous agents.

## User Feedback Summary
Users are generally impressed with the rapid iteration of NanoBot but are feeling the "growing pains" of platform integrations. Specifically, WeChat and Feishu users are vocal about wanting more granular control over UI elements like progress hints and thread behaviors ([#3452](https://github.com/HKUDS/nanobot/issues/3452)). There is a notable tension between the project's "ultra-lightweight" branding and its expanding feature set.

## Backlog Watch
*   **Anthropic API Compatibility ([#3095](https://github.com/HKUDS/nanobot/issues/3095)):** Users are asking for ways to use custom endpoints that follow the Anthropic API schema but aren't Anthropic-hosted; this issue has remained unresolved for two weeks despite active discussion.
*   **Telegram Group Allowlisting ([#2867](https://github.com/HKUDS/nanobot/pull/2867)):** A PR for more granular Telegram access control has been open since early April and is currently marked as "invalid," needing maintainer guidance to align with the project's ACL strategy.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest – 2026-04-30

## Today's Overview
Project activity is high, with 50 issues and 50 pull requests updated in the last 24 hours. While there were no new releases today, the development team has focused heavily on stabilizing auxiliary model fallbacks and resolving platform-specific regressions. The project is currently managing a significant volume of bug reports (44 active) relative to closed items, indicating a period of intensive maintenance following recent updates to the v0.8.0-v0.11.0 branch.

## Project Progress
The project successfully addressed several critical infrastructure and agent-logic bugs today through merged or closed PRs:
*   **Auxiliary Fallback Refactoring:** The hardcoded and now-defunct `gpt-5.2-codex` fallback was removed. The system now utilizes a more robust chain including OpenRouter and custom providers instead of "guessing" Codex model IDs ([#17765](https://github.com/NousResearch/hermes-agent/pull/17765)).
*   **CI Stability:** Main test suite regressions caused by host state and xdist leaks were stabilized, unblocking the PR validation pipeline ([#17660](https://github.com/NousResearch/hermes-agent/pull/17660)).
*   **Gamification/Dashboard:** Integrated the `hermes-achievements` plugin, adding over 60 badges and fixing session history scanning limits ([#17754](https://github.com/NousResearch/hermes-agent/pull/17754)).
*   **CLI Maintenance:** Fixed a recursive directory bug in the profile creation tool that caused infinite nesting ([#17743](https://github.com/NousResearch/hermes-agent/issue/17743)).

## Community Hot Topics
*   **The "Codex Collapse" ([#17533](https://github.com/NousResearch/hermes-agent/issues/17533)):** The rejection of `gpt-5.2-codex` by OpenAI's backend dominated discussions, as it broke all auxiliary fallbacks (compression, title generation) for ChatGPT-account users.
*   **Telegram UX Polish ([#6388](https://github.com/NousResearch/hermes-agent/issues/6388), [#6508](https://github.com/NousResearch/hermes-agent/issues/6508)):** Users are reporting friction with MarkdownV2 escaping (breaking bullet lists) and the failure of topic-bound skills to persist after a session reset.
*   **Build Failures ([#6352](https://github.com/NousResearch/hermes-agent/issues/6352), [#17773](https://github.com/NousResearch/hermes-agent/issues/17773)):** Persistent "red" status on Docker builds due to `pip` resolution depth and a new TypeScript error in the TUI build step are high-priority bottlenecks for new contributors.

## Bugs & Stability
1.  **[P1] TUI Build Failure ([#17773](https://github.com/NousResearch/hermes-agent/issues/17773)):** The `hermes --tui` command fails on `main` due to a TypeScript parameter mismatch in `/reload-mcp`.
2.  **[P1] SSH Directory Corruption ([#17767](https://github.com/NousResearch/hermes-agent/issues/17767)):** The SSH backend's `tar` extraction logic is overwriting remote home directory permissions, potentially breaking `sshd` access.
3.  **[P1] RPC Mismatch ([#17770](https://github.com/NousResearch/hermes-agent/issues/17770)):** Concurrent tool calls from `execute_code` are receiving mismatched responses, a critical thread-safety issue for the sandbox.
4.  **[P2] Docker "Resolution-Too-Deep" ([#6352](https://github.com/NousResearch/hermes-agent/issues/6352)):** The `[all]` extras graph is causing pip resolver explosions, preventing fresh Docker image builds.
5.  **[P2] Local File Access on Windows ([#17753](https://github.com/NousResearch/hermes-agent/issues/17753)):** Users report an inability to read local files in non-WSL Windows environments.

## Feature Requests & Roadmap Signals
*   **Progressive Tool Loading ([#6318](https://github.com/NousResearch/hermes-agent/pull/6318)):** A major PR is in review to dynamically swap full JSON schemas for compact text catalogs when tool definitions exceed 10% of the context window—crucial for small-context models.
*   **Expanded Platform Support:** New adapters for **Nextcloud Talk** ([#11458](https://github.com/NousResearch/hermes-agent/pull/11458)) and **Feishu Cloud Documents** ([#6378](https://github.com/NousResearch/hermes-agent/issues/6378)) are in the pipeline, signaling an expansion into enterprise-focused productivity suites.
*   **Hindsight Enhancements ([#6429](https://github.com/NousResearch/hermes-agent/issues/6429)):** Requests to include tool call/results in the Hindsight memory provider indicate a move toward more "forensic" long-term memory.

## User Feedback Summary
Current user sentiment reflects frustration with **auxiliary task reliability**. Multiple reports ([#17763](https://github.com/NousResearch/hermes-agent/issues/17763), [#17705](https://github.com/NousResearch/hermes-agent/issues/17705)) highlight 404 errors when generating chat titles, particularly with providers like MiniMax. While users appreciate the "intelligence" of the agent, the **stability of the "plumbing"** (Markdown rendering, CLI shortcuts like Ctrl+D, and provider-level configuration inheritance) remains the primary pain point.

## Backlog Watch
*   **Anthropic Auth ([#6347](https://github.com/NousResearch/hermes-agent/issues/6347)):** The OAuth refresh path has been failing with Cloudflare 403 errors since early April, leaving PKCE credentials unrefreshable.
*   **Skill Usage Tracking ([#17782](https://github.com/NousResearch/hermes-agent/issues/17782)):** The `bump_use()` function has zero production call sites, meaning skill usage metrics are currently non-functional despite existing in the codebase.
*   **Telegram Platform Hint ([#8244](https://github.com/NousResearch/hermes-agent/issues/8244)):** A lingering incorrect prompt hint tells the model that Telegram doesn't support Markdown, which contradicts actual adapter capabilities.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest: 2026-04-30

## Today's Overview
PicoClaw is experiencing a high-velocity development phase with 22 PRs and 12 issues updated in the last 24 hours. The project is undergoing a significant architectural transition, characterized by the deprecation of the Terminal User Interface (TUI) in favor of a more robust CLI and WebUI. Development focus has shifted toward advanced agentic capabilities, such as self-evolution and cross-agent delegation, while simultaneously addressing stability issues in LLM provider integrations.

## Releases
*   **v0.2.7-nightly.20260430.a36472b5**: A new nightly build has been released. 
    *   **Note**: This build includes the foundation for v0.2.7 and is considered unstable. 
    *   **Key Change**: This version likely integrates the initial "Self-Evolution" runtime and the removal of the TUI components.

## Project Progress
The project made significant strides today in both core features and infrastructure:
*   **Agent Self-Evolution**: Merged PR [#2722](https://github.com/sipeed/picoclaw/pull/2722) integrates the first usable self-evolution runtime, allowing agents to record task outcomes and generate skill drafts on the "hot path."
*   **Architectural Cleanup**: PR [#2710](https://github.com/sipeed/picoclaw/pull/2710) was closed, officially removing the TUI and adding CLI support for custom OpenAI-compatible endpoints.
*   **Channel Fixes**: Feishu image downloads were stabilized via API fallbacks and post-message support ([#2708](https://github.com/sipeed/picoclaw/pull/2708)), and tool feedback animation loops were resolved ([#2713](https://github.com/sipeed/picoclaw/pull/2713)).
*   **Infrastructure**: Docker builds were restored by fixing Go versioning and build directives ([#2700](https://github.com/sipeed/picoclaw/pull/2700)).

## Community Hot Topics
*   **TUI Deprecation ([#2208](https://github.com/sipeed/picoclaw/issues/2208))**: With 8 reactions and a finalized RFC, the community has reached a consensus to retire the TUI to focus maintenance efforts on the WebUI.
*   **OpenAI Responses API Refactor ([#2171](https://github.com/sipeed/picoclaw/issues/2171))**: Deep technical discussion (9 comments) continues regarding the migration from the Chat Completions API to the newer Responses API for better long-term alignment with OpenAI's recommendations.
*   **Multi-User Context ([#2715](https://github.com/sipeed/picoclaw/pull/2715))**: Active effort to attribute history messages per sender in group chats (Telegram/Discord), addressing a major pain point where agents lose track of who said what.

## Bugs & Stability
*   **Critical: Session History Race ([#2721](https://github.com/sipeed/picoclaw/issues/2721))**: A high-priority bug reports that the Anthropic Messages API is returning 400 errors due to a recurring race condition in `tool_use_id` within v0.2.5.
*   **Critical: Singleton Crash Loop ([#2720](https://github.com/sipeed/picoclaw/issues/2720))**: The gateway fails to start if a stale PID file exists and the PID has been reused by an unrelated system process.
*   **High: DeepSeek Compatibility ([#2718](https://github.com/sipeed/picoclaw/issues/2718))**: Non-multimodal models (like DeepSeek) are failing with 400 errors when an image exists in the history. A fix is currently in progress via PR [#2717](https://github.com/sipeed/picoclaw/pull/2717).
*   **Medium: Telegram SVG Support ([#2716](https://github.com/sipeed/picoclaw/issues/2716))**: SVG files are failing to send because the media detector incorrectly maps them to a format Telegram rejects as a "photo."

## Feature Requests & Roadmap Signals
*   **Agent Delegation ([#2531](https://github.com/sipeed/picoclaw/pull/2531))**: A major enhancement is in the works to allow agents to hand off tasks to other specialized agents synchronously.
*   **DeepSeek v4 "Thinking" Support ([#2706](https://github.com/sipeed/picoclaw/issues/2706))**: Users are requesting support for DeepSeek's `reasoning_content` field to improve the quality of AI responses.
*   **Slack Webhook Output ([#2719](https://github.com/sipeed/picoclaw/pull/2719))**: New output-only channel support for Slack is pending, which would allow easier notification integration.

## User Feedback Summary
Users are generally satisfied with the rapid expansion of agent skills but are hitting friction with **environment configuration**. Issues like [#2548](https://github.com/sipeed/picoclaw/issues/2548) (multiple auth credentials errors) and [#2623](https://github.com/sipeed/picoclaw/issues/2623) (request for `.env` file support) suggest that the configuration management system is becoming a bottleneck for new users. Additionally, users on resource-constrained hardware (Raspberry Pi Zero 2) are requesting pre-compiled builds with specialized support like WhatsApp ([#2625](https://github.com/sipeed/picoclaw/issues/2625)).

## Backlog Watch
*   **OpenAI-compatible Embeddings ([#2624](https://github.com/sipeed/picoclaw/pull/2624))**: This enhancement has gone stale and needs a maintainer review to allow local truncation of vectors for vLLM endpoints.
*   **Session Context Loss ([#2621](https://github.com/sipeed/picoclaw/issues/2621))**: An older bug regarding context loss after API timeouts remains open, potentially impacting reliability in production Docker environments.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest – 2026-04-30

## Today's Overview
NanoClaw is experiencing a surge in development activity, with 50 Pull Requests updated in the last 24 hours. The project is currently focused on expanding its integration ecosystem (Google Gemini, Matrix, and Feishu) and refining the core Agent SDK behaviors following the Opus 4.7 update. Activity is high, characterized by a rapid cycle of "Feature Skill" contributions and critical infrastructure fixes for containerized agent runners.

## Project Progress
Development today focused on enhancing connectivity and refining how agents handle large-scale context and complex scheduling.
*   **Provider Expansion:** Significant progress was made toward adding **Google Gemini** as a native provider ([#2136](https://github.com/qwibitai/nanoclaw/pull/2136)), utilizing the Gemini CLI's JSON-RPC backend.
*   **Infrastructure Fixes:** A critical fix was merged/closed regarding the `agent-runner` container, which previously overrode auto-compact settings unconditionally ([#1820](https://github.com/qwibitai/nanoclaw/issues/1820)). 
*   **Communication Bridges:** A new IPC-based decision bridge for **Feishu** (Lark) was introduced to handle pending agent decisions via a dedicated watcher ([#2141](https://github.com/qwibitai/nanoclaw/pull/2141)).
*   **Skill Deployments:** Several "OneCLI-native" skills were closed/finalized, including tools for **Gmail** ([#1961](https://github.com/qwibitai/nanoclaw/pull/1961)) and **Google Calendar** ([#1964](https://github.com/qwibitai/nanoclaw/pull/1964)), adhering to the v2 security invariant of using OneCLI for credential injection.

## Community Hot Topics
*   **Multi-Channel Strategy:** The integration of **Matrix E2EE** ([#1624](https://github.com/qwibitai/nanoclaw/pull/1624)) is a major point of interest, reflecting a demand for secure, self-hosted communication channels alongside traditional platforms.
*   **Model Control:** There is significant discussion around **Opus 4.7 behavior**, specifically how the SDK handles "thinking blocks" and context windows. Users are pushing for more granular control over these parameters as they hit token limits earlier than expected.
*   **Micropayments:** The `add-agentcash` skill ([#1767](https://github.com/qwibitai/nanoclaw/pull/1767)) introduces pay-per-call API access, signaling a move toward more complex agent-to-agent economic interactions.

## Bugs & Stability
1.  **High: Image Processing 400 Errors ([#2139](https://github.com/qwibitai/nanoclaw/issues/2139)):** Users are reporting total bot failure after specific image uploads, likely related to how the API handles multi-user document discussions.
2.  **Medium: Context Window Compaction ([#2109](https://github.com/qwibitai/nanoclaw/issues/2109)):** Reports indicate that even with Opus 4.7 (which supports 1M tokens), the system is compacting context at 200k.
3.  **Fix Pending: Schedule Task Routing ([#2142](https://github.com/qwibitai/nanoclaw/pull/2142)):** A fix is in progress for `schedule_task` dropping routing metadata (platform ID, thread ID) during system action handling.
4.  **Fix Pending: Container Env Passthrough ([#2138](https://github.com/qwibitai/nanoclaw/pull/2138)):** A PR exists to fix a bug where `AGENT_AUTO_COMPACT_WINDOW` is set on the host but fails to reach the spawned agent container.

## Feature Requests & Roadmap Signals
*   **Knowledge Base Scaffolding:** PR [#2133](https://github.com/qwibitai/nanoclaw/pull/2133) introduces a `knowledge/raw/` ingest directory, signaling that a **structured Wiki/RAG** feature is coming in the next version.
*   **Remote MCP Support:** The move to support **HTTP/SSE for MCP servers** ([#2131](https://github.com/qwibitai/nanoclaw/pull/2131)) suggests the project is moving beyond local `stdio` tools toward a more distributed architecture.
*   **Per-Group Configuration:** Users are requesting (and developers are implementing) the ability to override models and "effort" settings on a per-group basis ([#2129](https://github.com/qwibitai/nanoclaw/pull/2129)), allowing for cost-optimization across different chat contexts.

## User Feedback Summary
The current sentiment is a mix of high engagement with the "skill" ecosystem and frustration regarding **context management**. Users are clearly pushing the limits of the Opus 4.7 model and find the default "auto-compaction" behavior opaque and difficult to tune. There is a strong preference for the new **OneCLI** credential management system, as evidenced by the rapid migration of legacy tools (Gmail/YNAB) to this new standard.

## Backlog Watch
*   **PR #1624 (Matrix E2EE):** This massive PR has been open since April 4th. Given the complexity of E2EE and the demand for it, it requires urgent maintainer review to avoid falling behind the core branch.
*   **Issue #2109 (Context Compaction):** As more users move to long-context models, the 200k hard-cap/bug is becoming a primary bottleneck for power users and needs a definitive architectural fix or clearer documentation on environment variable overrides.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest - 2026-04-30

### 1. Today's Overview
Project activity for NullClaw on April 30, 2026, is relatively quiet but focused on refinement and documentation. The project saw movement on two issues, with zero new pull requests or releases. While code-level changes were minimal today, the focus remains on ensuring the project meets its core objective: running efficiently on resource-constrained hardware while maintaining a secure environment.

### 2. Releases
*No new releases were published today.*

### 3. Project Progress
Project progress today was limited to documentation cleanup. 
*   **Documentation Refinement:** Issue [#874](https://github.com/nullclaw/nullclaw/issues/874) was closed, addressing a gap in the security policy documentation. This ensures that the `default_allowed_commands` configuration—a critical security feature for an AI agent—is now properly documented for users.

### 4. Community Hot Topics
The most significant discussion currently centers on the efficiency of the project's search capabilities:
*   **#871 [bug] Critical: web_search is impractical on low-resource devices** ([Link](https://github.com/nullclaw/nullclaw/issues/871)): This issue highlights a conflict between NullClaw’s mission (running on weak devices) and its current implementation of web search. Users are reporting that current dependencies, such as the Brave Search API, introduce unnecessary friction (API keys/cost) that contradicts the "low-resource/local-first" ethos of the project.

### 5. Bugs & Stability
There is one major stability/usability bug currently under scrutiny:
*   **High Severity: Web Search Impracticality (#871):** While not a system crash, this is a functional blocker for the project’s target audience. The current `web_search` implementation is deemed "not usable in a practical way" for low-resource hardware. There is currently no PR attached to resolve this, though direct DuckDuckGo support has been suggested as a lightweight alternative.

### 6. Feature Requests & Roadmap Signals
Based on current activity, the roadmap is signaling a move toward **enhanced local-first utility**:
*   **Direct Search Integration:** The demand for direct DuckDuckGo support in #871 suggests that the next version may pivot away from heavy API dependencies in favor of "scrapers" or lighter-weight search protocols that don't require external API keys.
*   **Security Granularity:** The resolution of #874 indicates that the maintainers are tightening the security framework, likely preparing for a more robust command-execution sandbox in future updates.

### 7. User Feedback Summary
User sentiment remains constructive but highlights a growing pain point regarding **dependency management**. Users like **uMendex** emphasize that for NullClaw to succeed as a "cheap device" assistant, it must avoid "bloated" or "gated" external services. There is a clear desire for the project to remain self-contained and friction-less for the hobbyist developer.

### 8. Backlog Watch
*   **Issue #871 (Search Optimization):** This is the most critical item in the active backlog. Without a fix for the `web_search` efficiency, the project's utility on its intended hardware platforms (e.g., Raspberry Pi Zero or older microcontrollers) remains limited. Attention from maintainers is needed to define whether to implement a native scraper or a new lightweight provider.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest: 2026-04-30

## Today's Overview
IronClaw is currently in the midst of a massive architectural transition, centered on the **"Reborn" (V2) engine**. Activity is exceptionally high, with 50 PRs updated in the last 24 hours and a significant push to land the new substrate without the risks associated with monolithic PRs. The project is simultaneously streamlining its CI/CD pipeline, moving toward a "main-only" merge queue model while balancing the release of v0.27.0 with a "bug bash" targeting current staging instabilities.

## Releases
**ironclaw-v0.27.0 (2026-04-29)**
*   **Engine-V2 Core:** Introduced the canonical capability status vocabulary for the V2 runtime contract ([#2825](https://github.com/nearai/ironclaw/pull/2825)).
*   **Policy Centralization:** Unified the action-vs-capability surface policy across prompts, runtimes, and tool surfaces.
*   **Migration Note:** This version serves as a bridge, preparing the codebase for the full "Reborn" cutover.

## Project Progress
The team successfully closed 29 PRs today, primarily focusing on infrastructure and "Reborn" substrate modules:
*   **CI Infrastructure Redesign:** Closed several PRs ([#2779](https://github.com/nearai/ironclaw/pull/2779), [#2783](https://github.com/nearai/ironclaw/pull/2783), [#2877](https://github.com/nearai/ironclaw/pull/2877)) to phase out staging-promotion pipelines in favor of a GitHub Merge Queue on `main`.
*   **Reborn Substrate Landing:** Merged the secrets and network boundary crates ([#3077](https://github.com/nearai/ironclaw/pull/3077)), providing scoped secret stores and redacted network metadata.
*   **WASM Runtime:** Successfully "carved" the WASM runtime lane ([#3028](https://github.com/nearai/ironclaw/pull/3028)), though it was immediately followed by a more modern WIT-compatible implementation ([#3097](https://github.com/nearai/ironclaw/pull/3097)).
*   **Error Handling:** Fixed a critical error-poisoning bug in `ironclaw_processes` where broad `HostApiError` conversions were masking specific path errors ([#3084](https://github.com/nearai/ironclaw/pull/3084)).

## Community Hot Topics
*   **The Reborn Landing Strategy ([#2987](https://github.com/nearai/ironclaw/issue/2987)):** With 38 comments, this Epic tracks the delivery of the new architecture. The community and core team are debating how to land the "Reborn" kernel without breaking existing V1 integrations.
*   **CI Cutover ([#3104](https://github.com/nearai/ironclaw/pull/3104)):** A major overhaul of the merge queue is underway to handle the increased PR volume of the Reborn era.
*   **Native Reasoning Traces ([#3102](https://github.com/nearai/ironclaw/pull/3102)):** A new proposal to capture "Chain-of-Thought" (e.g., Anthropic's extended thinking, OpenAI's o-series summaries) as first-class IronClaw events has sparked high interest.

## Bugs & Stability
*   **Live Canary Failures:** Multiple failures in `public-smoke` and `persona-rotating` lanes ([#3075](https://github.com/nearai/ironclaw/issue/3075), [#3074](https://github.com/nearai/ironclaw/issue/3074)) indicate regressions in Anthropic-provided persona tests.
*   **TUI Regression:** High ASCII characters in the Terminal User Interface are failing to render correctly on several TTYs after recent builds ([#3103](https://github.com/nearai/ironclaw/issue/3103)).
*   **UI Race Conditions:** Issue [#3083](https://github.com/nearai/ironclaw/issue/3083) reports duplicate user creation due to missing debouncing on submission buttons.
*   **System Hangs:** Enabling "Auto Approvals" for tools currently causes the application to hang during the restart flow ([#3082](https://github.com/nearai/ironclaw/issue/3082)).

## Feature Requests & Roadmap Signals
*   **Reborn Specifics:** The roadmap is currently dominated by Reborn requirements: local developer profiles ([#3044](https://github.com/nearai/ironclaw/issue/3044)), runtime presets ([#3045](https://github.com/nearai/ironclaw/issue/3045)), and shared HTTP egress for WASM/MCP ([#3085](https://github.com/nearai/ironclaw/issue/3085)).
*   **Advanced Logic:** Native reasoning trace support ([#3102](https://github.com/nearai/ironclaw/pull/3102)) is likely to be a headline feature in the next minor release, allowing users to inspect "hidden" model thoughts.
*   **File Support:** The P1 request for PDF and document support in the web gateway ([#1341](https://github.com/nearai/ironclaw/issue/1341)) saw renewed interest, signaling a move beyond image-only multi-modality.

## User Feedback Summary
Current feedback indicates a project in a "growing pains" phase. Users are excited about the **Reborn** architecture's promise of cleaner "runtime presets" (e.g., simple "local coding agent" modes), but are frustrated by "Bug Bash" regressions in the hosted staging environments. Specifically, the UX around account management and TUI rendering is currently a primary source of friction for early adopters and QA testers.

## Backlog Watch
*   **OIDC Proxy Fix ([#2457](https://github.com/nearai/ironclaw/pull/2457)):** This PR, which makes audience claims optional for OIDC-proxying load balancers, has been open for 16 days and is critical for users deploying IronClaw in corporate environments.
*   **Web Gateway Attachments ([#1341](https://github.com/nearai/ironclaw/issue/1341)):** Originally opened in March, this enhancement remains the most requested feature for the Web UI and is currently blocked by the broader architecture shift.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest: 2026-04-30

## 1. Today's Overview
LobsterAI is currently in a stabilization phase following the release of version 2026.4.29. While daily issue volume remains low (2 new issues), there is significant background activity in the pull request pipeline, with 14 PRs updated in the last 24 hours. The project is focused on refining model configurations and expanding provider support (ChatGPT OAuth, Xiaomi Mimo), though it faces some friction regarding authentication UX and regional access restrictions.

## 2. Releases
**Version 2026.4.29 (Latest)**
*   **Model Configs:** Updated default configurations for **Volcengine** and **Qwen** ([#1828](https://github.com/netease-youdao/LobsterAI/pull/1828)).
*   **UX Improvements:** Removed an inaccurate "auto-restart" hint that appeared during the installation state to reduce user confusion ([#1](https://github.com/netease-youdao/LobsterAI/pull/1)).

## 3. Project Progress
The project recently completed a major merge of the 2026.04.27 release branch into `main` ([#1876](https://github.com/netease-youdao/LobsterAI/pull/1876)). Key advancements include:
*   **Authentication:** Added OAuth login support for ChatGPT.
*   **Provider Expansion:** New support for Xiaomi Mimo and Baidu Qianfan (Coding Plan).
*   **Skill Updates:** Significant upgrades to the YoudaoNote skill.
*   **Documentation:** Improved project specifications and README structures ([#1875](https://github.com/netease-youdao/LobsterAI/pull/1875)).

## 4. Community Hot Topics
*   **IM Bot Verification Block ([#1878](https://github.com/netease-youdao/LobsterAI/issues/1878)):** Users are reporting a "dead-end" when configuring the WeChat interface. The latest WeChat version requires a 6-digit code entry on the client side, but the LobsterAI UI currently lacks an input field for this, preventing successful setup.
*   **Security Hardening:** A cluster of "stale" but recently updated PRs ([#826](https://github.com/netease-youdao/LobsterAI/pull/826), [#828](https://github.com/netease-youdao/LobsterAI/pull/828), [#842](https://github.com/netease-youdao/LobsterAI/pull/842)) indicates a community push to fix path traversal vulnerabilities and implement URL protocol validation.

## 5. Bugs & Stability
*   **High Severity:** **IM Bot Auth Failure ([#1878](https://github.com/netease-youdao/LobsterAI/issues/1878))** – Functional blocker for WeChat integration.
*   **High Severity:** **Main Process Crash ([#852](https://github.com/netease-youdao/LobsterAI/pull/852))** – A pending fix for crashes occurring when asynchronous IPC messages are sent after a window is destroyed.
*   **Medium Severity:** **OpenAI 403 Errors ([#1877](https://github.com/netease-youdao/LobsterAI/issues/1877))** – Users in unsupported regions are facing token exchange failures.
*   **Stability:** **SQLite Bottlenecks ([#830](https://github.com/netease-youdao/LobsterAI/pull/830))** – Optimization for database write performance is pending review to reduce disk I/O overhead.

## 6. Feature Requests & Roadmap Signals
*   **Per-Channel IM Models:** Support is being developed to allow different models for different IM platforms (e.g., GPT-4 for Discord, a cheaper model for Telegram) within the same bot instance ([#838](https://github.com/netease-youdao/LobsterAI/pull/838)).
*   **MCP Batch Creation:** A new "JSON paste mode" for the Model Context Protocol (MCP) will likely allow users to import Claude Desktop configurations directly ([#835](https://github.com/netease-youdao/LobsterAI/pull/835)).
*   **Security Scanning UI:** Anticipate a new "Security Environment Scanning" dashboard to monitor Skill permissions and data access risks ([#842](https://github.com/netease-youdao/LobsterAI/pull/842)).

## 7. User Feedback Summary
The user base is currently focused on the **onboarding experience**. While the addition of new LLM providers is welcomed, users are frustrated by regional access hurdles (OpenAI 403) and UI omissions in the IM setup process. There is a clear demand for more "fail-safe" UI interactions that guide users through external authentication steps (like the 6-digit WeChat code).

## 8. Backlog Watch
*   **Security Fixes (Stale since March 25):** PRs [#826](https://github.com/netease-youdao/LobsterAI/pull/826) (shell security) and [#828](https://github.com/netease-youdao/LobsterAI/pull/828) (path traversal) have been pending for over a month. These address critical vulnerabilities and require maintainer review to ensure the application's safety.
*   **Duplicate Skill Prevention:** PRs [#827](https://github.com/netease-youdao/LobsterAI/pull/827) and [#836](https://github.com/netease-youdao/LobsterAI/pull/836) address issues where users accidentally install multiple copies of the same skill, causing workspace clutter.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest - 2026-04-30

## Today's Overview
Moltis has shown high development velocity over the last 24 hours, characterized by significant architectural expansions in communication channels and security hardening. The project released two minor updates (**20260429.01** and **.02**) to address immediate stability issues. With 8 PRs updated and 6 issues managed, the maintainers are currently focused on transitioning Moltis from a chat-based assistant into a multi-modal agent capable of handling telephony and advanced codebase indexing.

## Releases
*   **20260429.02 & 20260429.01**: These appear to be rapid-response maintenance releases. While specific changelogs weren't detailed in the metadata, they follow reports of Docker-specific regressions in Telegram connectivity and sandbox escapes. Users on the `20260428` branch are encouraged to update immediately to resolve containerized environment bugs.

## Project Progress
Significant features were merged or closed today, focusing on multi-modal identity and platform integration:
*   **Voice Personas & TTS Identity**: Merged [PR #916](https://github.com/moltis-org/moltis/pull/916), which introduces deterministic voice identities. This allows agents to maintain a consistent "spoken character" across different Text-to-Speech providers rather than improvising tone per message.
*   **Expanded Data Portability**: Merged [PR #917](https://github.com/moltis-org/moltis/pull/917), adding import support for Claude Code and Hermes data, centralizing the "Settings → Imports" UI.
*   **Security Hardening**: Closed [PR #924](https://github.com/moltis-org/moltis/pull/924), which addressed a critical vulnerability ([Issue #923](https://github.com/moltis-org/moltis/issues/923)) where sandboxed commands could bypass isolation and access the host filesystem via the `RestrictedHostSandbox`.

## Community Hot Topics
*   **Smart Chat Scrolling ([Issue #922](https://github.com/moltis-org/moltis/issues/922))**: The most discussed active issue involves a regression where a `ResizeObserver` aggressively forced the chat to the bottom, preventing users from scrolling up to read history during streaming. This highlights a high user demand for a polished, "frictionless" WebUI experience.
*   **Sandbox Security ([Issue #923](https://github.com/moltis-org/moltis/issues/923))**: This generated immediate attention as it touched on the core safety of running LLM-generated code. The rapid closure of the associated PR suggests the team prioritizes "Security First" for agentic execution.

## Bugs & Stability
1.  **Critical: Sandbox Escape ([Issue #923](https://github.com/moltis-org/moltis/issues/923))**: Commands meant for sandboxes were running on the host. **Status: Fixed** in [PR #924](https://github.com/moltis-org/moltis/pull/924).
2.  **High: Telegram Docker Failure ([Issue #918](https://github.com/moltis-org/moltis/issues/918))**: A regression in version `20260428.03` broke Telegram bots running in Docker. **Status: Closed/Resolved.**
3.  **Medium: UI Scroll Hijacking ([Issue #922](https://github.com/moltis-org/moltis/issues/922))**: Prevents reading history during active chat. **Status: Open**, fix proposed in [PR #925](https://github.com/moltis-org/moltis/pull/925).
4.  **Medium: Model Discovery Timeout ([Issue #919](https://github.com/moltis-org/moltis/issues/919))**: Discovery fails after 30 seconds, likely affecting users with large local model libraries or slow API responses.
5.  **Low: MCP Auth UI ([Issue #927](https://github.com/moltis-org/moltis/issues/927))**: Missing re-authenticate button for expired OAuth tokens on Model Context Protocol (MCP) servers.

## Feature Requests & Roadmap Signals
*   **Telephony Support**: [PR #920](https://github.com/moltis-org/moltis/pull/920) introduces a new `moltis-telephony` crate using Twilio. This signals a major move toward "Voice Agents" that can make and receive actual phone calls.
*   **Advanced Slash Commands**: [PR #926](https://github.com/moltis-org/moltis/pull/926) proposes several new commands (`/btw`, `/fast`, `/insights`, `/steer`, `/queue`). These are designed for "ephemeral side-chatter" and deeper control over the LLM's reasoning process.
*   **Autonomous Indexing**: [PR #921](https://github.com/moltis-org/moltis/pull/921) (Spec 007) aims to add auto-triggering for codebase indexing. Expect the next major version to feature a "set and forget" RAG experience for developers.

## User Feedback Summary
The recent activity reveals a split in the user base: **Power Users** are pushing for more complex agentic capabilities (Telephony, MCP, Sandbox execution), while **General Users** are currently frustrated by UI regressions (Chat scrolling) and integration stability (Telegram in Docker). There is clear satisfaction with the speed of bug fixes, but the "scroll-hijacking" issue indicates a need for more rigorous UI regression testing.

## Backlog Watch
*   **Sub-agent Configuration ([Issue #906](https://github.com/moltis-org/moltis/issues/906))**: Proposed by `bsarkisov`, this request to make sub-agents configurable in the WebUI remains open. As the project adds more "agentic" features like telephony, the lack of a granular configuration UI for sub-agents may become a bottleneck for complex workflows.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest | 2026-04-30

## Today's Overview
CoPaw maintains a high velocity of development, with 50 issues and 16 PRs updated in the last 24 hours. The project successfully transitioned to version **v1.1.5**, focusing on multilingual memory search and context optimization. Activity is characterized by a strong push toward enterprise channel stability (WeCom, Feishu) and significant frontend refinements to improve the long-term conversational experience.

## Releases: v1.1.5
The latest release focuses on refining memory and context management:
- **CJK-Aware Memory Search**: Implements character-level tokenization for Chinese, Japanese, and Korean queries while preserving Latin/digit runs, significantly improving retrieval accuracy for non-English users ([#3811](https://github.com/agentscope-ai/QwenPaw/pull/3811)).
- **Context Compaction Fallback**: Introduced a safety mechanism that triggers when LLM-based context compaction fails, ensuring agents don't crash during token-heavy sessions.

## Project Progress
Development focused heavily on UI state persistence and channel reliability:
- **UI State Persistence**: A critical fix was merged to restore chat sessions when switching between agents ([#3958](https://github.com/agentscope-ai/QwenPaw/pull/3958)) and to keep the Chat component mounted during navigation ([#3959](https://github.com/agentscope-ai/QwenPaw/pull/3959)), preventing task loss.
- **Enterprise Channels**: Fixed Feishu message deduplication ([#1403](https://github.com/agentscope-ai/QwenPaw/pull/1403)) and addressed WeCom connectivity issues.
- **Multimodal Support**: Basic infrastructure for image and file message support was integrated into the API ([#3509](https://github.com/agentscope-ai/QwenPaw/pull/3509)).
- **Documentation**: Updated the plugin system documentation and release notes ([#3946](https://github.com/agentscope-ai/QwenPaw/pull/3946), [#3918](https://github.com/agentscope-ai/QwenPaw/pull/3918)).

## Community Hot Topics
- **Channel Stability**: Issues involving Feishu and QQ channel message failures ([#981](https://github.com/agentscope-ai/QwenPaw/issues/981)) and persistent WeCom disconnection ([#2757](https://github.com/agentscope-ai/QwenPaw/issues/2757)) continue to dominate discussions, indicating a high demand for reliable enterprise integration.
- **Frontend Performance**: Users are reporting significant UI lag after 200+ rounds of dialogue, particularly during complex A2A (Agent-to-Agent) tasks ([#3350](https://github.com/agentscope-ai/QwenPaw/issues/3350), [#2890](https://github.com/agentscope-ai/QwenPaw/issues/2890)).
- **Workspace Logic**: Discussion is emerging on whether to separate "Core Config" from "User Documents" in the workspace to prevent accidental deletion of critical agent files ([#3967](https://github.com/agentscope-ai/QwenPaw/issues/3967)).

## Bugs & Stability
*   **Critical: Arbitrary File Traversal**: A vulnerability reported on Windows servers allows unauthorized file access via the path traversal ([#3955](https://github.com/agentscope-ai/QwenPaw/issues/3955)).
*   **High: Memory Error in File Reading**: `read_file_safe` incorrectly attempts to read up to 1GB into memory, causing crashes on low-RAM systems ([#3932](https://github.com/agentscope-ai/QwenPaw/issues/3932)).
*   **High: Identity Confusion**: A bug in channel message routing causes the "Main" agent to incorrectly switch to the workspace of the message sender, leading to persona breakdown ([#3957](https://github.com/agentscope-ai/QwenPaw/issues/3957)).
*   **Medium: System Freeze**: Debian 12 users report UI freezes when saving model settings unless run as root ([#3853](https://github.com/agentscope-ai/QwenPaw/issues/3853)).

## Feature Requests & Roadmap Signals
- **Multimodal Routing**: Request for separate vision model routing (e.g., using GPT-4o only for images while using a cheaper model for text) to optimize costs ([#3940](https://github.com/agentscope-ai/QwenPaw/issues/3940)).
- **Advanced Desktop Integration**: Transitioning the desktop app to **Tauri 2.x** is underway, which will likely provide a more lightweight and native experience compared to the current Electrobun-based build ([#3813](https://github.com/agentscope-ai/QwenPaw/pull/3813)).
- **GitHub Copilot Integration**: Support for GitHub Copilot as a model provider is in the final stages of review ([#3846](https://github.com/agentscope-ai/QwenPaw/pull/3846)).
- **UI Enhancements**: Strong demand for wide-screen modes for tables ([#3146](https://github.com/agentscope-ai/QwenPaw/issues/3146)) and timestamped chat logs ([#3038](https://github.com/agentscope-ai/QwenPaw/issues/3038)).

## User Feedback Summary
Users are generally impressed with CoPaw's flexibility but are expressing frustration with "vibe-coding" regressions where basic UI functionality (like input focus or paste-to-upload) is missing. There is also a recurring sentiment that the Python-based Windows implementation is resource-heavy, leading to requests for C++ core components or better Windows optimization ([#3964](https://github.com/agentscope-ai/QwenPaw/issues/3964)).

## Backlog Watch
- **Task Progress Observability**: PR [#3889](https://github.com/agentscope-ai/QwenPaw/pull/3889) (Live inter-agent task progress) is a complex feature that has been open for several days; it is vital for multi-agent coordination transparency and needs maintainer attention to finalize the hook logic.
- **WeChat Identity Mismatch**: PR [#3605](https://github.com/agentscope-ai/QwenPaw/pull/3605) regarding the "WeChat vs Weixin" naming collision in the registry has been under review for 10 days and is blocking channel stability.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

## ZeroClaw Project Digest - April 30, 2026

### 1. Today's Overview
ZeroClaw continues to see high development velocity with 50 PRs and 39 issues updated in the last 24 hours. The project is currently navigating a period of rapid channel expansion (WhatsApp, Matrix, WukongIM) while simultaneously addressing stability issues with newer high-reasoning models like DeepSeek-V4. While no new releases were tagged today, the focus is clearly on refining the "Thinking Mode" support and improving the web dashboard's parity with the CLI.

### 2. Project Progress
Several key PRs were merged or closed today, focusing on cross-platform communication and protocol stability:
*   **WukongIM Support**: Added capability to identify images from WukongIM, expanding the project's reach in specific IM ecosystems ([#6235](https://github.com/zeroclaw-labs/zeroclaw/pull/6235)).
*   **Cron Enhancements**: Merged multi-recipient delivery support for cron jobs, including CLI flags and integration for WhatsApp delivery ([#6234](https://github.com/zeroclaw-labs/zeroclaw/pull/6234)).
*   **ACP Protocol Stability**: Fixed tool output formatting for the Agent Communication Protocol (ACP), ensuring external clients receive accurate tool execution data ([#6035](https://github.com/zeroclaw-labs/zeroclaw/pull/6035)).

### 3. Community Hot Topics
*   **The "Fresh Install" Hurdle**: Issue [#6123](https://github.com/zeroclaw-labs/zeroclaw/issues/6123) is the most discussed item (15 comments), where users are hitting a workflow-blocking `default_model` error on fresh LXC/Ollama installs. This highlights a need for more robust onboarding validation.
*   **DeepSeek-V4 Integration**: Significant discussion revolves around the DeepSeek "Thinking Mode" API format. Both [#6059](https://github.com/zeroclaw-labs/zeroclaw/issues/6059) and [#6233](https://github.com/zeroclaw-labs/zeroclaw/issues/6233) highlight that current reasoning content handling is breaking multi-turn conversations, a high-priority item for users of high-intelligence, low-cost models.
*   **Token Efficiency**: Users are rallying around a proposal for "Skill Compilation" ([#5146](https://github.com/zeroclaw-labs/zeroclaw/issues/5146)) to minimize token consumption, indicating that operational cost is becoming a major concern for long-term agent usage.

### 4. Bugs & Stability
The project is currently tracking several high-severity (S0/S1) bugs:
1.  **S0 - Context Spillage**: Reported context leakage between Discord chats and scheduled cron tasks ([#5415](https://github.com/zeroclaw-labs/zeroclaw/issues/5415)). This is a critical security risk where private chat data could influence automated schedules.
2.  **S1 - Workflow Blocks**:
    *   Fresh install configuration failures ([#6123](https://github.com/zeroclaw-labs/zeroclaw/issues/6123)).
    *   WhatsApp Web fetch and Cron dispatch failures ([#6224](https://github.com/zeroclaw-labs/zeroclaw/issues/6224), [#6223](https://github.com/zeroclaw-labs/zeroclaw/issues/6223)).
3.  **S2 - Degraded Behavior**: Slack session continuity is breaking due to incorrect thread synthesis ([#6226](https://github.com/zeroclaw-labs/zeroclaw/issues/6226)), and Telegram's `mention_only` filter is failing for media messages ([#6229](https://github.com/zeroclaw-labs/zeroclaw/issues/6229)).

### 5. Feature Requests & Roadmap Signals
*   **Dream Mode ([#5849](https://github.com/zeroclaw-labs/zeroclaw/issues/5849))**: This "Periodic Memory Consolidation" feature is gaining traction. It signals a move toward agents that perform background self-reflection and long-term knowledge management during idle periods.
*   **Smart Truncation for Telegram ([#6225](https://github.com/zeroclaw-labs/zeroclaw/issues/6225))**: A request for better Markdown-aware message splitting, showing a shift in user focus toward UX and readability in chat interfaces.
*   **Web Dashboard Parity**: Multiple PRs ([#6179](https://github.com/zeroclaw-labs/zeroclaw/pull/6179), [#6220](https://github.com/zeroclaw-labs/zeroclaw/pull/6220)) suggest the next major version will likely feature a much more capable web UI, including full config CRUD and better session controls (Stop buttons, running indicators).

### 6. User Feedback Summary
Current user sentiment is a mix of **high engagement and configuration frustration**. Power users are pushing the boundaries with DeepSeek and complex Cron-to-WhatsApp workflows, but are often stymied by "silent failures" in memory recall ([#5170](https://github.com/zeroclaw-labs/zeroclaw/issues/5170)) or configuration typos that the system doesn't currently catch ([#6128](https://github.com/zeroclaw-labs/zeroclaw/issues/6128)). The recurring theme is a desire for "it just works" stability across the diverse ecosystem of supported providers and channels.

### 7. Backlog Watch
*   **Memory Session Mismatch ([#5550](https://github.com/zeroclaw-labs/zeroclaw/issues/5550))**: This issue regarding autosaved memories being invisible has been open since April 9th and remains unresolved, potentially leading to long-term "hallucinations" where the agent forgets context it supposedly saved.
*   **Security Policy Over-blocking ([#5518](https://github.com/zeroclaw-labs/zeroclaw/issues/5518))**: A high-priority bug where safe shell redirects (like `/dev/null`) are blocked by the security scanner, hindering advanced tool usage. A fix is needed to allow standard CLI patterns while maintaining safety.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/wangeDear/agents-radar).*