# OpenClaw Ecosystem Digest 2026-07-01

> Issues: 33 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-30 16:24 UTC

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

## 1. Today’s Overview
The project is alive with high development throughput: 45 pull requests were merged or closed in the last 24 hours, and version **v2026.6.11** shipped. The issue tracker remains active with 33 updated items, 25 of them still open, including several **P1** regressions and session-critical bugs. While the high merge volume shows strong community contribution and maintainer engagement, the backlog of open issues and long-lived PRs suggests that some high-severity items are waiting for deeper review or live reproduction. Overall, the project is in a fast-paced but somewhat reactive phase, with robust feature delivery offset by recurring stability regressions in provider and channel pathways.

## 2. Releases
**v2026.6.11** — *openclaw 2026.6.11*  
Highlights (partial, as provided):
- **More capable channel control:** Slack relay mode, native Mattermost `/oc_queue`, and per-DM model overrides make channel operations easier to automate and tune. (#94707, #95546, #95120)  
  Thanks @sjf-oa, @amknight, @xydigit-zt, @thomaszta, and @gandalf-at-lerian.
- **Richer operat…** *(summary truncated in source data)*

No breaking changes or migration notes were specified in the available excerpt.

## 3. Project Progress
**45 PRs merged/closed** in the last 24 hours, while the data window did not list them individually. A number of closed issues indicate delivered fixes and completed features:

- **Closed bugs:**  
  - iOS Talk ignoring Gateway TTS and using Realtime Voice — [#98154](https://github.com/openclaw/openclaw/issues/98154)  
  - Fallback model reply not delivered to channel (Feishu) — [#98194](https://github.com/openclaw/openclaw/issues/98194)  
  - macOS launchd Gateway stderr discarded — [#98199](https://github.com/openclaw/openclaw/issues/98199)  
  - Molty hosted workspace stuck on provisioning — [#98179](https://github.com/openclaw/openclaw/issues/98179)  
  - `openclaw security audit --deep` hanging — [#83075](https://github.com/openclaw/openclaw/issues/83075)  

- **Closed feature/requests:**  
  - AI/ML API provider partnership & ClawHub distribution — [#98192](https://github.com/openclaw/openclaw/issues/98192) *(now closed, possibly accepted for partnership pathway)*  
  - User-defined entity dictionary for PII masking — [#98157](https://github.com/openclaw/openclaw/issues/98157)  

- **Security fix:**  
  - State directory permissions relaxed by update-check writes — [#89589](https://github.com/openclaw/openclaw/issues/89589)  

## 4. Community Hot Topics
*Note: PR comment counts are missing in the dataset; only issue engagement is ranked.*  
The most discussed issues, by comment count and reactions, reflect deep user anxiety around **session integrity, message delivery, and provider reliability**:

1. **[#48003](https://github.com/openclaw/openclaw/issues/48003)** — *Steer mode does not inject messages mid-turn* (14 comments, 3 👍)  
   Users expect `messages.queue.mode: "steer"` to inject chat messages into the active agent turn, but messages are queued until turn end. The root cause is traced to a specific commit from March 2026; no fix PR has been opened yet.

2. **[#38327](https://github.com/openclaw/openclaw/issues/38327)** — *“Cannot convert undefined or null to object” crash with google-vertex/gemini-3.1* (9 comments, 3 👍)  
   A regression in 2026.3.2 crashes the embedded agent. Proven live-repro exists. Tagged `needs-maintainer-review` and `needs-product-decision`.

3. **[#94228](https://github.com/openclaw/openclaw/issues/94228)** — *Native Anthropic thinking block signatures corrupt long tool-use threads* (8 comments, 1 👍)  
   Long-lived sessions break permanently after a 400 error on thinking block signatures. No fix PR yet; requires maintainer attention.

4. **[#71058](https://github.com/openclaw/openclaw/issues/71058)** — *Support for multiple Azure/Teams bots on a single Gateway* (7 comments, 1 👍)  
   A feature request with active engagement, reflecting enterprise “multi-tenant” bot needs.

Underlying themes: **steering reliability, provider-specific regressions, and enterprise gateway scaling** dominate community conversations.

## 5. Bugs & Stability
Multiple **P1 (critical)** reports were active in the last 24 hours, many with fix PRs already linked:

- **Session & message loss regressions:**  
  - [#48003](https://github.com/openclaw/openclaw/issues/48003) — steer injection broken (no fix PR)  
  - [#98156](https://github.com/openclaw/openclaw/issues/98156) — session reset on abort settle timeout causes complete context amnesia (no fix PR yet)  
  - [#98204](https://github.com/openclaw/openclaw/issues/98204) — subagent reply suppressed when nested in wrapper payload (linked PR open)  

- **Provider & transport crashes:**  
  - [#98197](https://github.com/openclaw/openclaw/issues/98197) — `gpt-5.5` on `openai-chatgpt-responses` broken by SSE buffer cap regression (linked PR open)  
  - [#38327](https://github.com/openclaw/openclaw/issues/38327) — google-vertex crash (no fix PR)  
  - [#94228](https://github.com/openclaw/openclaw/issues/94228) — Anthropic thinking block 400 error (linked PR open, needs live-repro)  

- **Auth/secret-handling bugs:**  
  - [#98209](https://github.com/openclaw/openclaw/issues/98209) — iOS Talk treats SecretRef-backed ElevenLabs keys as missing; fix PR [#98210](https://github.com/openclaw/openclaw/pull/98210) open  
  - [#97314](https://github.com/openclaw/openclaw/issues/97314) — Google provider LLM path does not rotate API keys (fix shape clear, no fix PR)  

- **Already fixed:**  
  - Fallback reply not delivered [#98194](https://github.com/openclaw/openclaw/issues/98194) (closed)  
  - iOS Talk TTS default ignored [#98154](https://github.com/openclaw/openclaw/issues/98154) (closed)  

Stability remains the primary quality-of-life concern; steer and session-amnesia bugs directly hurt daily usability, and provider regressions (especially for Anthropic and Vertex) require urgent maintainer triage.

## 6. Feature Requests & Roadmap Signals
Feature requests and enhancement PRs point toward a **more autonomous, enterprise-grade gateway** with improved coordination and observability:

- **Closed/accepted:**  
  - AI/ML API provider partnership [#98192](https://github.com/openclaw/openclaw/issues/98192) — now closed, signalling official integration may be in progress.  
  - PII masking capability [#98157](https://github.com/openclaw/openclaw/issues/98157) — closed, possibly implemented or planned.

- **Open requests with traction:**  
  - Multiple Azure/Teams bots on one Gateway [#71058](https://github.com/openclaw/openclaw/issues/71058) — 7 comments, enterprise demand.  
  - Recover in-flight Gateway run on CLI disconnect [#98200](https://github.com/openclaw/openclaw/issues/98200) — aims for smoother reconnect.  
  - Silent-reply sentinel leakage when wrapped in punctuation [#98166](https://github.com/openclaw/openclaw/issues/98166).

- **PRs that may preview next features:**  
  - Agent coordination kernel [#97508](https://github.com/openclaw/openclaw/pull/97508) — durable multi-agent orchestration, large scope.  
  - Iteration budget for agent loop safety [#97485](https://github.com/openclaw/openclaw/pull/97485) — direct guard against tool-call loops.  
  - Hugging Face text-to-image [#72129](https://github.com/openclaw/openclaw/pull/72129) — new modality.  
  - Google Chat session threading [#68967](https://github.com/openclaw/openclaw/pull/68967) — better channel behaviour.

Given the release tempo, it is plausible that several agent-loop safety and gateway robustness PRs (like [#97485](https://github.com/openclaw/openclaw/pull/97485) and [#97508](https://github.com/openclaw/openclaw/pull/97508)) could land in the next version, alongside critical bugfixes.

## 7. User Feedback Summary
Real-world pain points from the past 24 hours:

- **Steer mode and message delivery fail to meet expectations** — users cannot seamlessly inject instructions mid-turn; some fallback replies never reach channels.  
- **Provider regressions cause crashes and silent failures** — Google Vertex and Anthropic native paths are brittle after updates, breaking long-running sessions.  
- **iOS Talk integration is fragile** — TTS provider selection and SecretRef resolution are inconsistent across Gateway and client.  
- **Enterprise users demand multi-bot support** — single Azure/Teams bot per Gateway is insufficient for many organizations.  
- **Leaked internal error banners degrade trust** — Feishu users see `… (agent) failed` or false failure text after successful runs.  
- **Positive sentiment:** The new channel controls (Slack relay, Mattermost queue, per-DM model overrides) are well received, with explicit thanks in the release notes.

Overall, users value the expanding channel ecosystem but are increasingly vocal about core reliability and message-path integrity.

## 8. Backlog Watch
Important items aging without resolution, needing maintainer attention:

- **[#48003](https://github.com/openclaw/openclaw/issues/48003)** (P1, reported 2026-03-16, 14 comments) — Steer injection broken; no fix PR open after >3 months.  
- **[#38327](https://github.com/openclaw/openclaw/issues/38327)** (P1, reported 2026-03-06, 9 comments) — google-vertex crash regression; needs maintainer review.  
- **[#58775](https://github.com/openclaw/openclaw/issues/58775)** (P2, reported 2026-04-01) — google-vertex provider merged into wrong transport path.  
- **[#71058](https://github.com/openclaw/openclaw/issues/71058)** (P2, enhancement, reported 2026-04-24) — multi-Teams bot request with substantial discussion but no implementation yet.  
- **PRs awaiting maintainer review for weeks:**  
  - [#89040](https://github.com/openclaw/openclaw/pull/89040) (P1, event-loop stall fix) — “ready for maintainer look” since June 1.  
  - [#95787](https://github.com/openclaw/openclaw/pull/95787) (P2, billing guard probes) — ready but awaiting merge.  
  - [#97845](https://github.com/openclaw/openclaw/pull/97845) (P1, tool-call XML leak fix) — ready since June 29.

The concentration of P1 bugs and ready-to-merge PRs dating back weeks suggests that maintainer review bandwidth may be the primary bottleneck.

---

## Cross-Ecosystem Comparison

# Cross‑Project Comparison Report — Personal AI Agent Ecosystem  
**Date:** 2026‑07‑01  
**Coverage:** OpenClaw, NanoBot, Hermes Agent, PicoClaw, NanoClaw, NullClaw, IronClaw, LobsterAI, CoPaw (QwenPaw), ZeroClaw (+ inactive: TinyClaw, ZeptoClaw, Moltis)

---

## 1. Ecosystem Overview  
The personal AI agent / assistant open‑source landscape is accelerating rapidly, with multiple projects sustaining daily PR counts above 40–50 and releasing features at a weekly cadence. Robust multi‑provider LLM integration, channel abstraction for messaging platforms, and agentic safety (tool‑call correctness, session persistence) are the critical frontiers. While some projects are pushing toward enterprise‑grade orchestration and plugin ecosystems, others focus on lightweight self‑hosted solutions. Community feedback consistently highlights message‑delivery reliability and security hardening as make‑or‑break factors for production adoption.

---

## 2. Activity Comparison  

| Project                   | Issues Updated (24h) | PRs Updated (24h) / Merged‑Closed | Release Status             | Health Score (Activity‑Maturity) |
|---------------------------|----------------------|-----------------------------------|----------------------------|----------------------------------|
| **OpenClaw**              | 33 (25 open)         | 45 / 45                           | **v2026.6.11** (stable)    | ⬆️ High‑velocity, reactive        |
| **NanoBot**               | 14 (8 closed)        | 67 / 35                           | No release today            | ⬆️ Very high closure rate        |
| **Hermes Agent**          | 13 (all open?)       | 50 / 3                            | No release                  | ⬆️ Active, platform bug‑fixing   |
| **PicoClaw**              | 7 (2 closed)         | 7 / 2                             | Nightly `v0.3.1‑nightly`    | ⮕ Steady, security‑focused       |
| **NanoClaw**              | 3 (1 closed)         | 9 / 1                             | No release                  | ⮕ Moderate, adapter work         |
| **NullClaw**              | 1                    | 4 / 4                            | No release                  | ⬇️ Low community, cron‑centric   |
| **IronClaw**              | 7 (all open)         | 50 / 23                           | No release                  | ⬆️ High‑velocity, QA‑driven      |
| **LobsterAI**             | ~4 (many stale)      | 14 / 14                           | **v2026.6.30** (stable)     | ⮕ Throughput high, discussion low |
| **CoPaw (QwenPaw)**       | 16                   | 50 / 22                           | No release (v2.0‑dev)       | ⬆️ Hyper‑active, community‑rich  |
| **ZeroClaw**              | 6 (2 closed)         | 50 / 4                            | No release                  | ⬆️ Design‑heavy, RFC‑driven      |
| **Moltis**                | 0                    | 3 (deps only)                     | No release                  | ⬇️ Maintenance‑only               |
| **TinyClaw / ZeptoClaw**  | 0                    | 0                                 | No release                  | ⛔ No activity                    |

---

## 3. OpenClaw’s Position  

**Advantages over peers**  
- **Proven release cadence**: Ships reproducible, named stable releases (v2026.6.11) while most competitors remain on nightly or pre‑release branches.  
- **Broadest channel ecosystem**: Native Slack relay, Mattermost queue, Feishu, per‑DM model overrides – unmatched in depth and enterprise readiness.  
- **Highest merged‑PR volume (45/day)**: Indicates a large active contributor base and maintainer throughput, although review capacity is strained.

**Areas where it lags**  
- **Core stability regressions** – steer injection broken since March, provider crashes (Vertex/Anthropic) remain open; reliability is the top community pain point.  
- **Backlog of high‑priority bugs and ready‑to‑merge PRs** suggests maintainer bandwidth is the bottleneck.  
- **Desktop / multi‑window UX** not a focus; projects like Hermes Agent and CoPaw are investing heavily in desktop clients.  
- **Plugin / extensibility model** less advanced than ZeroClaw’s Wasmtime host or NanoBot’s lightweight tool architecture.

**Community size**  
Larger than most peers, with high engagement on session integrity (#48003, 14 comments) and enterprise needs (multi‑Azure/Teams). The community is vocal and technically adept, but expect fixes, not just features.

---

## 4. Shared Technical Focus Areas  

### Provider reliability & multi‑model compatibility  
- **OpenClaw**: Anthropic thinking block corruption, Google Vertex crash, OpenAI SSE buffer regressions.  
- **NanoBot**: Tool‑call ID corruption, provider token persistence fixes.  
- **Hermes Agent**: Bedrock null image_url, DeepSeek thinking mode 400 errors.  
- **PicoClaw**: Volcengine raw XML leakage, OpenAI failures on NanoKVM.  
- **CoPaw**: DeepSeek V4 reasoning_content missing, 9router connection failures.  
- **NullClaw**: GLM/ZhipuAI thinking loops.  

### Message delivery & session integrity  
- **OpenClaw**: Steer injection broken, fallback reply not delivered, session amnesia on abort.  
- **NanoBot**: Heartbeat mis‑delivery, session consolidation loss (PR #4373).  
- **Hermes Agent**: Telegram duplicate messages, Feishu threading broken.  
- **IronClaw**: Global delivery target bug, routine creation failure.  
- **LobsterAI**: Scheduled task history empty, cron session reuse needed.  

### Security hardening  
- **PicoClaw**: ISATAP IPv6 SSRF fix, auth error surfacing.  
- **NanoClaw**: Symlink‑escape vulnerability patched.  
- **ZeroClaw**: Zip‑bomb protection requested, env‑secret blocking for HTTP tools.  
- **NanoBot**: DNS rebinding TOCTOU reported.  

### Agent orchestration & safety  
- **OpenClaw**: Agent coordination kernel PR (#97508), iteration budget (#97485).  
- **NanoBot**: Agent reliability layer (#4534), structured tool errors (#4610).  
- **CoPaw**: Loop detection mechanism with composable gates (#5657).  
- **IronClaw**: Subagent spawning, compaction budget overrides.  

### Channel & platform expansion  
- **Multiple projects**: New adapters for Matrix, SimpleX/Tox, WhatsApp, WeChat, Zulip, TrueConf, DeltaChat, Telegram threads.  
- **Demand for API‑driven integrations** (OpenClaw multi‑Teams, CoPaw OpenAI‑compat endpoint, NanoBot external triggers).  

---

## 5. Differentiation Analysis  

| Dimension          | OpenClaw                        | NanoBot                        | Hermes Agent                 | PicoClaw                 | CoPaw (QwenPaw)            | ZeroClaw                      |
|---------------------|----------------------------------|--------------------------------|------------------------------|--------------------------|----------------------------|-------------------------------|
| **Primary target**  | Power users, enterprise gateways | Self‑hosted, lightweight       | Desktop‑first, multi‑platform | Embedded/IoT, privacy   | Qwen‑ecosystem, collaboration | Plugin‑extensible runtime      |
| **Architecture**    | Monorepo, provider/channel abstractions | Lightweight core, modular tools | Tauri+Electron, gateway adapters | Python, C, security‑hardened | Rust‑based, skill‑sync | Rust, Wasmtime component model |
| **Key differentiator** | Release stability, broadest channel support | Rapid bug closure, OAuth flows | Desktop multi‑window, Feishu/DingTalk depth | Privacy‑first gateways (SimpleX/Tox) | Agent auto‑skill sync, loop detection | Pluggable skill registries, onboard tree |
| **Community model** | Large external contributors, enterprise feedback | Enthusiast, rapid‑fix culture  | Heavy platform integration, Duplicate‑fix PRs | Niche, privacy‑conscious   | Alibaba‑backed, active first‑timers | RFC‑driven design, strategic |

**Complementary strengths**: Hermes and CoPaw dominate the desktop experience; NanoBot leads in quick‑fix velocity; ZeroClaw pushes the plugin envelope; OpenClaw remains the reference for production gateway deployments.

---

## 6. Community Momentum & Maturity  

### Hyper‑active (50+ PRs/day, vibrant issue discussions)  
- **OpenClaw**, **NanoBot**, **Hermes Agent**, **IronClaw**, **CoPaw**, **ZeroClaw**  

These projects are shipping features daily, attracting new contributors, and responding to bugs within hours. CoPaw and ZeroClaw show strong design‑first cultures (RFCs, v2.0 milestones), while OpenClaw and IronClaw balance feature velocity with production‑hardening needs.

### Steady & focused (10–20 items/day)  
- **PicoClaw** (security‑oriented), **NanoClaw** (adapter completeness), **LobsterAI** (enterprise productivity with NetEase backing).  

### Low volume / dormant  
- **NullClaw** (feature‑complete scheduler, small community), **Moltis** (dependency bumps only), **TinyClaw / ZeptoClaw** (zero activity).  

**Stabilizing signs**: Projects like NanoBot and IronClaw are introducing structured tool errors, reliability layers, and stress‑testing, suggesting a shift from prototype to production. OpenClaw’s large bug backlog indicates it may need a stabilization sprint to maintain its lead.

---

## 7. Trend Signals  

1. **Provider abstraction is the hardest problem** – Nearly every project struggles with API‑specific serialisation (thinking blocks, tool_call IDs, SSE buffering). Developers should invest in provider‑side contract testing and canonical adapters.  
2. **Message delivery observability is now a baseline requirement** – Users expect mid‑turn injection, fallback replies, and heartbeat routing to work flawlessly; projects that lack these lose trust quickly.  
3. **Security sandboxing is moving from nice‑to‑have to mandatory** – SSRF, symlink escapes, zip bombs, and DNS rebinding are triggering rapid fixes and design changes (ZeroClaw Wasmtime, PicoClaw address validation).  
4. **Desktop and multi‑window experiences are the next battleground** – Hermes Agent and CoPaw are dedicating significant resources to this; OpenClaw’s absence here could become a competitive gap.  
5. **Plugin and skill ecosystems are being formalised** – ZeroClaw’s Wasmtime model, CoPaw’s skill auto‑sync, and OpenClaw’s ClawHub distribution signal a future where agents are extensible by third‑party developers.  
6. **Cron and background automation are maturing** – Several projects are rewriting schedulers with DB‑backed histories, per‑job timezones, and subagent engines (NullClaw, IronClaw, LobsterAI).  
7. **Privacy‑first channels (SimpleX, Matrix, Tox) are gaining vocal advocacy** – Although niche, these requests reflect growing user demand for self‑sovereign messaging integration.  

**Guidance for AI agent developers:** Prioritise robust provider‑agnostic abstractions, implement comprehensive delivery‑path tracing, harden all file and network boundaries early, and design for an extensible plugin model from day one. The community is trading “experimental demos” for “production‑ready assistants,” and those who fail to meet these expectations risk being overtaken by the rapidly maturing ecosystem.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-01

## 1. Today’s Overview
NanoBot remains under active development with **14 issues** and **67 pull requests** updated in the last 24 hours, including **8 closed issues** and **35 merged/closed PRs**. The project did not ship a new release today, but the high closure rate—coupled with **32 open PRs**—shows sustained feature delivery and community-driven fixes. Multiple long-standing bugs (tool-call corruption, install‑script crashes, Windows service restarts) were resolved, while a serious security report and a wave of feature requests hint at the next round of improvements.

## 2. Project Progress (merged/closed today)
Key fixes and enhancements that landed:

- **WebUI idle compaction bug** – #4609 fixed a regression where idle session maintenance was incorrectly refreshing `session.updated_at`, which could skew visibility and auto‑compaction scheduling.
- **OAuth login as main provider** – #4573 (merged) added `--set-main` flags to `nanobot provider login`, letting users adopt an OAuth provider as the default during setup.
- **Heartbeat channel delivery** – #4418 (closed) addressed a problem where heartbeat tasks were posting results to the most‑recently‑active channel instead of the channel that created the task; the resolution appears to implement the requested delivery context (likely via PRs like #4437).
- **Windows service restart instability** – #4513 (closed) and the gateway self‑heal PR #4547 together resolve the issue of `nssm`‑managed NanoBot failing or holding stale PIDs after `/restart`.
- **Provider token persistence & config refresh** – #1023 (closed) fixed a Docker‑path bug where OAuth tokens were not saved, and config reloads dropped unknown provider sections.
- **Install script crash** – #4599 was quickly closed; the default Linux TUI installer no longer exits immediately on startup.
- **Tool‑call ID corruption** – #4595 (closed) fixed `StreamingFileEditTracker` overwriting correct `tool_call.id` values, which previously permanently poisoned sessions.
- **GitHub Copilot Enterprise support** – #4220 (closed) extended the OAuth flow to cover GitHub Enterprise Server / Copilot for Business endpoints.
- **Conda virtual‑environment compatibility** – #4580 (closed) signalled a move toward allowing subprocesses to run in named conda environments.

## 3. Community Hot Topics

### 🔥 Active Discussions
- **Anthropic OAuth** [#4604] (2 comments, open) – A feature request originally posted in the discussions area, now escalated to an issue. Users want OAuth login support for Anthropic providers (claude.ai etc.), mirroring the existing Copilot flow. This signals growing multi‑provider usage.
- **Agent external trigger** [#4605] (0 comments, but posted by an enthusiastic early adopter) – The user asks for a way to invoke agent actions from external scripts, e.g., to trigger processing when a Gmail skill notices an important email. Indicates demand for headless/API‑driven workflows.

### 📈 Top Open PRs by Interest/Scope
- **Agent reliability layer** [#4534] (`priority: p1`) – A large effort adding verification feedback, long‑output handling, and budget convergence to prevent tasks from being lost.
- **Structured tool errors** [#4610] – Replaces string‑based error detection with a `ToolResult` contract; refactors all built‑in tools for consistency.
- **Heartbeat model override & session sharing** [#4549], [#4551] – Allow operators to route heartbeat checks to cheaper models and optionally share the target channel’s session.

*(PR comment counts were not available; selections based on priority labels and scope.)*

## 4. Bugs & Stability

### Open / Unresolved
| Severity | Issue / PR | Summary |
|----------|------------|---------|
| 🔴 High | [#4611] (open) | DNS rebinding TOCTOU in SSRF validation: `validate_url_target` resolves DNS but does not pin the IP for the subsequent request, potentially allowing a rebinding attack. No fix PR yet. |
| 🟡 Medium | [#4592] (open) | `ExecTool` path extraction misses absolute paths after `=` when `restrictToWorkspace` is enabled, opening a path traversal bypass. |
| 🟡 Medium | [#4603] (open, refactor) | Tool‑call ID mutation for WebUI progress correlation disrupts provider protocol integrity; a clean separation is being discussed. |

### Recently Fixed
- `apply_final_call_ids` overwriting correct tool‑call IDs (#4595)
- Installer crash (#4599)
- Windows `nssm` service restart (#4513, addressed by #4547)
- OAuth token persistence (#1023)
- Config migration crash when sections are `null` (#4583, open fix PR available)

Stability has clearly improved, with several painful regressions closed within 24 hours.

## 5. Feature Requests & Roadmap Signals

### New Requests (open)
- **Anthropic OAuth** [#4604] – likely to be prioritised given the Copilot OAuth pattern already exists.
- **External agent trigger** [#4605] – points toward a programmable API or webhook.
- **OpenAI Response API support** [#4612] – needed for certain enterprise setups that only expose the Responses endpoint.
- **Refactor tool‑call ID handling** [#4603] – essential for cleaning up the provider protocol before tool‑use becomes more complex.

### Upcoming Features from Open PRs
Several PRs flagged `priority: p2` are poised to merge soon:

- **Per‑session model presets** [#4555] – each conversation can keep its own model selection.
- **Dream duplicate skill guard** [#4554] – prevents Dream from creating duplicate skills.
- **Eager memory consolidation** [#4402] – optional archiving of conversation slices after each response.
- **Subagent A2A peer delegation** [#4571] – native agent‑to‑agent communication with depth guard.
- **WhatsApp activity cues** [#4563] – typing presence and reactions on the Neonize WhatsApp bridge.
- **Cron job model presets** [#4416] – run cron tasks with dedicated model/context‑window overrides.

**Prediction for next release:**
The `v0.9.x` line will likely deliver the reliability enhancements (#4534), structured tool errors (#4610), and a batch of heartbeat/cron quality‑of‑life improvements. If Anthropic OAuth (#4604) gets fast‑tracked, it could appear as a headline feature.

## 6. User Feedback Summary

- **Pain points:** Windows service management remains fragile (although today’s fixes help). Heartbeat mis‑delivery (#4418) caused confusion. The OAuth login flow felt incomplete without a way to set the new provider as default (#4573). Security‑conscious users are alerting the team to SSRF weaknesses.
- **Use cases:** Users are integrating NanoBot with external tools (Gmail, custom scripts), running it as a system service, and expecting it to work inside conda/virtual environments. Multi‑provider setups (Copilot + Anthropic) are growing.
- **Satisfaction:** One user wrote: *“loving it so far … the lightweight codebase makes it easy to read and understand the source”* ([#4605]). The enthusiasm is tempered by the need for more primitive‑level controls (external triggers, proper tool‑error handling).

## 7. Backlog Watch
Items that have been open for more than a week and may need maintainer attention:

- **PR #4373** (opened 2026-06-16) – `fix(memory): preserve delivery context during consolidation`. Labeled `bug, fix`, it prevents consolidation from dropping the delivery metadata needed for correct heartbeat/channel routing. Has not been merged despite being a 2‑week‑old fix with no obvious conflicts.
- **PR #4402** (opened 2026-06-18) – `feat(memory): add opt‑in eager consolidation`. Linked to a long‑standing issue (#2604), it adds a missing memory primitive. Still open after nearly two weeks, possibly awaiting design approval.
- **Issue #4611** (security) – newly opened, but critical; no assignee or response yet. It warrants immediate triage to avoid a CVE‑quality bug lingering.

---

*The project’s pulse is strong: rapid closure of bugs, a steady stream of community feature requests, and a deep pipeline of PRs covering reliability, memory, and cross‑provider support. The immediate priority should be the DNS rebinding security issue and the aging backlog fixes that keep session delivery correct.*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-01

## 1. Today’s Overview
The Hermes Agent repository remains extremely active with 50 pull requests updated and 13 new or active issues in the last 24 hours, yet no new releases were cut. The community is heavily focused on fixing platform‑specific bugs (Feishu, Telegram, DingTalk, Windows) and enhancing the Desktop experience, while the maintainers have merged or closed 3 PRs that were not captured in the top‑20 list. The overall health is strong, though a surge in bug reports suggests the latest builds may have introduced regressions in connected platforms and the memory/skills subsystem.

## 2. Releases
*No new releases published.*

## 3. Project Progress
Three PRs were merged or closed in the past 24 hours, but their details are not available in the provided data (they were not among the top 20 by activity). This likely reflects routine maintenance or small fixes.

Among the open work, notable progress includes:
- A **TUI test suite overhaul** (#55749) repaired 27 failing tests, restoring the CLI/TUI test suite to full health.
- **Feishu markdown tables** are being converted to interactive cards (#55759) to improve message rendering.
- A **gateway wrapper script** (#55748) is being introduced to fix intermittent Slack disconnects on macOS launchd.

Multiple duplicate bug‑fix PRs (e.g., cron zero‑interval #55751, Bedrock null image_url #55752, Windows subprocess breakaway #55753, Bedrock image parts #55754) indicate that maintainers are quickly addressing reported regressions.

## 4. Community Hot Topics
**Most Active Issue: [Feature] Support opening multiple independent desktop windows (#40394)**  
https://github.com/NousResearch/hermes-agent/issues/40394  
- 2 comments, 4 👍 reactions, open since 2026-06-06.  
- Users want to run parallel conversations with the same agent profile in separate Desktop windows, a limitation of the current single‑window `BrowserWindow` model.

**Related Desktop Window Requests**  
- Issue #55764 (open today): Secondary chat windows should support session switching or full‑window mode, reflecting a strong desire for richer multi‑window workflows.

**Underlying need:** The Desktop application is seen as the primary interface, but its window management lags behind professional productivity tools. Users expect the flexibility of a modern chat app (like Slack or Discord) with independent, switchable panes.

Other active discussions include Telemetry opt‑in (#55747, privacy) and prompt caching risks (#55743, cost optimization), illustrating a mature community concerned about privacy and performance.

## 5. Bugs & Stability
Today’s reported bugs are mostly platform‑specific regressions or tool‑level errors:

| Severity | Issue | Description | Fix Available? |
|----------|-------|-------------|----------------|
| **P1** | [#55647](https://github.com/NousResearch/hermes-agent/issues/55647) – `skill_manage` patches hallucinate old content; background review fork writes without reading first | The session background review loop can corrupt skill files by issuing patch edits based on conversation transcript alone, violating the read‑before‑write invariant. | No dedicated fix PR yet. |
| **P2** | [#55750](https://github.com/NousResearch/hermes-agent/issues/55750) – Feishu DM replied messages sent as plain text instead of threaded reply | Quoted replies are posted as separate messages, breaking conversation threading in Feishu. Root cause identified in `gateway/platforms/base.py`. | No direct fix; PR #55759 (Feishu table rendering) is related but not a fix for threading. |
| **P2** | [#55761](https://github.com/NousResearch/hermes-agent/issues/55761) – Telegram sends duplicate identical messages on short text‑only turns | Stream preview and final gateway send both deliver the full message, causing duplicates. | Not yet addressed. |
| **P2?** | [#55760](https://github.com/NousResearch/hermes-agent/issues/55760) – macOS browser‑CDP LaunchAgent uses normal Chrome.app, breaking visible Chrome windows | The helper app opens a headless Chrome that conflicts with the user’s normal Chrome session. | No fix PR. |
| **P3** | [#55755](https://github.com/NousResearch/hermes-agent/issues/55755) – Memory tool returns “Unknown action None” on invalid action strings | Misleading error message when an unrecognised action is sent (e.g., `"list"` instead of valid ones). | No fix PR. |
| **Unlabeled** | [#55762](https://github.com/NousResearch/hermes-agent/issues/55762) – Desktop sidebar empty after worktree creation in project mode with zero sessions | The sidebar fails to refresh when a project has no existing sessions and a worktree is created. | Not yet addressed. |

Multiple **duplicate bug‑fix PRs** (#55751, #55752, #55753, #55754, #55757, #55758) point to a rapid‑response culture but also suggest that similar issues are being opened in multiple places, possibly due to insufficient test coverage or communication.

## 6. Feature Requests & Roadmap Signals
Today’s feature requests and open PRs reveal a clear roadmap direction:

- **Multi‑window Desktop (#40394)** — heavily requested; if merged, would be a flagship Desktop improvement.
- **Vertex AI provider (#55742)** — a PR is open to add Google Vertex AI (AnthropicVertex SDK), enabling enterprise users to run Claude models without an Anthropic API key.
- **Journey CLI/TUI timeline (#55555)** — brings the merged Desktop Memory Graph to the terminal; already implemented as a PR, highly likely to land in the next release.
- **Zulip gateway adapter (#3335)** — open since 2026-03-27, still actively updated; signals continued expansion of chat platform support.
- **Telemetry opt‑in gating (#55747)** — privacy‑conscious users demand explicit consent before any telemetry is collected.
- **Memory provider ABC (#55744)** — architectural refactoring to accommodate multiple memory backends (holographic, plugins) is being designed, indicating plans for a pluggable memory system.

**Prediction for next version:** The Vertex AI provider and the /journey CLI feature are the most likely to be merged soon, given their completed implementation and alignment with recent Desktop work. Multi‑window Desktop may require more design discussion.

## 7. User Feedback Summary
Users are generally positive about the desktop and platform integrations but are hitting concrete pain points:

- **Platform integration**: Feishu users lose conversation context because replies aren’t threaded; Telegram users see duplicate messages, degrading the experience. DingTalk users are experiencing session loss on restarts (fixed in PR #55740).
- **Desktop experience**: The single‑window limitation is a major friction point for power users who multitask. Secondary windows lack session switching, making them less useful.
- **Reliability**: Background self‑improvement (skill patches) can corrupt data, and the memory tool’s obscure errors confuse developers. Cron jobs with `every 0m` caused spamming until a fix was proposed.
- **Privacy**: Strong voices demand opt‑in telemetry, with a clear issue (#55747) highlighting the community’s expectation of no new analytics without explicit consent.

**Satisfaction indicators:** The high number of community‑authored bug‑fix PRs (e.g., Bedrock fixes, Windows breakaway, file counting) shows a capable contributor base that is willing to fix issues themselves.

## 8. Backlog Watch
These long‑standing open items need maintainer attention to avoid bit‑rot:

- **PR #3335 – Zulip integration** (opened 2026-03-27, 3+ months)  
  https://github.com/NousResearch/hermes-agent/pull/3335  
  Adds a full‑fledged Zulip gateway adapter. Has been updated recently, but no merge signal.

- **PR #25186 – TrueConf adapter** (opened 2026-05-13, 1.5 months)  
  https://github.com/NousResearch/hermes-agent/pull/25186  
  Supports private chats and file transfer via TrueConf messenger. Needs review to avoid staleness.

- **Feature Request #40394 – Multi‑window Desktop** (opened 2026-06-06, 3 weeks)  
  https://github.com/NousResearch/hermes-agent/issues/40394  
  Despite significant community interest, no assigned milestone or design proposal exists.

- **PR #41496 – TUI remote image validation** (opened 2026-06-07)  
  https://github.com/NousResearch/hermes-agent/pull/41496  
  Security improvement for image uploads in TUI; awaiting review.

These items represent valuable community contributions and highly‑requested features that, if left unaddressed, could discourage further involvement.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-01

**Project:** PicoClaw (github.com/sipeed/picoclaw)  
**Period:** 2026-06-30 (last 24h snapshot)  

---

## 1. Today’s Overview  
PicoClaw maintained a steady development pace: 7 issues (5 open, 2 closed) and 7 pull requests (5 open, 2 merged/closed) were active. A new **nightly build** for v0.3.1 was released, indicating the main branch is iterating toward the next minor version. The community focus continues to split between polishing provider integrations, addressing platform-specific bugs, and pushing for new communication gateways. The presence of several **stale** but still-open issues suggests that some high-demand requests are awaiting prioritisation, while recent security and UX fixes underline the project’s attention to robustness.

---

## 2. Releases  

**v0.3.1-nightly.20260630.52320f48** (Nightly Build)  
*Release date: 2026-06-30*  
An automated, potentially unstable snapshot of the current `main` branch, ahead of the next stable release (v0.3.1).  
**Full changelog:** [Compare v0.3.1…main](https://github.com/sipeed/picoclaw/compare/v0.3.1...main)  
> ⚠️ **Caution:** This is not a production release. Use at your own risk; expect rough edges and breaking changes.

No new stable release was published.

---

## 3. Project Progress – Merged/Closed PRs  
Two pull requests were merged or closed today, delivering immediate improvements:

| PR | Type | Description | Impact |
|----|------|-------------|--------|
| [#3198](https://github.com/sipeed/picoclaw/pull/3198) | Bug fix / UX | Surface friendly auth error messages across providers | Users now see clear hints when API keys, tokens, or provider permissions fail, reducing “cryptic error” frustration. |
| [#3143](https://github.com/sipeed/picoclaw/pull/3143) | Security fix | Block private IPv4 addresses embedded in ISATAP IPv6 literals during web fetches | Closes SSRF bypass ([#3074](https://github.com/sipeed/picoclaw/issues/3074)); guards against exfiltration of internal resources. |

Both PRs originated from the community (authors lc6464) and represent real-world hardening.

---

## 4. Community Hot Topics  
Active discussions today centred on **privacy-friendly messaging gateways** and a **model‑specific tool‑call leakage**.

- **[#3093 – Feature Request: SimpleX or Tox gateway](https://github.com/sipeed/picoclaw/issues/3093)**  
  *4 comments, 👍 1, stale*  
  Users want PicoClaw to bridge to SimpleX, Wire, or Tox for end‑to‑end encrypted chat. The demand reflects a growing desire for self‑sovereign communication channels beyond existing integrations (Matrix, Telegram, etc.).  
  **Underlying need:** decentralised, censorship‑resistant, and metadata‑reducing gateways for high‑privacy use cases.

- **[#3153 – Bug: Volcengine Doubao Seed tool calls leak raw XML](https://github.com/sipeed/picoclaw/issues/3153)**  
  *2 comments, stale*  
  When using the Doubao model, tool calls occasionally appear as raw `<seed:tool_call>` text instead of being executed. This not only degrades user experience but also risks exposing sensitive tool definitions. The issue has been open for 8 days without a fix.  
  **Underlying need:** reliable tool‑use parsing for non‑OpenAI providers, especially those with proprietary serialisation formats.

Closed issue **[#3090 (Safari on iOS < 16.4)](https://github.com/sipeed/picoclaw/issues/3090)** also attracted 3 comments, signalling that a subset of users still rely on older Apple devices.

No open PR received comments or reactions in this period; the discussion is Issue‑driven.

---

## 5. Bugs & Stability  
Several open bugs affect key integrations and platform support. Ranked by potential impact:

| Severity | Issue | Status | Description | Fix available? |
|----------|-------|--------|-------------|----------------|
| **High** | [#3153](https://github.com/sipeed/picoclaw/issues/3153) | OPEN, stale | Volcengine Doubao tool‑call leak (raw XML exposed to user) | No |
| **High** | [#3195](https://github.com/sipeed/picoclaw/issues/3195) | OPEN | OpenAI GPT fails on NanoKVM 2.4.0 with default configuration | No |
| **Medium** | [#3197](https://github.com/sipeed/picoclaw/issues/3197) & [#3196](https://github.com/sipeed/picoclaw/issues/3196) | OPEN (duplicates) | OAuth login broken for Codex and Antygravity providers (v0.2.9) | No |
| **Closed** | [#3199](https://github.com/sipeed/picoclaw/issues/3199) | CLOSED | Custom model provider could not connect to local `http://127.0.0.1:16001/v1` | Likely invalid / environment‑specific; no fix PR linked. |

The leaked tool calls (#3153) are the most concerning from a security & reliability standpoint, while the NanoKVM/OAuth bugs could block new adoption paths. The recent auth‑error improvements (PR #3198) may indirectly help diagnose the OAuth issues, but the root cause remains unaddressed.

---

## 6. Feature Requests & Roadmap Signals  
Four open feature PRs, plus the community‑requested gateways, point to clear roadmap themes:

- **Messaging gateways** – PR [#3063](https://github.com/sipeed/picoclaw/pull/3063) adds **DeltaChat**; issue [#3093](https://github.com/sipeed/picoclaw/issues/3093) asks for SimpleX/Tox. Strong signal that users want more secure, decentralised chat options.  
- **Remote agent mode** – PR [#3118](https://github.com/sipeed/picoclaw/pull/3118) introduces a WebSocket‑based remote agent, enabling distributed PicoClaw setups. High chance of being merged if architecture review passes.  
- **Provider optimisation** – PR [#3163](https://github.com/sipeed/picoclaw/pull/3163) leverages **Bedrock prompt caching** for cost savings; PR [#3156](https://github.com/sipeed/picoclaw/pull/3156) exposes per‑turn token usage on the Pico channel, which helps with billing and monitoring.  
- **Tool output sanitisation** – PR [#3115](https://github.com/sipeed/picoclaw/pull/3115) fixes session corruption when generic tool output contains data‑URL strings.

**Prediction for next stable release:** DeltaChat gateway (#3063) and the remote agent mode (#3118) are strong candidates. The Bedrock caching (#3163) and token‑usage (#3156) features could follow, depending on maintainer capacity. The SimpleX/Wire/Tox request will likely require a separate PR.

---

## 7. User Feedback Summary  
**Pain points observed in this period:**

- **Broken model interactions** – Leaked tool calls and “AI doesn’t work” on specific platforms (NanoKVM, Volcengine) erode confidence.  
- **Provider lock‑out** – OAuth failures for Codex/Antygravity and local custom endpoint issues frustrate advanced users who want to plug in their own backends.  
- **Platform fragmentation** – iOS Safari incompatibility (closed but discussed) and Raspi‑specific errors hint at a need for wider system‑level testing.  
- **Desire for privacy** – Repeated requests for privacy‑first bridges (SimpleX, Tox, Wire, DeltaChat) show that a vocal segment of the community values self‑hosted, secure communication beyond conventional messengers.  

**Satisfaction signals:**  
- Quick security fixes (SSRF bypass closed in one day) indicate a responsive security posture.  
- UX improvements like clearer auth errors (#3198) are welcomed.  
- The active open PR landscape shows sustained external contribution, a sign of a healthy ecosystem.

---

## 8. Backlog Watch – Items Needing Maintainer Attention  
These Issues and PRs have remained open without visible progress or maintainer response, yet carry significant user weight:

| Item | Age | Why it matters |
|------|-----|----------------|
| [#3093](https://github.com/sipeed/picoclaw/issues/3093) – SimpleX/Tox gateway request | 21 days, stale | 4 comments + 👍; represents a growing user desire; no PR or comment from core team. |
| [#3153](https://github.com/sipeed/picoclaw/issues/3153) – Volcengine tool‑call leak | 8 days, stale | Security‑relevant; 2 comments; no triage label or assignee. |
| [#3063](https://github.com/sipeed/picoclaw/pull/3063) – DeltaChat gateway PR | 23 days | Feature PR from trusted contributor; needs review/merge decision. |
| [#3118](https://github.com/sipeed/picoclaw/pull/3118) – Remote agent WebSocket mode | 18 days | Likely useful for multi‑device setups; awaiting maintainer feedback. |
| [#3197](https://github.com/sipeed/picoclaw/issues/3197) / [#3196](https://github.com/sipeed/picoclaw/issues/3196) – OAuth login failures | 1 day (new, but duplicate) | Real‑time blocker for users of those providers; should be triaged quickly. |

Maintainers are encouraged to label and prioritise #3153 and the OAuth duplicates due to their immediate user impact. The gateway PRs (#3063) and feature requests (#3093) represent a strategic choice about expanding communication channels.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw Project Digest — 2026-07-01**

---

### 1. Today’s Overview
The project had a high-velocity day with 12 items updated (3 issues, 9 PRs). One security fix was merged, and eight feature/improvement PRs remain open. Community attention focused on attachment handling across chat adapters, agent provisioning, and a matrix native adapter. The overall health is active but there is notable technical debt around media reliability and adapter completeness.

---

### 2. Releases
No new releases published today.

---

### 3. Project Progress
- The critical **symlink‑escape security vulnerability** (#2828) has been resolved. PR [#2880](https://github.com/nanocoai/nanoclaw/pull/2880) was merged, closing the issue and adding path containment for all inbound file writes in A2A forwarding.

---

### 4. Community Hot Topics
- **Security advisory #2828** (closed) – 2 👍, no comments. The fix PR was merged today, reflecting high interest in sandbox integrity. Users care about host file‑system isolation when agents exchange attachments.
- **Discord attachment bug #2888** – open, 1 comment. Users are frustrated that images/files sent in Discord are not visible to the agent, breaking workflows that rely on visual context.
- **WhatsApp media drop #2894** and its immediate fix PR [#2895](https://github.com/nanocoai/nanoclaw/pull/2895) (both from contributor `echarrod`) demonstrate rapid response to a data‑loss bug. The community expects robust multi‑platform media handling.

---

### 5. Bugs & Stability
1. **Discord (and probably other URL‑based adapters) silently drops attachment content** [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) – **Severity: high**. The agent receives only metadata; file content is never downloaded. Root cause: `messageToInbound` in `chat-sdk-bridge.ts` does not fetch attachment bytes. No fix PR yet.
2. **WhatsApp adapter drops media on CDN fetch failure** [#2894](https://github.com/nanocoai/nanoclaw/issues/2894) – **Severity: medium**. A `catch` block swallows errors silently. Fix PR [#2895](https://github.com/nanocoai/nanoclaw/pull/2895) supplies `reuploadRequest` recovery and a visible note.
3. **New channel‑registered agent ignores installed provider, causing 401** [#2886](https://github.com/nanocoai/nanoclaw/pull/2886) – **Severity: medium**. On single‑provider installs, `createNewAgentGroup` hard‑codes the default provider. Fix PR [#2886](https://github.com/nanocoai/nanoclaw/pull/2886) (open) corrects the logic.

---

### 6. Feature Requests & Roadmap Signals
Open PRs suggest the following likely additions to upcoming releases:
- **Native Matrix adapter with persistent E2EE** [#2844](https://github.com/nanocoai/nanoclaw/pull/2844) – replaces the WASM‑based bridge, adds Rust‑backed crypto. Strong community demand for self‑hosted, privacy‑preserving channels.
- **Agent templates** [#2890](https://github.com/nanocoai/nanoclaw/pull/2890) – a loader, setup flow, and public library to stamp ready‑to‑run agent groups. Addresses onboarding friction.
- **Host‑mediated document rendering** [#2893](https://github.com/nanocoai/nanoclaw/pull/2893) – an `render_document` MCP tool running in an ephemeral, network‑isolated container. Would offload complex toolchains (Quarto/LaTeX) from the agent sandbox.
- **Channel adapter enhancements** – `resolveChannelName` interface [#2891](https://github.com/nanocoai/nanoclaw/pull/2891), Telegram thread support [#2892](https://github.com/nanocoai/nanoclaw/pull/2892), a WeChat adapter [#2889](https://github.com/nanocoai/nanoclaw/pull/2889). These fill gaps in multi‑platform messaging.
- **Daily‑news‑agent example** [#2889](https://github.com/nanocoai/nanoclaw/pull/2889) – serves as a reference implementation and showcases recurring task scheduling.

---

### 7. User Feedback Summary
- **Pain point – Media handling is unreliable.** Discord attachments are invisible, WhatsApp sometimes drops files, and even the previously fixed symlink issue highlights fragility around file transfer. Users expect transparent attachment forwarding like Telegram’s behaviour.
- **Onboarding frustration** – New agent groups often hit a 401 error because the provider isn’t inherited from the installation ( [#2886](https://github.com/nanocoai/nanoclaw/pull/2886) ). This is a blocker for single‑provider setups.
- **Growing demand for diverse channels** – WeChat, native Matrix, and the template system all point to users wanting easy, secure connections beyond the core adapter set. The community actively contributes those adapters.
- **Security consciousness** – The symlink advisory attracted attention; users and contributors care deeply about container isolation and host file‑system safety.

---

### 8. Backlog Watch
- **Native Matrix adapter PR** [#2844](https://github.com/nanocoai/nanoclaw/pull/2844) (open since 2026‑06‑24) – a substantial rewrite with no maintainer comments yet. It touches crypto and persistence, so it needs careful review and would benefit from community testing if prioritised.
- **Discord attachment bug** [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) – opened yesterday, no assigned fix or PR. Given its impact on Discord users, it should be triaged quickly.

---

*All links refer to the `nanocoai/nanoclaw` repository on GitHub.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-07-01

## Today’s Overview
NullClaw saw no new releases, but maintainers merged four pull requests yesterday, fixing a critical provider-side thinking loop and significantly expanding the cron scheduling subsystem. One new bug was reported—Telegram channels become unresponsive after idle periods—though no fix is available yet. The project is active and focused on stability hardening and production‑grade cron features.

## Releases
No new releases were published within the 24‑hour window.

## Project Progress
Four pull requests by contributor **yanggf8** were merged/closed on 2026‑06‑30:

- **[PR #641](https://github.com/nullclaw/nullclaw/pull/641)** – Fixed the GLM/ZhipuAI provider’s always‑on thinking mode that caused response loops, and corrected native `tool_calls` handling.
- **[PR #643](https://github.com/nullclaw/nullclaw/pull/643)** – Allowed agent cron jobs to omit the `command` field; previously, agent jobs with `"command": null` were silently skipped, causing all agent cron to disappear after a restart.
- **[PR #645](https://github.com/nullclaw/nullclaw/pull/645)** – Added `--account` flag to `nullclaw cron add-agent`, enabling full delivery routing (e.g., choosing a Telegram bot) directly from the CLI without manual JSON edits.
- **[PR #783](https://github.com/nullclaw/nullclaw/pull/783)** – Introduced a cron subagent engine with a DB‑backed scheduler, run history, JSON CLI output, and security hardening (atomic tick/enqueue/complete, per‑job timezone offsets, operator alerts).

These changes advance the cron subsystem and eliminate several provider‑level stability issues.

## Community Hot Topics
Only one issue was updated in the last day, and it has no comments or reactions, indicating low community engagement at the moment.  
- **[Issue #972](https://github.com/nullclaw/nullclaw/issues/972)** — *Bug*: Telegram channel stops responding after idle time (e.g. overnight).  
  Underlying need: persistent, reliable channel delivery in user‑facing bot deployments.

## Bugs & Stability
- **Newly reported (no fix yet)**  
  - **[#972](https://github.com/nullclaw/nullclaw/issues/972) – [bug] Telegram channel stops responding after idle time**  
    Severity: Medium (breaks user interaction). User confirms the backend agent processes commands, but Telegram messages are not delivered. No pull request addresses it yet.

- **Resolved**  
  - **[PR #641](https://github.com/nullclaw/nullclaw/pull/641)** closed a critical looping bug in the ZhipuAI/GLM provider when thinking mode was active, improving overall model stability.

## Feature Requests & Roadmap Signals
No new feature request issues were opened. However, the merged PRs strongly signal the near‑term roadmap:
- A revamped **cron subsystem** with subagent scheduling, run history, and JSON output (PR #783) is likely to appear in the next release.
- CLI usability improvements (`--account` flag, optional `command` field) indicate a push to make cron configuration fully scriptable and mistake‑proof.
These contributions suggest a near‑future release focused on production‑ready scheduling and on‑boarding ease.

## User Feedback Summary
- **Pain points**:  
  - Telegram channel fragility after idle disconnected periods (Issue #972).  
  - Previously, users had to manually edit `cron.json` to set delivery accounts or faced hidden job losses when `command` was absent—both were resolved today via PR #645 and #643.
- **Satisfaction uplift**: The thinking‑mode loop fix (PR #641) removes a confusing, repetitive response behaviour for GLM model users, and the cron CLI improvements reduce manual configuration friction. The rapid response by contributor yanggf8 shows strong maintainer attention to user pain points.

## Backlog Watch
No long‑standing issues or PRs appeared in the 24‑hour data window. However, the newly opened **[Issue #972](https://github.com/nullclaw/nullclaw/issues/972)** has not yet received a maintainer response. If the Telegram idle‑disconnect problem persists, it may need a keep‑alive mechanism and should be prioritised to avoid degrading user‑facing bot reliability.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-01

## 1. Today’s Overview
The project saw an extremely active day with 50 pull requests updated (23 merged/closed) and 7 new or updated issues, all of which remain open. Development velocity is high across core features, bug fixes, and developer experience improvements, with no releases cutting during this window. The influx of QA-reported bugs from staging environments and a persistent E2E failure indicate both rapid iteration and the need for improved stability in the hosted product.

## 2. Releases
No new releases were published in the last 24 hours.

## 3. Project Progress
Several notable pull requests were merged or closed today, advancing tooling and fixing critical paths:

- **[#5447](https://github.com/nearai/ironclaw/pull/5447) [codex] Skip durable resource writes when limits are unlimited** — Adds an opt-in fast path for `PersistentResourceGovernor` when limits are disabled, keeping stress runs efficient behind a feature flag.  
- **[#5444](https://github.com/nearai/ironclaw/pull/5444) Add provider latency stress mode** — Introduces an opt-in provider-backed model latency mode to `ironclaw_stress`, allowing realistic latency testing with full retry/failover coverage.  
- **[#5438](https://github.com/nearai/ironclaw/pull/5438) [codex] Fix GitHub search validation recovery** — Fixes `builtin.time` to accept UTC offsets and reclassifies GitHub 422 errors as invalid input, improving model-visible error handling.  
- **[#5445](https://github.com/nearai/ironclaw/pull/5445) Make missing outbound delivery targets recoverable** — Returns a `CapabilityOutcome::Failed` instead of a host error when an outbound delivery target cannot be resolved by any connected provider, making the failure visible to the model.  
- **[#5375](https://github.com/nearai/ironclaw/pull/5375) [codex] Port Reborn WebUI projects and settings coverage** — Expands browser test coverage for project management, settings search, provider flows, skills, and tool permissions.  
- **[#5410](https://github.com/nearai/ironclaw/pull/5410) build(deps): bump everything-else group** — Bumps 9 dependencies, including `agent-client-protocol` from 0.10.4 to 1.0.1.

High-impact open PRs nearing completion include **[#5441](https://github.com/nearai/ironclaw/pull/5441) (header notifications for automation approvals)**, **[#5451](https://github.com/nearai/ironclaw/pull/5451) (WAL + PRAGMA tuning for libSQL)**, and the user-facing failure detail improvement **[#5338](https://github.com/nearai/ironclaw/pull/5338)**.

## 4. Community Hot Topics
Although comment and reaction counts were not provided, the most active item is the routine delivery bug **[#5420](https://github.com/nearai/ironclaw/issues/5420)** (1 comment), which breaks user expectations by making delivery targets global instead of per-routine. The feature request for automation-triggered header notifications **[#5443](https://github.com/nearai/ironclaw/issues/5443)** is directly linked to an open implementation PR **[#5441](https://github.com/nearai/ironclaw/pull/5441)**, showing strong demand for observability into automation runs. The two QA issues **[#5426](https://github.com/nearai/ironclaw/issues/5426)** and **[#5429](https://github.com/nearai/ironclaw/issues/5429)** (routine creation failure and Web Search token requirement) represent immediate pain points being surfaced by active testers.

## 5. Bugs & Stability
**Critical**  
- **[#5420](https://github.com/nearai/ironclaw/issues/5420) Routine delivery target is global, not per-routine** — Setting Slack for one routine reroutes all triggered routines (including an email summary routine) to Slack. No fix PR exists yet.

**High**  
- **[#5426](https://github.com/nearai/ironclaw/issues/5426) Cannot create a routine: “system drive is not available”** — Affects hosted-staging; blocks routine creation entirely.  
- **[#5429](https://github.com/nearai/ironclaw/issues/5429) Web Search requires a NEAR AI Cloud API token** — On multi-tenant setups, users without tokens cannot use the feature. No immediate fix linked.

**Medium**  
- **[#5437](https://github.com/nearai/ironclaw/issues/5437) Daily pinchbench failure** — All 146 tasks failed with HTTP 400 from the model backend, invalidating the entire run. Possibly upstream model service issue.  
- **[#4108](https://github.com/nearai/ironclaw/issues/4108) Nightly E2E failed** — Continues to fail intermittently since May 27, indicating flaky CI or environment instability.

Several open PRs address related UX and bug areas (e.g., surface failure details [#5338](https://github.com/nearai/ironclaw/pull/5338), chat composer clearing [#5404](https://github.com/nearai/ironclaw/pull/5404)), but none directly resolve the top-listed bugs.

## 6. Feature Requests & Roadmap Signals
The explicit feature request for header notifications **[#5443](https://github.com/nearai/ironclaw/issues/5443)** is already being implemented in **[#5441](https://github.com/nearai/ironclaw/pull/5441)** and may land in the next release. Several ongoing PRs indicate upcoming performance and developer experience improvements:  
- Compaction context budget overrides **[#5435](https://github.com/nearai/ironclaw/pull/5435)** and frugal read/grep output **[#5450](https://github.com/nearai/ironclaw/pull/5450)** aim to reduce token costs in long tool-heavy tasks.  
- The re‑enabling of `spawn_subagent` tests **[#5431](https://github.com/nearai/ironclaw/pull/5431)** and the new Reborn Playwright CI workflow **[#5449](https://github.com/nearai/ironclaw/pull/5449)** signal maturation of sub‑agent capabilities.  
- Filesystem WAL tuning **[#5451](https://github.com/nearai/ironclaw/pull/5451)** could significantly boost CLI and stress‑test concurrency.

## 7. User Feedback Summary
Users actively build routines that integrate with Slack and Google Sheets, but are hitting reliability walls: a simple Slack delivery configuration changes delivery for *all* routines unexpectedly, routine creation fails entirely on staging, and Web Search silently breaks for users without a personal API token. The request for header notifications indicates that automation results are too easy to miss without dedicated alerts. QA testers are rapidly surfacing these issues, which suggests an engaged early-adopter community but also points to gaps in pre‑release validation.

## 8. Backlog Watch
- **[#4108](https://github.com/nearai/ironclaw/issues/4108) Nightly E2E failed** has been open since 2026‑05‑27 with no maintainer comments. This persistent CI failure needs triage to prevent masking genuine regressions.  
- The three freshly reported critical/high bugs ([#5420](https://github.com/nearai/ironclaw/issues/5420), [#5426](https://github.com/nearai/ironclaw/issues/5426), [#5429](https://github.com/nearai/ironclaw/issues/5429)) are at risk of lingering without immediate assignment or fix PRs.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-07-01

## 1. Today’s Overview
The LobsterAI repository saw high engineering throughput in the past 24 hours, with 14 merged/closed PRs and a new release (2026.6.30). Active issue resolution focused on fixing conversation rail regressions, scheduling reliability, and analytics cleanup. Community activity remains low in terms of discussion (few comments or reactions), but a newly opened performance comparison issue (#2230) signals growing user attention to efficiency. Three legacy feature requests and one long-standing bug sit in the stale backlog, indicating some user-requested improvements are awaiting maintainer review.

## 2. Releases

### LobsterAI 2026.6.30 (released 2026-06-30)
This release bundles diagnostic improvements, provider fallbacks, and analytics refinements. No breaking changes or migration notes are indicated.

**Key changes:**
- **Diagnostics logging** for Cowork and OpenClaw flows (PR #2229) – helps troubleshooting session loading, message pagination, and runtime errors.
- **OpenClaw provider fallback** – scoped built-in max token limits for known Anthropic‑format providers when the bundled catalog cannot be read (PR #2232).
- **Scheduled task history fix** – gateway‑backed run history initialization for scheduled tasks, preventing false empty states on startup (PR #2231).
- **Analytics cleanup** – unified Youdao Analyzer reporting with application, platform, and login parameters; removal of inferred prompt intent fields (PR #2233).
- **UI polish** – conversation rail tooltip enhancements, artifact resize behavior, and model edit UX refinement (PRs #2222, #2235, #2236).

## 3. Project Progress
14 PRs were merged/closed yesterday, advancing both stability and user experience:

- **Conversation rail fixes** (PRs #2218, #2222, #2223, #2224, #2225, #2226) – a series of reverts, reapplies, and cleanups restored correct navigation, tooltip preview cleanup, hover styling, and lazy loading in the conversation rail. The chaotic merge/revert chain was straightened out across `main` and `release` branches.
- **Scheduled task reliability** (PR #2231) – the task list/history IPI now initializes the OpenClaw gateway before reading cron jobs, avoiding empty results at startup.
- **OpenClaw runtime improvements** (PR #2234 – still open) – proposes a fix for cron yield descendant finalization to allow parent agents to continue when child agents complete, covering parallel/sequential cron scenarios.
- **Analytics & logging** (PRs #2229, #2233) – added diagnostic logs across session loading and message pagination, while removing prompt intent fields from analytics to avoid sending inferred user input semantics.
- **UI fixes** (PR #2235, #2236) – prevented prompt toolbar overlap when resizing artifacts and optimized model editing UI.
- **Release workflow** (PR #2237) – bundled the version release.

The only open, unmerged PRs are #2234 (yield descendant finalization) and #1372 (stale fix for multi‑file selection). All other closed PRs were merged/excluded as part of the release preparation.

## 4. Community Hot Topics
Discussions are mostly quiet; no issue or PR has more than 2 comments, and reactions are absent. The most active (by comment count) and potentially influential items:

- **Stale UX suggestions**  
  - [#1382](https://github.com/netease-youdao/LobsterAI/issues/1382) – Export log red colour prompt (2 comments). Users find the red colour misleading for success indicators.  
  - [#1426](https://github.com/netease-youdao/LobsterAI/issues/1426) – No success feedback after local skill upload and list not refreshed (2 comments).  
  - [#1427](https://github.com/netease-youdao/LobsterAI/issues/1427) – Duplicate skills can be added via local upload (2 comments).  
  These three stale items hint at a need for better feedback in skill management and UI design guidelines.

- **Performance comparison with CodeBuddy**  
  - [#2230](https://github.com/netease-youdao/LobsterAI/issues/2230) – New issue (0 comments yet) reporting 25 minute vs. 2 minute response times and 60 M vs. 67 k tokens for the same prompt. This is likely to generate discussion once maintainers respond.

- **Scheduled task session reuse**  
  - [#1381](https://github.com/netease-youdao/LobsterAI/issues/1381) – Request to run repeated cron tasks inside a single conversation window instead of creating a new session each time (1 comment). A practical workflow improvement.

The underlying need across these topics is a smoother, more predictable user experience, especially when integrating with external tools and handling long‑running automations.

## 5. Bugs & Stability

**High severity**
- **Massive performance and token discrepancy vs. CodeBuddy** ([#2230](https://github.com/netease-youdao/LobsterAI/issues/2230))  
  *Description:* Using the same model and prompt, LobsterAI takes 10× more time and 900× more tokens than CodeBuddy when attempting to interact with an installed database. No fix PR exists yet. This regression could severely impact user trust and adoption if not addressed quickly.

**Medium severity**
- **Multi‑file upload only keeps the last file** ([#1384](https://github.com/netease-youdao/LobsterAI/issues/1384), stale)  
  - A fix PR (#1372) has been open since April and includes unit tests, but remains unmerged. It addresses the closure capture bug in `addAttachment`. The PR is marked stale, waiting for review/merge.

**Low severity / edge cases**
- **WeChat robot duplicate message sync** ([#1383](https://github.com/netease-youdao/LobsterAI/issues/1383), stale) – identical messages sent from mobile WeChat are only synchronised once on the desktop client.  
- **WeChat conversation history not cleared after deletion** ([#1385](https://github.com/netease-youdao/LobsterAI/issues/1385), stale) – old messages reappear after deleting and restarting a chat.  
  These affect a niche user base (WeChat bot integration) and have not received a fix PR.

**Note:** The scheduled task history empty‑state bug was fixed by PR #2231 (merged), and conversation rail regressions were resolved by the chain of rail PRs (merged).

## 6. Feature Requests & Roadmap Signals
User‑facing feature requests that could influence the next release:

- **System notification for background task completion** – PR [#1428](https://github.com/netease-youdao/LobsterAI/pull/1428) (stale) adds Electron native notifications when a conversation finishes or errors while the window is not focused. Likely to be revived given the project’s focus on cowork and scheduler.
- **Scheduled task session consolidation** ([#1381](https://github.com/netease-youdao/LobsterAI/issues/1381)) – users want cron runs in the same conversation window to avoid session clutter. The yield‑finalization fix (PR #2234) may pave the way for smarter session management.
- **Skill addition feedback & deduplication** ([#1426](https://github.com/netease-youdao/LobsterAI/issues/1426), [#1427](https://github.com/netease-youdao/LobsterAI/issues/1427)) – trivial but important for skill‑based workflows. A small UI patch could resolve both.
- **Export UX colour** ([#1382](https://github.com/netease-youdao/LobsterAI/issues/1382)) – a simple colour change suggestion that might be bundled in a UI polish sprint.

The analytics overhaul (PR #2237) suggests the team is investing in understanding user behaviour; thus, improvements that increase feature discovery (like notification for completion) are strong candidates for the next cycle.

## 7. User Feedback Summary
Real user pain points extracted from recent issues:

- **Performance and efficiency:** Users expect LobsterAI to be competitive with tools like CodeBuddy. The 10× slowdown and enormous token usage indicate possible inefficiency in the underlying agent orchestration or API handling.
- **Workflow interruptions:** Multiple issues complain about duplicated sessions (cron), missing success feedback (skills), and confusing UI indicators (red colour for logs). These slow down daily usage and create uncertainty.
- **WeChat integration gaps:** Duplicate message handling and residual history undermine the reliability of the WeChat robot channel, which may be important for certain enterprise workflows.
- **File handling bugs:** Losing uploaded files undermines the “cowork” experience. The long‑open fix PR shows community willingness to contribute, but the bug persists in the released version.
- **Positive signals:** Users are actively filing bugs and even submitting fixes (PR #1372, #1428). The community cares about polishing the tool, though maintainer responsiveness to stale items appears low.

## 8. Backlog Watch
These items have been open for months without a maintainer decision and could benefit from attention:

- **Critical bug fix PR – multi‑file selection** [#1372](https://github.com/netease-youdao/LobsterAI/pull/1372) – submitted April 2, has unit tests, but remains stale. The associated issue (#1384) is also stale.
- **Background notification feature PR** [#1428](https://github.com/netease-youdao/LobsterAI/pull/1428) – a well‑described feature with a clear implementation, untouched since April.
- **Stale issues with clear UX improvements** – [#1382](https://github.com/netease-youdao/LobsterAI/issues/1382) (log colour), [#1381](https://github.com/netease-youdao/LobsterAI/issues/1381) (cron session reuse), and [#1383](https://github.com/netease-youdao/LobsterAI/issues/1383)/[#1385](https://github.com/netease-youdao/LobsterAI/issues/1385) (WeChat fixes) all represent low‑effort, high‑impact adjustments that would enhance user satisfaction.

The maintainers may want to triage these during the next planning session to prevent community contributions from languishing and to address recurring usability complaints.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis Project Digest — 2026-07-01**

---

### 1. Today’s Overview
The Moltis repository shows minimal development activity. Over the past 24 hours, there have been no new issues, no releases, and no user discussions. The only visible activity consists of automated dependency bump PRs managed by Dependabot—three PRs in total (one open, two recently closed). This pattern suggests that the project is in a maintenance-only or low‑activity phase, with no active feature work or community engagement.

---

### 2. Releases
*No releases were published on this date. This section is omitted as there are no new versions to detail.*

---

### 3. Project Progress
Two dependency‑update PRs were merged/closed today, keeping JavaScript tooling up to date:

- **PR #1134** – Chore(deps): bump `astro` (6.3.3 → 6.4.8) in `/docs` and `undici` in `/website`.  
  [moltis-org/moltis#1134](https://github.com/moltis-org/moltis/pull/1134)
- **PR #1121** – Chore(deps-dev): bump `esbuild` (0.25.12 → 0.28.1) in `/crates/web/ui`.  
  [moltis-org/moltis#1121](https://github.com/moltis-org/moltis/pull/1121)

Both are routine maintenance updates; no new features or bug fixes were introduced.

---

### 4. Community Hot Topics
There are no active discussions with comments or reactions. The open dependency bump PR **#1141** (esbuild + vite updates) has not attracted any attention.  
[PR #1141](https://github.com/moltis-org/moltis/pull/1141)

The lack of community interaction indicates that users are not raising new issues, requesting features, or commenting on changes. The project’s communication channels appear dormant.

---

### 5. Bugs & Stability
No bugs, crashes, or regressions were reported in the last 24 hours. There are no open issues, and the closed Dependabot PRs are stability‑oriented (bumping library versions) but are not linked to any user‑reported problems.

---

### 6. Feature Requests & Roadmap Signals
No user‑facing feature requests were observed. With zero open issues and only automated dependency PRs, there are no signals about what might appear in a future version. Development appears to have paused, so no next‑version prediction can be made.

---

### 7. User Feedback Summary
No direct user feedback (issues, pull request comments, or reactions) was received today. The absence of feedback makes it impossible to assess user satisfaction, pain points, or use cases. The repository currently lacks an active user community.

---

### 8. Backlog Watch
There are no long‑unanswered important issues or PRs. The only open PR is **#1141** (a Dependabot bump opened yesterday), which is not a functional concern.  
[PR #1141](https://github.com/moltis-org/moltis/pull/1141)

The lack of stalled, unresolved items suggests that the project either has no outstanding maintenance debt or that active triage has ceased. Maintainers should verify whether the project’s goals have been met or whether it requires re‑engagement.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

**CoPaw Project Digest – July 1, 2026**

---

### 1. Today’s Overview
CoPaw (QwenPaw) remains in an intense development cycle with 50 pull requests updated in the last 24 hours (28 open, 22 merged/closed) and 16 issue updates. No new version was released today, but the rapid closure of bugs and feature PRs indicates steady progress toward the next stable release. Community engagement is high: both bug reports and feature requests are receiving prompt attention, and several first-time contributors have landed improvements. The project trajectory suggests a major release (v2.0.0) is being shaped by these community-driven contributions.

### 2. Releases
No new releases today. The latest version on record remains 1.1.12.post2.

### 3. Project Progress (Today’s Merged / Closed PRs)
Key features and fixes that advanced today:

- **DingTalk @mentions in proactive sends** – `feat(channels): support dingtalk mentions` was merged ([#5590](https://github.com/agentscope-ai/QwenPaw/pull/5590)), enabling `@` user mentions via the shared API/CLI and cron text delivery.
- **Skill auto-sync** – `feat(skill): Add skill auto sync` ([#5639](https://github.com/agentscope-ai/QwenPaw/pull/5639)) allows pool skills to automatically sync to agents, with a change log accessible via the inbox.
- **UI polish** – Multiple UI fixes landed: non-owner tab info banner ([#5664](https://github.com/agentscope-ai/QwenPaw/pull/5664)), isolating sidebar session scrolling to simple mode ([#5656](https://github.com/agentscope-ai/QwenPaw/pull/5656)), and CI template channel name fix ([#5662](https://github.com/agentscope-ai/QwenPaw/pull/5662)).
- **Documentation** – README was updated and refined ([#5655](https://github.com/agentscope-ai/QwenPaw/pull/5655)).

### 4. Community Hot Topics (Most Active Issues / PRs)
Issues with the highest comment activity in the last 24 hours:

- **[#5401] Console crash on large tool-use history** (6 comments, closed) – The frontend failed to render sessions with heavy tool-use history because `tool_use`/`tool_result` blocks were converted to unsupported `type: "data"` blocks. This was a critical rendering bug that blocked users with complex agent interactions.
- **[#5403] Browser autofill hijacks search input** (5 comments, open) – The “Search providers” field in Model Configuration page is misidentified by browsers as a credential field, causing unwanted autofill popups. This remains a significant UX friction point.
- **[#5588] Memory search needs a reranker for two-stage retrieval** (4 comments, open) – Users requested a dedicated Reranker model (like qwen3-rerank) to improve recall precision as memory grows. An associated PR ([#5669](https://github.com/agentscope-ai/QwenPaw/pull/5669)) has already been opened, showing fast feature-response alignment.
- **[#5573] DeepSeek V4 thinking mode 400 errors** (4 comments, closed) – Complaints about missing `reasoning_content` fallback and `null` schema in tools when using OpenAI-compatible endpoints were resolved (likely with a backend patch). Community contributed debugging and validation.

Underlying needs: **stability on large-scale usage**, **better retrieval quality**, **smoother cross-model compatibility**, and **less UI friction**.

### 5. Bugs & Stability
List of notable bugs reported today, ranked by severity:

1. **Frontend crash on large tool history** – [#5401](https://github.com/agentscope-ai/QwenPaw/issues/5401) (closed). The app white‑screened when rendering sessions with extensive tool interactions. This is a critical usability issue for power users; a fix was apparently deployed, but the exact commit is not visible in today’s PR list.
2. **DeepSeek V4 thinking mode incompatibility** – [#5573](https://github.com/agentscope-ai/QwenPaw/issues/5573) (closed). Two separate 400 errors (streaming reasoning_content missing, tool schema null not sanitized) prevented usage via third‑party OpenAI endpoints. Now fixed.
3. **Qwen‑Image Tool installation error** – [#5587](https://github.com/agentscope-ai/QwenPaw/issues/5587) (open). Users cannot install the Qwen‑Image tool; no fix PR linked yet.
4. **9router-model connection failure** – [#5658](https://github.com/agentscope-ai/QwenPaw/issues/5658) (open). A persistent 400 error when routing through 9router for `qwen3.7-plus`; remains unresolved and has been recurring across upgrades.
5. **Cron silent execution & phantom notifications** – [#5566](https://github.com/agentscope-ai/QwenPaw/issues/5566) (open). Two intertwined bugs: (a) cron tasks cannot suppress empty replies, leading to spurious notifications; (b) `qwenpaw channels send` is unreachable from background scripts. A fix PR ([#5654](https://github.com/agentscope-ai/QwenPaw/pull/5654)) is under review, targeting the delivery boundary.

Overall, critical rendering and model‑compatibility bugs are being fixed rapidly, while environment‑specific issues (9router, cron) need further hardening.

### 6. Feature Requests & Roadmap Signals
Open enhancement requests that may influence next releases:

- **Two-stage retrieval with reranker** – [#5588](https://github.com/agentscope-ai/QwenPaw/issues/5588) + PR [#5669](https://github.com/agentscope-ai/QwenPaw/pull/5669) (qwen3-rerank integration). Likely to land soon.
- **Loop detection mechanism** – [#5657](https://github.com/agentscope-ai/QwenPaw/issues/5657) + PR [#5665](https://github.com/agentscope-ai/QwenPaw/pull/5665) (composable gate architecture). Appears well-developed and could be a headline feature for v2.0.0.
- **Custom Telegram BaseURL** – [#5630](https://github.com/agentscope-ai/QwenPaw/issues/5630) (open). Low complexity, high demand for self‑hosted Telegram environments.
- **Linux AppImage build** – [#5668](https://github.com/agentscope-ai/QwenPaw/issues/5668) (open). Tauri supports AppImage natively; this primarily needs packaging work.
- **Remove input character limit** – [#5670](https://github.com/agentscope-ai/QwenPaw/issues/5670) (open). Users find the current 10k cap restrictive for long‑context models.
- **Workspace file browser in chat** – [#5667](https://github.com/agentscope-ai/QwenPaw/issues/5667) (open). A request to view agent outputs without leaving the conversation.

Given the active PRs, **memory reranking** and **loop engineering** are strong candidates for the next release, possibly as part of the v2.0.0 milestone tracked in [#5273](https://github.com/agentscope-ai/QwenPaw/issues/5273).

### 7. User Feedback Summary
- **Pain points**: Frontend crashes when working with heavy tool chains (#5401); browser autofill constantly disrupts model search (#5403); insufficient retrieval accuracy without a reranker (#5588); missing Linux desktop build excludes a large user segment (#5668); and strict input limits stifle long‑form tasks (#5670).
- **Collaboration needs**: Users want rich interactions across channels – DingTalk @mentions (now done via #5590), Telegram custom endpoints (#5630), and reliable cron‑to‑channel messaging (#5566).
- **Model flexibility**: Several reports show users pushing the boundaries with non‑official endpoints (DeepSeek via micu_ai, 9router), revealing sharp edges in the provider abstraction layer.
- **Positive signals**: Contributors are actively submitting fixes and features (multiple `first-time-contributor` labels), indicating a welcoming project. Questions like the debounce‑bypass switch (#5663) show users are thinking about fine‑grained control.

### 8. Backlog Watch
- **PR #5151** – GitPanel tabs style fix (open since June 12). A simple CSS prefix mismatch remains unmerged.
- **PR #5097** – Shield icon vertical centering (open since June 11). Another minor UI fix awaiting review.
- **PR #5525** – Windows native sandbox implementation (open since June 25). A more complex feature with significant scope; needs maintainer bandwidth.
- **Issue #5273** – v2.0.0 bug tracker (open since June 17). Low comment activity but serves as a placeholder for pre‑release issues; it would benefit from a maintainer summary to guide community testing.

These items, though not critical, represent “paper‑cut” improvements that could enhance polish if reviewed and merged.

---

*All links point to the respective GitHub issues/PRs on [agentscope-ai/QwenPaw](https://github.com/agentscope-ai/QwenPaw).*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-01

## 1. Today’s Overview
The ZeroClaw project continues to see a high pace of development, with 50 pull requests updated in the last 24 hours (4 merged/closed) and 6 issues touched (2 closed, 4 new). No new releases were published, but the active contribution surface is broad: major features such as an end‑to‑end onboard tree, desktop app removal, CI hardening for Windows, and pluggable skill registries are all moving forward. Two accepted RFCs were closed today, confirming the project’s direction on the plugin host and skill registries. The community is simultaneously raising practical usability issues around web UI secret fields, HTTP tool auth, and zip‑bomb hardening. Overall health is **strongly active**, with rapid iteration across core runtime, security, channels, and web UI.

## 2. Releases
None in the last 24 hours.

## 3. Project Progress
**Merged / Closed Pull Requests (4 total; 2 visible in top-20):**
- **PR #8018** ([link](https://github.com/zeroclaw-labs/zeroclaw/pull/8018)) – fix(gateway): make agent rename re‑issue converge after a post‑persist partial failure (closes #7907). The rename split‑brain now correctly instructs operators to re‑issue the rename to converge.
- **PR #8017** ([link](https://github.com/zeroclaw-labs/zeroclaw/pull/8017)) – fix(gateway): persist agent delete config before archiving owned state, fixing a split‑brain where a persist failure left config naming an agent whose workspace had already been archived.
- *The other two merged/closed PRs are not in the top‑20 snapshot; they likely cover smaller fixes.*

**Closed Issues:**
- **Issue #6943** ([link](https://github.com/zeroclaw-labs/zeroclaw/issues/6943)) – [RFC] Deconflict Plugin System Goals in FND‑001. Accepted; replaces Extism with a direct Wasmtime component model host, targeting `wasm-wasip2`.
- **Issue #7816** ([link](https://github.com/zeroclaw-labs/zeroclaw/issues/7816)) – [Feature] Pluggable skill registries. Accepted; keeps the GitHub repo as the default tier and generalizes all other remote sources into a prefixed/flagged pluggable second tier.

## 4. Community Hot Topics
- **RFC #6943 – Plugin system host deconfliction** (4 comments, closed) – The discussion settled on a pure Wasmtime component model approach, removing Extism. This is a foundational architecture shift that will affect all plugin authors; the closed status signals a final decision.
- **Feature #7816 – Pluggable skill registries** (2 comments, closed) – Standardises how external registries (ClawHub, agentskills.io, etc.) are accessed, with user‑configurable prefixes. The closure means the design is accepted, and implementation can proceed.
- **PR #8033 – Two‑path onboard tree (LLM + deterministic)** (large, XL risk, many comments likely) – Introduces the `zeroclaw-onboard` crate as a walkable state tree emitted as data; it is a critical UX piece for first‑run experience and testing.
- **PR #8544 – Removal of the zeroclaw‑desktop Tauri app** (XL size) – A sweeping change to retire the desktop companion app, touching CI, docs, i18n, and the workspace. It will simplify the build surface but requires careful review.
- **PR #6297 – Poll‑vote / interactive‑reply events for Signal & WhatsApp** (open since May 3) – Adds `sendPollCreate` and `send_choice` to the channel boundary. Long‑running and high‑impact for channel‑rich interactions.

*Comment counts for PRs are unavailable in the provided snapshot; selection is based on scope, risk labels, and longevity.*

## 5. Bugs & Stability
- **⚠️ S1 – Workflow Blocked**  
  **#8553** ([link](https://github.com/zeroclaw-labs/zeroclaw/issues/8553)) – Agent cannot use environment variables as `http_request` secrets. When a bot token (e.g., `SLACK_BOT_TOKEN`) is in the ZeroClaw process environment, there is no working path for the agent to authenticate HTTP requests. No fix PR yet.
- **⚠️ S2 – Degraded Behaviour**  
  **#8554** ([link](https://github.com/zeroclaw-labs/zeroclaw/issues/8554)) – Skill zip extractor (`extract_zip_secure`) lacks protection against zip‑bombs; only compressed size is bounded, not decompressed entry count, ratio, or uncompressed size. This affects ClawHub installs. No fix PR yet.
- **Minor**  
  #8526 ([PR](https://github.com/zeroclaw-labs/zeroclaw/pull/8526)) fixes error chain preservation in `audit.rs` (signing key/HMAC), and #8514 ([PR](https://github.com/zeroclaw-labs/zeroclaw/pull/8514)) fixes `LibraryNotFound` error chaining in Aardvark hardware library. Both are low‑risk.

## 6. Feature Requests & Roadmap Signals
- **OpenAI‑compatible chat completions endpoint**  
  **#8550** ([link](https://github.com/zeroclaw-labs/zeroclaw/issues/8550)) – Requested by REL‑mame to enable standard clients like Open WebUI and LobeChat to connect without custom Websocket bridges. This is a strong integration gateway.
- **Secret field “set/not‑set” state indicator in Web UI**  
  **#8556** ([link](https://github.com/zeroclaw-labs/zeroclaw/issues/8556)) has an immediate implementation PR **#8557** ([link](https://github.com/zeroclaw-labs/zeroclaw/pull/8557)). Likely to land soon.
- **Accepted early‑stage RFCs** – The closure of #6943 (Wasmtime host) and #7816 (pluggable registries) signals that these strategic changes will begin landing in upcoming releases. Expect plugin ecosystem transformations and skill registry modularity in the next major version cycle.
- **On‑device board and desktop removal** – PR #8033 (onboard tree) and #8544 (desktop removal) indicate a push to simplify the onboarding and deployment surface; both are large and may be the headline features of the next release.

## 7. User Feedback Summary
- **Critical pain point**: Environment‑variable secrets for HTTP tools are blocked (#8553), leaving bots unable to use available credentials for authenticated calls. This is a workflow blocker (S1) with no known workaround.
- **Security concern**: The zip‑bomb vulnerability in skill extraction (#8554) worries users who install skills from external registries; the community expects sandbox caps on decompressed size and entry counts.
- **Usability**: The secret field UI (#8556) is confusing because it shows a password input regardless of whether a value is stored; users want a clear set/empty indicator. The already‑opened PR #8557 shows that this feedback is being acted upon immediately.
- **Integration demand**: Multiple users are requesting an OpenAI‑compatible API endpoint (#8550) to integrate ZeroClaw agents with popular chat front‑ends, reflecting a desire for seamless ecosystem interoperability.

## 8. Backlog Watch
- **PR #6297** ([link](https://github.com/zeroclaw-labs/zeroclaw/pull/6297)) – `feat(channels): expose poll‑vote / interactive‑reply events; add Channel::send_choice`. Opened on **2026‑05‑03** (8 weeks ago), high risk, size L. Implements poll creation and voting for Signal and WhatsApp. It has refreshed evidence and a detailed implementation, but remains open. This is a high‑value feature for conversational channels and should receive maintainer attention to avoid bit‑rot.
- **PR #8033** ([link](https://github.com/zeroclaw-labs/zeroclaw/pull/8033)) – `feat(onboard): two‑path onboard tree …`. Opened **2026‑06‑20**, XL size, high risk. A foundational onboarding rewrite that touches RPC and CLI. It is large and likely needs careful review cycles; early attention will reduce integration friction.
- **Issue backlog is currently empty** (all open issues are less than 24h old), suggesting that the team is keeping up with incoming reports.

---
*Generated from snapshot data of issues/PRs updated in the last 24 hours. No release activity was observed.*

</details>