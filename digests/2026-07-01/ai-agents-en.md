# OpenClaw Ecosystem Digest 2026-07-01

> Issues: 327 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-01 11:41 UTC

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

Here is the OpenClaw project digest for **July 1, 2026**.

---

## OpenClaw Project Digest — 2026-07-01

### 1. Today’s Overview
OpenClaw saw sustained high activity on July 1, with **327 issues** and **500 PRs** updated in the last 24 hours. The project released **v2026.6.11**, a polish release addressing rough edges around reliability and model setup failures. The community is heavily focused on regression bugs and session-state stability, with a cluster of "diamond lobster" severity issues around memory loss, auth provider errors, and subagent tool injection. While the release velocity is high, the volume of P1 regressions in the latest patch suggests ongoing integration fragility.

### 2. Releases
**New Release: v2026.6.11**

The team shipped v2026.6.11 today, described as a "rough edges" fix release. The release notes ([full notes](https://docs.openclaw.ai/releases/2026.6.11)) indicate fixes for:
- Misplaced replies
- Stuck sends
- Reconnect issues
- Model setup failures
- Safer admin defaults

There are no documented breaking changes or migration instructions in the release summary.

### 3. Project Progress
Today saw **83 merged/closed PRs** and **92 closed issues**. Notable merges and fixes include:

- **[CLOSED] #68936** — Autofix: add PR review autofix pipeline + Windows daemon (XL PR, closed after review)
- **[CLOSED] #98244** — Fix OpenAI Responses API 120-second streaming timeout (P1)
- **[CLOSED] #90389** — Fix Mattermost slash commands returning permanent HTTP 503 (regression fix, diamond lobster severity)
- **[CLOSED] #94964** — Fix deferred channel reload race during in-process restart (platinum hermit)
- **[CLOSED] #96344** — Fix channel-reload race causing EADDRINUSE crash loop
- **[CLOSED] #94772** — Fix gateway deferred channel reload cancellation when restart pending
- **[CLOSED] #98592** — Align macOS config path resolution
- **[CLOSED] #98596** — Preserve profile env for macOS launch at login
- **[CLOSED] #98568** — Add unit tests for Gmail watcher error classification

Key features advanced include a **Claude CLI reasoning preview** (PR #97565, XL, Discord/Telegram/Agents) and **Google Vertex AI provider with ADC auth** (PR #60860, XL, still open).

### 4. Community Hot Topics
The most engaged discussions today reflect core reliability and security concerns:

1. **#9443** (26 comments) — *Request: Prebuilt Android APK releases* — Strong user demand for official builds, submitted via AI assistant QING. Three thumbs-up. No fix PR exists.

2. **#92201** (16 comments) — *Embedded runner: freshly streamed thinking signatures intermittently invalid on replay (Anthropic)* — A diamond lobster issue with session-state/message-loss impact. Users report the recovery wrapper never fires because error text is genericized.

3. **#48003** (14 comments) — *Steer mode does not inject messages mid-turn for main sessions* — A long-standing diamond lobster P1 regression (since March 2026). Three thumbs-up. Linked PR exists but remains open.

4. **#7707** (13 comments) — *Feature Request: Memory Trust Tagging by Source* — Users want tag-based memory isolation to prevent poisoning from web scrapes/third-party skills. Diamond lobster, security impact.

5. **#45608** (11 comments) — *Pre-reset agentic memory flush* — Four thumbs-up. Users want `/new` and daily reset to flush memory like compaction does.

6. **#85103** (10 comments) — *Model fallback chain not triggered on provider-wide quota exhaustion* — A platinum hermit issue with session-state/message-loss/auth-provider impact.

7. **#85030** (9 comments) — *MCP tools not injected into subagent sessions* — Diamond lobster P1. Four thumbs-up. Beta release blocker that blocks `bundle-mcp` and per-tool allowlists.

**Underlying need**: Users are demanding better session isolation, reliable memory persistence, and smoother deployment (APK). The "diamond lobster" rating on 11 of the top 20 issues shows frustration with reliability regressions and missing developer-friendly features.

### 5. Bugs & Stability
Several regressions were reported today at critical severity:

| Severity | Issue | Description | Fix PR Exists? |
|----------|-------|-------------|----------------|
| **P0** | #84882 | memory-core Dreaming silently deletes daily memory files (data-loss, gold shrimp) | ✅ (linked) |
| **P1** | #98528 | Tool output (exec, web_fetch, web_search) returns empty after first call per turn — regression in v2026.6.11 | ❌ |
| **P1** | #98239 | `/pair qr` changes `gateway.bind` and breaks Tailscale Serve webchat | ❌ |
| **P1** | #98467 | File descriptor leak in `readUtterancesFromDir` | ❌ |
| **P1** | #92201 | Anthropic thinking signatures invalid on replay | ❌ |
| **P1** | #85030 | MCP tools not injected into subagent sessions | ❌ |
| **P1** | #98600 | ClickClack SecretRefs not resolving at runtime for exec/file | ✅ (just opened) |

A notable **v2026.6.11 regression** is #98528, where tool output returns empty after the first call per turn — this affects `exec`, `web_fetch`, and `web_search` for users who just upgraded.

### 6. Feature Requests & Roadmap Signals
Today's feature requests with strong community traction:

1. **#9443** — *Prebuilt Android APK releases* — Likely to land in next minor release. Unblocks mobile deployment.
2. **#7707** — *Memory Trust Tagging by Source* — Security-driven feature; may see early implementation in v2026.7.
3. **#45608** — *Pre-reset agentic memory flush* — High thumbs-up (4). Users want `/new` to be non-destructive.
4. **#90916** — *Topic-session families for one assistant across multiple named context lanes* — 2 thumbs-up. Moderately complex; unlikely before v2026.8.
5. **#95477** — *Post-task self-reflection for skill auto-creation* — Inspired by Hermes + SkillClaw + Reasonix. Blue-sky feature; lower priority.
6. **#71058** — *Multiple Azure/Teams bots on a single gateway* — Enterprise request; may be fast-tracked if Microsoft partnership is active.

**Prediction**: The Android APK and memory flush features have the strongest signal and are most likely to be included in v2026.7.x.

### 7. User Feedback Summary
**Pain Points (most frequent complaints):**
- **Session loss / context drop**: Users report `/new` and compaction silently lose critical memory. (#45608, #40418)
- **Tool injection failures**: MCP tools and subagent tool injection documented mechanisms don't work. (#85030)
- **Auth provider fallback issues**: Model fallback chains not firing on quota exhaustion; wrong auth profiles auto-selected. (#85103, #85126)
- **Android deployment**: No prebuilt APK despite documented Android source code. Users forced to build from source. (#9443)
- **MacOS LaunchAgent unrecoverable**: Upgrade from 2026.5.6 to 5.19 left macOS Gateway dead; only fix was Time Machine restore. (#85027)

**Satisfaction signals:**
- Release v2026.6.11 is explicitly a "we heard the feedback" release — the team is responsive.
- Three PRs today specifically address macOS deployment (config path resolution, launch-at-login, LaunchAgent plist).

**Dissatisfaction signals:**
- Multiple "beta release blocker" labels on issues show community frustration with stability.
- The high volume of P1 regressions in the latest patch erodes trust in the release pipeline.

### 8. Backlog Watch
Long-unanswered or stale important items needing maintainer attention:

| Issue | Age | Status | Why It Matters |
|-------|-----|--------|----------------|
| **#48003** — Steer mode doesn't inject mid-turn messages | 108 days (Mar 16) | Open, P1, linked PR open | Breaks basic multi-turn interaction; 14 comments, 3 thumbs-up |
| **#9443** — Prebuilt Android APK releases | 147 days (Feb 5) | Open, P2 | Blocks mobile adoption; 26 comments, 3 thumbs-up |
| **#58775** — google-vertex provider merged into google transport path | 92 days (Apr 1) | Open, P2, linked PR open | Breaks Vertex for users; 5 comments |
| **#71058** — Multiple Azure/Teams bots on single gateway | 69 days (Apr 24) | Open, P2 | Enterprise blocker; 8 comments |
| **#80286** — CLI `sessions --json` missing subagent metadata | 53 days (May 10) | Closed as stale | Was marked P2, closed without fix — affects subagent debugging |
| **#15645** (refiled as #96704) — Managed browser cookies never persist | Original issue auto-closed as stale, refiled Jun 25 | Open, P1 | Cookies lost on every restart; reported twice and stale-closed once — trust issue |

**Critical attention needed**: The **google-vertex provider regression** (#58775) has been open since April 1 with a linked PR still not merged. This is a major breaking issue for Vertex users. The **Android APK request** (#9443) has been open since February with no fix PR — this is the most-commented issue today and signals unmet mobile demand.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the provided community digest summaries.

---

### Ecosystem Overview
The personal AI assistant and agent open-source ecosystem is experiencing a period of intense, polarized activity. The landscape is bifurcated between mature, rapidly scaling reference implementations like **OpenClaw** and **Hermes Agent**, which are grappling with integration fragility from high release velocity, and a wave of next-generation forks and rewrites like **ZeroClaw** and **NanoClaw**, which are aggressively shipping new architectures (e.g., SOP engines, native adapters) while battling first-run stability issues. A common thread across nearly all projects is a painful transition from basic chatbot functionality to reliable, persistent, and secure agent-run platforms, with reliability, memory management, and multi-channel integration emerging as the core battlegrounds.

---

### Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Release Status (Today) | Health Score & Commentary |
|---|---|---|---|---|
| **OpenClaw** | 327 | 500 | v2026.6.11 (Polished) | **High Velocity / Fragile**. Extremely high activity but a significant volume of P1 regressions in the latest patch. |
| **ZeroClaw** | 25 | 50 | Pre-v0.8.3 | **Intense Build Phase**. High open vs. closed ratio, indicating rapid feature expansion with unresolved bugs. |
| **Hermes Agent** | 50 | 50 | None | **High / Stabilizing**. Healthy closure rate (42% issues, 40% PRs) with a coordinated effort to salvage stalled fixes. |
| **LobsterAI** | -- | 26 | 2026.6.30 (Patch) | **Burst of Completion**. Very high merge rate (23/26), rapidly clearing technical debt. |
| **CoPaw** | 14 | 50 | Pre-v2.0.0b2 | **High / Pre-Release**. Intense bug-fixing and feature work, with 50% of PRs merged. Community testing is active. |
| **NanoClaw** | 8 | 17 | None | **High / Teething**. High developer activity but plagued by a critical cluster of infrastructure bugs from recent changes. |
| **IronClaw** | 20 | 50 | None | **High / Fixing**. Heavy focus on stabilizing the "Reborn" runtime, with 30 PRs merged to fix concurrency issues. |
| **NanoBot** | -- | 41 | None | **Moderate / Consolidating**. High PR activity with a focus on security hardening (9 merged). Likely near a release candidate. |
| **PicoClaw** | 4 | 5 | Nightly v0.3.1 | **Steady Maintenance**. Low but consistent activity with community contribution engagement. |
| **NullClaw** | 1 | 4 | None | **Low / Maintenance**. Steady but quiet; no new releases, focused on merging dependency and cron fixes. |
| **Moltis** | 0 | 3 | None | **Maintenance Only**. Zero feature or bug activity; only automated dependency bumps. |
| **TinyClaw** | 0 | 0 | None | **Dormant**. |
| **ZeptoClaw** | 0 | 0 | None | **Dormant**. |

---

### OpenClaw's Position

- **Advantages vs. Peers**: OpenClaw’s dominance in scale is undeniable. With 327 issues and 500 PRs updated daily, it dwarfs all other projects listed. Its community is the largest, with the most active feature requests and bug reports. The release of v2026.6.11 as a direct response to user feedback shows a highly responsive development cycle.
- **Technical Approach Differences**: OpenClaw is a core reference, acting as a full-stack system. Peers like **ZeroClaw** are innovating with specific architectural concepts (e.g., a "Standard Operating Procedure" engine for agent workflows), while **NanoBot** focuses more narrowly on security and supporting core API standards.
- **Community Size Comparison**: OpenClaw’s community is an order of magnitude more active than its closest competitors. **Hermes Agent** (50 issues, 50 PRs) shows a significantly smaller but still highly active community, while a project like **PicoClaw** (4 issues, 5 PRs) represents a much smaller, niche user base. This scale for OpenClaw creates both power (extensive feedback) and friction (integration fragility).

---

### Shared Technical Focus Areas

Multiple projects are converging on the same critical challenges, indicating shared industry pain points.

1.  **Session State & Memory Persistence**: This is the #1 reliability issue across the board.
    - **OpenClaw**: Reports of "silent memory loss" (#84882) and "session-state instability."
    - **Hermes Agent**: Multiple fixes for "session state loss" and "context bleed" (#47268, #46934).
    - **NanoClaw**: Reports of "silent message swallowing" (#2902) where messages are lost without feedback.
    - **CoPaw**: Fixes are being merged to prevent "message loss during hot-reload" (#5562).

2.  **Multi-Channel & Provider Reliability**: Users demand their agents work everywhere, leading to integration fragility.
    - **OpenClaw**: Provider errors (Google Vertex, Mattermost) and "auth provider fallback issues" (#85103).
    - **Hermes Agent**: "Codex inconsistency" (#13834) and requests for native Gemini/Vertex AI providers (#12639).
    - **ZeroClaw**: Bugs in Telegram channel configuration (#8505) and missing MCP tool discovery (#8193).
    - **CoPaw**: Fixes for Telegram, QQ Channel, and WeChat adapters.

3.  **Tool/Plugin Discovery & Injection**: The ability for agents to reliably find and use tools is a persistent pain point.
    - **OpenClaw**: "MCP tools not injected into subagent sessions" (#85030) and "Tool output returns empty" (#98528).
    - **ZeroClaw**: "MCP tools missing from TUI sessions" (#8193).
    - **NanoBot**: Fixes for MCP resource/prompt gating (#4436).

4.  **Security Hardening**: SSRF, command injection, and credential management are being actively addressed.
    - **NanoBot**: Merged fixes for API authentication (#4548) and SSRF validation for DNS rebinding (#4611).
    - **Hermes Agent**: Fixed command approval bypasses via shell obfuscation (#30100).
    - **ZeroClaw**: Fix for zip-bomb skill extraction (#8554) and runtime policy for OTel privacy (#8462).

---

### Differentiation Analysis

- **Feature Emphasis**: **OpenClaw** is the broadest platform, focusing on a comprehensive set of features. **ZeroClaw** is differentiating with a proprietary "SOP engine" for complex workflow automation. **LobsterAI** is heavily emphasizing its "Cowork" and "OpenClaw" flows for collaborative coding. **NanoClaw** is pushing the boundaries on native channel adapters (Matrix, Discord, WeChat) and media handling.
- **Target Users**: **OpenClaw** and **Hermes Agent** target a broad developer audience looking for a powerful, customizable agent. **ZeroClaw** appears to target enterprise users with a focus on rigorous process automation (SOPs) and reliability. **LobsterAI** is strongly rooted in the Chinese developer community and emphasizes integration with programming tools. **PicoClaw** and **NullClaw** are smaller, more experimental forks likely targeting a technical, tinkerer audience.
- **Technical Architecture**: **IronClaw** is unique in its intense focus on its "Reborn" runtime architecture, specifically solving concurrency problems related to filesystem contention. **Moltis** appears to be an infrastructure project (documentation, website tooling) rather than a direct agent competitor.

---

### Community Momentum & Maturity

- **Tier 1 (High Velocity / Mass Adoption)**: **OpenClaw** is in a class of its own for raw activity. It is the "Linux kernel of the ecosystem"—the largest and most complex, but showing signs of stress from its own scale.
- **Tier 2 (Rapidly Iterating / Pre-Release)** : **ZeroClaw**, **CoPaw**, and **NanoClaw** are building at incredible speed. **ZeroClaw** is deep in a major feature cycle (SOP engine). **CoPaw** is in a pre-release phase for v2.0.0. **NanoClaw** is shipping daily but its "teething" problems suggest its architecture is still finding its footing. **IronClaw** is in a critical "fixing" phase, stabilizing its Reborn runtime.
- **Tier 3 (Stabilizing / Consolidating)**: **Hermes Agent** and **NanoBot** are showing healthy signs of maturity. They have high closure rates and are actively addressing technical debt and security. **Hermes Agent**'s "salvage" PRs are a sign of a disciplined team.
- **Tier 4 (Maintenance / Small Community)**: **PicoClaw** and **NullClaw** are healthy but smaller forks. **Moltis** is purely in maintenance mode.
- **Tier 5 (Dormant)**: **TinyClaw** and **ZeptoClaw** show no recent activity.

---

### Trend Signals

1.  **The Reliability Wall**: The single strongest signal from the community is that **reliability trumps features**. High-severity bugs related to session loss, silent failures, and tool injection gaps are the most discussed pain points, even for the most advanced projects. Users are willing to forgive missing features but not undependable agents.
2.  **The "Post-Chatbot" Maturation**: The ecosystem is moving away from "chat with an LLM" and toward "manage a persistent, autonomous agent." This is driving demand for **observability** (better logs, OTel policies), **state management** (memory persistence, session isolation), and **workflow automation** (cron engines, MCP tools, SOPs).
3.  **Platform-Native Thinking**: Users are no longer satisfied with a single CLI client. There is a massive and growing demand for native integrations across **Telegram, Discord, WhatsApp, Matrix, Slack, and QQ**. The ability to "set it and forget it" across channels is becoming a baseline requirement.
4.  **Security as a First-Class Feature**: With SSRF, command injection, and credential leaks being actively reported, security is no longer an afterthought. Projects that demonstrate proactive security hardening (like **NanoBot** and **Hermes Agent**) are building significant user trust.
5.  **The Chinese Developer Giant**: The presence of **LobsterAI** and the heavy activity in Chinese on the **CoPaw** project signals that the Chinese developer ecosystem is a massive, highly active, and increasingly influential force in the open-source AI agent space, driving demand for local integrations (WeChat, QQ) and Chinese-language support.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-01

## Today's Overview

NanoBot is in a period of **intense development activity**, with 41 pull requests updated in the last 24 hours and 9 merged/closed. The project maintains a healthy balance of feature work, security hardening, and bug fixing. The security posture is being actively strengthened, with two critical security issues addressed via merged PRs today. Community engagement is moderate, with open issues receiving timely attention from maintainers. No new releases were published today, suggesting the team is consolidating multiple changes before a version bump.

## Releases

**None.** No new releases were published today. Given the volume of merged PRs (9), a release candidate may be imminent.

## Project Progress

**9 PRs merged/closed today**, representing significant forward momentum:

- **Security Hardening** (Critical):
  - `#4548` — **API authentication parity**: OpenAI-compatible API server now requires `api_key` when binding to all interfaces (matching WS gateway behavior). Fixes issue `#4490`.
  - `#4436` — **MCP resource/prompt gating**: `enabledTools` allowlist now properly gates resource and prompt registration, not just tool listing. Fixes security advisory `#4434`.
  - `#4610` — **Structured tool error results**: Introduces `ToolResult.error(...)` marker, migrating away from fragile `result.startswith("Error")` string matching.

- **Refactoring & Developer Experience**:
  - `#4613` — WebUI provider model catalog classification moved to `ProviderSpec` metadata with `auto` default; simplifies provider registry maintenance.
  - *(Note: No version bump or changelog generated from these merges)*

## Community Hot Topics

1. **Issue #4615** `[bug] gateway startup crashes when CronService calls fsync() on parent directory`  
   *Comments: 2 | Updated: Today*  
   **Analysis**: This is a cross-platform filesystem compatibility bug affecting VirtualBox shared folders (vboxsf) and similar FUSE filesystems. Community member `chengyongru` already authored fix PR `#4617` within hours, demonstrating rapid maintainer response.  
   [View Issue](HKUDS/nanobot Issue #4615)

2. **Issue #4612** `[enhancement] Support openai response api`  
   *Comments: 1 | Updated: Today*  
   **Analysis**: User `practitionerjane` requests compatibility with OpenAI's *Response API* (not the Assistants API), indicating a gap in NanoBot's provider abstraction. This suggests emerging demand for OpenAI's newer API surface beyond the Chat Completions endpoint.  
   [View Issue](HKUDS/nanobot Issue #4612)

3. **Issue #4611** `[security] DNS rebinding TOCTOU in SSRF validation`  
   *Comments: 0 | 👍: 1*  
   **Analysis**: A serious SSRF bypass vector — `validate_url_target` does not pin resolved IP addresses, leaving a window for DNS rebinding attacks. No fix PR exists yet. The single upvote suggests community awareness but limited vocal concern.  
   [View Issue](HKUDS/nanobot Issue #4611)

## Bugs & Stability

| Severity | Issue | Description | Fix Status |
|----------|-------|-------------|------------|
| **High** | `#4615` | Gateway startup crash: `CronService.fsync()` fails on parent directories of vboxsf/fuse filesystems (`EINVAL`) | Fix PR `#4617` opened today by `chengyongru` — gracefully ignores `EINVAL` on directory fsync |
| **High** | `#4611` | DNS rebinding TOCTOU in SSRF validation allows internal network probing | No fix PR yet; vulnerability is latent and may require architectural changes to pin resolved IPs |
| **Medium** | `#4608` (PR) | Tool result context overflow: accumulated tool results can exceed context window budget | Fix PR `#4608` adds emergency truncation for current-iteration tool results |

## Feature Requests & Roadmap Signals

1. **OpenAI Response API support** (`#4612`) — User wants to connect NanoBot to GPT models via OpenAI's newer Response API. Given NanoBot's existing OpenAI-compatible layer, this may be a relatively straightforward provider abstraction addition. **Prediction**: Could appear in next minor release (e.g., v0.12.x) as a provider plugin.

2. **Multiline CLI input** (`#4614` PR by `m11y`) — Switches interactive CLI to `PromptSession` with Shift+Enter for newlines. This is a quality-of-life improvement that appears ready for merge. **Prediction**: Will merge within days.

3. **Context optimization** (`#4581` PR by `hamb1y`) — Reduces input tokens per turn, improving cost-efficiency and extending low-context model viability. **Prediction**: Likely to land in next release as it addresses a common user pain point (costs).

## User Feedback Summary

**Pain Points**:
- **Cross-platform filesystem compatibility**: Users on VirtualBox/Vagrant environments (vboxsf) experience startup crashes (`#4615`). Workaround exists (fix PR `#4617`).
- **Windows command execution inconsistency**: Multi-line vs single-line commands behave differently on Windows (`#4544`, fix PR `#4545`). Caused by inconsistent shell routing between `cmd.exe` and PowerShell.
- **API security gap resolved**: Users noted the OpenAI-compatible API server had no authentication, unlike the WS gateway (`#4490`). Now closed via PR `#4548`.

**Satisfaction Signals**:
- Rapid triage and fix PR creation for reported bugs (e.g., `#4615` → `#4617` in same day).
- Active community PRs addressing long-standing issues (context optimization `#4581`, memory consolidation `#4373`, `#4402`).

## Backlog Watch

**Long-unanswered / Stale Items Needing Maintainer Attention**:

| Issue/PR | Days Open | Description | Concern Level |
|----------|-----------|-------------|---------------|
| `#4611` | 1 day | DNS rebinding TOCTOU in SSRF validation — **no fix PR yet** | 🔴 High — Security vulnerability with no patch in sight |
| `#4402` (PR) | 13 days | Opt-in eager memory consolidation — no recent maintainer activity | 🟡 Medium — Valuable feature but stalled |
| `#4373` (PR) | 15 days | Memory delivery context preservation — waiting for review | 🟢 Low — Important for memory subsystem reliability but not critical |
| `#4416` (PR) | 12 days | Cron job model presets — no merge blockers identified | 🟢 Low — Feature-complete, likely needs final review |

**Notable**: The security-focused PRs (`#4436`, `#4548`) were merged promptly after filing, indicating security issues get immediate attention. Community members should consider whether `#4611` warrants a similar escalation.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-01

## Today’s Overview

Hermes Agent shows **high activity** today with 50 issues and 50 PRs updated in the last 24 hours. The project maintains a healthy **42% closure rate** on issues (21 closed out of 50 updated) and **40% merge rate** on PRs (20 merged/closed out of 50). No new releases were published. The community remains highly engaged around **Codex integration reliability**, **memory backend flexibility**, and **desktop app UX**. A notable pattern today is a coordinated *salvage* effort repurposing three stalled PRs (#49225, #48764, #48034) under fresh authors, suggesting maintainers are actively clearing a backlog of blocking fixes.

## Releases

**None.** No releases were published during this period.

## Project Progress

The following PRs were **merged or closed** today, representing completed work:

### Critical Gateway & Session State Fixes
- **[#56343](https://github.com/NousResearch/hermes-agent/pull/56343) — fix(codex): persist app-server turns to session DB, exactly once** — Crucially fixes Codex sessions having *zero* conversation memory; `session_search` and `conversation-distill` can now see Codex conversations.
- **[#56341](https://github.com/NousResearch/hermes-agent/pull/56341) — fix(cli): flush un-persisted messages before /resume and /branch** — Prevents mid-turn message loss when switching sessions.
- **[#56340](https://github.com/NousResearch/hermes-agent/pull/56340) — fix(gateway): recover from truncated responses** — Telegram sessions no longer stall on `⚠️ Response truncated` warnings; adds recovery attempt with exponential token headroom.
- **[#49225](https://github.com/NousResearch/hermes-agent/pull/49225) — fix(codex): persist app-server turns to session DB (original)** — The underlying PR that the salvage above builds on.
- **[#48764](https://github.com/NousResearch/hermes-agent/pull/48764) — fix(cli): flush un-persisted messages before /resume and /branch (original)** — Original fix for the session-message-loss bug.
- **[#48034](https://github.com/NousResearch/hermes-agent/pull/48034) — fix(gateway): recover from truncated responses (original)** — Original PR for truncated-response recovery.

### Session State & Cache Integrity
- **[#50405](https://github.com/NousResearch/hermes-agent/pull/50405) — fix(acp): stop _persist from deleting compression-archived history** — ACP session manager was destructively replacing messages on every save, deleting archived history.
- **[#55925](https://github.com/NousResearch/hermes-agent/pull/55925) — Investigate bg-review thread killing Telegram polling** — Closed but tracks investigation into why a failing background review terminates the Telegram poller.

### Security Hardening
- **[#30100](https://github.com/NousResearch/hermes-agent/pull/30100) — security: terminal command approval guards can be bypassed with shell obfuscation** — Closed with fixes for Base64 encoding and other bypass techniques.
- **[#26964](https://github.com/NousResearch/hermes-agent/pull/26964) — Harden approval detection for remote command substitution** — Added detection for `eval $(curl ...)` and similar forms.

### Other Bug Fixes
- **[#56323](https://github.com/NousResearch/hermes-agent/pull/56323) — fix Telegram compact /reasoning commands in groups** — `/reasoningmedium` treated as unknown command.
- **[#47163](https://github.com/NousResearch/hermes-agent/pull/47163) — fix(cron): multi-target email delivery only sends to first recipient** — Silent skipping of secondary email targets.
- **[#43849](https://github.com/NousResearch/hermes-agent/pull/43849) — Gateway can deliver assistant response without persisting assistant row** — Causes incorrect session replay on next turn.
- **[#34253](https://github.com/NousResearch/hermes-agent/pull/34253) — fix(gateway): Feishu session cancellation orphans session guard** — Permanently blocks subsequent messages.
- **[#42776](https://github.com/NousResearch/hermes-agent/pull/42776) — Fallback mechanism doesn't trigger on silent hangs/streaming timeouts** — Only activates on explicit errors.
- **[#46934](https://github.com/NousResearch/hermes-agent/pull/46934) — Bug: stale resume_pending sessions bypass idle reset** — Context bleed after gateway restart.
- **[#47268](https://github.com/NousResearch/hermes-agent/pull/47268) — Background review shares session context with main loop** — Causes premature stop with 11-77 character responses.
- **[#41986](https://github.com/NousResearch/hermes-agent/pull/41986) — delegate_task fails with ImportError** — Cannot import `STEER_CHANNEL_NOTE`.
- **[#54947](https://github.com/NousResearch/hermes-agent/pull/54947) — Agent cache cross-process guard spuriously invalidates** — On session-id switch under same session_key.
- **[#48765](https://github.com/NousResearch/hermes-agent/pull/48765) — Hermes Agent repeats completed shell tool results** — Deterministic duplicate submissions.
- **[#33265](https://github.com/NousResearch/hermes-agent/pull/33265) — Dashboard --tui: WebSocket rejected for non-loopback clients** — Even with `--insecure --host 0.0.0.0`.

## Community Hot Topics

| Issue | Type | Comments | 👍 | Summary |
|-------|------|----------|-----|---------|
| [#13834](https://github.com/NousResearch/hermes-agent/issues/13834) | Bug (Codex) | 16 | 3 | `openai-codex` fails on same machine where official Codex CLI works — network/auth mismatch |
| [#12639](https://github.com/NousResearch/hermes-agent/issues/12639) | Feature (Gemini) | 14 | **10** | Native Google/Vertex AI provider to bypass OpenRouter 402 errors & rate limits |
| [#47349](https://github.com/NousResearch/hermes-agent/issues/47349) | Feature (Memory) | 9 | 0 | Configurable memory backends — disable `memory.md`, use honcho/fact_store only |
| [#40166](https://github.com/NousResearch/hermes-agent/issues/40166) | Feature (Desktop) | 9 | **11** | Desktop app font size / zoom control missing entirely on macOS |
| [#52914](https://github.com/NousResearch/hermes-agent/issues/52914) | Bug (QQBot) | 7 | 4 | Infinite retry loop — `QQAdapter.connect()` missing `is_reconnect` parameter |

**Analysis:** The community's deepest pain points cluster around **provider reliability** (Codex auth failures, OpenRouter overhead) and **desktop app UX** (no zoom, no i18n). The most upvoted request (#12639, 10 👍) for native Gemini support signals strong demand to reduce dependency on intermediate proxy services.

## Bugs & Stability

### Critical (P0-P1)
- **[P0] #54947** (closed) — Agent cache cross-process guard spuriously invalidates on session-id switch — *Fixed via `3bc4a2ff78`*
- **[P1] #55925** (closed) — Failing bg-review kills Telegram polling coroutine — *Investigation complete; self-healing added via #55921*
- **[P1] #33265** (closed) — Dashboard WebSocket rejected for non-loopback clients — *Blocking remote administration*

### High Severity (P2)
- **Open:** [#55790](https://github.com/NousResearch/hermes-agent/issues/55790) — Stale credential pool entries cause removed providers to persist in model picker — *UI/state desync spanning Desktop and CLI*
- **Open:** [#55130](https://github.com/NousResearch/hermes-agent/issues/55130) — Dashboard 500s on every page load when basic auth is the only provider — *Blocked remote access*
- **Open:** [#55712](https://github.com/NousResearch/hermes-agent/issues/55712) — Remote dashboard session expires due to rotating refresh-token replay — *LAN session instability*
- **Open:** [#55420](https://github.com/NousResearch/hermes-agent/issues/55420) — `hermes update` crashes when managed uv binary is wrong-platform — *Blocks updates for cross-arch installs*
- **Open:** [#46709](https://github.com/NousResearch/hermes-agent/issues/46709) — Exceptional agent failure: 9-hour tool loop without verified shortcut fix — *Needs reproduction*
- **Closed:** [#48765](https://github.com/NousResearch/hermes-agent/issues/48765) — Hermes Agent repeats completed shell tool results — *Fixed*
- **Closed:** [#43849](https://github.com/NousResearch/hermes-agent/issues/43849) — Gateway delivers assistant response without persisting assistant row — *Fixed*

**Today's Fix PRs for open bugs:**
- [#55790](https://github.com/NousResearch/hermes-agent/issues/55790) (stale credentials) — **No fix PR yet**
- [#55130](https://github.com/NousResearch/hermes-agent/issues/55130) (dashboard auth 500) — **No fix PR yet**
- [#55420](https://github.com/NousResearch/hermes-agent/issues/55420) (uv binary crash) — **No fix PR yet**

### Moderate (P3)
- [#37897](https://github.com/NousResearch/hermes-agent/issues/37897) — [Desktop] Add i18n/language selector — *Feature, not urgent*
- [#40347](https://github.com/NousResearch/hermes-agent/issues/40347) — Russian locale for Desktop app — *Feature request with pre-built installer*
- [#42928](https://github.com/NousResearch/hermes-agent/issues/42928) — Support Intel Mac Desktop builds — *Duplicate of an existing request*
- [#56218](https://github.com/NousResearch/hermes-agent/issues/56218) — Slack Block Kit rendering — *Feature, not urgent*

## Feature Requests & Roadmap Signals

### High-Impact Requests (Likely Next Version)
1. **Native Gemini/Vertex AI provider** (#12639, 10👍) — Bypass OpenRouter entirely; reducing dependency costs and rate limits. *Strong candidate for next release given community demand.*
2. **Desktop font size/zoom control** (#40166, 11👍) — Highest upvoted open feature. macOS users cannot read the app on high-DPI screens. *Likely quick win.*
3. **Configurable memory backends** (#47349, 9 comments) — Replace hardcoded `memory.md`/`USER.md` with pluggable backends (honcho, fact_store). *Could unlock enterprise adoption.*
4. **Chinese localization** (#12961) — 104k+ stars but no i18n for the largest non-English user base.

### Lower Priority / Niche
- Russian locale (#40347) — Community has built installer already.
- Intel Mac support (#42928) — Blocked by build pipeline.
- Slack Block Kit rendering (#56218) — Niche Slack power-user need.

### New PRs Suggesting Roadmap Direction
- **#56333** — Claude Code history scanner for Desktop sidebar (M1) — *Suggests a Claude Code integration direction*
- **#55614** — mem0 self-hosted dashboard support — *Plugins ecosystem maturing*
- **#54535** — Read-only Slack channel history tool — *Slack gateway feature parity*
- **#51886** — Two-phase guest reply for Telegram — *Improves Telegram Bot API 10.0 compliance*
- **#56049** — X/Twitter fxtwitter fallback + cron date-token expander + LINE fixes — *Large community deployment patch dump*

## User Feedback Summary

### Pain Points (Repetitive)
- **Codex inconsistency**: Users report that official Codex CLI works where Hermes' `openai-codex` fails on the same machine (#13834). *Breeds distrust.*
- **Session state loss**: Multiple reports (e.g., #47268, #46934, #46709) of context bleed, premature stops, zombie sessions, and 9-hour tool loops. *Core reliability issue.*
- **Remote access barrier**: Dashboard unreachable with basic auth (#55130), WebSocket blocked on non-loopback (#33265), rotating tokens expire (#55712). *Limits deployment use.*
- **Approval bypass**: Shell obfuscation techniques circumvent command approval guards (#30100, #26964). *Security concern.*

### Satisfaction Signals
- **Plugin ecosystem growing**: Community-built `hermes-memory-pgvector` v0.3 (#29537) and mem0 self-hosted dashboard PR (#55614) show healthy third-party development.
- **Salvage PRs**: Maintainers are actively rescuing stalled community PRs (#56343, #56341, #56340), demonstrating responsiveness.
- **Telegram recovery**: Self-healing Telegram gateway (#55921) directly addresses recurring crash complaints.

### Use Cases
- **Personal assistant**: Desktop, CLI, TUI heavy users.
- **Team gateways**: Telegram, Slack, Feishu, QQBot, LINE multi-platform deployments.
- **Codex integration**: Developers using OpenAI Codex through Hermes for coding tasks.
- **Cron/automation**: Scheduled tasks with multi-target delivery (#47163 bug exposes usage).
- **Research/analysis**: `session_search` and `conversation-distill` for conversation analysis.

## Backlog Watch

### Needing Maintainer Attention (Long-unanswered / No PR)

| Issue | Created | Last Update | Significance |
|-------|---------|-------------|--------------|
| [#12639](https://github.com/NousResearch/hermes-agent/issues/12639) — Gemini native provider | 2026-04-19 | 2026-07-01 | 10👍, 14 comments, **no official response** |
| [#13834](https://github.com/NousResearch/hermes-agent/issues/13834) — Codex fails while official CLI works | 2026-04-22 | 2026-07-01 | High confusion, **no fix PR** |
| [#55790](https://github.com/NousResearch/hermes-agent/issues/55790) — Stale credential pool entries | 2026-06-30 | 2026-07-01 | UI/state bug, **no fix PR** |
| [#55130](https://github.com/NousResearch/hermes-agent/issues/55130) — Dashboard 500 with basic auth | 2026-06-29 | 2026-07-01 | Blocks remote dashboard, **no fix PR** |
| [#46709](https://github.com/NousResearch/hermes-agent/issues/46709) — 9-hour tool loop | 2026-06-15 | 2026-07-01 | **needs-repro** — but concerning if reproducible |
| [#29537](https://github.com/NousResearch/hermes-agent/issues/29537) — pgvector memory provider plugin | 2026-05-20 | 2026-07-01 | Community Show & Tell, **no official acknowledgement** |

### PRs That May Be Stalling
- **#33505** (Origin header WebSocket validation) — Open since 2026-05-27, no comments or updates. Security-relevant.
- **#51886** (Telegram two-phase guest reply) — Open since 2026-06-24, no merge activity. May need maintainer review.
- **#54535** (Slack history tool) — Open since 2026-06-29, no recent activity.

### Risk: Duplicate / Stale Issues
- **#42928** (Intel Mac) marked as duplicate — should be merged into canonical issue.
- **#47349** (Configurable memory) — 9 comments but no maintainer response — overlaps with plugin memory direction.
- **#56218** (Slack Block Kit) — Marked duplicate — needs canonical issue reference.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-01

## 1. Today's Overview
PicoClaw shows **moderate activity** with 4 issues updated and 5 PRs updated in the last 24 hours, including one new release. The project is actively maintained — a new nightly build was published, two PRs were merged/closed, and several important bugs received attention. The community is contributing both feature work (fallback chain configuration, Delta Chat gateway) and bug fixes, while two bugs related to tool call handling and local endpoint connectivity remain open. Overall, the project appears to be in a healthy development cycle with steady contributor engagement.

## 2. Releases
**New: Nightly Build v0.3.1-nightly.20260701.2cf030d2**  
[Full Changelog](https://github.com/sipeed/picoclaw/compare/v0.3.1...main)

This is an automated nightly build for **v0.3.1** and may be unstable. The changelog contains all commits since the last stable tag v0.3.1. Users should treat this as a pre-release for testing purposes. No breaking changes or migration notes are provided for this build.

## 3. Project Progress
Two PRs were merged/closed today:

- **[PR #3198] — fix(providers): surface friendly auth error messages** (merged)  
  Improvements to provider authentication error handling — API key, token, and permissions failures will now display clearer guidance to users via structured `common.HTTPError`.

- **[PR #3131] — fix(registry): add ok checks for tool schema type assertions** (closed/merged)  
  Adds explicit ok checks for three type assertions in `pkg/tools/registry.go`, preventing panics when tool schema map values are of unexpected types. Falls back to zero values (empty string/nil map).

These fixes enhance **error messaging** and **runtime stability** in the tool registry system.

## 4. Community Hot Topics

1. **[Issue #3153] — Volcengine Doubao Seed tool calls leak as `<seed:tool_call>` text** (open, 2 comments)  
   [View Issue](https://github.com/sipeed/picoclaw/issues/3153)  
   Active discussion around a bug where tool calls from `doubao-seed-2.0-pro` are returned as raw XML instead of being executed. This affects users on v0.2.8 and likely indicates an integration issue with Volcengine's specific response format. The underlying need is for robust tool-call parsing across providers.

2. **[Issue #3159] — Frequent task repetition (bug, 1 comment, Chinese language)**  
   [View Issue](https://github.com/sipeed/picoclaw/issues/3159)  
   User reports that when asked about "today's US news" then "today's French news," the model repeats the US news task before answering about France. This suggests a context or task queue management issue in multi-turn conversations. The user is on v0.2.9 with DeepSeek v4 Flash.

3. **[Issue #3201] — Feature: Support streaming output for QQ channel** (new today, 0 comments)  
   [View Issue](https://github.com/sipeed/picoclaw/issues/3201)  
   User requests token-by-token streaming for the QQ channel, noting only Telegram and Pico WebSocket currently implement `StreamingCapable`. This reflects growing demand for real-time output across all channel types.

## 5. Bugs & Stability

**High Severity:**
- **[Issue #3153] — Tool call leak with Volcengine Doubao Seed** (open, no fix PR yet)  
  Raw `<seed:tool_call>` text shown to users instead of executing tool calls. Affects v0.2.8+ with `doubao-seed-2.0-pro`. Core functionality is broken for affected users.

**Medium Severity:**
- **[Issue #3199] — Custom model provider cannot connect to `http://127.0.0.1` OpenAI-compatible endpoint** (closed)  
  This bug was **closed today** without a public fix. The issue was that localhost connections fail while other clients work fine. The close status without a linking fix PR is concerning — the root cause may have been a configuration issue or a bug resolved in the nightly build.

**Lower Severity:**
- **[Issue #3159] — Frequent task repetition** (open, stale label)  
  Multi-turn conversation logic issue causing repeated execution of previous tasks. No fix PR exists yet.

## 6. Feature Requests & Roadmap Signals

**Likely to ship in next version:**
- **[PR #3200] — Configurable default fallback chain** (open, very recently created)  
  Adds a dedicated UI workflow for setting default models, adding fallback models, reordering, and persisting the chain. This is a high-impact UX improvement for model management and is actively being developed.

- **[Issue #3201] — Streaming output for QQ channel** (new)  
  Aligns with the pattern of Telegram and WebSocket streaming. If implemented, it will unify the user experience across channels.

**Longer-term signals:**
- **[PR #3063] — Delta Chat gateway** (open, updated recently)  
  Adds support for the decentralized Delta Chat messenger. This could broaden PicoClaw's reach to privacy-focused users.

- **[PR #3157] — Android ADB remote operations tool** (open, stale)  
  Experimental ADB-backed tool for device control (screenshots, taps, swipe, etc.). This would enable mobile automation use cases but has been open since June 22 without activity.

## 7. User Feedback Summary
- **Pain Point #1:** Tool calls failing to execute with Volcengine Doubao – this is a **blocker** for users relying on that provider for tool-using tasks.
- **Pain Point #2:** Configuration confusion around custom model endpoints — the closed issue #3199 suggests users struggle to connect local services.
- **Pain Point #3:** Multi-turn conversation logic causing redundant task execution (Issue #3159) — impacts Q&A workflows where users ask related questions.
- **Satisfaction Signal:** The auth error improvements (PR #3198) show the team is responsive to user experience complaints about unclear error messages.
- **Desired Capability:** Streaming is now a recurring request across channels (Telegram done, QQ requested).

## 8. Backlog Watch
- **[Issue #3159] — Frequent task repetition** (stale, updated Jun 30)  
  [View Issue](https://github.com/sipeed/picoclaw/issues/3159)  
  Open for 8 days with only 1 comment. This is a usability bug that has not received maintainer response. The "stale" label may need re-evaluation.

- **[PR #3157] — Android ADB remote operations tool** (stale, updated Jun 30)  
  [View PR](https://github.com/sipeed/picoclaw/pull/3157)  
  Open since June 22 with no comments from maintainers. If intended for inclusion, it needs review and feedback. If not a priority, it should be communicated.

- **[PR #3063] — Delta Chat gateway** (open, updated Jun 30)  
  [View PR](https://github.com/sipeed/picoclaw/pull/3063)  
  Open since June 8. A maintainer review is overdue to either move this forward or provide guidance on next steps.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest
**Date:** 2026-07-01

---

## 1. Today's Overview

NanoClaw is experiencing a **high-activity period** with 8 issues and 17 pull requests updated in the last 24 hours, signaling intense development and rapid iteration. Today's data reveals a project grappling with **critical infrastructure stability issues** — particularly around networking, message reliability, and configuration handling — while simultaneously shipping substantial new features like agent templates, a native Matrix adapter, and a Discord channel adapter. The team merged or closed **10 pull requests** and kept **7 open**, indicating a healthy but busy review pipeline. However, the cluster of freshly filed `allixsenos` issues (numbers 2900–2903) describing silent failures and missing error feedback suggests the project is encountering **teething problems from recent architectural changes** that need immediate attention.

---

## 2. Releases

**No new releases today.** The last release predates the analyzed period.

*Note: Given the volume of merged PRs (10 today), a release candidate may be imminent. PRs addressing security (#2880), WhatsApp media handling (#2895), and document rendering (#2893) are strong candidates for inclusion.*

---

## 3. Project Progress

**10 pull requests were merged or closed today**, advancing multiple areas of the codebase:

### Security & Infrastructure
- **[PR #2880] – Inbox symlink escape fix (CWE-59)** — *merged* — Closes security issue #2828 (symlink-follow → arbitrary host file write). Now contains attachment forwarding on both inbound file-write and A2A relay paths. This is a **critical security hardening** for multi-tenant deployments.

### Channel Integrations
- **[PR #2889] – Daily-news agent + WeChat adapter** — *merged* — Adds a daily-news agent under a CLI group, plus a native `wechat.ts` channel adapter. Includes 33 vitest cases; TDD-driven development.
- **[PR #2884] – Discord channel adapter + approval-button fix** — *merged* — Adds production Discord integration via Chat SDK bridge, fixing DM approval-card routing (the same bug from PR #2899).
- **[PR #2891] – Optional `resolveChannelName` interface** — *merged* — Adds an optional method to `ChannelAdapter` to unblock Slack/Telegram channel resolution on the `channels` branch.
- **[PR #2885] – Slack Socket Mode in setup flow** — *merged* — Fixes a merge-branch issue where Slack Socket Mode setup was stuck on a feature branch. Now available on `main`.
- **[PR #2018] – DM-context Discord approval fix** — *merged* — Fixes button-click handler to read `interaction.user` (DM) in addition to `interaction.member.user` (guild).

### Media & Document Processing
- **[PR #2893] – Host-mediated document rendering** — *merged* — Adds `render_document` MCP tool that renders Quarto/LaTeX/Chromium documents in an **ephemeral, network-isolated container**. Keeps heavy toolchain out of agent containers.
- **[PR #2895] – WhatsApp media recovery via reuploadRequest** — *merged* — Fixes silent media drop by passing Baileys' `reuploadRequest` recovery context and surfacing failure notes.

### Operational & Minor
- **[PR #2874] – Signal boot-flap resilience** — *merged* — Prevents crash-looping when signal-cli has startup delays.
- **[PR #2875] – Deploy/Coolify skill** — *merged* — Adds deployment workflow integration.

---

## 4. Community Hot Topics

The most active and important discussions today center around **fundamental reliability and usability issues**:

### Critical: OneCLI Gateway Binding Mismatch [#2903](https://github.com/nanocoai/nanoclaw/issues/2903)
- **Status:** Open, 0 comments, filed today
- **Impact:** **Blocking** for new users. Fresh installs can never reach the gateway — "no agent ever responds." The docker bridge IP (`10.0.0.1`) doesn't match the gateway bind (`127.0.0.1`).
- **Underlying need:** The setup flow needs to either detect bridge networking and adjust, or document the correct post-install configuration. This is a **first-run experience blocker**.

### Silent Message Swallowing [#2902](https://github.com/nanocoai/nanoclaw/issues/2902)
- **Status:** Open, 0 comments, filed today
- **Impact:** User messages received on channels but not reaching agents (due to container spawn failure) are silently discarded — only logged to `error.log`. Users see no feedback.
- **Underlying need:** **Transparency is non-negotiable for user trust.** The system must surface agent-side failures back to the user via the channel itself.

### Webhook Server Crash on Bind Failure [#2900](https://github.com/nanocoai/nanoclaw/issues/2900)
- **Status:** Open, 0 comments, filed today
- **Impact:** Uncaught `EADDRINUSE` kills the entire host daemon, triggering crash-loop. Since webhooks are optional (polling channels don't use them), this is an **unnecessary single-point-of-failure**.
- **Underlying need:** Optional infrastructure should degrade gracefully, not kill the whole process.

### WEBHOOK_PORT Ignored in .env [#2901](https://github.com/nanocoai/nanoclaw/issues/2901)
- **Status:** Open, 0 comments, filed today
- **Root cause:** `config.ts` loads `.env` but doesn't overwrite process environment variables, so `WEBHOOK_PORT` only works as a real env var.
- **Underlying need:** Configuration should be consistent — if `.env` is the documented config mechanism, it must work.

### WhatsApp Media Inbound Drop [#2894](https://github.com/nanocoai/nanoclaw/issues/2894)
- **Status:** Open (related PR #2895 was merged, follow-up #2896 still open)
- **Impact:** Images, video, audio silently lost on direct CDN fetch failure.
- **Note:** A fix was merged today in #2895, with a follow-up #2896 still open.

---

## 5. Bugs & Stability

### Critical Severity
1. **OneCLI Gateway cannot reach agents (#2903)** — Fresh installs never respond. **No known fix PR.** Highest priority.
2. **Silent message swallowing (#2902)** — User messages lost without feedback. **No known fix PR.**
3. **Webhook server crash kills host daemon (#2900)** — Uncaught `EADDRINUSE` causes full process crash. **No known fix PR.**

### High Severity
4. **WEBHOOK_PORT silently ignored in .env (#2901)** — Configuration fails silently. **No known fix PR.**
5. **Discord DM approval buttons always reject (#2899)** — Fix in open PR #2899. Root cause: newline delimiter in `custom_id` not stripped before parsing.

### Medium Severity
6. **WhatsApp media download failure is silent (#2894)** — Fix merged in #2895, with follow-up #2896 to prevent regression from #2895.

### Low Severity
7. **E2E test probes (#2897, #2898)** — Smoke tests, safe to close.

---

## 6. Feature Requests & Roadmap Signals

### Likely in Next Release
- **Agent Templates** — PR #2890 (open) adds a template system for reusable agent bundles (instructions, MCP tools, skills). Includes public library, git repo, and local path loading. This is a **major usability improvement**.
- **Native Matrix E2EE Adapter** — PR #2844 (open) replaces Chat SDK bridge with a Rust-persistence-backed Matrix adapter using `matrix-bot-sdk` + `@matrix-org/matrix-sdk-crypto-nodejs`. This is **architecturally significant** for enterprise/self-hosted deployments.

### Strong Community Signals
- **WhatsApp media reliability** — Double PRs (#2895, #2896) on the same topic suggests high priority.
- **Chromium compatibility in containers** — PR #2771 (open, since June 15) adds `--shm-size` and `--init` config flags. Headless Chromium in Docker has known `/dev/shm` issues.
- **Voice transcription** — PR #2317 (open since May 7) adds a `/add-voice-transcription-free-whisper` skill with openai-whisper and whisper.cpp backends.

### Speculative Predictions
- The **template system (#2890)** will likely be in the next minor release — it lowers onboarding friction significantly.
- The **native Matrix adapter (#2844)** may take longer due to cryptographic complexity and the need for thorough review.
- The cluster of **infrastructure bugs (#2900–#2903)** will likely trigger a **point release** (v0.x.y) before feature releases resume.

---

## 7. User Feedback Summary

### Pain Points (High Priority)
- **"Fresh install doesn't work"** (#2903) — The most severe user-facing issue. New users cannot get a basic setup running. This is likely the #1 barrier to adoption.
- **"My messages disappear"** (#2902) — Users sending messages through channels see no response when the backend fails. This erodes trust.
- **"Configuration is inconsistent"** (#2901) — The documented `.env` approach doesn't work for webhook ports, forcing users to debug environment setup.

### Pain Points (Medium Priority)
- **"Discord approval buttons always reject"** (#2899) — A usability bug that makes Discord channel approvals unusable.
- **"WhatsApp media is silently lost"** (#2894) — Users sharing images/video get no feedback on failure.
- **"Signal keeps crashing on startup"** (#2874, merged today) — The fix in #2874 suggests users experienced crash loops with Signal integration.

### Satisfaction Indicators
- **Security fix shipped** (#2880) — Symlink attack vector closed; users who raised #2828 will see this as a win.
- **Document rendering in isolated containers** (#2893) — Architecture that keeps heavy toolchains out of agent containers is a positive design signal.

---

## 8. Backlog Watch

### Stale PRs Needing Maintainer Attention
1. **[PR #2317] – Voice transcription skill** — Open since **May 7** (55 days). No recent maintainer activity. This skill would be valuable for voice-heavy use cases.
2. **[PR #2771] – Configurable shm-size + --init** — Open since **June 15** (16 days). No recent reviewer activity. Essential for Chromium-based agents in Docker.

### Open Issues Without Recent Maintainer Activity
3. **[PR #2844] – Native Matrix E2EE adapter** — Open since June 24 (7 days). Large diff; may need architectural review before merging.
4. **[PR #2890] – Agent template system** — Open since June 30 (1 day). Fresh; needs review but is well-scoped.
5. **[PR #2892] – Telegram thread support** — Open since June 30 (1 day). Small fix; should be quick to merge.

### Recommendations
- **Immediately triage #2900–#2903** — These are ship-blockers. Assign owners and prioritize fixes.
- **Review #2890 (templates)** and **#2844 (Matrix)** — These represent major progress on usability and platform coverage.
- **Close #2897 and #2898** — E2E test probes should be cleaned up to reduce noise.
- **Engage on #2317** — The voice transcription skill has been waiting 55 days; either merge or provide feedback.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

Here is the project digest for **NullClaw** generated from GitHub data for **2026-07-01**.

---

## NullClaw Project Digest — 2026-07-01

### 1. Today's Overview
Project activity on 2026-07-01 is **moderate**, driven entirely by a batch of four merged pull requests that were updated in the last 24 hours. There are **no new releases** to announce, indicating the latest merged features are still in the `main` branch pipeline. A single open issue (#868) remains active, reporting a build failure on Android/Termux, which has received recent updates and community attention. Overall, the project shows steady maintenance progress but no new version cut today.

### 2. Releases
**None.** No new releases were published during this period.

### 3. Project Progress
Four pull requests were **merged/closed** (updated in last 24h), all by contributor **yanggf8**:

- **#641** — `fix(providers): fix GLM/ZhipuAI thinking mode and native tool_calls`  
  Fixes a critical logic bug where GLM servers forced thinking mode on every response, and resolves native tool call integration issues with the GLM/ZhipuAI provider.  
  [PR #641](https://github.com/nullclaw/nullclaw/pull/641)

- **#643** — `fix(cron): allow agent jobs to omit command field in cron.json`  
  Makes `command` optional for agent cron jobs, preventing silent data loss on gateway restart when the field was `null`.  
  [PR #643](https://github.com/nullclaw/nullclaw/pull/643)

- **#645** — `fix(cron): add --account flag to cron add-agent CLI`  
  Adds missing `--account` flag to the CLI, allowing users to specify `delivery_account_id` (e.g., which Telegram bot) without manual config editing.  
  [PR #645](https://github.com/nullclaw/nullclaw/pull/645)

- **#783** — `feat(cron): cron subagent, run history, JSON output, security hardening`  
  A **major feature** introducing a DB-backed cron subagent engine, run history tracking, JSON output for CLI, timezone offsets, delivery routing, operator alerts, and security hardening.  
  [PR #783](https://github.com/nullclaw/nullclaw/pull/783)

*Key advancement:* The cron subsystem received a significant overhaul (better CLI, persistence, security).

### 4. Community Hot Topics
- **Issue #868** — `[bug] zig build fails on Android/Termux (aarch64) with AccessDenied on options.zig linkat`  
  This is the **single most active** issue, with **6 comments**. User `NOTJuangamer10` reports a build failure on Android aarch64 when using `zig build -Doptimize=ReleaseSmall`. The error suggests a filesystem permission issue during the linking step. The community is discussing possible workarounds for Termux environments.  
  [Issue #868](https://github.com/nullclaw/nullclaw/issues/868)

*Underlying need:* Users on mobile/Android Linux (Termux) want to compile NullClaw natively. This signals a demand for **broader platform support** beyond standard desktop/server Linux.

### 5. Bugs & Stability
| Issue / PR | Severity | Description | Status |
|---|---|---|---|
| #868 | **High** | `zig build` fails on Android/Termux (aarch64) — `AccessDenied` on `options.zig linkat`. Blocks compilation on mobile Linux. | Open (no fix PR yet) |
| #641 (merged) | **High** | GLM/ZhipuAI provider forced thinking mode on every response, causing loops and unexpected reasoning content in non-thinking queries. | Fixed (merged) |
| #643 (merged) | **Medium** | Agent cron jobs with `"command": null` were silently skipped on load, causing all agent jobs to disappear after gateway restart. | Fixed (merged) |

*Observation:* The only currently open bug (#868) is platform-specific but blocks Android/Termux users entirely. No fix PR exists yet.

### 6. Feature Requests & Roadmap Signals
No explicit feature requests were raised as separate issues today. However, the **merged PR #783** reveals the project's roadmap direction:

- **Cron subagent engine** with persistent history, JSON output, per-job timezone offsets, and delivery routing.
- This suggests the team is investing heavily in **automation, scheduling, and observability** for agent workflows.

*Prediction for next version:* Expect a release soon including the cron subagent engine, GLM/ZhipuAI provider fixes, and general CLI usability improvements (e.g., `--account` flag).

### 7. User Feedback Summary
- **Pain points identified:**
  - Android/Termux users (aarch64) cannot compile NullClaw due to a filesystem permissions error during Zig build steps.
  - Previously, setting up delivery accounts for cron jobs required manual configuration file edits (now fixed via #645).
  - Agent cron jobs could silently lose their configuration data after a gateway restart if the `command` field was omitted (now fixed via #643).

- **Satisfaction:** Positive — merged PRs address real user friction in cron configuration and provider behavior.

- **Dissatisfaction:** The Android build issue (#868) remains unresolved, potentially frustrating mobile/tinkerer users.

### 8. Backlog Watch
- **Issue #868** — *Created 2026-04-23, still open after ~70 days.* No maintainer response or fix PR yet. This is a **critical backlog item** for Android/aarch64 support.  
  [Issue #868](https://github.com/nullclaw/nullclaw/issues/868)

- No other long-unanswered issues or PRs were observed in the current data window.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

Here is the IronClaw project digest for **2026-07-01**.

---

## IronClaw Project Digest
**Date:** 2026-07-01
**Source:** GitHub (nearai/ironclaw)

### 1. Today's Overview
The IronClaw project is in a high state of activity, processing 50 PRs and 20 issues in the last 24 hours. The development focus is overwhelmingly on the "Reborn" architecture, specifically addressing a critical "runtime wedge" caused by filesystem contention on concurrent turn-state writes. While the team landed a major fix for this wedge (PR #5486) and deployed several stability patches, the QA pipeline is flagging persistent failures related to runner lease expiration and turn-state contention, indicating the root cause is still being fully resolved. The project is in a fixing phase, with maintainers aggressively closing PRs (30 merged/closed) to stabilize the platform for the Reborn runtime.

### 2. Releases
No new releases were published today.

### 3. Project Progress
The team merged or closed **30 PRs** in the last 24 hours, indicating a push to stabilize the codebase. Key developments include:

- **Runtime Wedge Fix:** PR #5486 ([link](https://github.com/nearai/ironclaw/pull/5486)) was merged. It introduces an in-memory turn-state authority to prevent livelocks caused by concurrent same-user turns contending for the same `/turns/state.json` file.
- **Deploy Fix:** PR #5492 ([link](https://github.com/nearai/ironclaw/pull/5492)) enabled the `inmemory-turn-state` feature flag for the deployed `ironclaw-reborn` binary, operationalizing the fix from #5486.
- **Observability Enhancements:** PRs #5494 ([link](https://github.com/nearai/ironclaw/pull/5494)) and #5490 ([link](https://github.com/nearai/ironclaw/pull/5490)) added traces and logs for expired runner leases and turn-state file writes, aiding debugging.
- **UI Polish:** Fixes were merged for hiding skill activation messages in the chat (PR #5489, [link](https://github.com/nearai/ironclaw/pull/5489)), fixing the chat composer clearing issue (PR #5404, [link](https://github.com/nearai/ironclaw/pull/5404)), and removing the duplicate header from the Logs page (PR #5491, [link](https://github.com/nearai/ironclaw/pull/5491)).
- **Testing & CI:** PR #5487 ([link](https://github.com/nearai/ironclaw/pull/5487)) and #5484 ([link](https://github.com/nearai/ironclaw/pull/5484)) added latency spans and error-path coverage, respectively. PR #5448 ([link](https://github.com/nearai/ironclaw/pull/5448)) fixed a blocking CI issue with `release-plz`.

### 4. Community Hot Topics
The most critical discussion revolves around the instability of the Reborn runtime during high-load scenarios.

- **Runner Lease Expiration & Runtime Wedges:** Issue #5456 ([link](https://github.com/nearai/ironclaw/issues/5456)) and #5476 ([link](https://github.com/nearai/ironclaw/issues/5476)) are the top pain points. These describe routine failures due to runner leases expiring before model inference completes and turn-state filesystem CAS retries being exhausted. The underlying need is for more robust concurrent run management.
- **Multi-Actor Support Blocked:** Issue #5479 ([link](https://github.com/nearai/ironclaw/issues/5479)) is a blocker for E-MULTIUSER features, where the new one-runtime group harness fails when second threads attempt to use distinct actors.
- **Logs Debuggability:** Issue #5457 ([link](https://github.com/nearai/ironclaw/issues/5457)) is a developer pain point, as the Logs page remains blank for failed runs, completely blocking root cause analysis for these critical failures.

### 5. Bugs & Stability
Several high-severity bugs were reported or are actively being addressed:

- **Critical:**
    - **Runner Lease Expiry (P1):** Issue #5456 ([link](https://github.com/nearai/ironclaw/issues/5456)). The primary failure mode during QA, causing routine runs to fail. A fix PR #5494 ([link](https://github.com/nearai/ironclaw/pull/5494)) is open to add logging for recovery, but the timeout itself is not yet adjusted.
    - **Runtime Wedge / Runner "could not start":** Issue #5476 ([link](https://github.com/nearai/ironclaw/issues/5476)). The core concurrency problem addressed by the merged PR #5486, but QA is still seeing failures.
    - **System Drive Unavailable:** Issue #5426 ([link](https://github.com/nearai/ironclaw/issues/5426)). A blocker for creating routines in the hosted staging environment.
- **High:**
    - **Logs Page is Broken (P2):** Issue #5457 ([link](https://github.com/nearai/ironclaw/issues/5457)). An empty Logs page blocks debugging of the critical failures above.
    - **Memory Privacy Issue:** Issue #5460 ([link](https://github.com/nearai/ironclaw/issues/5460)). A significant data leak where workspace memories are visible to all users instead of only the creator.
- **Medium:**
    - **Duplicate Header on Logs Page (P3):** Issue #5458 ([link](https://github.com/nearai/ironclaw/issues/5458)). Fix PR #5491 is open.

### 6. Feature Requests & Roadmap Signals
The most visible feature requests are focused on configuration and security:

- **Configurable Skills & Tools:** Issue #5459 ([link](https://github.com/nearai/ironclaw/issues/5459)) is a clear roadmap signal for a user and admin permissions model for installing/uninstalling WASM tools and skills. This is likely a high-priority feature for the next release post-stability fixes.
- **Strongly-Typed Credential Scopes:** Issue #5464 ([link](https://github.com/nearai/ironclaw/issues/5464)) points to a need for better guards around credential management, a prerequisite for the host-managed SSO work. This is a security enhancement that could land soon.

### 7. User Feedback Summary
User pain points are highly technical and focused on reliability and usability:

- **Stability & Reliability:** Users are experiencing high failure rates with routine runs. The most frequent complaints involve "runner lease expiration" and "system drive unavailable" errors, making the platform unreliable for multi-tool workflows.
- **Debugging Frustration:** The blank Logs page is a major source of dissatisfaction for developers and QA engineers, as it prevents them from diagnosing why their workflows are failing.
- **Privacy Concern:** Users are explicitly reporting that personal memories stored in a workspace are visible to other users, which is a critical trust and security issue.

### 8. Backlog Watch
Several important issues require maintainer attention:

- **Nightly E2E Failures:** Issue #4108 ([link](https://github.com/nearai/ironclaw/issues/4108)) has been failing since May 27, with an update just yesterday. This is a critical health indicator that has been red for over a month and needs immediate investigation.
- **K8s Sandbox Runtime (Blocked):** PR #2979 ([link](https://github.com/nearai/ironclaw/pull/2979)) from April 27 is a large feature (size: XL) from a new contributor that appears stuck. It has a high-risk label and spans many scopes, suggesting it requires significant code review bandwidth from the core team.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the LobsterAI project digest for **2026-07-01**.

---

## LobsterAI Project Digest: 2026-07-01

### Today's Overview
LobsterAI has seen a significant burst of activity today, with **26 Pull Requests** updated in the last 24 hours, of which a staggering **23 were merged or closed**. This is well above the average and indicates a major push to resolve technical debt and ship features. A new release (`2026.6.30`) was also published, focusing on logging and bug fixes. However, community sentiment is mixed; while the core team is shipping rapidly on the "Cowork" and "OpenClaw" flows, users are raising concerns about performance bottlenecks and a perceived lack of UI/UX polish. The project appears healthy in velocity but is facing increasing scrutiny regarding resource management and feature parity with dedicated programming tools.

### Releases
- **LobsterAI 2026.6.30** (Released 2026-06-30)
    - **What's Changed:**
        - `feat(logging)`: Added diagnostics for the Cowork and OpenClaw flows to improve debugging capabilities.
        - `fix(openclaw)`: Implemented a fallback for catalog max token limits to prevent processing failures.
        - `fix(schedule)`: (Partial description) Addressed scheduling issues.
    - **Migration Notes:** No breaking changes or specific migration steps are indicated in this release. It is a standard patch and feature release.

### Project Progress
The core team (primarily `liuzhq1986`, `btc69m979y-dotcom`, and `liugang519`) merged a high volume of PRs today. Key advancements include:
- **Cowork & Artifacts:** A major feature landed for the Cowork flow: a dedicated **Subagent Artifact Panel** and the ability to **auto-open new previews** (HTML, video, local services, etc.) when the right panel is closed, drastically improving the user workflow.
- **OpenClaw Stability:** A critical fix was merged to **delay plan recovery** until an aborted OpenClaw run has fully settled, preventing session file lock collisions.
- **Deployment & Environment:** The team fixed the share-deployment system to use a **standalone Node environment**, ensuring packaging commands run reliably regardless of the user’s global setup.
- **MCP Ecosystem:** Added **Qichacha** integration to the MCP marketplace and introduced grouped server management for multi-server MCP services, improving the scalability of the integration system.
- **Bug Fixes:** Addressed a **macOS fullscreen black screen** bug, **compact prompt toolbar** layout issues, and fixed **usage analytics** reporting for edge cases (skills, IM, etc.).
- **Stale PRs Merged:** Several long-stale PRs (from April) were finally merged, including Agent import/export, scheduled task import/export, and sidebar icon bar navigation.

### Community Hot Topics
- **#2239: "Trend Judgment: The 'OpenClawization' of Programming Tools and the Programming Tooling of OpenClaw"** [OPEN]
    - **Link:** [Issue #2239](https://github.com/netease-youdao/LobsterAI/issues/2239)
    - **Analysis:** This is the most strategic discussion today. The author argues that AI tools and desktop agents are converging and that LobsterAI must deeply integrate with programming tools (e.g., via MCP) to remain competitive. This signals a strong community desire for LobsterAI to function as more than just an assistant—users want it to be a core part of their development workflow.

- **#2243: "skills.load.watch performance bottleneck + persistence bug + lack of UI switch"** [OPEN]
    - **Link:** [Issue #2243](https://github.com/netease-youdao/LobsterAI/issues/2243)
    - **Analysis:** A highly technical but critical report. The user (who has 174 skills) details how the file-watching system for skills causes severe performance degradation by consuming excessive I/O and tokens. The request to add a manual UI toggle reflects a need for more granular user control over resource-intensive background processes.

### Bugs & Stability
- **[HIGH] #2243: skills.load.watch Performance Bottleneck**
    - **Description:** The automatic file watcher for skills causes performance issues (high I/O, token waste, slow startup) for users with large skill libraries. It lacks a UI switch to disable it.
    - **Link:** [Issue #2243](https://github.com/netease-youdao/LobsterAI/issues/2243)
    - **Fix Status:** Reported today; no fix PR yet.
- **[MEDIUM] #2239: Observed OpenClaw Failure Finals as System Errors**
    - **Description:** This was identified as a potential issue leading to lock collisions and incorrect state during aborted runs.
    - **Fix Status:** **Fixed** via PR #2247 today.
- **[MEDIUM] #2246: Black Screen on macOS Fullscreen Close**
    - **Description:** Closing a macOS fullscreen app resulted in a black screen before hiding to tray.
    - **Fix Status:** **Fixed** via PR #2246 today.
- **[LOW] #1361: "Delete" Button in English on Chinese UI**
    - **Description:** A long-standing localization bug where the delete button for custom agents shows "delete" instead of the Chinese translation.
    - **Link:** [Issue #1361](https://github.com/netease-youdao/LobsterAI/issues/1361)
    - **Fix Status:** Stale, open for 3 months. No recent activity.

### Feature Requests & Roadmap Signals
- **Deeper Programming Tool Integration:** Issue #2239 strongly signals a request for LobsterAI to evolve from a personal assistant into a hub that orchestrates programming actions (via OpenClaw or MCP). This is likely a high-priority roadmap item.
- **MCP Ecosystem Expansion:** PR #2244 (adding Qichacha) shows the team is actively building the MCP marketplace. Future versions will likely add more "grouped" service integrations.
- **User-Controlled Performance Settings:** Issue #2243 indicates a growing demand for user-facing controls for performance-critical features (like file watching). A "Settings -> Skills -> Performance" section is a plausible future addition.
- **Standardized Import/Export:** The merging of stale PRs for Agent and Scheduled Task import/export (#1366, #1291) suggests these features are now officially part of the product roadmap, enabling better data portability and sharing.

### User Feedback Summary
- **Pain Points:**
    - **Performance:** Users with large skill sets are experiencing severe slowdowns due to background file watching (Issue #2243). This is a significant point of dissatisfaction for power users.
    - **UI/UX Gaps:** Issues like English text in the Chinese UI (#1361) and a lack of immediate confirmation for duplicate keyboard shortcuts (#1425) suggest the user interface requires more polish.
    - **Integration Strategy:** While powerful, users feel the "OpenClaw" system is not yet seamlessly integrated with standard programming workflows, requiring manual effort to link tools (Issue #2239).
- **Satisfaction:**
    - The rapid merging of long-standing feature requests (Agent export, sidebar icons, scheduled task import) shows the team is listening to the backlog, which is generating goodwill among users who have been waiting for these features.

### Backlog Watch
- **#1361: Localization (Delete Button)** - [Issue #1361](https://github.com/netease-youdao/LobsterAI/issues/1361)
    - *Status:* Stale for 3 months. A low-effort fix that would resolve a visible user experience flaw for Chinese-speaking users.
- **#1362: Cowork Permission Modal (ESC Key)** - [PR #1362](https://github.com/netease-youdao/LobsterAI/pull/1362)
    - *Status:* Open for 3 months. A small quality-of-life improvement for the Cowork workflow that has not been merged.
- **#1367: Scheduled Task Duplicate Name Validation** - [PR #1367](https://github.com/netease-youdao/LobsterAI/pull/1367)
    - *Status:* Open for 3 months. A data integrity fix that prevents users from creating multiple tasks with the same name, which could lead to confusion.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

Here is the Moltis project digest for **2026-07-01**.

---

## Moltis Project Digest
**Date:** 2026-07-01
**Data Source:** GitHub (moltis-org/moltis)

### 1. Today's Overview
The Moltis project shows a maintenance-focused state today, with zero new issues or releases reported in the last 24 hours. Activity was concentrated on dependency management, with **3 Pull Requests** updated (2 closed, 1 still open). The closure of two older dependency bumps indicates that the core team is actively keeping the build toolchain (esbuild, Astro, undici) up to date, reducing potential security or compatibility debt. The single open PR suggests ongoing routine updates to JavaScript/Node dependencies. Overall, while feature development appears paused, the project demonstrates healthy "housekeeping" health.

### 2. Releases
**None.**
No new releases were published on this date.

### 3. Project Progress
Two Pull Requests were **merged/closed** in the last 24 hours, both focused on dependency maintenance:

- **#1134 [CLOSED]:** (Dependencies) Bumped `astro` from 6.3.3 to 6.4.8 in the `/docs` directory and `undici` in the `/website` directory. This updates the static site generator and HTTP client for documentation infrastructure. ([View PR](https://github.com/moltis-org/moltis/pull/1134))
- **#1121 [CLOSED]:** (Dependencies) Bumped `esbuild` from 0.25.12 to **0.28.1** in `/crates/web/ui`. This is a significant version jump for the JavaScript bundler, likely bringing performance and compatibility improvements to the UI build step. ([View PR](https://github.com/moltis-org/moltis/pull/1121))

No feature-level code changes were merged.

### 4. Community Hot Topics
There are no issues or PRs with significant community comments or reactions in this period. All activity is automated (Dependabot). The lack of user discussion suggests the community is either satisfied with the current stable state or engaged on other channels (e.g., Discord). The underlying need here is purely operational: keeping the supply chain secure and compliant.

### 5. Bugs & Stability
**No bugs, crashes, or regressions** were reported in the last 24 hours. The project currently has zero active issues, indicating a stable baseline.

### 6. Feature Requests & Roadmap Signals
**No new feature requests** were submitted in this window. The roadmap remains opaque from this data pull. Given the focus on infrastructure updates (esbuild v0.28.1, Astro v6.4.8), the next version of Moltis will likely prioritize build performance and documentation infrastructure improvements rather than user-facing features.

### 7. User Feedback Summary
**No direct user feedback** (issues, comments, reactions) was recorded today. The absence of complaints or support requests suggests that recent dependency updates have not introduced regressions, and current functionality meets user expectations.

### 8. Backlog Watch
**No items on watch.** There are zero open issues on the repository.

- **Open PR #1141:** [dependencies] `chore(deps): bump the npm_and_yarn group across 3 directories with 4 updates`. This is a live PR by Dependabot. It requires a maintainer review and merge. While low risk, it should not be left open long to avoid dependency drift. ([View PR](https://github.com/moltis-org/moltis/pull/1141))

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-01

**Generated from GitHub data | Data source: github.com/agentscope-ai/CoPaw**

---

## 1. Today's Overview

The CoPaw project shows **very high development activity** on July 1, 2026, with **50 PRs updated** in the last 24 hours (exactly half merged/closed, half open) and **14 issues updated** (11 active, 3 closed). The project is currently in a **v2.0.0 pre-release phase** with beta builds (v2.0.0b2) available, which is driving intense bug-fixing and feature work. Key themes today include **channel integration fixes** (Telegram, QQ, WeChat), **memory system enhancements** (reranker support, ADBPG migration), **plugin lifecycle fixes**, and **computer-use desktop automation** (Windows UIA). No new releases were cut today, but the v2.0.0 stable release appears to be actively converging.

---

## 2. Releases

**No new releases were published today.** The latest available versions are:
- **v1.1.12.post2** (stable channel)
- **v2.0.0b2** (pre-release/beta)

---

## 3. Project Progress

**25 merged or closed PRs today** — here are the most significant:

| PR | Description | Theme |
|---|---|---|
| [#5562](https://github.com/agentscope-ai/QwenPaw/pull/5562) | **fix: re-enqueue in-flight batch on CancelledError** to prevent message loss during hot-reload (first-time contributor) | Reliability |
| [#5574](https://github.com/agentscope-ai/QwenPaw/pull/5574) | **fix: refresh chat on channel session updates** — automatic Web UI refresh when messages come from channels (first-time contributor) | UX |
| [#5510](https://github.com/agentscope-ai/QwenPaw/pull/5510) | **fix(tool-calls): cap tool responses before context insertion** — defense-in-depth for context explosion (first-time contributor, Under Review) | Stability |
| [#5690](https://github.com/agentscope-ai/QwenPaw/pull/5690) | **fix: add `audio` to `_FORMATTER_SKIPPED_TYPES`** for reasoning_content alignment (first-time contributor) | Correctness |
| [#5068](https://github.com/agentscope-ai/QwenPaw/pull/5068) | **fix(e2e): fix token usage test empty state detection** in clean environments | Testing |
| [#5699](https://github.com/agentscope-ai/QwenPaw/pull/5699) | **fix(telegram): move typing indicator start** to reduce phantom "typing…" (180s bug) | UX |
| [#5686](https://github.com/agentscope-ai/QwenPaw/pull/5686) | **fix(browser): dispose Playwright driver on cleanup** — fix driver process leaks | Stability |
| [#5665](https://github.com/agentscope-ai/QwenPaw/pull/5665) | **feat: Loop Engineering — Composable Gate Architecture & Frontend Settings** (open, large feature) | New Feature |
| [#5691](https://github.com/agentscope-ai/QwenPaw/pull/5691) | **feat(console): add reranker config UI** for reme0.4 memory search (open, new today) | New Feature |
| [#5692](https://github.com/agentscope-ai/QwenPaw/pull/5692) | **feat(memory): add reranker for search results** on reme0.4 (open, new today) | New Feature |

**Notable first-time contributor contributions** (5 today): `mynameyi` landed 3 fixes, `wananing` contributed context explosion defense, and multiple other new contributors are active — a healthy sign for community growth.

---

## 4. Community Hot Topics

**Most active discussion (by comments):**

1. **#5630 — Custom BaseURL support for Telegram** | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/5630)
   - **8 comments**, 2 days old, still open
   - **Need**: Users behind proxy/censorship environments need custom Telegram API base URLs
   - **📈 Trend**: This is a blocked access workaround request — high practical value for enterprise/restricted network users

2. **#5063 — Headroom context compression integration (CLOSED)** | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/5063)
   - **8 comments**, closed today
   - **Need**: 60-95% token reduction via local-first reversible compression
   - **Outcome**: Accepted and closed — likely to appear in v2.0.0

3. **#5273 — v2.0.0 Pre-release Bug Tracker** | [Issue](https://github.com/agentscope-ai/QwenPaw/issues/5273)
   - **2 comments, 1 👍** — central tracking issue
   - **📈 Trend**: Signals community is actively testing pre-release builds

**Underlying community dynamics:**
- **Chinese-speaking users** are highly active (many issues in Chinese)
- **Channel integration** (Telegram, QQ, WeChat) is the #1 area of interest
- **Plugin system instability** is causing real user friction (see #5689)
- **Enterprise/restricted-network users** are requesting proxy/custom endpoint support

---

## 5. Bugs & Stability

### High Severity (user-facing crashes/data loss)

| Issue | Summary | Status | Fix PR? |
|---|---|---|---|
| [#5701](https://github.com/agentscope-ai/QwenPaw/issues/5701) | **Concurrent access to same agent causes freeze/crash** (v1.1.10) — multiple browser tabs → deadlock | **OPEN** | None yet |
| [#5703](https://github.com/agentscope-ai/QwenPaw/issues/5703) | **Tool approval prompts appear despite "disable all approval" setting** (v2.0.0b1 regression) | **OPEN** | None yet |
| [#5689](https://github.com/agentscope-ai/QwenPaw/issues/5689) | **Plugin removal leaves stale import**, causing dialog crash (v1.1.12.post2) | **OPEN** | [#5695](https://github.com/agentscope-ai/QwenPaw/pull/5695) (fix in review) |
| [#5658](https://github.com/agentscope-ai/QwenPaw/issues/5658) | **Cannot connect to 9router-proxied models** — persistent error across versions | **OPEN** | None yet |

### Medium Severity

| Issue | Summary | Status | Fix PR? |
|---|---|---|---|
| [#5696](https://github.com/agentscope-ai/QwenPaw/issues/5696) | **QQ Channel `self._http` becomes None after websocket reconnect** → AttributeError | **OPEN** | None yet |
| [#5676](https://github.com/agentscope-ai/QwenPaw/issues/5676) | **Available skills not listed in system prompt** (v2.0.0b2) — skills unreachable | **OPEN** | None yet |
| [#5688](https://github.com/agentscope-ai/QwenPaw/issues/5688) | **CSS prefix mismatch:** `ant-` vs configured `qwenpaw-` → styles may be broken | **OPEN** | None yet |

### Low Severity / Questions

| Issue | Summary | Status |
|---|---|---|
| [#5670](https://github.com/agentscope-ai/QwenPaw/issues/5670) | Request to remove 10k character input limit | **OPEN** |
| [#5668](https://github.com/agentscope-ai/QwenPaw/issues/5668) | Request for Linux AppImage build | **OPEN** |

**Key stability pattern**: Several bugs are **v2.0.0 regressions** (approval override, skills in system prompt, plugin removal) — the pre-release phase is catching real issues.

---

## 6. Feature Requests & Roadmap Signals

### Likely to land in v2.0.0 (based on PR activity & issue acceptance):

| Feature | Evidence | Confidence |
|---|---|---|
| **Reranker for memory search** (reme0.4) | Two PRs today: [#5691](https://github.com/agentscope-ai/QwenPaw/pull/5691) (console UI) + [#5692](https://github.com/agentscope-ai/QwenPaw/pull/5692) (backend) — full-stack | **Very High** |
| **Loop Engineering — Composable Gate Architecture** | [#5665](https://github.com/agentscope-ai/QwenPaw/pull/5665) — 1200+ line PR with backend + frontend | **Very High** |
| **Headroom context compression** | Issue [#5063](https://github.com/agentscope-ai/QwenPaw/issues/5063) was closed/accepted today | **High** (post-v2.0.0) |
| **ADBPG REST-only + auto search** | [#5296](https://github.com/agentscope-ai/QwenPaw/pull/5296) — large refactor, under review | **High** |
| **Windows desktop GUI automation** (computer-use) | [#5187](https://github.com/agentscope-ai/QwenPaw/pull/5187) — 4000+ line PR, still open | **Medium** (large scope) |

### User-requested features with community traction:

| Request | Votes/Citations | Likelihood |
|---|---|---|
| Custom Telegram BaseURL ([#5630](https://github.com/agentscope-ai/QwenPaw/issues/5630)) | 8 comments | High (simple config change) |
| Remove 10k input character limit ([#5670](https://github.com/agentscope-ai/QwenPaw/issues/5670)) | 1 comment | Medium (design decision) |
| Linux AppImage build ([#5668](https://github.com/agentscope-ai/QwenPaw/issues/5668)) | 1 comment | Medium (Tauri supports it) |

---

## 7. User Feedback Summary

### Pain Points (real user reports today):

1. **"Concurrent access to the same agent freezes the whole system"** ([#5701](https://github.com/agentscope-ai/QwenPaw/issues/5701))
   - Active user with multiple tabs → complete freeze
   - ⚠️ **Highest severity**: blocks multi-user or multi-tab workflows

2. **"I turned off all tool approvals but it still pops up"** ([#5703](https://github.com/agentscope-ai/QwenPaw/issues/5703))
   - Regression in v2.0.0b1 — user on restricted container, cannot bypass
   - **Frustration level**: High — setting is saved but ignored

3. **"9router proxy still broken after multiple versions"** ([#5658](https://github.com/agentscope-ai/QwenPaw/issues/5658))
   - User has waited through multiple upgrades with no fix
   - **Frustration level**: Very high — long-standing issue

4. **"Plugin deletion leaves garbage — now dialog crashes"** ([#5689](https://github.com/agentscope-ai/QwenPaw/issues/5689))
   - Real business impact: user's dialog pipeline broken by plugin lifecycle bug
   - Fix PR [#5695](https://github.com/agentscope-ai/QwenPaw/pull/5695) in review

### Positive Signals:

- **5 first-time contributors** had PRs merged today
- **Active v2.0.0 testing** from the community (bug tracker [#5273](https://github.com/agentscope-ai/QwenPaw/issues/5273))
- **Documentation improvement** — Architecture page added ([#5653](https://github.com/agentscope-ai/QwenPaw/pull/5653))
- **Website modernization** — Blog section + SEO improvements ([#5697](https://github.com/agentscope-ai/QwenPaw/pull/5697))

---

## 8. Backlog Watch

| Item | Type | Age | Last Update | Need |
|---|---|---|---|---|
| [#5658](https://github.com/agentscope-ai/QwenPaw/issues/5658) — 9router proxy broken | Bug | 2 days | 2026-07-01 | Maintainer reply — user waited through multiple versions |
| [#5701](https://github.com/agentscope-ai/QwenPaw/issues/5701) — Agent multi-tab freeze | Bug | 0 days | 2026-07-01 | Urgent — blocks concurrent access, needs prioritization |
| [#5296](https://github.com/agentscope-ai/QwenPaw/pull/5296) — ADBPG REST-only migration | PR | 14 days | 2026-07-01 | Under review — large refactor, needs final maintainer approval |
| [#5187](https://github.com/agentscope-ai/QwenPaw/pull/5187) — Windows GUI automation | PR | 17 days | 2026-07-01 | 4000+ line PR, may need scope reduction or full review cycle |
| [#5342](https://github.com/agentscope-ai/QwenPaw/issues/5342) — Tool result hard cap (CLOSED) | Enhancement | 12 days | Closed today | ✅ Merged via [#5510](https://github.com/agentscope-ai/QwenPaw/pull/5510) |

**Items needing immediate maintainer attention:**
- **#5701** (freeze) — no maintainer response yet, should be escalated
- **#5703** (approval override) — v2.0.0 release blocker if not fixed
- **#5658** (proxy) — user has been waiting across versions, deserves a status update

---

**Project Health Summary:**
- 🟢 **Activity**: Very high — 50 PRs and 14 issues/day indicates strong momentum
- 🟢 **Community growth**: Multiple first-time contributors active
- 🟡 **Stability**: v2.0.0 pre-release phase has uncovered regressions (approval, skills, plugins) that need resolution before GA
- 🟡 **Backlog**: No critical long-neglected items, but real user pain points need faster triage
- 🟢 **Feature velocity**: Memory reranker, loop engineering, architecture documentation — impressive forward progress

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-01

## Today's Overview

ZeroClaw shows intense development velocity with **50 PRs** and **25 issues** updated in the last 24 hours, though open work vastly outpaces closures (45 open PRs vs 5 merged/closed, 21 open issues vs 4 closed). The project is deep in a **v0.8.3 release cycle**, with multiple tracker issues (#8070, #8073) coordinating gateway, web, ZeroCode, onboarding, observability, CI, and documentation work. Activity is sharply concentrated on **security hardening**, **channel infrastructure**, and **SOP (Standard Operating Procedure) engine** expansion. Several **priority:p1 bugs** are blocking workflows, particularly around MCP tool visibility, Telegram configuration, and agent interruption in the web dashboard. The maintainer team appears responsive, with multiple fix PRs already in flight for today's reported bugs.

## Releases

**No new releases today.** The project is in an active development phase for v0.8.3, with no published release artifacts.

## Project Progress

**5 PRs merged/closed today:**

- **#8521** (XL) — `feat(amqp): SOP fan-in dispatch path` — Merged. AMQP deliveries can now drive the SOP engine alongside the agent loop, with credential secret fixing and fan-in usage documentation. A major infrastructure addition.
- **#8579** — `fix(slack): add thread history scope` — Closed. Adds `channels.slack.<alias>.thread_history_scope` for sender-, thread-, or channel-wide Slack conversation history.
- **#8549** — `fix(gateway): advertise actual listener port in A2A discovery cards` — Closed. Fixes stale port advertising when starting gateway with `--port` overrides.
- **#8585** — `ci: Outdated dependencies found — 2026-07-01` — Closed (automated CI dependency check).
- **#6943** — `[RFC]: Deconflict Plugin System Goals in FND-001` — Closed. Resolves architectural RFC for replacing Extism with direct wasmtime component model hosting.

**Notable open PRs advancing features:**
- **#8589** — Spanish translations with locale detection fix
- **#8504** (XL) — Git forge channel with SOP ingress (GitHub App provider)
- **#8551** (L) — WASM plugin channel host bindings
- **#8486** (XL) — OpenAI chat completions endpoint (needs author action)

## Community Hot Topics

**Most active discussions:**

1. **#8193** — *MCP tools/tool_search missing from TUI sessions* (6 comments, 0 👍)  
   The top-severity bug. Two users confirmed MCP servers expose tools but Zerocode TUI sessions don't receive them. Gateway sees the tools. This is a **critical UX gap** for MCP integration.  
   [Issue #8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)

2. **#8057** — *CI scheduled security jobs* (3 comments, 0 👍)  
   Proposes CodeQL, npm audit, cargo outdated, Trivy, SBOM for heavy security checks off the critical PR path. Important for project security maturity.  
   [Issue #8057](https://github.com/zeroclaw-labs/zeroclaw/issues/8057)

3. **#8462** — *RFC: Runtime Policy for OTel LLM and Tool Content* (3 comments, 0 👍)  
   Addresses data privacy concerns: when OTel is enabled, all LLM/tool content currently flows to the backend. Proposes policy controls to strip/mask sensitive content.  
   [Issue #8462](https://github.com/zeroclaw-labs/zeroclaw/issues/8462)

4. **#8505** — *Telegram channel cannot be configured* (3 comments, 0 👍)  
   User reports `zeroclaw channels doctor` claims channels not set up even after following quickstart. Bot doesn't respond on Telegram. Blocking basic functionality.  
   [Issue #8505](https://github.com/zeroclaw-labs/zeroclaw/issues/8505)

5. **#8550** — *OpenAI-compatible chat completions endpoint* (1 comment, 0 👍)  
   User requests standard OpenAI API compatibility so tools like Open WebUI, LobeChat, and custom integrations can connect. A high-demand integration point.  
   [Issue #8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550)

**Underlying need:** The community is demanding **reliable MCP tool discovery**, **standard API compatibility** (OpenAI), **stable channel configuration** (Telegram), and **security/privacy controls** for observability. These are maturity and production-readiness requirements.

## Bugs & Stability

**Priority S1 (workflow blocked) — 7 active bugs:**

1. **#8193** — *MCP tools/tool_search missing from TUI sessions*  
   Gateway sees tools, TUI doesn't. Risk: high. **No fix PR yet.**  
   [Issue #8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)

2. **#8505** — *Telegram channel cannot be configured*  
   Doctor claims not set up even after quickstart. Risk: high. Likely related to configuration parsing.  
   [Issue #8505](https://github.com/zeroclaw-labs/zeroclaw/issues/8505)

3. **#8559** — *Agents stop work when exiting web dashboard chat window*  
   Exiting chat interrupts agent loops. Blocks background work. Risk: high.  
   [Issue #8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559)

4. **#8563** — *SOPs not available through web dashboard chat*  
   SOPs at `/zeroclaw-data/.zeroclaw/shared/sops` not detected by agent runtime. Risk: high.  
   [Issue #8563](https://github.com/zeroclaw-labs/zeroclaw/issues/8563)

5. **#8553** — *Agent cannot use env vars as http_request secrets*  
   No working path for agents to use environment variables for HTTP auth. Risk: high.  
   [Issue #8553](https://github.com/zeroclaw-labs/zeroclaw/issues/8553)

6. **#8560** — *browser_open hangs agent turn on headless host*  
   Unbounded subprocess wait when browser can't open. Also affects robot-kit TTS and ffmpeg. Risk: high.  
   [Issue #8560](https://github.com/zeroclaw-labs/zeroclaw/issues/8560)

7. **#8554** — *Harden skill zip extractor against zip-bomb inflation* (S2)  
   Entry-count, ratio, and decompressed-size caps needed. Risk: high. **Fix PR #8554 exists** (same number).  
   [Issue #8554](https://github.com/zeroclaw-labs/zeroclaw/issues/8554)

**Fixes in progress:**
- **#8582** — *Fix zerocode ephemeral daemon not terminating on connection failure* — PR open
- **#8463** — *Cap interactive CLI stdin lines to 1 MiB* — PR open (needs author action)
- **#8465** — *Thread CancellationToken through cron::run for explicit shutdown* — PR open

**Previously resolved today:**
- **#8386** — SQLite default memory backend silently degrading to keyword-only search (closed)

## Feature Requests & Roadmap Signals

**New feature requests filed today (July 1):**

1. **#8581** — *Centralize SOP ingress adapters for fan-in sources* (enhancement)  
   Shared adapter layer so new channels don't reinvent SOP event conversion. Follow-up to #8521.  
   [Issue #8581](https://github.com/zeroclaw-labs/zeroclaw/issues/8581)

2. **#8568** — *Mixture-of-Agents (MoA) virtual model provider* (RFC)  
   Named preset with aggregator/judge model + parallel reference models for multi-perspective reasoning.  
   [Issue #8568](https://github.com/zeroclaw-labs/zeroclaw/issues/8568)

3. **#8586** — *Centralize webhook channel message dispatch* (enhancement)  
   Shared gateway helper for autosave, agent dispatch, reply delivery across webhook-backed channels.  
   [Issue #8586](https://github.com/zeroclaw-labs/zeroclaw/issues/8586)

4. **#8584** — *Bring dashboard localization into Fluent flow* (enhancement)  
   Move web dashboard i18n from TypeScript dictionary to same Fluent system as Rust surfaces.  
   [Issue #8584](https://github.com/zeroclaw-labs/zeroclaw/issues/8584)

5. **#8556** — *Secret fields show set/not-set state* (enhancement)  
   UI improvement for password inputs: distinguish between empty and already-configured.  
   [Issue #8556](https://github.com/zeroclaw-labs/zeroclaw/issues/8556)

6. **#8541** — *Matrix channel thread-scoped history* (enhancement)  
   Opt-in for Matrix thread or conversation-bound session history.  
   [Issue #8541](https://github.com/zeroclaw-labs/zeroclaw/issues/8541)

7. **#8583** — *Channel/source shared-boundary cleanup tracker* (enhancement)  
   Architecture cleanup for shared lifecycle, schema, streaming, trust, config across channels.  
   [Issue #8583](https://github.com/zeroclaw-labs/zeroclaw/issues/8583)

8. **#8587** — *More SOP examples in documentation* (docs)  
   User requests richer SOP syntax examples beyond basic ones.  
   [Issue #8587](https://github.com/zeroclaw-labs/zeroclaw/issues/8587)

**Predictions for v0.8.3:**
- **MoA virtual model provider** (#8568) is transformative but complex — likely a v0.9 candidate
- **OpenAI-compatible endpoint** (#8550) has an open PR (#8486) and high community demand — likely for v0.8.3
- **SOP ingress centralization** (#8581, #8586) are cleanup/follow-up items — moderate chance
- **Secret UI improvements** (#8556) are low-effort UX wins — likely for v0.8.3

## User Feedback Summary

**Pain points expressed today:**

- **Web dashboard agent interruption** (#8559): User reports blocking background work when closing chat. *"This completely blocks from doing stuff while the agent is working or even looking at his files."* — Suggests need for persistent background agent sessions.
- **SOP invisibility** (#8563): SOPs configured in the standard shared directory are not detected. User followed StageHand examples but got no visibility.
- **MCP tool discovery gap** (#8193): Gateway sees tools, TUI doesn't. *"MCP servers connect and expose tools, but Zerocode TUI sessions do not receive the discovered MCP tools."* — Two users confirmed.
- **Telegram setup failure** (#8505): Quickstart and zerocode configuration doesn't produce working Telegram bot. User tried multiple setup paths.
- **HTTP secret configuration friction** (#8553): No working path for using environment variables as secrets in http_request tool.
- **Documentation gaps** (#8587): SOP syntax examples are too basic. Users need complex, real-world examples.
- **browser_open hanging** (#8560): Headless environments cause indefinite hangs. Also affects TTS and ffmpeg tools.

**Satisfaction signals (positive):**
- Active discussion and collaborative debugging on issues (#8193, #8057)
- PRs from diverse contributors (Spanish localization, Git forge channel, WhatsApp features)
- Quick maintainer response to new issues (same-day triage on all July 1 reports)

## Backlog Watch

**Items needing maintainer attention:**

1. **#8550** — *OpenAI-compatible chat completions endpoint* (P2, needs-maintainer-review)  
   Filed yesterday, has parallel PR #8486 (needs-author-action). Needs maintainer to resolve the duplicate path.  
   [Issue #8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550)

2. **#8553** — *Agent cannot use env vars as http_request secrets* (P1, needs-maintainer-review)  
   S1 bug filed yesterday, no fix PR yet. Blocks all authenticated HTTP requests from agents.  
   [Issue #8553](https://github.com/zeroclaw-labs/zeroclaw/issues/8553)

3. **#8541** — *Matrix channel thread-scoped history* (P2, needs-maintainer-review)  
   Needs architectural decision on scope boundaries.  
   [Issue #8541](https://github.com/zeroclaw-labs/zeroclaw/issues/8541)

4. **#8463** — *Cap interactive CLI stdin lines to 1 MiB* (P1, needs-author-action)  
   Fix PR stalled waiting for author response. Security-relevant (unbounded allocation).  
   [Issue #8463](https://github.com/zeroclaw-labs/zeroclaw/issues/8463)

5. **#8486** — *OpenAI chat completions endpoint PR* (needs-author-action)  
   Large PR (XL) overlapping with #8550 feature request. Needs maintainer to resolve direction.  
   [Issue #8486](https://github.com/zeroclaw-labs/zeroclaw/issues/8486)

**Aging items:**
- **#8193** (MCP tools bug) — 9 days old, no fix PR, S1 severity — highest risk item
- **#8505** (Telegram channel bug) — 2 days old, no fix PR, S1 severity — high priority
- **#8559** (web dashboard agent interruption) — 1 day old, S1, no fix yet

**Overall assessment:** ZeroClaw is in a **high-velocity feature expansion phase** with significant infrastructure work (SOP engine, AMQP, Git forge, WASM plugins). The v0.8.3 release cycle is active but the **6 open S1 bugs** represent a stability risk that should be addressed before release. Security posture is improving (zip-bomb protection, wasmtime bump, audit cleanups). Community engagement is strong with diverse contributors, but the backlog of `needs-maintainer-review` items suggests maintainer bandwidth is a potential bottleneck.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/ys578/agents-radar).*