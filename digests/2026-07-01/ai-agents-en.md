# OpenClaw Ecosystem Digest 2026-07-01

> Issues: 309 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-30 17:11 UTC

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

# OpenClaw Project Digest — 2026-07-01

## Today's Overview

OpenClaw shows elevated activity with **309 issues updated** (266 open) and **500 PRs updated** (447 open) in the last 24 hours—indicating a medium-to-high activity day centered primarily on ongoing open work rather than rapid closure. The single new release v2026.6.11 focuses on improving channel control capabilities. While 43 issues and 53 PRs were closed/merged, the large volume of stale open items (many weeks old) suggests the project is in a sustained maintenance-and-feature cycle with friction in moving critical fixes through review. Multiple P1 regressions and session-state bugs remain unresolved, pointing to tension between feature velocity and stability.

**🔗 [OpenClaw on GitHub](https://github.com/openclaw/openclaw)**

---

## Releases

### v2026.6.11 — openclaw 2026.6.11

**Highlights:**
- **More capable channel control** — Slack relay mode, native Mattermost `/oc_queue`, and per-DM model overrides improve automation and tuning of channel operations
- **Additional updates** (release notes truncated in source data; full changelog expected at release tag)

**Migration note:** No breaking changes or special migration steps were announced in the snippet.

**🔗 [v2026.6.11 Release](https://github.com/openclaw/openclaw/releases/tag/v2026.6.11)**

---

## Project Progress

**53 PRs merged/closed** in the last 24 hours. Notable closed items:

| PR | Description |
|---|---|
| **#97758** (closed) | Fixes `antml:`-namespaced tool call XML from being rendered as visible text when an Anthropic endpoint degrades native `tool_use` blocks into plain text. Fixes #97750. |
| **#68936** (closed) | Adds a PR review autofix pipeline using the Claude Agent SDK, plus a Windows daemon for background gateway supervision. |
| **#97970** (closed) | Fixes `openclaw update` automatically setting `gateway.bind: "lan"` which conflicted with `auth.mode: "none"` and caused Gateway crash loop on startup. |
| **#89589** (closed) | Fixes state directory permissions being reset to 0775 by update-check JSON writes, resolving a security audit warning. |
| **#84256** (closed) | Fixes `openclaw plugins update --all` downgrading manually-updated npm plugins to their originally recorded install version. |
| **#81525** (closed) | Fixes `media-understanding` silently routing images to vision models without validating declared capabilities. |

**Open progress highlights:**
- Multiple PRs now have `status: 👀 ready for maintainer look` — including bot-status context exposure for Discord (#97824), Slack (#97822), and Google Chat (#97825), plus a fix for duplicate same-session turns during gateway connection drops (#97903).
- A large `feat(agents): opt-in self-evolving SOUL.md` PR (#95793) is open and under review.
- An onboarding streamlining PR (#98218) proposes making `openclaw` launch the TUI for configured installs and a guided flow for fresh setups.

---

## Community Hot Topics

### Most Active Issues (by comment count)

| Issue | Comments | Theme |
|---|---|---|
| **#48003** — Steer mode doesn't inject messages mid-turn | 14 comments, 3 👍 | Core session-state bug: `messages.queue.mode: "steer"` queues messages instead of injecting them at tool boundaries. Regressed in March. Needs maintainer decision. 🔗[Issue](https://github.com/openclaw/openclaw/issues/48003) |
| **#84516** — Codex replies silently truncated at ~1000 chars | 11 comments, 2 👍 | Agent replies being cut off mid-sentence with `stopReason: null`. Platinum-severity, affects headless OpenClaw usage. 🔗[Issue](https://github.com/openclaw/openclaw/issues/84516) |
| **#38327** — "Cannot convert undefined or null to object" with google-vertex/gemini-3.1 | 9 comments, 3 👍 | Long-running regression since March. Blocks all embedded agent usage with that provider. 🔗[Issue](https://github.com/openclaw/openclaw/issues/38327) |
| **#94228** — Anthropic `thinking` blocks brick tool-use threads | 8 comments, 1 👍 | Native Anthropic path permanently breaks sessions when replaying historical `thinking` blocks. 🔗[Issue](https://github.com/openclaw/openclaw/issues/94228) |
| **#83959** — Codex app-server startup retries exhaust before replacement ready | 8 comments, 1 👍 | Crash-loop in Codex harness during agent turn scheduling. 🔗[Issue](https://github.com/openclaw/openclaw/issues/83959) |

### Most Reacted Issues

| Issue | Reactions (👍) | Signal |
|---|---|---|
| **#94518** — DeepSeek cache hit rate <10% after 6.x upgrade | **9 👍** | **Highest community energy.** Breaking change in caching logic has major cost implications for DeepSeek users. Fix not yet accepted. 🔗[Issue](https://github.com/openclaw/openclaw/issues/94518) |
| **#84527** — Add Antigravity CLI backend (replace google-gemini-cli) | **10 👍** | Strong demand for migration path as Google phases out Gemini CLI. Deadline June 18 imminent. 🔗[Issue](https://github.com/openclaw/openclaw/issues/84527) |
| **#48003** — Steer mode message injection | 3 👍 | Diamond-lobster-rated bug affecting core messaging reliability. |
| **#38327** — google-vertex/gemini regression | 3 👍 | P1 regression, high frustration with 3+ months unresolved. |
| **#84256** — Plugin downgrade on update (now closed) | 3 👍 | Community-relieving fix—users were being silently downgraded. |

**Analysis:** Users are most concerned about **cost and performance** (DeepSeek cache collapse), **core reliability** (steer mode, message truncation, session bricking), and **provider continuity** (Google Gemini CLI deprecation). The DeepSeek issue has the highest non-comment signal—9 upvotes—indicating a broad user base affected.

---

## Bugs & Stability

### Critical / P1 Bugs (open, no fix PR linked)

| Issue | Severity | Impact | Notes |
|---|---|---|---|
| **#48003** Steer mode doesn't inject messages mid-turn | 🦞 Diamond Lobster | Message loss, session state corruption | Root cause known (commit 9889c6da5). Needs maintainer review since March. No fix PR. 🔗[Issue](https://github.com/openclaw/openclaw/issues/48003) |
| **#84516** Silent truncation at ~1000 chars in Codex replies | 🐚 Platinum Hermit | Message loss | No fix PR; needs live repro + product decision. 🔗[Issue](https://github.com/openclaw/openclaw/issues/84516) |
| **#38327** google-vertex/gemini-3.1 "Cannot convert undefined or null" | 🐚 Platinum Hermit | Crash loop, auth provider broken | Regression since 2026.3.2, unresolved for months. No fix PR. 🔗[Issue](https://github.com/openclaw/openclaw/issues/38327) |
| **#94228** Anthropic `thinking` blocks brick long tool-use threads | 🐚 Platinum Hermit | Complete session loss | Manifested June 17. Needs live repro + linked PR is open. 🔗[Issue](https://github.com/openclaw/openclaw/issues/94228) |
| **#83959** Codex app-server startup retries exhaust | 🦞 Diamond Lobster | Crash loop | Fix PR linked but needs maintainer review. 🔗[Issue](https://github.com/openclaw/openclaw/issues/83959) |
| **#84536** Preemptive context overflow silently kills embedded sessions | 🐚 Platinum Hermit | Message loss, crash loop | No fix PR; blocked on product decision. 🔗[Issue](https://github.com/openclaw/openclaw/issues/84536) |
| **#97877** Empty-error-retry blocked by `hadPotentialSideEffects` guard | 🦞 Diamond Lobster | Silent terminal failure on transient 5xx after tool calls | Fix is labeled `queueable-fix` but unassigned. 🔗[Issue](https://github.com/openclaw/openclaw/issues/97877) |

### Newly Reported Bugs (last 24h)

| Issue | Summary | Fix PR? |
|---|---|---|
| **#98101** HTTP 429 with "overloaded" body misclassified as rate limit | Provider overload errors show wrong user-facing message | None yet 🔗[Issue](https://github.com/openclaw/openclaw/issues/98101) |
| **#97911** `tools.deny: ["skill_workshop"]` doesn't hide tool from Codex deferred tools | Security boundary bypass | Needs maintainer review 🔗[Issue](https://github.com/openclaw/openclaw/issues/97911) |
| **#97826** `sendVideo` omits width/height for videos ≥16 MB causing wrong aspect ratio | Media quality regression | Needs live repro 🔗[Issue](https://github.com/openclaw/openclaw/issues/97826) |
| **#97970** (closed) Update auto-sets `gateway.bind: lan` conflicting with `auth.mode: none` | **Fixed today** in v2026.6.11? | PR #97970 closed 🔗[Issue](https://github.com/openclaw/openclaw/issues/97970) |

### New Fix PRs Submitted Today

| PR | Fix For | Status |
|---|---|---|
| **#98207** Deliver subagent replies with nested visible text | #98204 (subagent reply dropped) | Needs proof 🔗[PR](https://github.com/openclaw/openclaw/pull/98207) |
| **#98003** Wire `buildGuardedModelFetch` into Cloudflare Anthropic client | Client-side fetch not guarded | Ready for maintainer 🔗[PR](https://github.com/openclaw/openclaw/pull/98003) |
| **#98223** Bound OAuth token exchange reads to prevent OOM | Google extension OOM risk | New, un-reviewed 🔗[PR](https://github.com/openclaw/openclaw/pull/98223) |

**Stability Assessment:** The project is carrying multiple months-old P1 regressions (#48003, #38327) still without fix PRs. The high volume of session-state and message-loss bugs (#84516, #84536, #94228) suggests core agent execution paths are fragile. The DeepSeek cache regression (#94518) and the newly reported `empty-error-retry` guard (#97877) indicate further instability in provider interaction layers.

---

## Feature Requests & Roadmap Signals

### Active Feature Requests (high community interest)

| Feature | Issue | Interest | Status |
|---|---|---|---|
| **Antigravity CLI backend** (replace deprecated google-gemini-cli) | **#84527** | **10 👍** | Needs product decision; Google's June 18 deadline has passed—urgent. |
| **Support multiple Azure/Teams bots on single Gateway** | **#71058** | 1 👍 | Needs product decision. |
| **Expose stable plugin SDK for installed skill workflows** | **#81913** | 1 👍 | Needs security review; linked PR open. |
| **Linear persistent workspace mode for blind users** | **#82450** | 1 👍 | Accessibility request; maintainer review needed. |
| **Direct video upload to LLM** | **#27482** | 0 👍 | Long-standing (Feb 2026); needs product decision. |

### Roadmap Predictions

Based on PR activity and community urgency:

1. **Antigravity CLI (agy) support** — Likely to land within 1–2 releases given the Google deadline has passed and 10 users upvoted. PR #84527 is already linked.
2. **Self-evolving SOUL.md** (#95793) — Opt-in agent personality evolution via reflection sub-turn. Large PR under review; candidate for next minor release.
3. **Streamlined onboarding** (#98218) — Making `openclaw` start the TUI natively for configured installs, easing first-run experience.
4. **Bot status exposure across channels** — Multiple "ready for maintainer" PRs for Slack, Discord, Google Chat to expose whether a message sender is a bot—likely to ship together.

---

## User Feedback Summary

### Pain Points
- **Cache cost explosion** — DeepSeek users report cache hit rate dropping from normal levels to <10% after the 6.x upgrade (#94518, 9 👍). This directly impacts API costs.
- **Silent message loss** — Multiple users report replies being silently truncated (#84516), sessions ending without notification (#84536), and messages queued but never dispatched (#48003, #84154).
- **Provider breakage on upgrade** — The google-vertex/gemini regression (#38327) has been open since March, and the DeepSeek cache regression (#94518) since June 18—both frustrating upgrades.
- **CLI cold-start regression** — 14-second delay on all CLI commands after 2026.5.12 (#82070) degrades developer experience.

### Positive Signals
- **Blind user testimonial** — A fully blind user (#82450) describes OpenClaw as "one of the most powerful AI work interfaces I have ever used," praising video promo, browser automation, and music research workflows.
- **Strong issue engagement** — 14 comments on #48003 and 11 on #84516 show users are invested in diagnosing and fixing bugs, not just reporting them.
- **Feature enthusiasm** — 10 👍 for Antigravity CLI and 9 👍 for DeepSeek cache fix show users actively advocate for what matters to their workflows.

### Dissatisfaction Indicators
- Multiple P1 regressions open for weeks or months (#38327 since March 6, #48003 since March 16).
- Users report having to manually rollback (#83968 macOS crash, #82070 CLI regression) to regain stability.
- The `tools.deny` bypass (#97911) raises security trust concerns—configuration that should hide tools does not work in Codex mode.

---

## Backlog Watch

### High-Impact Issues Needing Maintainer Attention

| Issue | Age | Stalled On |
|---|---|---|
| **#38327** google-vertex/gemini-3.1 regression (P1, 🐚 Platinum) | **118 days** (March 6) | Needs maintainer review, product decision, live repro |
| **#48003** Steer mode message injection (P1, 🦞 Diamond) | **107 days** (March 16) | Needs maintainer review; linked PR still open |
| **#58775** google-vertex merged into google transport (P2, 🐚 Platinum) | **90 days** (April 1) | Needs live repro |
| **#77093** Gmail Pub/Sub pushes not processed in Docker (P2, 🐚 Platinum) | **57 days** (May 4) | Needs maintainer review, live repro |
| **#81567** GPT-4o sessions exit after single response (P1, 🐚 Platinum) | **49 days** (May 13) | Needs maintainer review, product decision, live repro |
| **#81490** Subagent completion spawns fresh run instead of resuming (P1, 🐚 Platinum) | **48 days** (May 13) | Needs maintainer review, product decision, live repro |
| **#82662** Isolated cron agentTurn setup times out (P2, 🐚 Platinum) | **45 days** (May 16) | Needs maintainer review, product decision, live repro |
| **#94518** DeepSeek cache hit rate <10% (P1, 🐚 Platinum) | **13 days** (June 18) | Needs product decision, linked PR open, live repro |

### Stale PRs Without Activity

| PR | Age | Status |
|---|---|---|
| **#74235** fix(googlechat): preserve thread reply target via delivery | **63 days** | `⏳ waiting on author` since April 29 |
| **#75043** Add provider-aware automatic TTS emotion mapping | **62 days** | `⏳ waiting on author` since April 30 |
| **#75018** feat: Add Gradium realtime STT provider | **62 days** | `⏳ waiting on author` since April 30 |
| **#75662** fix(agents): pause yielded main-session runs | **61 days** | `👀 ready for maintainer look` since May 1 |

**Analysis:** The project shows a concerning number of high-severity bugs open for over a month, several with no fix PR at all (#38327, #81567, #81490). The backlog of "waiting on author" PRs (many from April–May) suggests contributor frustration with review cycles. Given the volume of new issues (309/day) versus closures (43/day), the project is accumulating technical debt faster than it resolves it.

---

*Generated from GitHub data for OpenClaw (github.com/openclaw/openclaw) for 2026-07-01. All links point to the public repository.*

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Comparison Report
**Date:** 2026-07-01 | **Analysis Period:** 24 hours ending 2026-07-01

---

## 1. Ecosystem Overview

The personal AI assistant open-source landscape exhibits a **bimodal development pattern** characterized by intense activity in established reference projects alongside smaller specialized forks pursuing platform-specific or lightweight deployments. The ecosystem spans from general-purpose agent orchestration frameworks (OpenClaw, Hermes Agent, ZeroClaw) to lightweight embedded variants (PicoClaw, NanoClaw, NullClaw) and application-specific tools (LobsterAI, CoPaw). A clear **architectural divergence** is emerging between monolithic agent platforms with integrated WebUIs and modular, gateway-first designs. The community is collectively grappling with provider integration fragility, cross-platform media handling inconsistencies, and the tension between feature velocity and core stability—with multiple projects carrying months-old P1 regressions while simultaneously shipping major new capabilities.

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | PRs Merged/Closed | Release Today | Health Score* | Activity Tier |
|---|---|---|---|---|---|---|
| **OpenClaw** | 309 (266 open) | 500 (447 open) | 53 | ✅ v2026.6.11 | ⚠️ Medium | Tier 1 (Sustained heavy) |
| **ZeroClaw** | 50 (45 open) | 50 (46 open) | 4 | None | ⚠️ Medium | Tier 1 (Sustained heavy) |
| **Hermes Agent** | 50 (43 open) | 50 (43 open) | 7 | None | ✅ High | Tier 1 (Sustained heavy) |
| **CoPaw** | 23 (15 open) | 50 (28 open) | 22 | None | ✅ High | Tier 2 (High velocity) |
| **IronClaw** | 14 (13 open) | 50 (29 open) | 21 | None | ✅ High | Tier 2 (High velocity) |
| **LobsterAI** | 8 (6 open) | 16 (2 open) | 14 | ✅ v2026.6.30 | ✅ High | Tier 2 (Focused bursts) |
| **NanoBot** | 14 (6 open) | 67 (32 open) | 35 | None | ✅ High | Tier 2 (High velocity) |
| **PicoClaw** | 7 (5 open) | 7 (5 open) | 2 | ✅ v0.3.1-nightly | ⚠️ Medium | Tier 3 (Moderate) |
| **NanoClaw** | 3 (2 open) | 9 (8 open) | 1 | None | ✅ High | Tier 3 (Moderate) |
| **NullClaw** | 2 (2 open) | 4 (0 open) | 4 | None | ⚠️ Medium | Tier 3 (Moderate) |
| **Moltis** | 0 | 3 (1 open) | 0 | None | ⚠️ Low | Tier 4 (Maintenance) |
| **TinyClaw** | 0 | 0 | 0 | None | ⚠️ Inactive | Tier 4 (Inactive) |
| **ZeptoClaw** | 0 | 0 | 0 | None | ⚠️ Inactive | Tier 4 (Inactive) |

*\*Health Score: Qualitative composite of bug fix velocity, maintainer responsiveness, PR merge rate, and community engagement.*

| Project | Active Contributors (24h) | Total Open Issues | Median Issue Age (High Severity) |
|---|---|---|---|
| **OpenClaw** | ~30-40 | 266 | 60-120 days for P1s |
| **ZeroClaw** | ~10-15 | 45 | 10-90 days |
| **Hermes Agent** | ~15-20 | 43 | <7 days for new bugs |
| **CoPaw** | ~10-15 | 15 | <14 days |
| **NanoBot** | ~8-12 | 6 | <30 days |

---

## 3. OpenClaw's Position

### Advantages vs. Peers
- **Scale and maturity**: Largest ecosystem with 500+ daily PRs and the most comprehensive feature set (multi-channel, multi-provider, plugin system, media understanding, cron scheduling). The only project shipping regular tagged releases alongside a nightly CI pipeline.
- **Community engagement**: Highest community signal (9+ upvotes on critical issues like DeepSeek cache regression #94518), indicating a broad and invested user base. Users actively diagnose and contribute to bug resolution (14 comments on steer mode bug).
- **Reference implementation status**: Functions as the ecosystem's "reference architecture" — four downstream forks (NanoClaw, PicoClaw, NullClaw, ZeroClaw) explicitly model aspects of their design on OpenClaw's component architecture.

### Technical Approach Differences
- **Monolithic by design**: OpenClaw integrates gateway, agent loop, TUI, CLI, and plugin system into a single codebase with a unified configuration model. By contrast, ZeroClaw pursues crate-level modularity with RFC-driven governance, while NanoBot emphasizes a lightweight codebase designed for readability and ease of modification.
- **Provider abstraction**: OpenClaw's provider layer is expansive but brittle—multiple P1 regressions (#38327, #84516) have lingered for months. NanoBot and Hermes Agent ship fixes faster, suggesting lighter provider abstractions that are easier to maintain.
- **Plugin architecture**: OpenClaw's plugin system uses npm packages with update management (fixes #84256), whereas ZeroClaw is building WASM-based plugins with sandboxing, and Hermes Agent supports zero-patch plugins (e.g., hermes-companion).

### Community Size Comparison
- **OpenClaw**: ~30-40 daily active contributors, 266 open issues, 447 open PRs — largest in ecosystem
- **ZeroClaw**: ~10-15 daily contributors, 45 open issues, 46 open PRs — second largest by issue volume
- **Hermes Agent**: ~15-20 contributors, 43 open issues — strong desktop-focused community
- **CoPaw**: ~10-15 contributors, 15 open issues — growing Chinese-market community

### Weaknesses
- **Stability debt**: Carries 7+ P1 bugs unresolved for 48-118+ days with no fix PRs (#48003, #38327, #84516). Multiple bug types recur across projects (session state corruption, silent message loss) but other projects fix them faster.
- **Review bottleneck**: 53 PRs merged vs. 500 updated daily, with many open PRs labeled "ready for maintainer look" for weeks. Four downstream forks show faster PR merge rates relative to their volume.

---

## 4. Shared Technical Focus Areas

Requirements emerging across **multiple projects**:

| Requirement | Affected Projects | Evidence |
|---|---|---|
| **Per-task/per-cron model/configuration overrides** | OpenClaw, NanoBot, CoPaw, NullClaw, ZeroClaw | PR #5652 (CoPaw: per-cron model override), Issue #8226 (ZeroClaw: per-agent env vars), PR #4549 (NanoBot: heartbeat model_override) |
| **Multi-channel media handling parity** | OpenClaw, NanoClaw, PicoClaw, LobsterAI, CoPaw | Discord attachment loss (#2888 NanoClaw), WhatsApp CDN failures (#2894), Telegram duplicate messages (#55761 Hermes), WeChat sync bugs (#1383 LobsterAI) |
| **Memory/retrieval improvements with rerankers** | OpenClaw (#94518), CoPaw (#5588), NanoBot (#4373/#4402) | Dedicated reranker model support, eager consolidation, cache hit rate optimization |
| **Plugin ecosystem maturation** | OpenClaw (#81913), ZeroClaw (#8551), Hermes (#28893), CoPaw (#5669) | Stable plugin SDKs, WASM sandboxing, zero-patch plugins, gateway lifecycle hooks |
| **Gateway reliability / silent death protection** | OpenClaw, NanoBot, Hermes, PicoClaw, NullClaw | Telegram polling failures (#55769 Hermes), cron job disappearance (#643 NullClaw), empty-error-retry guard (#97877 OpenClaw) |
| **Observability and diagnostics** | OpenClaw, LobsterAI (#2229), ZeroClaw (RFC #8462) | Diagnostic logging for Cowork and agent sessions, LLM span capture, OTel content policy |
| **Multi-provider support expansion** | OpenClaw (#84527), NanoBot (#4604/#4612), PicoClaw (#3093) | Antigravity CLI, Anthropic OAuth, OpenAI Response API, decentralized protocols |

---

## 5. Differentiation Analysis

| Project | Primary Target Users | Key Differentiator | Technical Architecture |
|---|---|---|---|
| **OpenClaw** | Power users, self-hosters, multi-platform deployers | Broadest feature set, largest community, "reference" status | Monolithic Python/TUI with npm plugins |
| **ZeroClaw** | Rust ecosystem, production deployments, multi-tenant | RFC-driven governance, crate-level modularity, WASM plugins | Modular Rust crates, RFC process |
| **Hermes Agent** | Desktop users, macOS/Windows, chatbot enthusiasts | Best desktop UI (Native + WebUI), desktop-specific features (memory graph, projects) | Python with Electron desktop |
| **NanoBot** | Developers wanting lightweight, hackable codebase | Lightweight (~tens of KLOC), easy to modify, strong heartbeats/reliability layer | Minimal Python, CLI + WebUI |
| **CoPaw** | Chinese-market users, DingTalk/WeCom/Feishu integration | Best Chinese platform support, Windows sandbox, LoRA model integration | Python, DingTalk-first |
| **LobsterAI** | Youdao ecosystem users, CoPilot alternative | Production analytics/logging, Youdao integration, Cowork flow | Python, analytics-heavy |
| **NanoClaw** | Matrix E2EE users, multi-platform multi-agent deployers | Native Matrix E2EE adapter, agent templates, daily news agent | Python, security-hardened |
| **PicoClaw** | Embedded/small device users (NanoKVM) | Lightweight, nightly builds, SIPBOC/decentralized protocol interest | Minimal Python |
| **NullClaw** | CLI-first users, Telegram-heavy workflows | Minimal overhead, strong cron subsystem | Minimal Python |
| **IronClaw** | High-scale, storage-intensive deployments | WAL-mode libSQL, stress testing framework, Reborn WebUI | Rust + Python, storage-optimized |
| **Moltis** | Documentation/website reliability | Low activity; documentation-focused | Astro-based docs |

---

## 6. Community Momentum & Maturity

### Tier 1: Sustained Heavy Activity (10+ daily contributors, 50+ daily PRs)
- **OpenClaw** — **Mature but carrying technical debt.** Largest contributor base, but the oldest unresolved P1s (118 days) in the ecosystem. The v2026.6.11 release cycle shows continued feature velocity, but the 7:1 open-to-closed PR ratio indicates a growing review bottleneck.
- **ZeroClaw** — **Architectural consolidation phase.** RFC-driven governance is producing well-specified designs (plugin system, onboarding, CI hardening) but S0 bugs (#5542, 3 months unresolved) signal execution gaps between design and operational stability.
- **Hermes Agent** — **Desktop-focused momentum.** Highest bug fix velocity (7 bugs with fix PRs submitted same day as report). The v0.17.0 release appears stable, with community building plugins (hermes-companion) indicating a healthy plugin ecosystem is forming.

### Tier 2: High Velocity / Focused Bursts (5-15 daily contributors, 15-50 daily PRs)
- **NanoBot** — **Rapid iteration, high throughput.** 35 PRs merged/closed in 24h suggests a highly responsive maintainer team. The four-month OAuth token persistence bug (#1023) finally closed, signaling backlog cleanup is happening. Strongest candidate for "lightweight alternative" to OpenClaw.
- **CoPaw** — **Chinese ecosystem leader.** 22 PRs merged in 24h with strong first-time contributor onboarding. v2.0.0 alpha track is driving feature velocity, but UX bugs with 3-month tail (#1372, #1381) suggest prioritization of new features over polish.
- **IronClaw** — **Storage and CI infrastructure focused.** 21 PRs merged, with clear progress in storage performance (WAL mode, unlimited-limits fast path) and CI/testing coverage (Playwright, cargo-llvm-cov). Burst of bug bash reports indicates a polish cycle in progress.
- **LobsterAI** — **Release-driven, analytics-focused.** 14 PRs merged alongside the v2026.6.30 release. Longest backlog tail (90-day-old PR #1372 for multi-file selection) suggests capacity constraints on UX issues.

### Tier 3: Moderate / Niche Activity (2-5 daily contributors, 3-10 daily PRs)
- **PicoClaw** — **Lightweight, nightly-driven.** 2 PRs merged, new nightly build. Slow review cycle (DeltaChat PR #3063 stale for 23 days). Cluster of new bugs (#3195-#3199) suggests nightly builds may introduce regressions.
- **NanoClaw** — **Security-focused, responsive.** 1 PR merged (critical symlink fix), maintainers responsive to security vulnerabilities. Small community but high-quality contributions.
- **NullClaw** — **Single-contributor driven.** All 4 PRs today from `yanggf8`. Telegram reliability issue (#972) may signal integration fragility. Low community engagement.

### Tier 4: Maintenance / Inactive
- **Moltis** — Automated dependency updates only. Zero community engagement or feature work.
- **TinyClaw, ZeptoClaw** — No activity. Effectively dormant.

---

## 7. Trend Signals

### Industry Trends Extracted from Community Feedback

1. **Platform lock-in anxiety is driving multi-provider demand.** Users are actively seeking migration paths away from Google Gemini CLI (#84527, 10 👍 in OpenClaw) and toward flexible provider configurations. Projects that support local/self-hosted models alongside commercial APIs are favored—multi-model support for a single custom provider is a growing request (#55573, Hermes Agent).

2. **Memory systems are becoming a cost battleground.** The DeepSeek cache regression (#94518, 9 👍) triggered intense community frustration because caching directly impacts API bills. Projects are responding with two-stage retrieval with dedicated rerankers (CoPaw #5588, NanoBot #4373/#4402) and context reduction optimizations (NanoBot #4581). Expect memory cost optimization to be the "killer feature" of the next 3 months.

3. **Desktop-first agents are gaining traction, but WebUI is converging.** Hermes Agent's desktop-native experience (memory graph, projects) is attracting a different user segment than OpenClaw's CLI/TUI-first design. However, ZeroClaw is removing its Tauri desktop app in favor of web/WASM, suggesting uncertainty about the optimal distribution model. The coexistence of desktop and web approaches indicates the market has not yet settled.

4. **Plugin ecosystems are diversifying beyond npm.** The ecosystem is splitting into three plugin models: (a) npm-based (OpenClaw), (b) WASM-sandboxed (ZeroClaw), and (c) zero-patch Python plugins (Hermes Agent). CoPaw's first-time contributor submitting a memory reranker PR (#5669) shows that low-friction plugin contribution models attract new contributors.

5. **Security hardening is accelerating, driven by agentic workflows.** NanoClaw's swift symlink-escaping fix (#2828→#2880, 9 days) and PicoClaw's ISATAP SSRF guard (#3143) demonstrate awareness of agent-specific attack surfaces. ZeroClaw's RFC #8462 (OTel content policy) and PicoClaw's DNS rebinding bug (#4611) show the community is thinking proactively about data governance in observability pipelines.

6. **Chinese-market ecosystems are an independent vector of innovation.** CoPaw's DingTalk @mention support, WeCom file handling, and Feishu integration represent capabilities that Western-focused projects (OpenClaw, Hermes) do not address. Similarly, NanoBot's GLM/ZhipuAI fix (#641) and Alibaba Cloud provider support indicate a parallel demand stream from users of Chinese AI providers. Projects that offer parity across both ecosystems will have a structural advantage.

### Value for AI Agent Developers

- **Gateway reliability is the #1 operational concern** across all projects. Silent failures (Telegram polling death, Discord attachment drops, cron job disappearance) undermine trust in agentic workflows. Developers should prioritize error recovery, reconnection logic, and diagnostic logging over feature additions.

- **Per-task configuration precision** (cron-specific models, per-channel routing, per-agent memory policies) is the feature most requested by power users moving from experimentation to production. The "one-size-fits-all" configuration model is failing.

- **Cost observability is a growing requirement.** Users want to understand which agents, which channels, and which tools are driving API costs. The DeepSeek cache issue is the tip of the iceberg—projects that provide built-in cost analysis (token counters, per-session spend, cache hit rates) will differentiate.

- **Contributor friction remains high in large projects.** OpenClaw's review bottleneck and 60-120 day P1 resolution times contrast sharply with Hermes Agent's same-day fix PRs. Developers choosing a project to contribute to should evaluate maintainer responsiveness as heavily as feature completeness.

- **The WASM plugin model (ZeroClaw) and zero-patch plugin model (Hermes) represent competing philosophies** for extensibility. WASM provides stronger security guarantees and language independence, while zero-patch plugins allow rapid prototyping. The ecosystem likely needs both, but developers should watch which model attracts more community extensions.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-01

## Today's Overview

NanoBot enters July with a period of intense development activity: 67 PRs were updated in the past 24 hours (32 open, 35 merged/closed), alongside 14 updated issues (8 closed). No new releases were published today. The project shows strong contributor engagement across reliability, memory, heartbeat, and WebUI areas, with several high-priority fixes in progress. The 35 closed PRs and 8 resolved issues indicate a maintainer team that is actively processing contributions.

## Releases

No new releases were published today. The last release remains the previously published version.

## Project Progress

35 PRs were merged or closed in the last 24 hours, reflecting significant throughput. Notable merged/closed work includes:

- **CLI OAuth login improvement** — PR [#4573](https://github.com/HKUDS/nanobot/pull/4573) (by hamb1y) adds `--set-main` / `--main` flags to `nanobot provider login`, fixing a usability pain point where OAuth-only setups were not properly configured.
- **WebUI session compaction fix** — PR [#4609](https://github.com/HKUDS/nanobot/pull/4609) (by chengyongru) prevents idle compaction from refreshing `session.updated_at`, avoiding repeated AutoCompact scheduling and keeping session recency accurate.

Several cross-cutting features advanced and remain open:
- **Reliability layer** — PR [#4534](https://github.com/HKUDS/nanobot/pull/4534) (Re-bin) adds verification feedback, long-output handling, and runtime budget convergence to the agent loop.
- **Heartbeat improvements** — PRs [#4549](https://github.com/HKUDS/nanobot/pull/4549) and [#4551](https://github.com/HKUDS/nanobot/pull/4551) (dajiaohuang) add model override and isolated session config for heartbeat tasks.
- **Memory consolidation** — PRs [#4373](https://github.com/HKUDS/nanobot/pull/4373) and [#4402](https://github.com/HKUDS/nanobot/pull/4402) (yu-xin-c) preserve delivery context during consolidation and add opt-in eager consolidation.
- **Dream skill deduplication guard** — PR [#4554](https://github.com/HKUDS/nanobot/pull/4554) (michaelxer) blocks Dream from creating duplicate skills.

## Community Hot Topics

- **Issue #1023** (2 👍) — "Provider login tokens not persisted + config refresh drops unknown providers" by vojtabiberle, finally closed after four months. This long-standing bug affected OAuth token persistence and config migration, a critical pain point for Docker/Podman users.  
  [Link](https://github.com/HKUDS/nanobot/issues/1023)

- **Issue #4513** — Windows nssm system service `/restart` bug (Quincy-Zh). Two reproduction scenarios with port-binding race conditions and stale service state. The issue is closed, with PR [#4547](https://github.com/HKUDS/nanobot/pull/4547) (dajiaohuang) providing the self-heal fix for PID mismatch after restart.  
  [Link](https://github.com/HKUDS/nanobot/issues/4513)

- **Issue #4603** (0 comments, by chengyongru) — Refactor request to stop mutating `tool_call.id` for WebUI file-edit progress correlation. This touches on a core protocol concern: streaming progress tracking should not pollute provider-level identifiers. A thoughtful refactoring that balances WebUI needs against protocol integrity.  
  [Link](https://github.com/HKUDS/nanobot/issues/4603)

- **Issue #4605** (0 comments, by chengyongru) — "One thing I'd love to have: a way to trigger an agent action from an external script." User running Gmail classification via gws CLI desires a programmatic action trigger. This represents a growing power-user need for API-driven agent invocation.  
  [Link](https://github.com/HKUDS/nanobot/issues/4605)

## Bugs & Stability

**High Severity:**
- **Issue #4611** — "Security: DNS rebinding TOCTOU in SSRF validation" (axelray-dev). `validate_url_target` resolves DNS via `socket.getaddrinfo` and checks IPs, but the resolved IP is not pinned — a TOCTOU race allows DNS rebinding to internal IPs after validation. No fix PR exists yet; this is a security bug requiring urgent attention.  
  [Link](https://github.com/HKUDS/nanobot/issues/4611)

**Medium Severity:**
- **Issue #4595** (closed) — `apply_final_call_ids` overwrites correct tool_call IDs for non-file-edit tools, causing permanent session poisoning. Affects all tool types. A subtle data-corruption bug in streaming edit tracking.  
  [Link](https://github.com/HKUDS/nanobot/issues/4595)

- **Issue #4513** (closed, fixed by PR #4547) — Windows nssm system service `/restart` fails due to PID mismatch and port binding. Self-healing fix merged.  
  [Link](https://github.com/HKUDS/nanobot/issues/4513)

**Low Severity:**
- **Issue #4599** (closed) — Linux install script crash in TUI. Closed as fixed.  
  [Link](https://github.com/HKUDS/nanobot/issues/4599)

- **Issue #4592** (open) — ExecTool path extraction misses absolute paths after equals sign (e.g., `--output=/tmp/foo` is not recognized), causing `restrictToWorkspace` to fail on valid commands.  
  [Link](https://github.com/HKUDS/nanobot/issues/4592)

## Feature Requests & Roadmap Signals

Several feature requests signal where the project is heading:

1. **Anthropic OAuth support** — Issue [#4604](https://github.com/HKUDS/nanobot/issues/4604) (by chengyongru, open) requests Anthropic OAuth integration, a natural extension to multi-provider support.

2. **OpenAI Response API** — Issue [#4612](https://github.com/HKUDS/nanobot/issues/4612) (practitionerjane) requests support for OpenAI's non-compatible response API mode, indicating demand for broader provider compatibility beyond the standard chat completions format.

3. **External agent triggers** — Issue [#4605](https://github.com/HKUDS/nanobot/issues/4605) requests a programmatic way to trigger agent actions from external scripts (e.g., Gmail classification pipeline). This aligns with the heartbeat trigger work in PR [#4437](https://github.com/HKUDS/nanobot/pull/4437) and may be addressed by extending the heartbeat CLI.

4. **GitHub Copilot Enterprise** — Issue [#4220](https://github.com/HKUDS/nanobot/issues/4220) (closed) requested GHE / Copilot for Business support. The closure suggests this may have been addressed or deprioritized.

5. **Per-session model preset** — PR [#4555](https://github.com/HKUDS/nanobot/pull/4555) (dajiaohuang, open) stores model preset in session metadata, allowing per-conversation model selection. Likely to land in next release.

6. **WebUI Markdown export** — PR [#4587](https://github.com/HKUDS/nanobot/pull/4587) (boogieLing, open) adds session export to Markdown with speaker labels and collapsible tool activity. A user-facing feature that WebUI users have requested.

**Predictions for next release:** The heartbeat model_override (PR #4549), isolated_session (PR #4551), and per-session model preset (PR #4555) are likely candidates. The reliability layer (PR #4534) may be too large to merge quickly. The A2A delegation work (PR #4571) is complex but progressing.

## User Feedback Summary

Positive signals:
- **Issue #4605** author states: "Compared to OpenClaw, the lightweight codebase makes it easy to read and understand the source, which I really appreciate." This reflects a key differentiator for NanoBot against heavier alternatives.

Pain points expressed:
- **Windows system service users** face port-binding and state-file issues after `/restart` (Issue #4513). While PR #4547 provides a fix, the problem affected production deployments.
- **OAuth token persistence** (Issue #1023) was a four-month unresolved pain point for Docker users, now closed.
- **Install script reliability** (Issue #4599) crashed on Linux without user interaction — though closed, this affects new user adoption.
- **SSRF vulnerability** (Issue #4611) represents a genuine security concern for users running NanoBot in networked environments.

## Backlog Watch

- **Issue #1023** — Provider login tokens not persisted. Now closed after 4 months. Maintainers took a long time to address this critical OAuth bug for Docker users. The closure signals resolution but the delay is notable.

- **Issue #4220** — GitHub Copilot Enterprise support. Closed without resolution notes visible. Enterprises relying on GHE may still lack support.

- **Issue #4611** — DNS rebinding security vulnerability. New report with no fix PR yet. This should be prioritized given the security implications for SSRF validation.

- **PR #4373** and **PR #4402** — Memory consolidation fixes/features (yu-xin-c). Both have been open since June 16 and 18 respectively, with active updates. These are complex memory system changes that require careful review but are critical for production memory behavior.

- **PR #4581** (hamb1y) — Context reduction optimization. Related to #4588. This addresses a core cost/reliability concern for long-running conversations. The PR has been updated but remains open.

---

*Generated from GitHub data for HKUDS/nanobot as of 2026-07-01.*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — July 1, 2026

## Today's Overview

Hermes Agent saw an exceptionally high-activity day on June 30, with 50 issues and 50 pull requests updated in the last 24 hours, indicating intense community-wide development effort. The project maintains a healthy open-to-closed ratio of roughly 7:1 for issues, with 5 closed issues and 7 merged/closed PRs. A significant wave of bug reports and fixes arrived simultaneously, suggesting either a new edge-case discovery campaign or rapid stabilization work following the v0.17.0 release. No new releases were published today. The community is actively contributing both bug fixes and feature expansions, with particular focus on gateway stability, desktop UI polish, and plugin extensibility.

## Releases

No new releases today. The latest available version remains v0.17.0, released on June 19, 2026.

## Project Progress

Seven pull requests were merged or closed today, representing meaningful forward progress:

- **#47603** ([PR](https://github.com/NousResearch/hermes-agent/pull/47603)) — *fix(gateway): resolve button-prompt clarifies via typed replies* — Closed. Improves gateway UX by allowing text input to fulfill button/multiple-choice clarification prompts when users type instead of tapping.
- **#55730** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55730)) — *Hermes Desktop crashes every 4-6hrs* — Closed. Memory leak bug resolved.
- **#54999** ([Issue](https://github.com/NousResearch/hermes-agent/issues/54999)) — *[Bug]: unknown projects.create* — Closed. Desktop project creation failure fixed.
- **#53257** ([Issue](https://github.com/NousResearch/hermes-agent/issues/53257)) — *[Setup]: installation dead on Ubuntu* — Closed. Installation script issue addressed.
- **#55331** ([PR](https://github.com/NousResearch/hermes-agent/pull/55331)) — *fix(desktop): handle stale backend when creating projects* — Closed. Detects outdated backends and shows clear upgrade message.
- **#55771** ([PR](https://github.com/NousResearch/hermes-agent/pull/55771)) — *fix: CI stability improvements* — Closed. Test race condition fix and action version bumps.

## Community Hot Topics

The most active discussions today reveal a community focused on building comprehensive agent capabilities:

1. **#28893** ([Issue](https://github.com/NousResearch/hermes-agent/issues/28893)) — *Showcase: hermes-companion plugin* (6 comments) — A zero-patch plugin bundling persona evolution, emotional state, ambient processing, and proactive check-ins. This is a showcase of what the community is building atop Hermes, referencing four other feature requests, indicating strong demand for a cohesive "companion" layer.

2. **#16259** ([Issue](https://github.com/NousResearch/hermes-agent/issues/16259)) — */model auto-detect hijacks custom:* providers* (5 comments, 1 👍) — A persistent bug where custom providers get silently switched to OpenRouter. The community is invested in fixing this because custom/local model support is critical for self-hosted users.

3. **#55647** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55647)) — *background-review skill hallucination* (3 comments) — A critical P1 bug where the agent's self-improvement system overwrites skills it hasn't read, generating phantom content. This touches on core agent safety.

4. **#9645** ([Issue](https://github.com/NousResearch/hermes-agent/issues/9645)) — *Configurable Proactive Check-Ins* (3 comments, 7 👍) — The most-liked feature request today. Users want Hermes to occasionally send unsolicited, human-feeling messages.

5. **#55633** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55633)) — *Windows Electron Desktop infinite process spawning* (3 comments) — A crash-adjacent bug on Windows affecting core desktop experience.

## Bugs & Stability

A significant wave of bug reports arrived today, several with corresponding fix PRs already submitted:

### P1 (Critical)
- **#55769** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55769)) — *Telegram polling silently dies after bg-review thread failures* — Gateway goes silent while process stays alive. No fix PR yet.
- **#55647** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55647)) — *background-review skill hallucination* — Agent overwrites skills without reading them first. No fix PR yet.

### P2 (High)
- **#55760** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55760)) — *macOS browser-cdp breaks visible Chrome windows* — LaunchAgent headless mode conflict.
- **#55761** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55761)) — *Telegram duplicate messages on short text turns* — Stream preview + gateway final send race.
- **#55750** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55750)) — *Feishu quote-reply broken in DM* — Fix PR #55766 submitted.
- **#55712** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55712)) — *Remote dashboard token rotation expiration* — Session expiry loop.
- **#55633** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55633)) — *Windows desktop infinite process spawning* — `OpenConsole.exe`/`conhost.exe`/`git.exe` infinite loop.

### P3 (Medium)
- **#55755** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55755)) — *Memory tool 'Unknown action None' error* — Fix PR #55768 submitted.
- **#55779** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55779)) — *DEFAULT_CONFIG duplicate "kanban" key* — Fix PR #55778 submitted.
- **#55774** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55774)) — *hermes meet node NameError crash* — Fix PR #55772 submitted.
- **#55775** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55775)) — *Desktop UI stuck "Summarizing thread" panel* — No fix PR yet.
- **#53813** ([Issue](https://github.com/NousResearch/hermes-agent/issues/53813)) — *Sidebar loses session↔project association after compaction* — No fix PR yet.

## Feature Requests & Roadmap Signals

Today's feature requests cluster around several themes pointing toward the next major release:

1. **Plugin Ecosystem Maturation** — **#28893** (hermes-companion) and **#55765** ([PR](https://github.com/NousResearch/hermes-agent/pull/55765)) (memory write plugin hooks) signal a push toward a fully extensible plugin architecture. The community wants to build custom companion layers without patching core.

2. **Multi-Session Orchestration** — **#54734** ([Issue](https://github.com/NousResearch/hermes-agent/issues/54734)) (native workflow models) and **#40394** ([Issue](https://github.com/NousResearch/hermes-agent/issues/40394)) (multiple independent desktop windows) indicate demand for parallel agent workflows and window management.

3. **Terminal Feature Parity** — **#55555** ([PR](https://github.com/NousResearch/hermes-agent/pull/55555)) (CLI+TUI `/journey` timeline) brings the desktop Memory Graph to the terminal, suggesting a push for equal capabilities across interfaces.

4. **Multi-Model Provider Support** — **#55573** ([Issue](https://github.com/NousResearch/hermes-agent/issues/55573)) — Users want to configure multiple models for a single custom OpenAI-compatible provider, indicating growing use of local model servers.

**Prediction:** The next minor release (v0.18.0) will likely include plugin lifecycle hooks, the `/journey` command, and multiple fixes for the gateway stability issues revealed today.

## User Feedback Summary

**Pain Points (from bug reports):**
- Desktop stability remains a concern: crashes (memory leaks), UI freezes, sidebar state corruption all reported across platforms
- Telegram gateway is fragile: polling dies silently, messages get duplicated, video files fail to cache
- Custom/local provider support has rough edges: model auto-detection overrides manual configuration, multi-model selection is cumbersome
- Windows users face unique issues: infinite process spawning, installation failures, Electron quirks

**Use Cases (from feature requests):**
- **Personal AI companion** (#28893) — Users building always-on, emotionally-aware agents
- **Multi-agent orchestration** (#18420) — Product intelligence pipelines using named specialist profiles
- **Home automation integration** (#13529) — Activity API for Home Assistant/Telegram/Discord cross-platform use
- **Long-running project supervision** (#15400) — Heartbeat-driven agent runs for supervised projects

**Satisfaction Signals:** The community is actively building plugins and contributing fixes, indicating strong engagement. Multiple "community showcase" submissions suggest users are productively extending Hermes' capabilities.

## Backlog Watch

Several important items remain stagnant or need maintainer attention:

1. **#16259** ([Issue](https://github.com/NousResearch/hermes-agent/issues/16259)) — */model auto-detect hijacks custom:* providers — Open since April 26, 5 comments, 1 👍. P2 bug with known root cause but no fix PR.

2. **#10164** ([Issue](https://github.com/NousResearch/hermes-agent/issues/10164)) — *Context-aware skills prompt budget management* — Open since April 15, 3 comments. Critical for long sessions. No fix PR despite clear problem description.

3. **#33536** ([PR](https://github.com/NousResearch/hermes-agent/pull/33536)) — *fix(bedrock): decode base64 data URL* — Open since May 27. P3 but blocks Bedrock users from sending images. No recent activity.

4. **#25186** ([PR](https://github.com/NousResearch/hermes-agent/pull/25186)) — *Add TrueConf gateway adapter* — Open since May 13. Community contribution with no reviewer activity.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-01

## Today's Overview
PicoClaw is showing moderate activity with 7 issues and 7 PRs updated in the last 24 hours. A new nightly build (v0.3.1-nightly) was released, though marked as potentially unstable. The project has 5 open active issues and 2 closed issues, with 5 open PRs and 2 merged/closed. A cluster of new bugs reported today suggests the nightly build or recent changes may have introduced regressions in authentication, provider connectivity, and platform compatibility. The community remains engaged around gateway feature requests and provider improvements.

## Releases
A single release was published today:

**[Nightly Build v0.3.1-nightly.20260630.52320f48](https://github.com/sipeed/picoclaw/compare/v0.3.1...main)** — Automated nightly build that may be unstable. No breaking changes or migration notes documented. Intended for testing upcoming features on the `main` branch.

## Project Progress
Two PRs were merged/closed today:

- **[PR #3198](https://github.com/sipeed/picoclaw/pull/3198) (closed)** — `fix(providers): surface friendly auth error messages` by lc6464. Improves provider authentication error handling with structured HTTP errors, giving users clearer guidance when API keys or permissions fail. Likely addresses user confusion seen in recent support threads.

- **[PR #3143](https://github.com/sipeed/picoclaw/pull/3143) (closed)** — `fix(web): block private IPv4 embeds in ISATAP literals` by lc6464. Fixes an SSRF guard bypass (issue #3074) by teaching the IP classifier to recognize ISATAP IPv6 literals that embed private or loopback IPv4 addresses.

## Community Hot Topics
- **[Issue #3093](https://github.com/sipeed/picoclaw/issues/3093) (open, 4 comments, 1 👍)** — User requests gateway support for SimpleX, Wire, or Tox. The issue has been open since June 10 and is marked stale, indicating user interest in decentralized communication protocols that hasn't yet gained maintainer traction.

- **[Issue #3090](https://github.com/sipeed/picoclaw/issues/3090) (closed, 3 comments)** — Panel not working on Safari iOS <16.4. Closed today, though the fix PR isn't explicitly linked. This affected users on older iOS devices running PicoClaw v0.2.9.

- **[Issue #3153](https://github.com/sipeed/picoclaw/issues/3153) (open, 2 comments)** — Volcengine Doubao Seed tool calls leak raw `<seed:tool_call>` text instead of executing. This is a provider-specific bug affecting a subset of users, but it's been open since June 22 without a fix PR.

**Analysis**: The most active topics revolve around gateway expansion (decentralized protocols) and provider-specific bugs. The Volcengine issue (#3153) may be under-invested given it's a documented regression in tool-call execution.

## Bugs & Stability

**High Severity:**
- **[Issue #3195](https://github.com/sipeed/picoclaw/issues/3195) (open)** — OpenAI GPT does not work on NanoKVM with default config. New issue (reported today). User configured gpt-5.4 per documentation but all interactions return errors. No comments or fix PR yet. Possible regression in NanoKVM 2.4.0 integration.

- **[Issue #3199](https://github.com/sipeed/picoclaw/issues/3199) (closed)** — Custom model provider cannot connect to `http://127.0.0.1` OpenAI-compatible endpoint. Closed today with 0 comments — unclear if a fix was applied or if it was a misconfiguration. This pattern (local endpoint refusal) is worrying.

**Medium Severity:**
- **[Issue #3197](https://github.com/sipeed/picoclaw/issues/3197) / [#3196](https://github.com/sipeed/picoclaw/issues/3196) (open)** — Duplicate reports from same author: Codex and Antygravity OAuth login not working on v0.2.9. Authentication flow appears broken for at least two providers.

**Low Severity:**
- **[Issue #3153](https://github.com/sipeed/picoclaw/issues/3153) (open)** — Volcengine tool call leak. Reproducible but only affects specific Doubao models.

*Note: No fix PRs exist for any of today's new bugs.*

## Feature Requests & Roadmap Signals
- **[PR #3063](https://github.com/sipeed/picoclaw/pull/3063) (open)** — `feat: add deltachat gateway` by trufae. Open since June 8, this adds a DeltaChat gateway. Combined with Issue #3093 (SimpleX/Tox), there is clear community demand for decentralized messaging integrations. Likely candidates for v0.3.2.

- **[PR #3118](https://github.com/sipeed/picoclaw/pull/3118) (open)** — Add remote Pico WebSocket mode to the `picoclaw agent` command. Enables remote agent operation over WebSocket. Still open since June 12, awaiting review.

- **[PR #3163](https://github.com/sipeed/picoclaw/pull/3163) (open)** — AWS Bedrock Converse prompt caching via cache points. Performance optimization for Bedrock users. Open since June 23.

**Prediction for next release (v0.3.1 stable):** The auth error improvement (#3198) and ISATAP SSRF fix (#3143) were just merged — strong candidates. The DeltaChat gateway (#3063) and remote agent mode (#3118) have been open for weeks and may land if maintainers prioritize before stable cut.

## User Feedback Summary
- **Pain point**: Local/self-hosted users are hitting connectivity issues with custom OpenAI-compatible endpoints (#3199) and NanoKVM deployments (#3195), suggesting the networking layer may have regressed in recent builds.
- **Pain point**: OAuth login failures for Codex and Antygravity (#3196/#3197) are blocking users on v0.2.9 — two duplicates in one day indicates this is not an isolated case.
- **Pain point**: Volcengine tool-call leakage (#3153) undermines trust in the tool-use pipeline for provider-specific integrations.
- **Satisfaction signal**: The community is actively contributing gateway features (DeltaChat, SimpleX/Tox requests) and performance improvements (prompt caching), indicating developer engagement.
- **Dissatisfaction signal**: Multiple stale issues (tagged `[stale]`) and PRs waiting weeks for review may frustrate contributors.

## Backlog Watch
- **[Issue #3093](https://github.com/sipeed/picoclaw/issues/3093) (open, stale)** — SimpleX/Tox gateway request. Open since June 10, stale-tagged, 4 comments, 1 upvote. No maintainer response. Community has interest but feature has not been picked up.

- **[Issue #3153](https://github.com/sipeed/picoclaw/issues/3153) (open, stale)** — Volcengine tool-call leak. Open since June 22, stale-tagged, 2 comments. A functional regression in tool execution that could affect production users.

- **[PR #3063](https://github.com/sipeed/picoclaw/pull/3063) (open, stale)** — DeltaChat gateway. No reviewer activity since June 8. Contributor effort may be wasted if not merged or given feedback soon.

- **[PR #3118](https://github.com/sipeed/picoclaw/pull/3118) (open)** — Remote agent WebSocket mode. No reviewer activity since June 12. Significant feature addition with no maintainer engagement.

**Maintainer attention needed**: The accumulation of stale items (2 issues + 2 PRs) without maintainer responses, combined with today's cluster of new bugs, suggests the project may need more reviewer bandwidth or a triage pass to clear the backlog before v0.3.1 stable release.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-01

## 1. Today's Overview
NanoClaw shows **elevated development velocity** with **9 open pull requests** and **3 issues updated in the last 24 hours**, indicating an active sprint cycle. Security and platform reliability dominate the current focus: a critical symlink-escaping vulnerability (#2828) has been fixed and merged (#2880), while two separate media-handling bugs in Discord and WhatsApp adapters surfaced simultaneously. The project is expanding its **platform reach** with a native Matrix E2EE adapter (#2844) and a new **WeChat channel adapter** (#2889), alongside infrastructure improvements like ephemeral document rendering (#2893) and agent templates (#2890). Overall project health is strong, with responsive maintainers and clear prioritization of security hardening.

## 2. Releases
**No new releases** in the last 24 hours. The last tagged release precedes this digest period.

## 3. Project Progress
One PR was merged/closed in the last 24h:

- **PR #2880** (merged) — `fix(security): contain inbox symlink escapes in attachment writes` — **Closes CWE-59 vulnerability** #2828. This is a high-impact security fix that prevents compromised agents from using symlinks within writable session directories to write arbitrary files on the host system. The fix applies to **both** inbound file-write paths, making it a critical hardening measure for multi-agent deployments.

Eight PRs remain open with active development:
- **PR #2895** — WhatsApp media recovery via `reuploadRequest`
- **PR #2893** — Ephemeral container-based document rendering
- **PR #2892** — Telegram thread/forum support
- **PR #2891** — `resolveChannelName` interface addition
- **PR #2890** — Agent template system
- **PR #2889** — Daily news agent + WeChat channel
- **PR #2886** — Provider inheritance fix for channel-registered agents
- **PR #2844** — Native Matrix E2EE adapter

## 4. Community Hot Topics

| Issue/PR | Type | Engagement | Topic |
|----------|------|------------|-------|
| [#2828](https://github.com/nanocoai/nanoclaw/issues/2828) | Issue (CLOSED) | 2 👍 | Security: symlink-follow to arbitrary file write |
| [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) | Issue (OPEN) | 1 comment | Discord attachment content loss |
| [#2894](https://github.com/nanocoai/nanoclaw/issues/2894) | Issue (OPEN) | 0 comments | WhatsApp media CDN failure |

**Analysis:** The closed security advisory (#2828) garnered the most community attention (2 reactions), reflecting high concern for sandbox integrity in multi-agent setups. The Discord attachment issue (#2888) and WhatsApp media issue (#2894) both point to a **pattern of inconsistent media handling across adapters** — suggesting users are relying heavily on file/image exchange in their agent interactions, and parity across chat platforms is a growing pain point.

## 5. Bugs & Stability

**High Severity**
- **Issue #2888** (OPEN) — **Discord attachments silently dropped**: The `messageToInbound` bridge only downloads attachment metadata, never content. Agent sees only file type/name. **Fix PR:** Not yet filed. Workaround: Use Telegram. **Risk:** Agents lose context from screenshots, documents, and images sent via Discord.
- **Issue #2894** (OPEN) — **WhatsApp inbound media silently dropped on CDN fetch failure**: The `catch` block swallows `Failed to fetch stream` errors. **Fix PR:** [#2895](https://github.com/nanocoai/nanoclaw/pull/2895) (open) implements `reuploadRequest` recovery path. **Risk:** Silent data loss — agent never knows media was sent.

**Resolved**
- **Issue #2828** (CLOSED) — **Symlink-follow security vulnerability** — Fixed by merged PR #2880.

**Medium Severity**
- **PR #2886** (OPEN) — **Channel-registered agents inherit wrong provider**: On single-provider installs, new agents created via channel approval use default (Claude) instead of the user's configured provider, causing 401 errors. Fix proposed in #2886.

## 6. Feature Requests & Roadmap Signals

**High-probability next-version features:**

1. **Native Matrix E2EE Adapter** (#2844) — Replaces the Chat SDK bridge (`@beeper/chat-adapter-matrix`) with a Rust-crypto-backed native adapter. This is a **massive upgrade** for Matrix users who need persistent end-to-end encryption without WASM crypto limitations. Likely to merge within 1-2 sprints given the 6-day active development history.

2. **Agent Templates** (#2890) — A reusable bundle system for stamping out agent groups with instructions, MCP servers, and skills. Template sources include a public library, local paths, or any git repo. Signals a **shift toward composable, shareable agent deployments** — expect this to be a cornerstone of the next minor release.

3. **Daily News Agent + WeChat Channel** (#2889) — Adds a production-ready `daily-news-agent` with HN/RSS digest, recurring 9:00 task scheduling, and a **native WeChat adapter**. Strong signal that Chinese-market users and news-aggregation use cases are being prioritized.

4. **Ephemeral Document Rendering** (#2893) — Host-mediated rendering of Quarto/LaTeX/Chromium documents in a **network-isolated ephemeral container**. This keeps heavy/dangerous toolchains outside the agent runtime — a security-first design choice that may become the preferred pattern for agent-sidecar processes.

**Less likely for next release:**
- Telegram thread support (#2892) is a small flag flip — trivial, will likely merge soon.
- `resolveChannelName` interface (#2891) is a type-level fix blocked by dependent PRs.

## 7. User Feedback Summary

**Pain Points Expressed:**
- **Inconsistent cross-platform media handling**: A user reports "Telegram works fine" while Discord drops attachments entirely (#2888). This creates **platform lock-in** — users feel forced onto Telegram for image-dependent workflows.
- **Silent failures in WhatsApp**: The CDN fetch failure is swallowed without any warning (#2894) — the agent never knows media was attempted, making debugging impossible without diving into logs.
- **Provider configuration breaks for new agents**: Single-provider installs hit 401 errors because new agents default to Claude (#2886) — a frustrating onboarding friction for users who have customized their LLM provider setup.

**Satisfaction Signals:**
- The **swift security fix** (#2828 → #2880, 9 days from report to merge) demonstrates strong maintainer responsiveness and builds trust in the project's security posture.
- The **Matrix E2EE rewrite** (#2844) addresses a long-standing community request for persistent encryption, and the choice of Rust crypto bindings (not WASM) shows technical depth.

**Use Cases Driving Development:**
- Multi-platform chat agent deployment (Discord, Telegram, WhatsApp, Matrix, now WeChat)
- Document-aware agents (render + analyze using ephemeral containers)
- Scheduled news aggregation (HN + RSS with LLM digest)
- Composable agent templates for rapid deployment

## 8. Backlog Watch

**No critical backlog items** — all open issues and PRs have been updated within the last 48 hours, indicating active triage. The three open issues all have either a fix PR open or have been reported within the last day.

**Items worth monitoring:**
- **PR #2844** (Matrix E2EE adapter) — 6 days open, no blockers mentioned but is a large rewrite. Could benefit from reviewer bandwidth.
- **PR #2889** (Daily News + WeChat) — Adds a new channel adapter alongside a group example. Watch for integration testing coverage since WeChat is a complex platform.
- **PR #2886** (Provider inheritance fix) — 2 days open with no comments. Low complexity, good candidate for quick review to prevent user frustration on single-provider installs.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest
**Date:** 2026-07-01

## 1. Today's Overview

NullClaw shows moderate activity today with 2 open issues and 4 merged PRs, all of which were closed during the last 24 hours. No new releases were published. The project maintains steady contributor momentum, particularly from user `yanggf8` who landed a significant cron subsystem enhancement alongside provider and CLI fixes. The two open issues relate to Android/Termux build failures and Telegram channel responsiveness, both indicating ongoing platform-specific stability work. Overall, the project appears healthy with active maintenance but moderate community engagement.

## 2. Releases

No new releases were published on this date. The latest available release remains v2026.4.17 (referenced in Issue #868).

## 3. Project Progress

Four PRs were merged/closed today, all authored by `yanggf8`:

- **[[CLOSED] #641 – fix(providers): fix GLM/ZhipuAI thinking mode and native tool_calls](nullclaw/nullclaw PR #641)**  
  Resolves three interrelated issues with the `glm-cn`/`zhipu-cn` provider: thinking parameter always-on causing response loops, native tool calls not triggering, and thinking parameters not propagating to `keep_alive` requests. This improves reliability for users of these Chinese AI providers.

- **[[CLOSED] #643 – fix(cron): allow agent jobs to omit command field in cron.json](nullclaw/nullclaw PR #643)**  
  Agent cron jobs previously required a redundant `command` field that caused silent job disappearance on gateway restart if set to `null`. Now `command` is optional, with the loader falling back to the `prompt` field. This fixes a data-loss bug in scheduled agent tasks.

- **[[CLOSED] #645 – fix(cron): add --account flag to cron add-agent CLI](nullclaw/nullclaw PR #645)**  
  Adds missing `--account` flag to `nullclaw cron add-agent`, enabling full delivery routing (e.g., specifying which Telegram bot to use) directly from CLI without manual `cron.json` editing.

- **[[CLOSED] #783 – feat(cron): cron subagent, run history, JSON output, security hardening](nullclaw/nullclaw PR #783)**  
  Major cron subsystem enhancement introducing a DB-backed scheduler with run history table, worker queue, support for skill/agent/shell job types, per-job timezone offsets, delivery routing, operator alerts, and JSON CLI output. Also includes security hardening.

These changes collectively strengthen the cron subsystem significantly while fixing provider compatibility and CLI usability issues.

## 4. Community Hot Topics

The most active discussion this period centers on:

- **[#868 – zig build fails on Android/Termux (aarch64)](nullclaw/nullclaw Issue #868)**  
  *5 comments, 0 reactions* – This long-running issue (created April 23) concerns a build failure with `AccessDenied` during file linking on aarch64 Android/Termux environments. The user reports using Zig 0.16.0 and nullclaw v2026.4.17. While comments are not detailed in the summary, the issue has persisted for over 2 months without resolution, suggesting a niche but unresolved platform compatibility problem.

- **[#972 – telegram channel stops responding after idle time](nullclaw/nullclaw Issue #972)**  
  *0 comments, 0 reactions* – Newly opened today. The user reports Telegram channel connectivity dies overnight, though the nullclaw backend continues running normally (verified via `nullclaw agent -m "ping"` output). The issue has no comments yet, indicating it may still be awaiting triage.

No other issues or PRs show significant comment or reaction activity. The low reaction counts suggest limited community voting or endorsement of specific items.

## 5. Bugs & Stability

**High Severity:**
- **[#972 – Telegram channel ceases response after idle](nullclaw/nullclaw Issue #972)** – New today. The Telegram integration appears to lose connectivity during prolonged idle periods (overnight). The backend remains functional, pointing to a potential connection re-establishment bug in the Telegram channel implementation rather than a core agent failure. No existing fix PR. *(Severity: High – affects primary user-facing channel)*

**Medium Severity:**
- **[#868 – Zig build fails on Android/Termux (aarch64)](nullclaw/nullclaw Issue #868)** – Long-standing (2+ months) build blocker for Android users. The `AccessDenied` error on `linkat` suggests filesystem permission issues or a Zig toolchain incompatibility on Termux. No fix PR exists. *(Severity: Medium – platform-specific; affects mobile/non-standard deployments)*

**Resolved Bugs Today:**
- Silent cron job disappearance on gateway restart when `command` field was `null` (PR #643) – **fixed**
- GLM/ZhipuAI thinking mode causing response loops and tool call failures (PR #641) – **fixed**

## 6. Feature Requests & Roadmap Signals

Based on recent merged PRs and open issues, the following feature signals emerge:

- **Cron subsystem expansion** – PR #783 represents a major investment in cron capabilities: DB-backed scheduler, subagent support, JSON output, security hardening. Likely to see further refinement in next minor release.

- **Telegram channel reliability** – Issue #972 suggests users need auto-reconnect or keep-alive mechanisms for Telegram channels. A fix or enhancement is probable in the next cycle.

- **Android/Termux build support** – Issue #868 remains unresolved. Given niche demand, this may not be a priority unless more users report it, but could be addressed if maintainers target Termux as a supported deployment environment.

- **CLI completeness** – PR #645 (adding `--account` flag) shows ongoing incremental improvements to CLI ergonomics. Expect more `cron` CLI enhancements and possibly broader CLI audit.

Predicted for next version (v2026.7.x): Telegram channel keep-alive fix, additional cron JSON output refinements, and possibly a build guide for Termux.

## 7. User Feedback Summary

- **Pain point #1 – Build fragmentation**: The Android/Termux build failure (#868) highlights that nullclaw’s build system does not fully support non-standard Linux environments. User `NOTJuangamer10` reported this over 2 months ago with no resolution, suggesting limited testing on mobile/ARM Linux.

- **Pain point #2 – Persistent connection management**: User `i11010520` reports that Telegram channels fail silently after idle periods. This indicates a reliability gap in long-running deployments where connections timeout without reconnection logic.

- **Satisfaction signal**: The quick merge of 4 PRs from `yanggf8` (including a significant cron feature) suggests productive contributor-maintainer collaboration, though community engagement (reactions, comments) remains low overall.

- **Use case evidence**: Telegram as primary delivery channel is confirmed across both open issues (#972) and fixed PRs (#645), indicating heavy reliance on Telegram integration. Cron scheduling for automated agent tasks is also a clear use case given the focus on cron improvements.

## 8. Backlog Watch

The following items require maintainer attention:

- **[Issue #868 – zig build fails on Android/Termux](nullclaw/nullclaw Issue #868)**  
  *Created: 2026-04-23 | Updated: 2026-06-30* – Unresolved for 69 days. With 5 comments but 0 maintainer responses shown, this may have been missed. An acknowledgment or reproduction attempt would help the user.

- **[Issue #972 – Telegram channel stops responding](nullclaw/nullclaw Issue #972)**  
  *Created: 2026-06-30* – Newly opened today with zero comments. Needs triage to determine if this is a known issue, a configuration problem, or a genuine bug requiring a fix.

**No long-unanswered PRs** are evident; all 4 today’s PRs were closed promptly. The backlog is minimal but the two unanswered issues, particularly #868, warrant review to avoid user attrition.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-01

## 1. Today's Overview

IronClaw showed **very high development velocity** over the past 24 hours, with **50 pull requests** updated (29 open, 21 merged/closed) and a focused burst of **14 issues** (13 active, 1 closed). The team processed **21 PRs through merge or close** — a strong throughput sign — while the issue tracker remained stable with no new spikes. Core-area activity centered on storage performance (libSQL WAL tuning, memory-store heartbeats, stress concurrency), Reborn WebUI fixes (composer behavior, notification headers, error surfacing), and CI infrastructure expansion (Playwright workflows, LLVM coverage). A coordinated **bug bash** produced six quality reports (P1–P3 severity) covering automation naming, conversation ordering, skill routing, and authentication flows — suggesting the Reborn launch is in a late-stage polish cycle. No new releases were cut today.

## 2. Releases

**No new releases** in the last 24 hours.

---

## 3. Project Progress

**21 PRs merged or closed today**, reflecting substantial forward movement across three major themes:

### Storage & Performance
- **#5451** (merged) — Enabled **WAL mode + tuned PRAGMAs** on the libSQL backend, eliminating the slowest `DELETE` rollback journal mode that was a bottleneck for concurrent-turn writes.
- **#5447** (merged) — Added an **unlimited-limits fast path** for the resource governor, skipping durable resource writes when limits are unbounded; stress runs now isolate on this fast path.
- **#5444** (merged) — Added **provider-latency stress mode** to `ironclaw_stress`, routing through real provider calls with retry/failover/circuit-breaker behavior.
- **#5438** (merged) — Fixed **GitHub search validation recovery**, now accepting `utc_offset` on `builtin.time::now` and classifying 422 responses as invalid input (not generic failure).

### Reborn Backend & WebUI
- **#5448** (merged) — **Unblocked main-only checks** by removing the generated WebUI v2 bundle from source control, fixing a CI failure where tracked files matched `.gitignore`.
- **#5445** (merged) — Made **missing outbound delivery targets recoverable**: when a target ID cannot be resolved, returns a model-visible `Failed` instead of a host error.
- **#5441** (merged) — Added **header notification bell** for automation approvals with popover/drawer message list.
- **#5431** (merged) — Re-enabled **`spawn_subagent` surface** and un-ignored end-to-end spawn tests (roadmap T0-SPAWN).

### CI & Testing
- **#5449** (merged) — Added a **Reborn Playwright workflow** for standalone browser scenarios, configurable for PR or nightly CI.
- **#5430** (merged) — Added **[cargo-llvm-cov] integration-tier coverage job** (T0-COV) for informational per-PR coverage signal.
- **#5454** (merged) — Stabilized **QA 2E assistant text gate** with better response-block matching and flexible email wording.
- **#5434** (merged) — Fixed **zero-credits test flake** in the Reborn coverage suite.

### Bug Fixes & Polish
- **#5404** (merged) — Fixed **chat composer not clearing after send**; restores draft on rejected sends with regression coverage.
- **#5338** (merged) — Surfaces **real failure detail instead of generic `invalid_input`** in Reborn WebUI across multiple failure paths.

---

## 4. Community Hot Topics

| Issue/PR | Activity | Key Signal |
|----------|----------|------------|
| **#5420** — Routine delivery target is a global default, not per-routine | 1 comment, last updated 2026-06-30 | Users discovering delivery routing is **shared across all routines** — an email summary and Slack-delivered automation collide |
| **#5443** — Add header notifications for automation tasks | 0 comments, created 2026-06-30 | Feature request turned into **PR #5441 (merged)** within hours — fast team response |
| **#5426** — Cannot create routine: system drive not available | 1 comment, created 2026-06-29 | Critical QA blocker: routine creation fails when system drive is inaccessible |
| **#5415** — Multi-tool Google Sheets workflow fails with protocol violation (P1) | 0 comments, created 2026-06-29 | **Highest-severity bug bash report**: 18–25 tool call workflows consistently fail |
| **#5437** — Daily failure taxonomy (2026-06-30) | 0 comments, created 2026-06-30 | Systematic failure analysis: 146 non-pass tasks all failing with HTTP 400 (model routing) |
| **#5421** — Web search not zero-config; re-prompts for auth | 0 comments, created 2026-06-29 | Two distinct issues: Exa MCP inactive by default, and web_search re-auths even when chat works |
| **#5428** — Harden mock-MCP test egress layer | 0 comments, created 2026-06-30 | Three pre-existing test defects deferred from behavior-preserving refactor |

**Underlying needs**: Users are hitting real multi-connection, multi-automation workflows and discovering **cross-cutting state leaks** (delivery targets, authentication boundaries). The bug bash found consistent **backend failures in complex tool sequences** (10+ calls) and **inconsistent UI state** (conversation ordering, connection status). The fast-track from feature request (#5443) to merged PR (#5441) in the same day shows strong team alignment on UX improvements.

---

## 5. Bugs & Stability

### Critical/High Severity (P1–P2)

| Issue | Severity | Description | Status |
|-------|----------|-------------|--------|
| **#5415** | P1 | Multi-tool Google Sheets workflow (email → sheet) fails with protocol violation | Open; no fix PR yet |
| **#5416** | P2 | Incorrect Google connection state causes contradictory auth flow | Open; affects UX trust |
| **#5417** | P2 | Wrong skill activated for Hacker News search (activates "tech-debt-tracker") | Open; skill routing defect |
| **#5418** | P2 | Conversation messages appear in wrong order after tool activity | Open; UI rendering sequenced incorrectly |

### Medium Severity (P3)

| Issue | Severity | Description | Status |
|-------|----------|-------------|--------|
| **#5419** | P3 | No option to rename an automation | Open; proposed UX feature |
| **#5429** | — | Web Search requires NEAR AI Cloud API token (not zero-config) | Open; affects first-time setup |
| **#5420** | — | Routine delivery target is global, not per-routine | Open; **cross-routine state leak** |
| **#5426** | — | Cannot create routine: system drive not available | Open; QA blocker for hosted-staging |

### Infrastructure/Test Failures

| Issue | Description | Status |
|-------|-------------|--------|
| **#4108** | Nightly E2E has been failing since 2026-05-27 | Long-standing; last updated 2026-06-30 |
| **#5437** | 146 non-pass tasks in pinchbench: all HTTP 400 from `model/deepseek/...` | Fresh analysis; suggests model routing misconfiguration |

**Fix-PR pairing**: No open fix PRs directly target the P1 bug (#5415). The **#5445** (merged) fix for missing delivery targets is related to the delivery state leak in #5420. The **#5454** stabilization PR addresses the QA text gate but not the underlying protocol violations.

---

## 6. Feature Requests & Roadmap Signals

### Built & Merged
- **Header notifications for automation approvals** (#5443 → #5441, merged) — Likely in next release
- **Per-routine delivery target** (implied by #5420 fix needed) — High priority for UX consistency

### Proposed but Not Yet Addressed
- **Rename automation** (#5419) — Low effort, high impact for user discoverability
- **Zero-config web search** (#5421) — Essential for first-run experience; team aware

### Roadmap Milestones
- **T0-COV** (Coverage CI job, merged #5430)
- **T0-SPAWN** (Subagent spawn re-enabled, merged #5431)
- **M1-webui-product** tag appears in #5412 (log copy fix, closed)
- The **reborn-backend-coverage-roadmap.md** is actively being executed (Tier 0 tasks)

**Prediction**: The next release will likely include header notifications, subagent spawn, storage performance improvements (WAL, memory heartbeats, unlimited-limits fast path), and the merged web-search/CI coverage work. The per-routine delivery target fix (#5420) could be fast-tracked as a P0 patch.

---

## 7. User Feedback Summary

### Real Pain Points (from bug bash & QA)
1. **Automation naming is immutable**: Auto-generated names are too long/truncated, and users cannot edit (#5419)
2. **Tool-heavy workflows fail silently**: 18–25 call sequences hit "protocol violations" with no actionable error (#5415)
3. **UI ordering is incorrect**: Conversation context jumps above tool activity blocks (#5418)
4. **Connection state is confusing**: Agent says "Gmail already connected" before authentication (#5416)
5. **Skill routing is unpredictable**: "Search Hacker News" triggers "tech-debt-tracker" instead of web search (#5417)
6. **Configuration burden**: Web search requires API token even when chat works (#5429, #5421)

### Use Cases
- **Email-to-sheet automation**: Checking emails and populating spreadsheets (failed, #5415)
- **Cross-channel delivery**: Setting one routine to Slack reroutes all deliveries (frustrating, #5420)
- **Automation discovery**: Users only notice new tasks if they open the Automations page (#5443)
- **Web search in local dev**: Requires manual API token setup even with existing working chat (#5421)

**Satisfaction indicators**: The team's rapid response to #5443 (anti-pattern: users miss automation results) shows alignment with user needs. However, the P1 protocol violations and P2 ordering/state bugs suggest **complex multi-tool workflows are not yet stable**.

---

## 8. Backlog Watch

| Issue | Age | Type | Why It Matters |
|-------|-----|------|----------------|
| **#4108** — Nightly E2E failed | 34 days (2026-05-27) | 🟡 Infrastructure | Long-running E2E failure undermines confidence in automated testing; last updated today but not resolved |
| **#5101** — Reuse cargo-component installer in live canary (PR) | 10 days (2026-06-20) | 🟡 CI | Open PR from a new contributor; low activity despite being "risk: medium" and potentially blocking CI consistency |
| **#5369** — Suppress Cranelift debug log floods (PR) | 3 days (2026-06-27) | 🟢 Polish | New contributor PR; might need maintainer review to avoid log noise in production |
| **#5428** — Harden mock-MCP test egress layer | 0 days (2026-06-30) | 🟢 New | Deferred defects from refactor; low urgency but could mask regressions |

**Notable**: The **Nightly E2E** (#4108) has been failing for over a month with no resolution mentioned — this is the largest backlog risk. The new contributor PRs (#5101, #5369) are low-risk but could benefit from maintainer attention to keep contributor momentum.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the structured LobsterAI project digest for **2026-07-01**.

---

## LobsterAI Project Digest — 2026-07-01

### 1. Today's Overview
Activity spiked significantly following yesterday's `2026.6.30` release, with 16 PRs updated (14 merged/closed) and 8 issues updated (2 closed). The team executed a major release containing analytics enhancements, diagnostic logging improvements, and critical fixes for OpenClaw and Cowork flows. While the release appears to have gone smoothly, the project is carrying a long tail of stale UX bugs (6 open issues), and a newly filed high-severity performance regression (#2230) comparing response times against CodeBuddy demands immediate attention.

### 2. Releases
**New Version: LobsterAI 2026.6.30 (Released 2026-06-30)**
- **Highlights:**
  - Unified Youdao Analyzer usage reporting (common app/platform/language parameters).
  - Expanded analytics across app start, settings, prompt input, conversations, artifacts, agents, skills, MCP, kits, IM, and scheduled tasks.
  - Diagnostic logging added for Cowork session loading, message pagination, and OpenClaw runtime error handling.
  - Fallback `maxTokens` limits for native Anthropic-format OpenClaw providers when bundled catalog is unreadable.
  - Scheduled task history now initializes the OpenClaw gateway client properly on startup.
  - UI fix: prevented prompt toolbar overlap when resizing artifacts in Cowork.
- **Breaking Changes:** None explicitly documented.
- **Migration Notes:** No migration steps provided; likely a seamless update.

### 3. Project Progress
The following major areas advanced in the last 24 hours:

- **Analytics & Telemetry:**
  - Added comprehensive diagnostic logging for Cowork and OpenClaw flows (#2229).
  - Removed prompt intent fields from analytics to avoid sending inferred user input semantics (#2233).
- **UI/UX (Cowork):**
  - Fixed conversation rail tooltips (cleaned plan-mode tags, increased preview length) (#2218, #2222, #2223).
  - Avoided accidental revert of rail fixes to release branch (#2225, #2226, #2224).
- **OpenClaw Engine:**
  - Fixed fallback `maxTokens` limits for native providers (#2232).
  - Fixed cron descendant finalization so sub-agent completion drives parent agent execution (#2234, still open).
- **Scheduled Tasks:**
  - Restored gateway-backed run history, fixing empty/not-ready state on startup (#2231).
- **General:**
  - Optimized model edit UI (#2236).

### 4. Community Hot Topics
| Item | Type | Last Updated | Comments | Link |
|---|---|---|---|---|
| #1382: Suggestion to change red highlighting (red implies failure) | Issue | 2026-06-30 | 2 | [View](https://github.com/netease-youdao/LobsterAI/issues/1382) |
| #1381: Cron tasks open new session each time; request to keep in same session | Issue | 2026-06-30 | 1 | [View](https://github.com/netease-youdao/LobsterAI/issues/1381) |
| #1426: Adding skills via upload lacks success feedback & list refresh | Issue | 2026-06-30 | 2 | [View](https://github.com/netease-youdao/LobsterAI/issues/1426) |
| #1427: Duplicate skills allowed when adding locally | Issue | 2026-06-30 | 2 | [View](https://github.com/netease-youdao/LobsterAI/issues/1427) |

All four of these are "stale" issues (created April 3, 2026), indicating persistent but unaddressed UX friction. Users are frustrated by: confusing color semantics, workflow inefficiency (new sessions for cron), lack of visual feedback, and data integrity (duplicate skills).

### 5. Bugs & Stability
**High Severity:**
- **#2230 (NEW — 2026-06-30):** Same model (DBX) and prompt is **10x slower** in LobsterAI (25 min) vs. CodeBuddy (2m24s), consuming 60M tokens vs. 67K tokens. This is a critical performance and cost regression. No fix PR exists yet.

**Medium Severity (Stale, UX):**
- **#1383:** Duplicate identical messages from WeChat mobile only sync once to Lobster desktop.
- **#1384:** Selecting multiple files in chat only retains the last file (fix PR #1372 has been open since April 2).
- **#1385:** Deleting a WeChat session does not clear history; re-asking brings back old messages.
- **#1426 / #1427:** Successful skill upload shows no feedback; duplicate skills can be created.

### 6. Feature Requests & Roadmap Signals
- **Persistent cron session context (#1381):** Users want scheduled tasks to reuse the same conversation window rather than creating a new one each run. This is a clear UX quality-of-life improvement likely to appear in a future release given the team's recent work on scheduled tasks (#2231).
- **Improved visual feedback for skill operations (#1426):** The lack of success/error feedback and stale list after upload suggests the skill management UI needs rework.
- **Logging/diagnostics improvements (#2229) were just shipped**, signaling the team is investing in production debuggability.

### 7. User Feedback Summary
- **Performance Dissatisfaction:** A user explicitly compared LobsterAI to CodeBuddy and found LobsterAI to be **10x slower** with ~900x more token consumption (#2230). This is a severe competitive disadvantage.
- **WeChat Integration Pain:** Two issues (#1383, #1385) highlight broken WeChat sync behavior—message deduplication and session history cleanup failures—indicating the WeChat bot integration is immature or regression-prone.
- **File Handling Regression:** The multi-file upload bug (#1384) has an open fix PR (#1372) since April 2, suggesting the fix is complex or stuck in review.
- **Color Semantics Confusion (#1382):** Chinese users expect red to denote errors, not informational warnings.

### 8. Backlog Watch
| Item | Created | Stale Since | Risk | Link |
|---|---|---|---|---|
| **PR #1372:** Fix multi-file selection (only last file kept) | 2026-04-02 | 90 days | High — unresolved UX regression | [View](https://github.com/netease-youdao/LobsterAI/pull/1372) |
| **Issue #1381:** Cron task session reuse | 2026-04-03 | 89 days | Medium — repeated user frustration | [View](https://github.com/netease-youdao/LobsterAI/issues/1381) |
| **Issue #1382:** Red highlighting suggestion | 2026-04-03 | 89 days | Low — cosmetic but popular | [View](https://github.com/netease-youdao/LobsterAI/issues/1382) |
| **Issue #1385:** WeChat session cleanup failure | 2026-04-03 | 89 days | Medium — data integrity concern | [View](https://github.com/netease-youdao/LobsterAI/issues/1385) |
| **PR #2234:** OpenClaw cron descendant finalization (OPEN) | 2026-06-30 | 1 day | Medium — cron reliability fix in review | [View](https://github.com/netease-youdao/LobsterAI/pull/2234) |

The project's health is mixed: the release cadence is strong, but a significant tail of **3-month-old UX bugs** with open fix PRs suggests either capacity constraints or prioritization of new features over backlog cleanup. The new performance regression (#2230) should be escalated to critical severity.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-01

## 1. Today's Overview
Moltis had a quiet 24-hour period with zero new issues and no releases. Activity was limited to dependency maintenance: three pull requests were updated, with one remaining open and two recently closed. No feature work, bug reports, or user-facing changes were observed. The project appears to be in a low-activity window, with ongoing automated dependency updates signaling steady maintenance but no new development momentum.

## 2. Releases
**No new releases.**  
The latest available releases remain unchanged. No version bumps, changelogs, or migration notes to report.

## 3. Project Progress
**No merged or closed PRs today** (2026-07-01).  
However, two PRs were *closed* in the preceding days (both updated yesterday):
- **PR #1134** (closed 2026-06-30) — Bumped `astro` from 6.3.3 to 6.4.8 in `/docs` and `undici` in `/website`. Improves documentation tooling and website dependency hygiene.  
  [GitHub](https://github.com/moltis-org/moltis/pull/1134)
- **PR #1121** (closed 2026-06-30) — Bumped `esbuild` from 0.25.12 to 0.28.1 in `/crates/web/ui`. This is a significant jump for a core build tool, likely bringing performance or compatibility improvements.  
  [GitHub](https://github.com/moltis-org/moltis/pull/1121)

## 4. Community Hot Topics
**No hot topics today.**  
The only open PR (#1141) has zero comments and zero reactions. It is a routine Dependabot automation for `esbuild` and `vite` bumps across multiple directories. No meaningful community discussion or interest was detected.  
[Open PR #1141](https://github.com/moltis-org/moltis/pull/1141)

## 5. Bugs & Stability
**No bugs, crashes, or regressions reported today.**  
No stability concerns surfaced in the last 24 hours. The project appears stable in this window.

## 6. Feature Requests & Roadmap Signals
**No feature requests or roadmap signals observed.**  
All activity was purely dependency maintenance. No user-submitted features, design discussions, or roadmap hints were present.

## 7. User Feedback Summary
**No user feedback available.**  
There were no issues, comments, or reactions indicating user satisfaction, dissatisfaction, pain points, or use cases. Community engagement appears minimal.

## 8. Backlog Watch
**No items require maintainer attention.**  
- There are no long-unanswered issues or PRs needing response.  
- The single open PR (#1141) is a routine Dependabot update less than 24 hours old and does not yet warrant escalation.  
- No stale or ignored contributions were identified.

---

**Project Health Assessment:**  
Low activity with no community engagement. While dependency upkeep continues, the lack of user interaction, feature development, or bug fixes suggests either a maintenance-only phase or a lull before a planned milestone. Maintainers may want to review if community channels (e.g., discussions, forums) are seeing activity not reflected in GitHub issues/PRs.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-01

## Today's Overview

The CoPaw project shows **elevated activity** with 23 issues and 50 PRs updated in the last 24 hours, indicating a high-velocity development cycle. The team closed 8 issues and merged 22 PRs, resolving critical bugs across frontend rendering, channel integrations, and runtime behavior. No new releases were published; the project remains on v1.1.12.post2 with the v2.0.0 alpha track ongoing. The community is highly engaged, contributing both bug reports and feature implementations via first-time contributors, particularly in memory retrieval, cron job flexibility, and attachment handling.

---

## Releases

**No releases today.** The latest published version remains `1.1.12.post2`. Pre-release work continues on the `v2.0.0-alpha.1` branch, tracked in issue [#5273](https://github.com/agentscope-ai/CoPaw/issues/5273).

---

## Project Progress

**22 merged/closed PRs** advanced the codebase today. Key accomplishments:

- **Loop Engineering System** — [#5665](https://github.com/agentscope-ai/CoPaw/pull/5665) introduces a composable gate-based architecture for agent loop control, with frontend settings UI. This addresses community concerns about infinite loops in agentic workflows.
- **DingTalk @Mention Support** — [#5590](https://github.com/agentscope-ai/CoPaw/pull/5590) (closed, under review) adds `@mention` parameters for proactive sends, cron delivery, and API calls, enabling multi-agent collaboration in DingTalk groups.
- **Runtime Spawn Subagent Fix** — [#5660](https://github.com/agentscope-ai/CoPaw/pull/5660) restores `spawn_subagent` functionality broken in the Runtime 2.0 migration (fixes [#5523](https://github.com/agentscope-ai/CoPaw/issues/5523)).
- **Per-Cron Model Override** — [#5652](https://github.com/agentscope-ai/CoPaw/pull/5652) honors `request.model` in cron job executor, responding to user demand for per-job model configuration.
- **Windows Native Sandbox** — [#5525](https://github.com/agentscope-ai/CoPaw/pull/5525) (open, first-time contributor) adds a native Windows sandbox implementation.
- **Desktop GUI Automation** — [#5187](https://github.com/agentscope-ai/CoPaw/pull/5187) (open) implements Windows desktop GUI automation with UIA and Tauri control mode.

---

## Community Hot Topics

| Issue/PR | Title | Comments | Type |
|----------|-------|----------|------|
| [#5401](https://github.com/agentscope-ai/CoPaw/issues/5401) | Console: session with large tool-use history fails to render | 6 | Bug (Closed) |
| [#5403](https://github.com/agentscope-ai/CoPaw/issues/5403) | Browser autofill hijacks search input in Model Configuration | 5 | Bug (Open) |
| [#5588](https://github.com/agentscope-ai/CoPaw/issues/5588) | 记忆搜索支持专用 Reranker 模型实现两阶段检索 | 4 | Enhancement (Open) |
| [#5561](https://github.com/agentscope-ai/CoPaw/issues/5561) | Agent 链接飞书机器人后长信息无法接收 | 4 | Bug (Open) |
| [#5550](https://github.com/agentscope-ai/CoPaw/issues/5550) | Remote SSH plugin dependency loop + leftover processes | 4 | Bug (Closed) |

**Analysis:** The community is demanding three things: (1) **higher performance retrieval** (two-stage search with rerankers), (2) **better long-content handling** across channels and the chat UI, and (3) **improved plugin stability** particularly for Remote SSH. The DingTalk @mention PR [#5590](https://github.com/agentscope-ai/CoPaw/pull/5590) was highly anticipated, closing the enhancement issue [#5564](https://github.com/agentscope-ai/CoPaw/issues/5564) with 3 comments. The v2.0.0 tracking issue [#5273](https://github.com/agentscope-ai/CoPaw/issues/5273) remains the central coordination point with 2 comments and a 👍.

---

## Bugs & Stability

**High Severity:**
- **[#5624](https://github.com/agentscope-ai/CoPaw/issues/5624) (Closed)** — Tool call result card counter always displays `1` for `glob_search`, `read_file`, etc. **Root cause:** frontend card title not reflecting actual result count. **Status:** Fixed.
- **[#5573](https://github.com/agentscope-ai/CoPaw/issues/5573) (Closed)** — DeepSeek V4 thinking mode produces two types of 400 errors on OpenAI-compatible endpoints: missing `reasoning_content` fallback in streaming and unsanitized `null` type in tool schemas. **Status:** Fix confirmed, merged.
- **[#5660](https://github.com/agentscope-ai/CoPaw/pull/5660) (Open)** — Runtime 2.0 migration broke `spawn_subagent` in four ways (missing runtime tool descriptor, duplicate session creation, config key mismatch, subagent runtime owner). **Status:** Fix PR submitted and under review.

**Medium Severity:**
- **[#5561](https://github.com/agentscope-ai/CoPaw/issues/5561) (Open)** — Feishu (飞书) bot cannot receive replies longer than a threshold; messages are sent as files instead. **Status:** Reported, no fix yet.
- **[#5658](https://github.com/agentscope-ai/CoPaw/issues/5658) (Open)** — Cannot connect to 9router-forwarded model requests (400 error on `contrast` field). **Status:** Reported, awaiting triage.
- **[#5616](https://github.com/agentscope-ai/CoPaw/issues/5616) (Open)** — Automation tasks terminating spontaneously without manual intervention. **Status:** Reported, no root cause identified.

**Low Severity:**
- **[#5403](https://github.com/agentscope-ai/CoPaw/issues/5403) (Open)** — Browser autofill hijacks search input on Model Configuration page (UX annoyance, no data leak).
- **[#5554](https://github.com/agentscope-ai/CoPaw/issues/5554) (Closed)** — WeCom (企业微信) bot file messages interrupted by channel restart. **Status:** Fixed.

---

## Feature Requests & Roadmap Signals

**Most Likely for Next Release:**
- **Memory Two-Stage Retrieval** ([#5588](https://github.com/agentscope-ai/CoPaw/issues/5588)) — Community strongly desires dedicated reranker models (qwen3-rerank) atop embedding-only retrieval. PR [#5669](https://github.com/agentscope-ai/CoPaw/pull/5669) by a first-time contributor already implements this with a `rerank_enabled` toggle.
- **Unlimited Chat Input** ([#5670](https://github.com/agentscope-ai/CoPaw/issues/5670)) — Users want to remove the 10k character limit to leverage 256K–1M context windows. Minimal frontend change.
- **Attachment-Only Sends** ([#5663](https://github.com/agentscope-ai/CoPaw/issues/5663), closed as question) — Users want to send images/files without text and bypass debounce. PR [#5659](https://github.com/agentscope-ai/CoPaw/pull/5659) implements this.
- **Custom Telegram BaseURL** ([#5630](https://github.com/agentscope-ai/CoPaw/issues/5630)) — Request to support self-hosted Telegram bot API proxies.

**Longer-Term Signals:**
- **Loop Detection Mechanism** ([#5657](https://github.com/agentscope-ai/CoPaw/issues/5657)) — Agentic workflows stuck in loops with Qwen3.6 models. PR [#5665](https://github.com/agentscope-ai/CoPaw/pull/5665) introduces a gate architecture that may address this.
- **Linux AppImage Build** ([#5668](https://github.com/agentscope-ai/CoPaw/issues/5668)) — Desktop app missing native Linux release despite Tauri support.
- **Workspace File Browser** ([#5667](https://github.com/agentscope-ai/CoPaw/issues/5667)) — Users want to browse agent-generated files without leaving chat.
- **DingTalk Streaming Speed** ([#5603](https://github.com/agentscope-ai/CoPaw/issues/5603)) — Character-by-character output in DingTalk card streaming is too slow vs. Console.

---

## User Feedback Summary

**Positive signals:**
- The team is responsive to community needs, as evidenced by rapid PRs for DingTalk @mentions, per-cron model overrides, and attachment-only sends.
- First-time contributors are actively welcomed: three `first-time-contributor` PRs merged or submitted today (memory rerank, Windows sandbox, attachment-only sends).

**Pain points:**
- **Channel integration frustrations:** Feishu (长消息), WeCom (文件处理中断), DingTalk (卡片流速度), Telegram (无自定义 BaseURL) — channel reliability remains uneven.
- **Retrieval quality degrades with scale:** Users accumulating memory over time see recall drop; two-stage retrieval is a pressing need.
- **Debounce/input limits feel arbitrary:** Users report that workarounds (saving text to files) reduce convenience.
- **Plugin lifecycle issues:** Remote SSH dependency loop and naming conflicts cause installation failures.

**Satisfaction:** The 2.0.0 pre-release tracker (#5273) has only 1 👍 but no panic reports, suggesting the alpha is stable enough for community testing.

---

## Backlog Watch

| Issue/PR | Age | Last Update | Status | Concern |
|----------|-----|-------------|--------|---------|
| [#5273](https://github.com/agentscope-ai/CoPaw/issues/5273) | 13 days | 2026-06-30 | Open | v2.0.0 bug tracker — has 2 comments but no maintainer summary update since creation. Community may be waiting for a consolidated status report. |
| [#5151](https://github.com/agentscope-ai/CoPaw/pull/5151) | 18 days | 2026-06-30 | Open | GitPanel tab styles broken due to CSS prefix conflict (`ant-` vs `qwenpaw-`). Open for 18 days, may need maintainer review. |
| [#5097](https://github.com/agentscope-ai/CoPaw/pull/5097) | 19 days | 2026-06-30 | Open | Shield icon not vertically centered in Security settings — minor but unmerged for 19 days. |
| [#5187](https://github.com/agentscope-ai/CoPaw/pull/5187) | 16 days | 2026-06-30 | Open | Windows desktop GUI automation — significant feature addition, 16 days open, no maintainer review comments visible. |
| [#5566](https://github.com/agentscope-ai/CoPaw/issues/5566) | 4 days | 2026-06-30 | Open | Cron silent execution + DingTalk delivery failures — has PR [#5654](https://github.com/agentscope-ai/CoPaw/pull/5654) under review. Watch for merge conflicts with #5590. |
| [#5616](https://github.com/agentscope-ai/CoPaw/issues/5616) | 1 day | 2026-06-30 | Open | Automation tasks terminating spontaneously — reported but no logs or reproduction steps provided. Needs maintainer guidance. |

**CRITICAL WATCH:** Issue [#5658](https://github.com/agentscope-ai/CoPaw/issues/5658) (9router proxy 400 error) has been ongoing across versions, suggesting a deeper issue with request schema validation in the OpenAI-compatible adapter. The user reports the bug has persisted "from early versions," indicating a possible regression or long-standing schema mismatch that the team has not fully addressed.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-01

## 1. Today's Overview

ZeroClaw is in a period of intense architectural consolidation, with **45 open issues** and **46 open PRs** actively moving. Today's activity shows **50 issues** and **50 PRs** touched in the last 24 hours, driven by two major thrusts: (1) several large RFCs progressing toward implementation decisions on plugin systems, provider models, and workspace security, and (2) execution-focused tracker issues for the **v0.8.3 release** (runtime, provider serialization, and tool execution). The project has **no new releases** today, but the PR queue indicates significant concrete work landing soon, particularly around the new `onboard` crate, AMQP SOP dispatch, and the removal of the deprecated desktop Tauri app. A notable trend is the high volume of **RFC-type issues** (10+) that are now moving from "open question" to "accepted and in rollout" status, signaling that governance decisions are converging.

## 2. Releases

**No new releases.** The last mention of a release candidate is within RFC #6808, which tracks features starting from `0.8.0-beta-1` and current at `0.8.1`. The v0.8.3 release is in active preparation, tracked by two umbrella issues: [#8360 (provider/native-tool serialization)](https://github.com/zeroclaw-labs/zeroclaw/issues/8360) and [#8071 (runtime/agent-loop execution)](https://github.com/zeroclaw-labs/zeroclaw/issues/8071).

## 3. Project Progress

**Merged/closed today:** 5 issues closed, 4 PRs merged/closed.

Key advances visible in today's PR activity:
- **Desktop app removal:** PR [#8544](https://github.com/zeroclaw-labs/zeroclaw/pull/8544) (open) proposes removing the entire `zeroclaw-desktop` Tauri crate, signaling a strategic shift away from native desktop toward web/WASM-based UI.
- **Onboarding rework:** PR [#8033](https://github.com/zeroclaw-labs/zeroclaw/pull/8033) (open, XL-sized) wires the new `zeroclaw-onboard` crate end-to-end, implementing a walkable state tree for both LLM-driven and deterministic onboarding paths over RPC and CLI.
- **Plugin system foundations:** PR [#8551](https://github.com/zeroclaw-labs/zeroclaw/pull/8551) adds channel host bindings (wasi:http, inbound queue, config jail) and registration API for WASM plugins, a direct implementation step following RFC #6943.
- **CI hardening:** PRs [#8516](https://github.com/zeroclaw-labs/zeroclaw/pull/8516) and [#8517](https://github.com/zeroclaw-labs/zeroclaw/pull/8517) add submodule integrity checks and Windows-specific Clippy gating to the quality gate.
- **Telegram fix:** Issue [#8505](https://github.com/zeroclaw-labs/zeroclaw/issues/8505) (bug, Telegram channel configuration blocked) was opened with S1 severity; no fix PR yet.

## 4. Community Hot Topics

Most active discussions today:

1. **[RFC #6808 — Work Lanes, Board Automation, and Label Cleanup](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)** (13 comments) — The most-commented issue, a governance RFC that has been in rollout since `0.8.0-beta-1`. Now at revision 6, it proposes making work routing automatable without manual maintainer overhead. The high engagement suggests the community is invested in how the project organizes itself.

2. **[Bug #8193 — MCP tools missing from TUI sessions](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)** (6 comments, S1 severity) — Gateway sees MCP tools, but Zerocode TUI sessions do not receive them. This workflow-blocking bug has two user reports, indicating a real deployment hiccup for MCP users.

3. **[Bug #5542 — Consecutive OOM in WSL2](https://github.com/zeroclaw-labs/zeroclaw/issues/5542)** (6 comments, S0 severity) — A long-standing memory issue (filed April 2026) that killed processes with 8.4GB RSS. Despite being marked `status:accepted` and `status:no-stale`, it has no fix PR, which may concern users on memory-constrained environments.

4. **[Feature #8226 — Per-agent custom environment variables](https://github.com/zeroclaw-labs/zeroclaw/issues/8226)** (4 comments) — Proposes `runtime_context` and `runtime_secrets` blocks for multi-tenancy across process lanes and shared MCP instances. The need to handle token/parameter isolation across agents is a sign of production-grade deployment patterns emerging.

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **S0** (data loss/security risk) | [#5542](https://github.com/zeroclaw-labs/zeroclaw/issues/5542) | Consecutive OOM in WSL2 | None open |
| **S0** | [#8094](https://github.com/zeroclaw-labs/zeroclaw/issues/8094) | Anthropic provider added via Quickstart unavailable until reset | None open |
| **S1** (workflow blocked) | [#8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193) | MCP tools missing from TUI sessions | None open |
| **S1** | [#7804](https://github.com/zeroclaw-labs/zeroclaw/issues/7804) (closed) | Non-alternating Anthropic messages causing provider 400 | Closed (fix shipped) |
| **S1** | [#8505](https://github.com/zeroclaw-labs/zeroclaw/issues/8505) | Telegram channel cannot be configured | None open |
| **S2** (degraded) | [#8386](https://github.com/zeroclaw-labs/zeroclaw/issues/8386) | SQLite default memory backend silently degrades to keyword-only search (needs embedding model) | None open |
| **S2** | [#5269](https://github.com/zeroclaw-labs/zeroclaw/issues/5269) | Installation docs missing `cargo binstall` method | None open |

**Key stability observations:**
- The S0 OOM bug (#5542) has been open since April 2026 without a fix, despite being marked as `no-stale`. This is a growing risk for WSL2 users.
- The Telegram configuration bug (#8505) was just opened (2 days ago) and is already S1 — a sign of immediate user impact.
- The Anthropic message ordering bug (#7804) was closed, meaning the provider gap was addressed.
- The SQLite/embedding silent degradation (#8386) is a user experience risk: new users following quickstart will not get vector search, but won't know it.

## 6. Feature Requests & Roadmap Signals

**Likely for v0.8.3 (based on tracker issues):**
- **Per-agent environment variables** (Issue [#8226](https://github.com/zeroclaw-labs/zeroclaw/issues/8226)) — addresses a clear multi-tenancy need and has an RFC with `risk:high` and `needs-author-action`, suggesting design is close to final.
- **`await_sessions` for delegate tool** (Issue [#7882](https://github.com/zeroclaw-labs/zeroclaw/issues/7882)) — a concrete tool improvement that could merge quickly given it has `status:in-progress`.
- **Per-cron-job `uses_memory` flag** (Issue [#8397](https://github.com/zeroclaw-labs/zeroclaw/issues/8397)) — small, well-scoped feature with `status:accepted`.

**Longer-term architecture signals:**
- **RFC #8462 — Runtime Policy for OTel LLM and Tool Content** — This split from the structured-observability umbrella RFC addresses a critical data governance question: when observability-otel is enabled, should every LLM call's input/output be captured as OTel spans? This is a privacy-sensitive design decision.
- **RFC #8396 — Wire-Protocol-First Provider Model** — Proposes making `wire_api` the primary organizing axis for providers, which would be a significant refactor of the provider abstraction layer.
- **FR #8251 — Surface relationship memory as workflows** — Building on knowledge graph tools restored in #8182, this would make relationship memory usable by operators, not just programmatically accessible.

**Deprecation signals:**
- PR #8544 removes the Tauri desktop app entirely, suggesting web and CLI are the focus.
- RFC #8043 proposes folding the standalone `aardvark-sys` crate into `zeroclaw-hardware`, a tidying up of the crate graph.

## 7. User Feedback Summary

**Pain points expressed:**
- **MCP tool visibility gap** (Issue #8193): Two users reported that MCP servers connect and expose tools, but the TUI doesn't show them. This is a core user-facing integration point — MCP is a key extensibility mechanism.
- **Quickstart provider reuse friction** (PR #8522): Users adding providers via Quickstart struggle to find/select existing providers from a long list. PR #8522 addresses this immediately by putting existing providers at the top.
- **Channel configuration failures** (Issue #8505): A user reports `zeroclaw channels doctor` falsely claims channels are not set up after Quickstart. The Telegram bot does not respond, and the agent only replies in CLI. This is a serious "it just doesn't work" experience.
- **Consecutive OOM** (Issue #5542): Users on WSL2 hit unrecoverable out-of-memory conditions. The lack of a fix after 3 months is a notable gap.
- **Installation difficulty** (Issue #5269): A user specifically asked for `cargo binstall` documentation — a thinko that makes installation harder than needed for Rust users.

**Satisfaction signals:**
- Feature #6642 (capture full prompt/completion on LLM spans) was closed, meaning observability integration is progressing well.
- Feature #7816 (pluggable skill registries) was closed, adding flexibility for users who want community skill sources beyond the GitHub default.

## 8. Backlog Watch

High-priority items needing maintainer attention:

| Issue | Status | Risk | Age | Why concerning |
|-------|--------|------|-----|----------------|
| [#5542](https://github.com/zeroclaw-labs/zeroclaw/issues/5542) — Consecutive OOM in WSL2 | `accepted`, `no-stale`, `r:needs-repro` | High | 3 months (Apr 9) | S0 severity, no fix PR, community may be losing trust |
| [#3767](https://github.com/zeroclaw-labs/zeroclaw/issues/3767) — Cross-channel TOTP gate | `accepted`, `no-stale` | High | 3.5 months (Mar 17) | P1 security feature, `no-stale` but no implementation activity |
| [#7952](https://github.com/zeroclaw-labs/zeroclaw/issues/7952) — Publish full-channel prebuilt assets | `blocked`, `needs-maintainer-review` | High | 11 days (Jun 19) | Blocked waiting for maintainer decision; affects release process |
| [#8056](https://github.com/zeroclaw-labs/zeroclaw/issues/8056) — CI required PR gate (cargo audit, lockfile) | `blocked`, `needs-maintainer-review` | High | 10 days (Jun 20) | Security CI improvements held by review bottleneck |
| [#8057](https://github.com/zeroclaw-labs/zeroclaw/issues/8057) — CI scheduled security jobs (CodeQL, Trivy) | `blocked`, `needs-maintainer-review` | High | 10 days (Jun 20) | Same bottleneck, different CI track |
| [#8094](https://github.com/zeroclaw-labs/zeroclaw/issues/8094) — Anthropic provider unavailable until reset | `blocked`, `needs-author-action` | Medium | 9 days (Jun 21) | S0 data loss / security risk, but waiting on author response |
| [#8386](https://github.com/zeroclaw-labs/zeroclaw/issues/8386) — SQLite default silently degrades search | `in-progress`, `accepted` | High | 3 days (Jun 27) | New user experience risk; actively being worked |
| [#8505](https://github.com/zeroclaw-labs/zeroclaw/issues/8505) — Telegram channel cannot be configured | `accepted`, `quickstart` | High | 1 day (Jun 29) | Brand new S1 bug, no fix yet |

**Overall project health:** ZeroClaw is in a healthy but intense phase of architectural consolidation — many RFCs are resolving into concrete PRs (onboarding, plugins, CI), and the community is actively shaping the roadmap. The main risk is **backlog debt**: two S0-severity bugs have gone unfixed for months, and several security-critical CI improvements are blocked on maintainer review. The project's reliance on RFC-driven governance is producing well-considered designs, but may be slowing closure on high-severity operational issues.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/ys578/agents-radar).*