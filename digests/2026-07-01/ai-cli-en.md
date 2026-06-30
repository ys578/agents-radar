# AI CLI Tools Community Digest 2026-07-01

> Generated: 2026-06-30 16:24 UTC | Tools covered: 9

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Pi](https://github.com/badlogic/pi-mono)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [DeepSeek TUI](https://github.com/Hmbown/DeepSeek-TUI)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## Cross-Tool Comparison

# Cross-Tool AI CLI Ecosystem Report — July 1, 2026

## 1. Ecosystem Overview
The AI CLI tools landscape is rapidly evolving from single-model chat assistants into multi-agent, extensible development platforms. All major players are shipping frequent updates with a sharp focus on agent reliability, MCP (Model Context Protocol) integration, and enterprise-grade security. Open-source communities are driving demand for model fallback, granular permissions, and richer terminal/IDE experiences. The competition is intensifying around sub-agent orchestration, session management, and deep editor integration, signalling a maturing market where developer ergonomics and trust are as critical as raw model capability.

## 2. Activity Comparison

| Tool | Hot Issues Highlighted | PRs Listed | Latest Release (last 24h) |
|------|------------------------|------------|----------------------------|
| **Claude Code** | 10 | 10 | v2.1.196 |
| **OpenAI Codex** | 10 | 10 | rust-v0.143.0-alpha.31 |
| **Gemini CLI** | 10 | 10 | v0.51.0-nightly.20260630 |
| **GitHub Copilot CLI** | 10 | 1 | v1.0.66 |
| **Kimi Code CLI** | 1 | 2 | none |
| **OpenCode** | 10 | 10 | none |
| **Pi** | 10 | 10 | none |
| **Qwen Code** | 6 | 10 | v0.19.3-nightly.20260630 |
| **DeepSeek TUI** | 10 | 10 | none (v0.8.66 merge batch) |

*Issues/PRs counted from the digest’s curated highlights, not necessarily the total daily volume.*

## 3. Shared Feature Directions
Requirements that appear **simultaneously** across multiple tool communities:

- **MCP ecosystem maturation**  
  OpenAI, Gemini, OpenCode, Copilot CLI, and DeepSeek are all investing in MCP: environment variable expansion for secrets, file transfer protocol support, prompt templates, and dedicated CLI management commands. The protocol is becoming the de facto standard for extending AI tools.

- **Agent orchestration reliability and sub-agent safety**  
  Gemini (subagent hangs, MAX_TURNS recovery), Qwen (plan‑mode isolation, loop detection), DeepSeek (high‑fanout UI freezes), and Claude Code (cowork private marketplace) are all working on making sub-agents trustworthy, loop‑free, and non‑destructive.

- **Granular permissions and security hardening**  
  Claude Code (OAuth revocation gap), OpenCode (editable “always allow” patterns), DeepSeek (typed allow/deny rules, wildcard tool blocking), and Gemini (sandbox escapes) highlight a universal shift toward fine‑grained, auditable trust models.

- **Session and context lifecycle management**  
  Claude Code (transcript auto‑deletion), DeepSeek (token explosion, cache hit improvements), OpenCode (small‑model task routing, session completion determinism), and Pi (excludeFromContext, auto‑compaction errors) all reflect a need for cost‑aware context compaction, session resume, and intelligent memory handling.

## 4. Differentiation Analysis

- **Claude Code** leans heavily into **enterprise VS Code integration** (diff review UI, org default models), robust **Windows/macOS desktop fixes**, and OAuth security. Its community cares deeply about IDE workflow parity with Copilot.
- **OpenAI Codex** differentiates with a **durable TUI/app‑server architecture**, sandboxed execution, and **Azure DevOps** demand. It targets power users who value custom models and resilient, restart‑surviving sessions.
- **Gemini CLI** is heavily **agent‑oriented** with skills and sub‑agents, frequent nightlies, and a strong focus on **safety guardrails** (destructive commands, sandbox escapes). Its community is vocal about agent hangs and reasoning stability.
- **GitHub Copilot CLI** remains the **tightest GitHub‑ecosystem integration**: plugin system, model switching (Claude Opus, GPT), and terminal UX polish. Community requests centre on repo‑scoped plugins and theme customisation.
- **Kimi Code** is a **nascent entry** from Moonshot AI, with a small community focused on basic shell UX and interactive prompt continuity. Feature depth is minimal compared to others.
- **OpenCode** stands out with **multi‑provider flexibility and native model fallback** (90👍), a feature‑rich desktop app with direct file editing, and a strong community‑driven agenda (interactive steering, configurable small‑model routing).
- **Pi** is **extension‑first**, offering fine‑grained context control (excludeFromContext), session event hooks, and TUI polish (redo, padding). It appeals to developers building custom AI toolchains on top.
- **Qwen Code** emphasizes **daemon‑based collaboration** (ACP protocol, channel loops, group backfill), mobile‑responsive web shell, and sub‑agent plan isolation. It addresses team workflows and Windows path quirks extensively.
- **DeepSeek TUI (CodeWhale)** focuses on **high‑fanout multi‑agent performance**, token‑cache optimisation, and enterprise safety (typed permission rules). It’s the most cost‑conscious and performance‑sensitive community.

## 5. Community Momentum & Maturity

- **Highest engagement (upvotes/comments):** Claude Code (#33932 with 127👍, #60366 with 89 comments) and OpenAI Codex (#10665 with 73👍, #30224 with 62 comments) lead in raw community activity. OpenCode also shows strong demand (90👍 for fallback).
- **Rapid iteration:** Gemini CLI and Qwen Code push nightly releases; Claude Code and Copilot CLI ship regular versioned updates. DeepSeek TUI merges large batches of PRs for imminent releases. OpenCode and Pi merge steadily without version bumps.
- **Moderate activity:** Pi and DeepSeek have loyal, technically deep communities but smaller overall volume. Kimi Code is still in early traction building.
- **Maturity indicators:** Claude Code and OpenAI Codex exhibit enterprise‑grade feature sets and security incident responses. Copilot CLI’s polished release notes and plugin ecosystem show a mature product. Gemini CL’s heavy focus on bug fixes (P1 items) suggests a tool still hardening for production. OpenCode’s architectural V2 refactoring and MCP CLI addition demonstrate evolving maturity.

## 6. Trend Signals
Key industry signals for developers and technical decision-makers:

- **MCP has become a non‑negotiable integration backbone.** Tools that don’t invest in MCP management, security, and prompts risk falling behind in extensibility.
- **Agentic reliability is the next front.** Communities are rejecting black‑box agents that hang, loop, or misreport success; demand for graceful degradation, loop detection, and safe sub‑agent delegation is universal.
- **Model flexibility is now table stakes.** Users expect custom model support (BYOK), provider fallback, and transparent cost/performance trade‑offs. Hardcoded model selections (e.g., Gemini’s browse agent, Copilot CLI’s `explore` tool) are being called out as bugs.
- **Security and permission models are tightening.** OAuth token revocation, sandbox escapes, and coarse‑grained tool approvals are no longer acceptable. Fine‑grained, editable, and persistent permissions are the new norm.
- **Terminal/IDE UX convergence accelerates.** Inline diff reviews, live panels, interactive steering, and cursor/hotbar customisation point to a future where the boundary between terminal and IDE dissolves into a unified agentic workspace.
- **Enterprise integration is deepening.** Private marketplaces, Azure DevOps support, organization‑wide model defaults, and channel‑based collaboration show that these tools are being embedded into enterprise workflows, not just individual developer setups.

*Reference value: Developers should prioritize familiarity with MCP standards, invest in agent safety patterns, and architect for multi‑provider/model fallback. The tools with the strongest community voice today are Claude Code and OpenAI Codex, while OpenCode and DeepSeek TUI are the ones to watch for cost‑efficient, extensible, and community‑driven alternatives.*

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills — Community Highlights Report
**Data as of: 2026-07-01 | Repository: [anthropics/skills](https://github.com/anthropics/skills)**

---

## 1. Top Skills Ranking (Most-Discussed PRs)

| # | PR | Skill / Topic | Status | Attention Signal |
|---|----|---------------|--------|------------------|
| 1 | [#1298](https://github.com/anthropics/skills/pull/1298) | **skill-creator: run_eval.py recall fix** — Fixes the description-optimization loop that always reports 0% recall, plus Windows stream reading and parallel-worker bugs | OPEN | Top of sorted-by-comments list; 10+ independent reproductions; directly referenced by Issues [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 👍7) and [#1169](https://github.com/anthropics/skills/issues/1169) |
| 2 | [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** — Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents | OPEN | High community interest in quality-of-life document output improvements |
| 3 | [#486](https://github.com/anthropics/skills/pull/486) | **ODT Skill** — Create, fill, read, and convert OpenDocument Format files (.odt, .ods); template filling and ODT→HTML parsing | OPEN | Addresses open-source document ecosystem; triggers on LibreOffice/ODF mentions |
| 4 | [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer + skill-security-analyzer** — Meta-skills evaluating Skill structure/documentation (20% weight) and security posture across five dimensions | OPEN | Direct response to quality concerns echoed in Issue [#202](https://github.com/anthropics/skills/issues/202) (8 comments, closed) and Issue [#492](https://github.com/anthropics/skills/issues/492) (32 comments) |
| 5 | [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** — Full testing stack: Testing Trophy model, AAA pattern, React component testing, and testing philosophy | OPEN | Fills a critical gap — no existing skill covers systematic testing guidance |
| 6 | [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** — Four-dimension reasoning quality gate (completeness, consistency, grounding, actionability) applied before delivery | OPEN | Universal applicability; replaces earlier PR #1361 |
| 7 | [#181](https://github.com/anthropics/skills/pull/181) | **SAP-RPT-1-OSS predictor** — Wraps SAP's open-source tabular foundation model for predictive analytics on business data | OPEN | Enterprise niche; leverages TechEd 2025 release |
| 8 | [#147](https://github.com/anthropics/skills/pull/147) | **codebase-inventory-audit** — 10-step systematic workflow for orphaned code detection, documentation gap analysis, and infrastructure bloat identification | OPEN | Produces a single-source-of-truth `CODEBASE-STATUS.md` |

---

## 2. Community Demand Trends (from Issues)

| Trend | Source Issue(s) | Signal Strength |
|-------|-----------------|-----------------|
| **Trust & Namespace Governance** — Community demands clear separation between official Anthropic skills and community contributions to prevent impersonation and permission-abuse vectors | [#492](https://github.com/anthropics/skills/issues/492) (32 comments, 👍2) | 🔴 Strongest single issue |
| **Org-Wide Skill Distribution** — Enterprise users need shared skill libraries, not manual `.skill` file transfers via Slack/Teams | [#228](https://github.com/anthropics/skills/issues/228) (14 comments, 👍7) | 🟠 High |
| **Skill Evaluator Reliability** — The description-optimization loop (`run_eval.py` / `run_loop.py`) is fundamentally broken (0% recall), making skill improvement tooling unusable | [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 👍7) + [#1169](https://github.com/anthropics/skills/issues/1169) (3 comments) | 🟠 High |
| **Persistent Agent Memory** — Growing interest in compact, symbolic memory formats that reduce context-window consumption across long-running agent sessions | [#1329](https://github.com/anthropics/skills/issues/1329) (7 comments) | 🟡 Emerging |
| **Agent Safety & Governance** — Patterns for policy enforcement, threat detection, trust scoring, and audit trails in AI agent systems | [#412](https://github.com/anthropics/skills/issues/412) (6 comments, closed) | 🟡 Niche but persistent |
| **Cross-Platform & Cross-Provider Compatibility** — Windows support is broken at multiple layers (subprocess, encoding, pipes); Bedrock integration is unclear | [#1061](https://github.com/anthropics/skills/issues/1061) (3 comments, 👍1) + [#29](https://github.com/anthropics/skills/issues/29) (4 comments) | 🟡 Pain-point driven |
| **Skills as MCP Endpoints** — Desire to expose Skill APIs via the Model Context Protocol for composable, callable AI software | [#16](https://github.com/anthropics/skills/issues/16) (4 comments) | 🟢 Early-stage vision |

---

## 3. High-Potential Pending Skills (Active, Unmerged)

These PRs have demonstrable community attention and may land in the next merge cycle:

| PR | Skill | Why It Matters |
|----|-------|----------------|
| [#514](https://github.com/anthropics/skills/pull/514) | **document-typography** | Solves a universal AI-document pain point no one explicitly asks for but everyone notices |
| [#486](https://github.com/anthropics/skills/pull/486) | **ODT Skill** | Unlocks the LibreOffice/ODF ecosystem for Claude; ISO-standard document workflows |
| [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality-analyzer + skill-security-analyzer** | Meta-tooling that could become a gate for all future community skill submissions |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** | Fills the largest developer-workflow gap in the current skills catalog |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** | Lightweight, universal quality-gate that works across all models and stacks |
| [#154](https://github.com/anthropics/skills/pull/154) | **shodh-memory** | Directly addresses the persistent-context demand surfaced in Issue [#1329](https://github.com/anthropics/skills/issues/1329) |
| [#147](https://github.com/anthropics/skills/pull/147) | **codebase-inventory-audit** | Systematic technical-debt discovery for mature projects |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for _trust infrastructure and quality assurance tooling_ — spanning namespace governance (Issue [#492](https://github.com/anthropics/skills/issues/492), 32 comments), broken evaluator reliability (Issues [#556](https://github.com/anthropics/skills/issues/556)/[#1169](https://github.com/anthropics/skills/issues/1169) + PRs [#1298](https://github.com/anthropics/skills/pull/1298)/[#1323](https://github.com/anthropics/skills/pull/1323)), meta-quality analyzers (PR [#83](https://github.com/anthropics/skills/pull/83)), and self-audit delivery gates (PR [#1367](https://github.com/anthropics/skills/pull/1367)) — indicating the ecosystem is maturing from _building more skills_ toward _building confidence in skills._**

---

*Report generated from [anthropics/skills](https://github.com/anthropics/skills) activity through 2026-07-01. All PRs listed are OPEN; priorities inferred from comment volume rankings and cross-reference Issue activity.*

---

# Claude Code Community Digest — 2026-07-01

## Today’s Highlights
Claude Code v2.1.196 ships with organization-level default model support and human-readable session names. The community is loudly discussing a bizarre “API Error” on trivial prompts and rallying around a highly-voted request for a Copilot-style diff review UI in VS Code. Multiple PRs land essential Windows & macOS fixes for the plugin system, while a closed security issue exposes a dangerous OAuth token revocation gap.

---

## Releases
**[v2.1.196](https://github.com/anthropics/claude-code/releases/tag/v2.1.196)** (published in the last 24h)
- Organization default models: admins configure a default model in the org console; it appears as **“Org default”** (or “Role default”) in `/model` when no personal model is selected.
- Session naming: new sessions now receive readable default names immediately, making them easier to identify and reference in subsequent messages.

---

## Hot Issues

1. **[#60366] [BUG] Saying “hi” returns an API Error citing Usage Policy violation**  
   *89 comments · 👍 23*  
   A trivial greeting triggers a usage-policy rejection. Users suspect an overzealous content filter or model regression. The high comment count shows widespread confusion and frustration with opaque model behaviour.

2. **[#28125] Cowork can’t add private GitHub marketplace**  
   *28 comments · 👍 28*  
   Developers using private marketplace extensions cannot integrate them into Claude Code’s cowork feature, severely limiting customisation in enterprise environments.

3. **[#33932] VS Code Extension: Diff review UI similar to GitHub Copilot Edits Review**  
   *26 comments · 👍 127*  
   The single most 👍’d open issue. Users want inline, side-by-side diff reviews directly in the chat panel rather than jumping to separate editor tabs. Strong signal for the IDE team.

4. **[#29716] WorktreeCreate / Remove hooks not called in Claude Desktop**  
   *22 comments · 👍 23*  
   Hook events that fire correctly in CLI mode never trigger in the Desktop app, breaking automation workflows for users who rely on custom hooks.

5. **[#43801] [SECURITY] “Log out all sessions” + instance revocation does not invalidate OAuth tokens** (closed)  
   *21 comments · 👍 5*  
   OAuth tokens remain valid for days after revocation, even after a VM cold boot. This serious security gap undermines the logout mechanism entirely; the issue was closed but remains a critical reference.

6. **[#39678] Code Review incorrectly reports overage limit reached when spend is $0/$250**  
   *13 comments · 👍 12*  
   Organisations see “spend limit reached” errors despite zero usage, blocking GitHub PR code reviews and eroding trust in billing controls.

7. **[#66056] Right-click paste broken since ~2.1.167: mouse reporting captures right-click**  
   *5 comments · 👍 10*  
   A recent regression in the terminal UI intercepts right-click events, forcing a Shift+right-click workaround. A major papercut for terminal power users on Linux.

8. **[#62476] Claude Code silently deletes conversation transcripts after 30 days by default**  
   *5 comments · 👍 6*  
   Conversations are auto-purged without clear warning, leading to lost context and debug history. Users demand a configurable retention policy or at least a visible notice.

9. **[#71951] Claude Desktop (macOS) — 69s main-thread freeze on every launch after [buddy] bridge started**  
   *4 comments · 👍 0*  
   A full freeze on startup persists across resets and reinstalls, making the Desktop app unusable for affected users.

10. **[#68316] macOS version of Claude Desktop becomes corrupted, freezes, requiring full Reset App**  
    *4 comments · 👍 0*  
    Repeated corruption forces a complete app reset, indicating a deeper stability issue on macOS Desktop.

---

## Key PR Progress

1. **[#68699] fix(hookify): add Python wrapper and normalize plugin root paths on Windows**  
   Windows backslash paths break inline bash scripts; a `python3` stub from Microsoft Store silently fails. This PR wraps Python calls and normalizes paths.

2. **[#68701] fix(security-guidance): strip CRLF from Python version probe on Windows**  
   Python’s Windows line endings caused version comparisons to fail. Stripping `\r\n` ensures the security-guidance plugin loads correctly.

3. **[#68702] fix(ralph-wiggum): guard PROMPT_PARTS expansion against `set -u` on bash 3.x (macOS)**  
   macOS’s old bash enables `set -u` by default, breaking the ralph-wiggum plugin due to an unbound array expansion.

4. **[#68686] fix(hookify): rename shadowed ‘field’ variable and fix inline dict comma parsing**  
   A module-level `field` was accidentally shadowed, and comma-separated inline dicts weren’t parsed correctly.

5. **[#68694] fix(security-guidance): normalize CLAUDE_PLUGIN_ROOT path separators on Windows**  
   All six hook commands now convert backslashes to forward slashes so that `${CLAUDE_PLUGIN_ROOT}` doesn’t break inline scripts.

6. **[#68689] fix(security-guidance): block symlink escape in extensibility config reads**  
   A malicious `.claude/claude-security-guidance.md` symlink could read arbitrary local files (e.g., `~/.ssh/id_rsa`). This PR prevents the escape.

7. **[#68693] fix(scripts): add duplicate label additively, don’t replace existing labels**  
   The issue-closing script was replacing all labels with `[duplicate]`, silently dropping platform/area tags. Now it appends.

8. **[#68707] feat(bug-reporter): add /bug command to file GitHub issues from the terminal**  
   A new `bug-reporter` plugin with a `/bug` slash command lets users submit bug reports directly to the `anthropics/claude-code` repo without leaving the terminal.

9. **[#72451] fix: remove statsig.anthropic.com from init-firewall.sh**  
   The hostname no longer resolves, causing firewall initialisation failures during devcontainer startup. Cleaned out of the allowlist.

10. **[#72361] Add Claude Gateway on GCP example deployment assets** (closed)  
    Reference Terraform and configuration assets for running Claude Gateway on Google Cloud, complementing the published walkthrough.

---

## Feature Request Trends
- **Inline diff/editing review in VS Code** – By far the most-requested enhancement (#33932). Developers want to approve, edit, and reject file changes without leaving the chat panel, à la GitHub Copilot Edit.
- **Private marketplace & cowork integration** – Support for privately-hosted extensions in cowork sessions (#28125) is a growing need for internal toolchains.
- **Hook lifecycle completeness** – Hooks for `/branch`, worktree operations, and parent session tracking (#29716, #42656) are missing, limiting advanced workflow automation.
- **Persistent memory/context** – Requests for long-term memory across sessions (#42659) keep surfacing, though the specific ticket was closed as stale.
- **Session history & archival control** – Users want explicit control over transcript retention, including configurable auto-delete policies (#62476).

---

## Developer Pain Points
- **Opaque model behaviour & false policy rejections** – Innocent prompts triggering Usage Policy errors (#60366) undermine trust; developers need clearer explanations and reliable behaviour.
- **Security token management** – The OAuth revocation gap (#43801) proves that logout doesn’t really log you out, a critical concern for enterprises.
- **Platform stability (macOS Desktop)** – Blank screens, launch freezes, and recurring corruption (#50901, #71951, #68316) make the Desktop app unreliable on Apple hardware.
- **Windows gaps** – Cowork windows that don’t open (#71780), broken right-click paste (#66056), extra VS Code windows (#31257), and VSCode extension misbehaviour (#63580) reveal a fragmented Windows experience.
- **Cost display & code review bugs** – Erroneous overage alerts with zero spend (#39678) block code reviews and confuse budget tracking.
- **Silent data loss** – Transcripts automatically deleted after 30 days (#62476) catch developers off guard, erasing valuable debugging context.

---

*Stay up to date: [Claude Code releases](https://github.com/anthropics/claude-code/releases) · [Top issues](https://github.com/anthropics/claude-code/issues?q=is%3Aissue+state%3Aopen+sort%3Acomments-desc)*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest – 2026-07-01

## Today’s Highlights
The end of June brings a new Rust alpha release (`v0.143.0-alpha.31`) alongside lively discussions about **GPT-5.5 token clustering anomalies** (#30364). Several critical regressions in the desktop app—particularly around tool calls, MCP connectivity, and missing UI indicators—are drawing intense attention. On the pull-request side, a flurry of merges introduces durable user-message queuing and tighter WebSocket liveness checks, laying infrastructure for more resilient conversations.

## Releases
- **rust-v0.143.0-alpha.31** – No release notes were provided in the data feed. The version is available as an alpha cut for Rust toolchain users. [Release `0.143.0-alpha.31`](https://github.com/openai/codex/releases/tag/rust-v0.143.0-alpha.31)

## Hot Issues
*Picked for community engagement and impact.*

1.  **[#30224 – “[bug, custom-model, app, config] This model is not supported when using X-OpenAI-Internal-Codex-Responses-Lite.”](https://github.com/openai/codex/issues/30224)** (62 💬, 👍20)  
    **Why it matters:** Users trying to leverage the `Responses-Lite` internal header for custom models hit a hard block, indicating that the experimental fast-path isn’t fully plumbed for all model configs. The high comment volume suggests this is a roadblock for many power users.

2.  **[#30364 – “[bug, model-behavior, rate-limits] GPT-5.5 Codex reasoning-token clustering at 516/1034/1552 may be leading to degraded performance on complex tasks.”](https://github.com/openai/codex/issues/30364)** (25 💬, 👍36)  
    **Why it matters:** A reproducible spike in reasoning output tokens at exact boundaries hints at a batching or quantization artifact in `gpt-5.5`. The community is concerned this could silently compromise reasoning depth on difficult problems. 36 upvotes show strong agreement that this needs investigation.

3.  **[#28969 – “[bug, enhancement, CLI, config, plan] Add setting to disable the auto-resolve in 60 seconds for questions.”](https://github.com/openai/codex/issues/28969)** (6 💬, 👍60)  
    **Why it matters:** CLI users are frustrated by the 60-second auto‑resolve that cuts off thoughtful follow‑ups. Despite relatively few comments, the **60 upvotes** make it the most-requested single tweak this cycle. It’s a clear signal that the default timeout doesn’t suit deep planning workflows.

4.  **[#10665 – “[enhancement, codex-web, azure] Feature Request: Native Azure DevOps (Azure Repos) Integration for Codex.”](https://github.com/openai/codex/issues/10665)** (26 💬, 👍73)  
    **Why it matters:** This long-standing request now has **73 👍** and sustained discussion. Enterprises on Azure DevOps want the same first-class repo experience that GitHub enjoys. The demand highlights Codex’s growing role in non‑GitHub ecosystems.

5.  **[#2680 – “[enhancement, mcp] Support environment variable expansion.”](https://github.com/openai/codex/issues/2680)** (5 💬, 👍21)  
    **Why it matters:** Developers using MCP with secret keys are forced to hardcode secrets into JSON configs. The request for `${ENV_VAR}` expansion mirrors an already-available feature in competing tools. The steady upvotes show this is a security and usability pain point.

6.  **[#29140 – “[bug, extension, tool-calls, skills, app-server] App-server crashes on any tool call (‘thread_tools’ unknown feature key) — sudden onset, no local trigger.”](https://github.com/openai/codex/issues/29140)** (9 💬, 👍0)  
    **Why it matters:** A hard crash in the VS Code extension’s app-server on every tool invocation breaks Codex’s core functionality for users on macOS. The sudden onset without code changes suggests a server-side configuration issue or rollout mishap, triggering emergency-like attention.

7.  **[#30440 – “[bug, sandbox, app] Codex uses bundled pnpm instead of host toolchain.”](https://github.com/openai/codex/issues/30440)** (10 💬, 👍11)  
    **Why it matters:** Sandboxed commands ignore the user’s carefully configured Node ecosystem, breaking builds that rely on host-installed `pnpm` and global packages. The 11 upvotes indicate that the sandbox’s hermetic defaults are chafing against real-world monorepo workflows.

8.  **[#22802 – “[bug, app, remote] Mobile remote setup fails with ‘Secure setup failed’ when connecting to computer.”](https://github.com/openai/codex/issues/22802)** (20 💬, 👍10)  
    **Why it matters:** Mobile remote control is a headline feature, but pairing from iOS/macOS is failing for multiple users. 20 comments show a persistent, unresolved breakage that undermines the “Codex anywhere” promise.

9.  **[#30693 – “[bug, windows-os, context, app] Codex Desktop 26.623 on Windows: context-window usage indicator missing again from composer UI.”](https://github.com/openai/codex/issues/30693)** (3 💬, 👍1)  
    **Why it matters:** The context gauge that helps users manage token budgets vanished again on Windows after a recent update. For power users dependent on that feedback, its absence leads to unexpected context compaction and usage surprises, as echoed in related issue #30689.

10. **[#30348 – “[bug, codex-web, app, connectivity, app-server] Bug Report: Unable to Create New Conversations in Codex Desktop (thread/start Timeout).”](https://github.com/openai/codex/issues/30348)** (2 💬, 👍0)  
    **Why it matters:** Although low on comments, this is a total blocker for Desktop users who can’t start any new thread. Combined with #29376 and #30724 (both MCP‑related connection‑blocking issues), it points to systemic fragility in thread initialization when remote services are unreachable.

## Key PR Progress
*Highlighting merged and in-progress changes that shape the platform.*

1.  **[#28307 (CLOSED) – feat: queue TUI follow‑ups through app‑server](https://github.com/openai/codex/pull/28307)**  
    Sends plain follow‑up messages from the TUI to the app‑server’s durable queue so they survive TUI process restarts. Fundamental for reliable long‑running sessions.

2.  **[#28267 (CLOSED) – feat: dispatch queued user messages through core idle extensions](https://github.com/openai/codex/pull/28267)**  
    Routes the queued messages into the idle turn boundary via a new `QueuedItemService` core extension, ensuring ordered FIFO processing alongside goals.

3.  **[#28265 (CLOSED) – feat: accept user submissions at idle turn boundaries](https://github.com/openai/codex/pull/28265)**  
    Allows queued user messages to enter the idle gate with the same metadata, context, and telemetry as direct submissions. Unblocks end‑to‑end queuing for the TUI and other clients.

4.  **[#28266 (CLOSED) – feat: add durable user message queue storage](https://github.com/openai/codex/pull/28266)**  
    Introduces a dedicated `queue_1.sqlite` database with transactional claim operations so queued messages persist across app‑server restarts and are safely handed off to exactly one worker.

5.  **[#25283 (CLOSED) – feat: synchronize runtime workspace roots in thread settings](https://github.com/openai/codex/pull/25283)**  
    Stores runtime workspace roots in thread settings so queued and direct turns see identical workspace context. Critical for consistent tool resolution in queued scenarios.

6.  **[#28425 (CLOSED) – [codex] Carry fork lineage in initial history](https://github.com/openai/codex/pull/28425)**  
    Explicitly carries fork ancestry through initial history, eliminating fragile fallback plumbing. Improves session resume and fork transparency.

7.  **[#27945 (CLOSED) – Seed session pickers from the state DB](https://github.com/openai/codex/pull/27945)**  
    Uses the indexed State DB for an immediate first page of sessions in resume/fork pickers, making them interactive instantly while the full filesystem scan completes in the background.

8.  **[#28337 (CLOSED) – [code-reviewed] Add gated MCP SEP-2631 file transfer](https://github.com/openai/codex/pull/28337)**  
    Adds disabled‑by‑default support for the draft MCP file‑transfer protocol (`SEP-2631`). A forward‑looking feature gated behind a flag, preparing for upcoming MCP capabilities.

9.  **[#30643 (OPEN) – bound Rendezvous WebSocket liveness](https://github.com/openai/codex/pull/30643)**  
    Enforces a 60‑second Pong requirement on Noise Rendezvous WebSockets and bounds write backpressure. Aims to prevent silent connection stalls in the Codex remote‑execution harness.

10. **[#27932 (CLOSED) – feat(core): let the model change working directory](https://github.com/openai/codex/pull/27932)**  
    Permits the model to switch working directories on request, enabling long‑running tasks to move across checkouts or generated workspaces without being pinned to the starting cwd.

## Feature Request Trends
- **Native Azure DevOps / Azure Repos integration** (#10665, 73 upvotes) – the most prominent ecosystem expansion demand.  
- **Environment variable expansion in MCP configs** (#2680, 21 upvotes) – security and convenience for secret management.  
- **Disable / configure the CLI’s 60‑second auto‑resolve** (#28969, 60 upvotes) – desire for deep‑planning sessions without interruption.  
- **Improved plugin/skill discovery and ownership labeling** (evidenced by PR #26340 and related issues) – users want clear indications of which skills belong to which plugins.  
- **Better sandbox‑to‑host toolchain alignment** (e.g., #30440) – allow the host’s `pnpm`, `npm`, or other tools to be used inside sandboxed commands.  
- **Resilient MCP and remote connection handling** (multiple issues) – users expect that a single failing MCP server shouldn’t block conversation creation; a consistent call for graceful degradation.

## Developer Pain Points
- **MCP connectivity fragility** – Failing or unreachable MCP servers block new conversation creation (`#29376`, `#30348`, `#30724`). Windows stdio MCP handshake failures (`#29247`) and the missing MCP tools in Desktop vs. CLI (`#30343`) compound the experience.  
- **Desktop app stability on Windows** – Recurring crashes when opening Settings (`#30735`), sandbox helper launch failures (`#30732`), and missing context-window indicators (`#30693`) create an unreliable Windows UX.  
- **Tool‑call and app‑server regressions** – Sudden breakage like `#29140` (crashes on any tool call due to an unknown feature key) disrupts development mid‑flow with no clear workaround.  
- **Performance and resource usage** – High GPU consumption while the window is visible (`#26736`) and system‑freeze‑inducing temperature spikes on Windows 11 (`#30055`) point to rendering and compute‑scheduling inefficiencies.  
- **Context‑window / usage transparency** – Unexpectedly high usage consumption (`#30689`) and the disappearing usage indicator (`#30693`) leave users guessing whether their context has been compacted, fuelling frustration with rate‑limit resets (`#30641`).  
- **Sandbox‑host mismatch** – The forced use of a bundled `pnpm` (`#30440`) and Windows sandbox helper path resolution errors (`#30732`) break build scripts that depend on the developer’s own toolchain.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Gemini CLI Community Digest — 2026-07-01**

---

### Today’s Highlights
Stability and agent reliability dominate the conversation as the team ships a new nightly while addressing critical bugs in agent termination signals, shell command hangs, and recursive reasoning. Multiple pull requests tackle deep issues like thought leakage, sandbox escapes, and late tool-call side effects, signalling a strong push toward production hardening.

---

### Releases  
- **[v0.51.0-nightly.20260630.gae0a3aa7b](https://github.com/google-gemini/gemini-cli/releases/tag/v0.51.0-nightly.20260630.gae0a3aa7b)** – Routine nightly build. No version notes beyond the changelog diff.  
  **Full Changelog**: [compare v0.51.0-nightly.20260629…v0.51.0-nightly.20260630](https://github.com/google-gemini/gemini-cli/compare/v0.51.0-nightly.20260629.gae0a3aa7b...v0.51.0-nightly.20260630.gae0a3aa7b)

---

### Hot Issues  
1. **[#22323 Subagent recovery after MAX_TURNS is reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)**  
   *P1 bug – 8 comments, 2 👍*  
   The `codebase_investigator` subagent claims success and GOAL termination even when it hit the turn limit without performing analysis. This misreporting poisons agent orchestration and hides genuine failures.

2. **[#21409 Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)**  
   *P1 bug – 7 comments, 8 👍*  
   A highly‑upvoted pain: whenever Gemini defers to the generalist subagent it hangs indefinitely. Simple operations (e.g., folder creation) freeze until the user forces the model to avoid subagents. Community frustration is palpable.

3. **[#25166 Shell command execution gets stuck with “Waiting input”](https://github.com/google-gemini/gemini-cli/issues/25166)**  
   *P1 bug – 4 comments, 3 👍*  
   Even after a shell command completes, the UI remains in “Awaiting user input” state. This blocking behaviour breaks workflows and erodes trust in autonomous task completion.

4. **[#21968 Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)**  
   *P2 bug – 6 comments, 0 👍*  
   Users report that custom skills (e.g., `gradle`, `git`) and subagents are rarely triggered automatically. The model must be explicitly instructed, limiting the value of the extensibility model.

5. **[#26525 Add deterministic redaction and reduce Auto Memory logging](https://github.com/google-gemini/gemini-cli/issues/26525)**  
   *P2 security – 5 comments, 0 👍*  
   Auto Memory reads local transcripts and sends them to the model before secrets are redacted. Secrets end up in the extraction model’s context and possibly in logging, posing a data‑leak risk.

6. **[#26522 Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)**  
   *P2 bug – 5 comments, 0 👍*  
   Sessions that the extractor deems low-signal are never marked processed, causing the same sessions to be repeatedly picked up. This wastes API credits and local resources.

7. **[#22672 Agent should stop/discourage destructive behavior](https://github.com/google-gemini/gemini-cli/issues/22672)**  
   *P2 feature/customer‑issue – 3 comments, 1 👍*  
   The model occasionally uses `git reset --force` or similar destructive commands when safer alternatives exist. Users want guardrails, especially when managing databases and git history.

8. **[#21983 browser subagent fails in wayland](https://github.com/google-gemini/gemini-cli/issues/21983)**  
   *P1 bug – 4 comments, 1 👍*  
   On Wayland Linux, the browser agent terminates immediately with GOAL but does nothing. This breaks cross‑platform usability for a growing user segment.

9. **[#24246 Gemini CLI encounters 400 error with > 128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)**  
   *P2 bug – 3 comments, 0 👍*  
   When the tool registry grows beyond 128 entries, the agent receives a 400 error from the API. A smarter tool‑scoping mechanism is needed.

10. **[#22267 Browser Agent ignores settings.json overrides](https://github.com/google-gemini/gemini-cli/issues/22267)**  
    *P2 bug – 3 comments, 0 👍*  
    Overrides like `maxTurns` in `settings.json` are ignored by the Browser Agent. This silently breaks user configuration and makes session behaviour unpredictable.

---

### Key PR Progress  
1. **[#28164 fix(core): limit recursive reasoning turns per single user request](https://github.com/google-gemini/gemini-cli/pull/28164)**  
   Implements a 15‑turn cap (configurable via `maxSessionTurns`) for recursive reasoning loops, protecting CPU and API quotas.

2. **[#27971 fix(core): strip thoughts from scrubbed history turns and resolve thought leakage](https://github.com/google-gemini/gemini-cli/pull/27971)**  
   Surgically removes leaked internal monologues from history that were confusing subsequent turns and causing infinite loops.

3. **[#28096 fix(core): drop late tool calls after SIGINT cancellation](https://github.com/google-gemini/gemini-cli/pull/28096)**  
   Prevents side‑effect tool calls that arrive after user‑cancel, closing a gap where cancelled operations still executed local changes.

4. **[#28215 Harden file-write scope: stop sandbox/auto-accept writes to .gemini and .gitconfig](https://github.com/google-gemini/gemini-cli/pull/28215)** (closed)  
   Blocks the agent from modifying its own configuration files and global git config, closing a sandbox‑escape vector under prompt injection. Critical security improvement.

5. **[#28089 feat(core): implement MCP elicitation (form + url) capability](https://github.com/google-gemini/gemini-cli/pull/28089)**  
   Implements MCP elicitation per the 2025‑11‑25 spec, enabling `form` and `url` modes in MCP clients. Unlocks richer interactive patterns with MCP servers.

6. **[#28219 fix(cli): parse commented settings.json in memory bootstrap](https://github.com/google-gemini/gemini-cli/pull/28219)**  
   Fixes the lightweight parent process so it can read `settings.json` with comments without falling back to default memory configuration.

7. **[#28099 fix(cli): show descriptive sandbox label in footer](https://github.com/google-gemini/gemini-cli/pull/28099)**  
   On macOS, the footer now shows the seatbelt profile name instead of a generic “current process” label, improving transparency.

8. **[#27936 fix(vscode-ide-companion): add missing activate() Disposables](https://github.com/google-gemini/gemini-cli/pull/27936)** (closed)  
   Corrects a comma‑operator bug in the VS Code extension that caused disposable registrations to leak. Restores proper cleanup.

9. **[#28126 fix(core-tools): show ellipsis on multi-line edit snippets](https://github.com/google-gemini/gemini-cli/pull/28126)**  
   The edit tool’s description now appends `...` when content is truncated, making it clear when a diff snippet is incomplete.

10. **[#28100 fix(vscode-ide-companion): register Disposables leaked by comma operators](https://github.com/google-gemini/gemini-cli/pull/28100)**  
    Another fix for the same `(A, B)` comma‑operator pattern in the VS Code extension, ensuring both Disposables are registered. Complement to PR #27936.

---

### Feature Request Trends  
- **AST‑aware tooling**: Investigations into AST‑based file reads, search, and codebase mapping are tracked across multiple issues (e.g., #22745, #22746, #22747). The goal is to improve agent accuracy and reduce turn count.  
- **Better subagent & skill adoption**: Users want the model to proactively use skills and subagents without explicit prompting (#21968), and to surface subagent trajectories for debugging (#22598).  
- **Evaluations and QA infrastructure**: There is a push for robust component‑level evals (#24353), stabilized internal benchmarks (#23166), and always‑passing steering tests (#23313).  
- **Auto Memory security and efficiency**: Requests to add deterministic redaction (#26525), avoid infinite retries (#26522), and surface invalid inbox patches (#26523) indicate a maturing memory subsystem.  
- **Agent safety**: Proposals to discourage destructive commands (#22672) and prevent config overwrites (PR #28215) show a growing demand for built‑in guardrails.

---

### Developer Pain Points  
- **Agent hangs and perpetual waits**: Generalist subagent freezes (#21409), shell commands stuck at “Waiting input” (#25166), and interactive‑prompt deadlocks (#22465) are top reliability complaints.  
- **Misleading termination signals**: Subagent “success” despite turn‑limit exhaustion (#22323) and crashes during output hooks (#22186) make it hard to trust campaign completion.  
- **Configuration ignored**: Settings overrides silently dropped (Browser Agent #22267, subagent activation #22093) undermine user control.  
- **Terminal UI glitches**: Flicker on resize (#21924) and corruption after external editors (#24935) degrade the interactive experience.  
- **Model loses context or loops**: Thought leakage (PR #27971) and recursive reasoning without bounds (PR #28164) are active areas of repair, hinting at past struggles with model stability.  
- **Workspace pollution**: The model scatters temporary scripts across random directories (#23571), complicating clean commits and workspace hygiene.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI Community Digest — July 1, 2026**

### 1. Today’s Highlights
The v1.0.66 release ships with Claude Opus 4.8 Fast, MCP header improvements, and a cursor behavior fix, while retiring Opus 4.6 Fast. The community’s loudest requests remain project‑scoped plugins (17 👍) and fully custom, shareable terminal themes (20 👍), both of which saw renewed discussion in the last 24 hours.

### 2. Releases
**v1.0.66** (2026-06-30)  
- Use a non‑blinking block cursor during interactive sessions; restores the terminal’s default cursor on exit.  
- Add support for Claude Opus 4.8 Fast and deprecate Claude Opus 4.6 Fast.  
- MCP `add`/`edit` form now accepts HTTP‑style `Key: value` headers.  
- Prevent LSP servers from starting twice during session initialisation.

### 3. Hot Issues
1. **#1665 – Plugins scoped to project/repository** [CLOSED]  
   [link](https://github.com/github/copilot-cli/issues/1665) • 17 👍, 10 comments  
   Request for repo‑level plugin loading so teams can use tooling without cluttering global installs. Closed today after sustained interest.

2. **#1504 – Custom theme support** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/1504) • 20 👍, 4 comments  
   Users want to create and share custom themes (e.g., via JSON), going beyond the built‑in palette.

3. **#3727 – Regression: `userPromptSubmitted` hook `additionalContext` not injected** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3727) • 0 👍, 6 comments  
   Between v1.0.59 and v1.0.60 the plugin hook stopped passing extra context to the planner, breaking prompt‑enrichment workflows.

4. **#3874 – `preToolUse` hook denial does not work** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3874) • 0 👍, 2 comments  
   A hook meant to block tool execution is ignored, undermining agent guardrails.

5. **#3954 – `explore` tool hardcodes model to `gpt-5.4-mini`, ignoring custom/BYOK config** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3954) • 0 👍, 0 comments  
   Breaking change for users with custom model endpoints; the exploration tool disregards the configured model.

6. **#3976 – Native `tgrep` indexer OOM‑kills host on large monorepos** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3976) • 0 👍, 0 comments  
   The Rust trigram index daemon lacks a memory cap and can consume all available RAM, crashing the system.

7. **#3977 – Persist autopilot mode across interactive turns** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3977) • 0 👍, 0 comments  
   Request for a flag/setting to keep `--autopilot` active beyond the first task, rather than falling back to interactive mode.

8. **#3979 – Extension API to render a live panel in the terminal** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3979) • 0 👍, 0 comments  
   Extension authors want a progress dashboard or sub‑agent status panel beyond the current `session.log` text stream.

9. **#3980 – Esc‑cancel during blocking `read_agent` kills the background agent** [OPEN]  
   [link](https://github.com/github/copilot-cli/issues/3980) • 0 👍, 0 comments  
   Cancelling a wait on a background agent terminates the agent itself, leaving it unrecoverable.

10. **#3973 – MCP OAuth re‑auth repeatedly fails on Windows with excluded loopback port** [OPEN]  
    [link](https://github.com/github/copilot-cli/issues/3973) • 0 👍, 0 comments  
    When Windows excludes the cached redirect port, re‑authentication loops until the cached registration is manually deleted.

### 4. Key PR Progress
Only one PR was updated in the last 24 hours:  
- **#2587 – Add automated issue classification with GitHub Agentic Workflows** [CLOSED]  
  [link](https://github.com/github/copilot-cli/pull/2587)  
  Introduces an AI‑powered workflow (`gh-aw`) that automatically applies `area:` labels and the `triage` label to opened/reopened issues, improving issue management.

### 5. Feature Request Trends
- **Repository/project‑scoped plugins** (#1665) – teams want per‑repo tooling without global side effects.  
- **Rich terminal customisation** (#1504, #3979) – demand for custom themes, shareable colour schemes, and extension‑driven live UI panels.  
- **Persistent agent modes** (#3977) – users want autopilot to survive across multiple turns, plus desktop notifications (#2941) when a background agent needs input.  
- **BYOK and model flexibility** (related: #3911, #3978, #3954) – reliable switching between built‑in and custom models, and consistent model selection across all sub‑tools.

### 6. Developer Pain Points
- **Hook instability** – regressions that silently break plugin hooks (#3727, #3874) erode trust in the extension model.  
- **Model switching & BYOK bugs** – switching models often reverts or fails (#510, #3911, #3978); tools like `explore` ignore custom endpoints (#3954).  
- **Windows‑specific friction** – clipboard stops working while CLI is running (#3981), git symlinks prevent plugin install (#2286), and MCP OAuth re‑auth loops (#3973).  
- **Resource overconsumption** – the native `tgrep` indexer can OOM large repos (#3976); LSP servers were starting twice (fixed in v1.0.66).  
- **Regressions in core UX** – drag‑and‑drop file attach no longer works on macOS (#3955), and mouse‑movement garbage appears in the UI (#3972).  
- **Networking gaps** – `web_fetch` tool fails with `TypeError: fetch failed` despite working login (#3948).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest – 2026-07-01

## Today’s Highlights
A new bug report reveals that the “Approve for this session” feature is broken in v0.20.1, potentially undermining the trust-based interactive workflow. Meanwhile, a long‑running UI improvement PR is ready for review, and a closed PR adds support for passing an initial prompt while keeping the shell session alive.

## Releases
No new releases in the last 24 hours.

## Hot Issues
* **[#2480](https://github.com/MoonshotAI/kimi-cli/issues/2480) – `[bug] Approve for this session doesn't work`**  
  Author: Econ01 | 0 comments | 0 👍  
  On Kimi Code CLI v0.20.1 (OAuth, K2.7 Code, macOS arm64), the session‑level approval command is not being respected. This disrupts workflows that rely on granting temporary trust without per‑command confirmations. No community reaction yet, but the issue is critical for interactive security models.

## Key PR Progress
* **[#1600](https://github.com/MoonshotAI/kimi-cli/pull/1600) – `feat(shell): highlight user input with bright blue and separator for better visibility`** (OPEN)  
  By liuchong. Enhances the shell UI by rendering user‑echoed text in bright blue (`#007AFF`) and adding a full‑width separator line after each input, improving visual distinction between user and assistant messages. A long‑running PR originally opened in March, now seeing renewed activity.

* **[#2246](https://github.com/MoonshotAI/kimi-cli/pull/2246) – `feat(shell): add --prompt-interactive option`** (CLOSED)  
  By shuizhongyueming. Resolves [#2240](https://github.com/MoonshotAI/kimi-cli/issues/2240). Introduces `--prompt-interactive` (`-P`) to start the shell with an initial prompt and then remain open for follow‑up questions, combining one‑shot convenience with interactive continuity. This PR was merged/closed, likely landing in a future release.

## Feature Request Trends
Based on recent activity, the community is pushing for **more fluid interactive experiences**:
- **Start‑with‑prompt workflows**: The closed PR [#2246](https://github.com/MoonshotAI/kimi-cli/pull/2246) directly addresses the demand to pass an initial prompt and stay in the shell (see [#2240](https://github.com/MoonshotAI/kimi-cli/issues/2240)).
- **Shell UI refinements**: Open PR [#1600](https://github.com/MoonshotAI/kimi-cli/pull/1600) suggests a desire for clearer visual separation between user input and AI output, pointing toward a broader interest in terminal UX polish.

## Developer Pain Points
- **Session‑level trust broken**: Bug [#2480](https://github.com/MoonshotAI/kimi-cli/issues/2480) indicates that the “Approve for this session” mechanism is unreliable, forcing developers to either approve every command individually or disable safeguards entirely—a significant friction in automated workflows.
- **Hard‑to‑distinguish user input**: The long‑standing PR [#1600](https://github.com/MoonshotAI/kimi-cli/pull/1600) reflects a common complaint that the shell interface does not adequately differentiate user‑typed text from other output, causing confusion during fast‑paced interactions.
- **Missing interactive‑prompt entry**: Before [#2246](https://github.com/MoonshotAI/kimi-cli/pull/2246), users had to choose between a one‑shot prompt and a fully manual shell; the merged PR addresses this gap, showing it was a recurring need.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-01

## Today’s Highlights
No new releases shipped, but the community was buzzing around a long-running socket connection error (#1692) that continues to affect users even after being closed. Meanwhile, the most-upvoted feature request is native model fallback / failover (#7602) and there’s fresh momentum behind interactive steering (#19205) as newer models support it. Core V2 refactoring delivered multiple internal clean-up PRs, and a new `opencode mcp` CLI landed for managing MCP servers.

## Hot Issues

1. **[#7602 Native Model Fallback / Failover Support](https://github.com/anomalyco/opencode/issues/7602)**  
   The community’s top request (90 👍) asks for automatic retry with a different model when the primary fails or rate-limits. Currently only same-model fallback exists; this missing capability breaks long-running agent tasks. High comment activity signals strong demand from teams building production pipelines.

2. **[#19205 Support Interactive Steering](https://github.com/anomalyco/opencode/issues/19205)**  
   With GPT‑5.4 now supporting interactive steering, users want OpenCode to expose the same ability—send a message during a running task to guide the agent. Gained 23 👍 quickly, reflecting excitement about this new control paradigm.

3. **[#1692 Socket connection closed unexpectedly](https://github.com/anomalyco/opencode/issues/1692)**  
   A closed but still frequently-referenced issue (35 comments, 19 👍) about the `fetch()` socket error. Many users still encounter it, suggesting the underlying race condition or TLS handling isn’t fully resolved in all environments.

4. **[#34215 Desktop app extremely slow/hangs due to massive `opencode.global.dat`](https://github.com/anomalyco/opencode/issues/34215)**  
   Base64-encoded PDFs in prompt history bloated the global state file to 179 MB+, causing minutes-long freezes at startup and 4GB GPU memory usage. Five 👍 highlight that performance degradation from attachment storage is a real pain.

5. **[#34614 `small_model` tasks should be configurable, not hardcoded](https://github.com/anomalyco/opencode/issues/34614)**  
   Right now only `title` and `summary` tasks use the local small model. Developers want to route cheap operations (commit messages, linting, code search) to a local model without rewriting internals. A request for external configurability.

6. **[#24795 Allow editing the “always” permission pattern before confirming](https://github.com/anomalyco/opencode/issues/24795)**  
   When granting permanent permissions, the auto-generated pattern sometimes is too broad. Users would like to edit the pattern inline before confirming—a small UX improvement that resonates (3 👍, 3 comments).

7. **[#34640 MCP tool optional array fields materialized as empty arrays](https://github.com/anomalyco/opencode/issues/34640)**  
   OpenCode sends `[]` for omitted optional MCP array arguments, triggering mutually-exclusive validation on the server side. This breaks tool calls where optional arrays shouldn’t be present at all. An interoperability bug for MCP users.

8. **[#34652 SchemaError when Anthropic provider returns nested array as JSON string](https://github.com/anomalyco/opencode/issues/34652)**  
   Claude’s native tool calls sometimes return a nested array as a JSON-encoded string instead of a real array, causing `todowrite` and similar tools to fail validation. The issue points to a missing coercion step in the Anthropic adapter.

9. **[#34644 GitHub Copilot provider not registered for Student plan](https://github.com/anomalyco/opencode/issues/34644)**  
   Students on the Copilot plan can’t use the provider after authenticating—it simply doesn’t appear. This blocks educational users who rely on the free student subscription.

10. **[#33473 Opencode Go / Deepseek V4 flash – 25% usage consumed with no cache hits](https://github.com/anomalyco/opencode/issues/33473)**  
    After an upgrade to 1.17.8, a user saw a quarter of their monthly quota disappear in one day, apparently because caching wasn’t working. A billing/usage bug that worries paying subscribers.

## Key PR Progress

1. **[#34654 fix(auth): validate OPENCODE_AUTH_CONTENT against Auth.Info schema](https://github.com/anomalyco/opencode/pull/34654)**  
   The env‑var path for `OPENCODE_AUTH_CONTENT` now runs through schema validation, closing #34075. This prevents malformed auth payloads from being injected via environment variables.

2. **[#26861 fix(tui): Old messages disappearing during long sessions](https://github.com/anomalyco/opencode/pull/26861)**  
   Adds lazy‑scroll loading in the TUI so older messages don’t vanish. Scrolling up fetches the next 50 messages, addressing a long-standing bug (#7380) that frustrated CLI users.

3. **[#34625 refactor(core): remove domain layer exports](https://github.com/anomalyco/opencode/pull/34625)**  
   Part of a stacked V2 cleanup: hides core domain implementation layers and removes default layer exports, leaving only approved exception factories. This pushes toward a cleaner public API for 2.0.

4. **[#34254 fix(app): scope session page errors](https://github.com/anomalyco/opencode/pull/34254)**  
   Adds an ErrorBoundary inside the session page so that session‑load failures no longer crash the entire tab shell. Route resolution now lives inside the session panel frame, improving desktop app resilience.

5. **[#34651 fix(desktop): clean stale draft stores](https://github.com/anomalyco/opencode/pull/34651)**  
   Removes empty scoped store files on startup and prunes stale/capped drafts while preserving non‑empty workspace stores. Includes unit tests for cleanup—a direct response to storage bloat issues.

6. **[#34643 feat(cli): add mcp list, add, auth, and logout commands](https://github.com/anomalyco/opencode/pull/34643)**  
   New `opencode mcp` subcommands let users manage MCP servers from the command line: list configured servers, add local/remote servers, and handle OAuth authentication. Brings MCP management to the V2 CLI.

7. **[#33017 feat(app): edit files directly in the app](https://github.com/anomalyco/opencode/pull/33017)**  
   A long‑desired feature: files opened in the desktop app can now be edited directly (with save and auto‑save), rather than being read‑only. This reduces the “ask the AI to do it” friction for small tweaks.

8. **[#34531 feat(core): support mcp prompts](https://github.com/anomalyco/opencode/pull/34531)**  
   Exposes MCP prompt definitions and `getPrompt` through the core MCP wrapper, allowing servers to provide reusable prompt templates. Sorted stably across connected servers.

9. **[#17080 fix(cli): show multi-file apply_patch diffs](https://github.com/anomalyco/opencode/pull/17080)**  
   The CLI permission view now shows per‑file diffs when a patch affects multiple files, closing #17076. A significant quality‑of‑life improvement for patch‑based approval workflows.

10. **[#34646 fix(app): keep live sessions during list refresh](https://github.com/anomalyco/opencode/pull/34646)**  
    Prevents stale session‑list responses from dropping sessions created while a refresh request was in flight. Keeps totals at least as large as the locally retained root list, with regression coverage.

## Feature Request Trends
- **Model fallback / failover** — overwhelmingly the most‑voted request; teams want automatic retry with an alternative model when the primary fails or hits rate limits.  
- **Interactive steering** — with next‑gen models supporting steerable generation, users want OpenCode to expose the ability to send mid‑task guidance (e.g., “pause and switch to approach B”).  
- **Configurable small‑model routing** — developers ask to move more cheap tasks (commit messages, linting, search) to local models via configuration rather than hardcoded system agents.  
- **Permission UX refinement** — editing the “always allow” pattern before confirmation is a small but frequent ask, reflecting deeper desire for more granular permission control.  
- **Whole‑word selection in TUI** — while minor, double‑click word selection is a native‑feel expectation that keeps popping up.

## Developer Pain Points
- **Connectivity & error resilience**: recurring socket connection errors (#1692) and `ResourceExhausted` worker‑limit hits (#34613) indicate that the retry/recovery logic still has gaps, especially in long‑running sessions.  
- **Desktop performance with attachments**: large base64‑encoded attachments (PDFs) can bloat global state to hundreds of megabytes, causing extreme startup lag and memory spikes (#34215).  
- **MCP argument coercion bugs**: omitted optional arrays get sent as empty `[]` (#34640), and Anthropic’s provider sometimes returns nested arrays as JSON strings (#34652) — both break tool calls and force workarounds.  
- **Session monitoring determinism**: users building on the SDK struggle to know when a session has actually completed, not just become idle (#3815).  
- **Input regressions**: HOME/END keys stop working after the first message in the TUI (#32053), breaking cursor navigation for CLI‑first users.  
- **Billing and usage visibility**: sudden cache‑hit drops (#33473) can consume large portions of paid quotas without warning, leaving subscribers uneasy about cost controls.  
- **Copilot for Students**: the GitHub Copilot provider is invisible after authentication for Student plan users (#34644), blocking a free access route that many expected to work.

*Digest curated from the [opencode repository](https://github.com/anomalyco/opencode). For full details, follow the linked issues and pull requests.*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

**Pi Community Digest – July 1, 2026**

---

### 1. Today’s Highlights
The community closed a long‑standing UI complaint where the streaming markdown output forcibly scrolled to the bottom (42 comments), and a fix for the ECONNRESET process crash was addressed. Several pull requests landed that introduce configurable chat padding, TUI redo support, and the heavily‑requested `excludeFromContext` flag for extension‑sent messages, marking a productive day for both usability and extensibility.

---

### 2. Releases
No new releases in the last 24 hours.

---

### 3. Hot Issues
1. **[#5825 – Streaming markdown forces scroll to bottom](https://github.com/earendil-works/pi/issues/5825)**  
   When `clear on shrink` was enabled, Pi would prematurely jump back to the bottom as the model streamed its answer. Intense discussion (42 comments) lead to a close, confirming it was a full‑re‑render side‑effect.

2. **[#5463 – Auto‑compaction after final turn throws error](https://github.com/earendil-works/pi/issues/5463)**  
   The coding agent crashes with `Cannot continue from message role: assistant` after a normal turn. The bug, upvoted by 5 users, highlights fragility in the agent’s queue draining logic; remains open.

3. **[#5654 – Add `excludeFromContext` to custom messages via `sendMessage()`](https://github.com/earendil-works/pi/issues/5654)**  
   Extension developers want a flag to keep custom messages in the UI but out of the LLM’s context, mirroring the existing bash‑execution behaviour. 8 comments and a companion PR attest to strong interest.

4. **[#1837 – Feature Request: temperature, top_p, and other generation parameters](https://github.com/earendil-works/pi/issues/1837)**  
   A long‑standing power‑user ask (6 thumbs‑up) to let users tune temperature, top_p, etc., beyond per‑provider workarounds. The conversation continues about whether this should be a built‑in setting.

5. **[#6019 – OpenAI Responses mid‑stream retryable error is not retried](https://github.com/earendil-works/pi/issues/6019)**  
   When OpenAI’s API sends a recoverable error mid‑stream, Pi finalises the message with `stopReason: "error"` instead of retrying. This undermines session reliability, and the issue (closed) clarifies the expected behaviour.

6. **[#6103 – Empty tool results mislabeled as “(see attached image)”](https://github.com/earendil-works/pi/issues/6103)**  
   A latent core bug causes empty tool‑call outputs to display an image hint, exposed by extensions like `pi-hashline-edit-pro`. Three commenters confirmed the confusing UX.

7. **[#6133 – Pi crashes with ECONNRESET during streaming](https://github.com/earendil-works/pi/issues/6133)**  
   A TCP reset from the provider escaped the streaming try/catch and killed the process as an uncaught exception. Closed after attention to undici’s error propagation, fixing a critical stability problem.

8. **[#6151 – Support `image_url` content type (pass URL directly without base64)](https://github.com/earendil-works/pi/issues/6151)**  
   Currently all images are converted to base64 data URIs, wasting tokens and CPU. The request asks for a direct URL path, with developers citing latency and cost benefits.

9. **[#6162 – Extension tool changes not reflected before next provider request](https://github.com/earendil-works/pi/issues/6162)**  
   When an extension calls `pi.setActiveTools()` during a tool execution, the same run didn’t use the updated tool set until the next turn. This state‑refresh gap was quickly addressed with a matching PR.

10. **[#5901 – Contribution Proposal: Durable HITL tool‑call interrupts](https://github.com/earendil-works/pi/issues/5901)**  
    A proposal to add persistent human‑in‑the‑loop approval for tool calls, inspired by LangChain middleware. While closed as `no‑action`, the discussion points to growing demand for enterprise‑grade guardrails.

---

### 4. Key PR Progress
1. **[PR #5678 – Add `excludeFromContext` for custom messages](https://github.com/earendil-works/pi/pull/5678)**  
   Implements the flag across agent harness and extensions, ensuring compaction and branching respect excluded messages. Still under discussion but highly anticipated.

2. **[PR #6176 – Apply extension tool changes before the next provider request in the same run](https://github.com/earendil-works/pi/pull/6176)**  
   Directly fixes issue #6162 by refreshing session runtime state between tool executions, so dynamic tool registration takes effect immediately.

3. **[PR #6115 – Add configurable chat padding](https://github.com/earendil-works/pi/pull/6115)**  
   A long‑discussed topic: offering control over padding around messages in the TUI. Closed with the note that a more holistic flag system may be needed, but the patch paves the way.

4. **[PR #6169 – Disable padding for assistant messages](https://github.com/earendil-works/pi/pull/6169)**  
   A lighter alternative that removes surrounding blank lines for assistant messages only, providing a cleaner conversation view. Closed and linked to report #6168.

5. **[PR #6182 – Add redo support to editors](https://github.com/earendil-works/pi/pull/6182)**  
   Implements the missing redo operation in the TUI’s input and editor components, a frequently requested complement to the existing undo.

6. **[PR #6175 – Emit session name changes to extensions](https://github.com/earendil-works/pi/pull/6175)**  
   Notifies extensions when a session is renamed, enabling reactive UI or logging plugins. Closed after a working demo.

7. **[PR #5832 – Surface provider HTTP error body instead of opaque SDK message](https://github.com/earendil-works/pi/pull/5832)**  
   Previously, proxy 403 errors were lost, showing `UnknownError` or `(no body)`. This fix propagates the real HTTP body, vastly improving debugging behind gateways.

8. **[PR #6178 – Guard against undefined content in tool result messages](https://github.com/earendil-works/pi/pull/6178)**  
   Extensions returning empty results (like `get_kline`) could trigger an undefined content exception; the fix ensures graceful fallback.

9. **[PR #6170 – Avoid replaying historical inline images](https://github.com/earendil-works/pi/pull/6170)**  
   Stops re‑rendering terminal image escapes when rebuilding past context, substituting lightweight `[Image: ...]` labels and saving memory bandwidth.

10. **[PR #6184 – Add launch.json for development](https://github.com/earendil-works/pi/pull/6184)**  
    Trivial chore that commits a VS Code debug configuration, making it easier for new contributors to run and debug Pi locally.

---

### 5. Feature Request Trends
- **Extension developer ergonomics** – `excludeFromContext` (#5654), session name change events (#6175), and immediate tool state refresh (#6162) all aim to give extension authors finer control over context and session lifecycle.
- **Model parameter control** – Power users continue to ask for temperature, top_p and other generation knobs (#1837), suggesting a growing desire for built‑in tuning rather than custom providers.
- **Multimodal improvements** – The demand for direct image URLs without base64 re‑encoding (#6151) and fixing base64 corruption with certain providers (#6164) shows that developers want more efficient and robust image handling.
- **Session management shortcuts** – Requests like combined `/new` + `/name` (#6046) and durable HITL tool interruptions (#5901) reflect a push for more streamlined session workflows and enterprise control.
- **Accessibility** – Issue #4687’s screen‑reader noise complaint highlights that inclusive TUI design is becoming a recurring theme, though the effort needed is significant.

---

### 6. Developer Pain Points
- **Streaming UI glitches** – The forced scroll‑to‑bottom (#5825) and process‑killing ECONNRESET (#6133) illustrate a fragile streaming layer that still surprises users and breaks sessions.
- **Agent state management bugs** – Auto‑compaction errors (#5463) and stale tool registrations (#6162) indicate edge cases in the agent’s turn lifecycle that break long‑running coding sessions.
- **Opaque error messages** – When providers return errors, the message is often lost (PR #5832 finally addresses 403 bodies), leaving developers to guess the cause when working with proxies or custom endpoints.
- **TUI noise and accessibility** – ASCII‑art borders and dynamic decorations confuse screen readers (#4687), and the discussion about padding (#6115, #6169) shows that the default visual density isn’t ideal for all users.
- **Missing built‑in redo** – Despite having undo for a while, the lack of a complementary redo (#6183) frustrated TUI‑heavy users until PR #6182 filled the gap.
- **Provider pricing mismatches** – Inaccurate hardcoded data for Xiaomi MiMo models (#6138) can break cost estimations, a reminder that provider‑specific configuration needs constant maintenance.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

## Qwen Code Community Digest — 2026-07-01

### Today's Highlights
The daemon and subagent safety continue to dominate activity, with a critical P1 follow-up for ACP loop detection and parallel PRs to lock down plan‑mode tools inside subagents. A new nightly release landed infrastructure tweaks, and the channel‑based collaboration features are maturing rapidly, with loop support, group history backfill, and daemon‑managed channel workers all in review.

### Releases
**[v0.19.3-nightly.20260630.e00fe6a27](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.3-nightly.20260630.e00fe6a27)**  
A documentation refresh for the daemon docs and an initial implementation of a configurable auto‑* feature (details cut off).

### Hot Issues
1. **#6084 [OPEN] Follow up ACP daemon loop detection review fixes**  
   *Priority P1 bug* – The merged loop guard can still miss stop‑hook continuations and repeated invalid tool calls. This is the top stability concern; fixing it blocks the daemon from hanging indefinitely.  
   [QwenLM/qwen-code#6084](https://github.com/QwenLM/qwen-code/issues/6084)

2. **#6083 [OPEN] Restrict plan mode tools in ordinary subagents**  
   *Priority P2 feature request* – Subagents shouldn’t receive `enter_plan_mode` / `exit_plan_mode`; plan ownership must stay with the parent session. Safety and UX depend on this isolation.  
   [QwenLM/qwen-code#6083](https://github.com/QwenLM/qwen-code/issues/6083)

3. **#6086 [OPEN] Advertise vision-bridge as `_meta.imageCapability` on ACP initialize**  
   *Integration feature request* – Enables ACP hosts (like sudowork) to discover that Qwen Code’s vision bridge can handle images transparently, simplifying multi‑backend image pipelines.  
   [QwenLM/qwen-code#6086](https://github.com/QwenLM/qwen-code/issues/6086)

4. **#6075 [CLOSED] ACP daemon can loop indefinitely on repeated invalid tool parameters**  
   *Priority P1 bug (resolved)* – A model repeatedly calling `ask_user_question` with a malformed string instead of an array could lock the daemon in a loop. The fix (merged yesterday) is now being tightened by #6084.  
   [QwenLM/qwen-code#6075](https://github.com/QwenLM/qwen-code/issues/6075)

5. **#6030 [CLOSED] Windows‑style tilde paths resolve under the current directory**  
   *Bug, P3 (resolved)* – `~\docs` with backslashes was treated as a literal relative path on Windows, breaking home‑directory shortcuts. A classic path‑normalisation pain.  
   [QwenLM/qwen-code#6030](https://github.com/QwenLM/qwen-code/issues/6030)

6. **#6000 [CLOSED] Mobile sidebar with session list and responsive UX improvements**  
   *Feature request, P3 (resolved)* – The web shell hid the session sidebar on small screens; now a mobile‑friendly alternative and responsive polish land in the main branch.  
   [QwenLM/qwen-code#6000](https://github.com/QwenLM/qwen-code/issues/6000)

### Key PR Progress
1. **Restrict plan mode tools in ordinary subagents**  
   [#6087](https://github.com/QwenLM/qwen-code/pull/6087), [#6088](https://github.com/QwenLM/qwen-code/pull/6088) – Two implementations that prevent subagents from entering/exiting plan mode. The parent session retains ownership; subagents inherit plan constraints but cannot change the mode. Critical for predictable plan‑mode workflows.

2. **ACP daemon loop review follow‑ups**  
   [#6085](https://github.com/QwenLM/qwen-code/pull/6085) – Lands the missing stop‑hook cases and a stable invalid‑tool bucket so error text changes can’t evade the 3‑strike limit. Makes loop detection a terminal turn path that preserves final context.

3. **Channel loop support**  
   [#6073](https://github.com/QwenLM/qwen-code/pull/6073) – `/loop add`, `/loop list`, `/loop cancel` now work inside channel group chats, with persisted lifecycle state and execution through the existing channel session pipeline.

4. **Daemon‑managed channel worker for `serve --channel`**  
   [#6031](https://github.com/QwenLM/qwen-code/pull/6031) – Implements the backend readiness step for channel serving: the daemon spawns an out‑of‑process channel worker, connects it back to the server, and keeps it alive. Foundation for repeatable `--channel` flags.

5. **Session archive support**  
   [#6058](https://github.com/QwenLM/qwen-code/pull/6058) – Moves sessions between `chats/` and `chats/archive/`, exposes active‑vs‑archived listings, and prevents loading archived sessions. Gives users a first‑class way to tidy their session list.

6. **Sessionless workspace remember**  
   [#5884](https://github.com/QwenLM/qwen-code/pull/5884) – A hidden daemon‑managed task that enqueues a memory remember call without creating or restoring a user‑visible session, ideal for background workspace context injection.

7. **Compact session timeline rail**  
   [#6078](https://github.com/QwenLM/qwen-code/pull/6078) – Web shell gets a minimal left‑gutter rail with expandable turn detail cards, keeping a full‑history overview accessible without taking over the message view.

8. **Group history backfill for channels**  
   [#6074](https://github.com/QwenLM/qwen-code/pull/6074) – Missed group messages (bot not mentioned) can be persisted locally and injected as bounded untrusted context on the next real mention, improving contextual replies in busy channels.

9. **Fix Windows permission persistence due to path case‑sensitivity**  
   [#2670](https://github.com/QwenLM/qwen-code/pull/2670) – Long‑standing community PR (open since March) that finally fixes “Always allow” not sticking across sessions on Windows by normalising path comparisons to be case‑insensitive.

10. **Resolve ACP permission votes across connections**  
    [#5912](https://github.com/QwenLM/qwen-code/pull/5912) – Permission responses from one connection are no longer invisible to others, making daemon‑issued permission request IDs connection‑qualified, so a vote from any attached client can satisfy a pending request.

### Feature Request Trends
- **Subagent safety & isolation** – Plan‑mode locking (#6083), ACP permission voting (#5912), and the broader desire to treat subagents as delegable workers without conversation‑level authority.  
- **Channel‑native collaboration** – Loop support, history backfill, daemon managed workers, and unified channel‑session affordances signal a strong push toward team‑oriented usage.  
- **Session lifecycle & memory** – Archiving (#6058), sessionless workspace‑remember (#5884), and timeline visualisation (#6078) point to users wanting more control over long‑lived, context‑rich sessions.  
- **Mobile / responsive web shell** – Requests for sidebar‑free session switching (#6000) and responsive UX show that browser‑based access is a growing use case.  
- **Integration‑friendly ACP protocol** – Explicit capability advertising (vision‑bridge, image capabilities) to make Qwen Code a first‑class citizen in multi‑tool orchestration hosts.

### Developer Pain Points
- **ACP daemon stability** – Infinite loops from tool‑call edge cases (#6075, #6084) remain a recurring friction, especially in non‑interactive automation.  
- **Windows path quirks** – Tilde‑path resolution (#6030), case‑sensitive permission comparisons (#2670), and editor command parsing (#2683) frustrate Windows users and occasionally block first‑run experiences.  
- **Mobile web shell gaps** – Lack of session switching and hidden sidebar on small screens (#6000) forced mobile users into cumbersome work‑arounds; now partially addressed.  
- **Subagent tool confusion** – The ability for subagents to accidentally enter plan mode or execute lifecycle tools (#6083) created surprising behaviour that eroded trust in delegated workflows.  
- **Model endpoint ambiguity** – Vision models sharing the same provider + model id but different base URLs needed manual workarounds; PR #6070 is tackling this, but it’s been a consistent source of mis‑configuration.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

**DeepSeek TUI Community Digest — 2026-07-01**

---

## Today’s Highlights
The v0.8.66 release gate dominated the last 24 hours: a heavy series of merges tackled a systemic freeze during high sub-agent fanout, restoring UI responsiveness. Concurrently, several new community PRs targeted Windows background window suppression, MCP security, and exact binary release preferences, while the Hotbar now ships hidden by default until a user opts in.

## Releases
No new version was published in the last 24 hours.

## Hot Issues

1. **#1177 — Input cache hit rate critically low**  
   *24 comments · opened 2026-05-08*  
   Users comparing with DeepSeek‑Reasonix report ~95%+ cache hit there, while CodeWhale sits far below. High token waste and latency are the top community concern.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/1177)

2. **#1120 — Remaining cache hit problems**  
   *21 comments · opened 2026-05-08*  
   Even after fixes, repeated project edits still show low cache hits. The discussion centres on further root-cause analysis, suspecting prompt structure or session handling.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/1120)

3. **#743 — Token consumption explosion**  
   *13 comments · opened 2026-05-05*  
   A user reported consuming 400 million tokens in half a day. The thread highlights excessive request density and per‑turn token bloat, with requests to optimise dialogue compaction.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/743)

4. **#1186 — Typed persistent permission rules**  
   *10 comments · opened 2026-05-08*  
   A feature request for fine‑grained allow/deny/ask rules scoped by tool name, command prefix, or workspace path. Seen as essential for safety‑conscious enterprise use.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/1186)

5. **#3821 — Session permanently damaged after long output / approval timeout**  
   *1 comment · opened 2026-06-30*  
   Two scenarios (long tool output with approval dialog timeout) freeze the agent irrecoverably, requiring a restart. High severity, newly reported.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/3821)

6. **#3819 — MCP OAuth authentication UX issues**  
   *1 comment · opened 2026-06-30*  
   Stale tokens aren’t auto‑refreshed, errors are silent, and foreground login can time out. Makes connecting to OAuth‑protected MCP servers (e.g., Nordic Semiconductor) painful.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/3819)

7. **#1512 — Mouse scroll only shows user posts, not model output**  
   *3 comments · opened 2026-05-12*  
   A UI bug: scrolling with the mouse wheel past the user’s own messages hides the model’s response. Needs a TUI rendering fix.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/1512)

8. **#1641 — Agent mode lacks fallback strategy on tool failures**  
   *3 comments · opened 2026-05-14*  
   When external tools fail (anti‑bot protection, timeout), the agent retries blindly until the whole task fails. Request for graceful degradation or alternative tool switching.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/1641)

9. **#2061 — Hotbar: MMO‑style quick action bar (umbrella)**  
   *3 comments · opened 2026-05-25*  
   Product direction shifted: Hotbar will be optional and hidden by default. Discussion continues on discoverability, customisation, and source adapters.  
   [Link](https://github.com/Hmbown/CodeWhale/issues/2061)

10. **#1425 — Session freeze/hang after large text processing with sub‑agents**  
    *1 comment · opened 2026-05-11*  
    Processing a 3‑million‑word novel with 10 sub‑agents caused `agent_wait` timeouts and apparent session death. Investigation shows the session was actually interrupted, not fully hung.  
    [Link](https://github.com/Hmbown/CodeWhale/issues/1425)

## Key PR Progress

1. **#3812 – Allow agent starts to join parallel dispatch batches**  
   *closed · child of #3800*  
   Previously, multiple `agent` tool calls in one turn were serialised. Now they can fan out in parallel, dramatically reducing launch latency for high‑fanout scenarios.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3812)

2. **#3813 – Non‑blocking send for ListSubAgents refresh events**  
   *closed · child of #3800*  
   Changed the engine event channel sending to non‑blocking, preventing UI/engine stalls when many sub‑agent statuses arrive simultaneously.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3813)

3. **#3816 – Persist sub‑agent state off the manager write‑lock hot path**  
   *closed · child of #3800*  
   Moved JSON serialisation and file writes out of the critical section, reducing lock contention during fanout bursts.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3816)

4. **#3809 – Render sub‑agent sidebar from a read‑only snapshot**  
   *closed · child of #3800*  
   Changed sidebar refresh to use a read lock instead of a write lock, avoiding contention with completion updates and persistence.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3809)

5. **#3808 – Use `try_lock` on shell manager in async refresh paths**  
   *closed · child of #3800*  
   Replaced blocking mutex locks with `try_lock` in two UI refresh paths, preventing UI thread blockage when background shells held the lock.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3808)

6. **#3814 – Keep approval controls visible inline**  
   *closed · fix for #3799*  
   Approval prompts no longer clip the action row on short terminals; footer and controls are now rendered in a scrollable structured layout.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3814)

7. **#3815 – Hide Hotbar until explicit opt‑in**  
   *closed · product decision #3807*  
   Fresh installations no longer show the Hotbar panel. It remains available via `/hotbar` and explicit config, keeping v0.8.66 focused on reliability.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3815)

8. **#3825 – Expand `${VAR}` env placeholders in MCP stdio config**  
   *open*  
   Allows secrets to be injected via environment variables in `mcp.json` without leaking them to the child process’s environment, using pre‑expansion on the config file.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3825)

9. **#3824 – Support wildcard disallowed tool prefixes**  
   *open*  
   Extends `disallowed_tools` to accept prefix patterns (e.g., `mcp__*`), letting users hide entire MCP servers’ dynamic tools without knowing every tool name in advance.  
   [Link](https://github.com/Hmbown/CodeWhale/pull/3824)

10. **#3817 – Preserve YOLO authority for runtime continuations**  
    *closed*  
    Fixed a regression where a YOLO session would still prompt for approval on `git push` or PR creation when the action originated from a sub‑agent handoff or continuation.  
    [Link](https://github.com/Hmbown/CodeWhale/pull/3817)

## Feature Request Trends
- **Caching and token efficiency**: Input cache hit rate improvements are the loudest demand, coupled with token‑consumption reduction via smarter compaction and prefix‑stable prompts.  
- **Granular execution policies**: Typed allow/deny rules, wildcard tool blocking, and persistent permission profiles point toward enterprise‑grade safety.  
- **Agent resilience**: Fallback strategies on tool failure, graceful degradation, and session recovery after long runs or timeouts are frequently requested.  
- **Sub‑agent scalability**: Reliable high‑fanout parallel execution without UI freezes, timeouts, or processes hanging (underscored by the v0.8.66 fixes).  
- **Onboarding and discoverability**: Setup wizard, `/constitution` personalisation, and optional Hotbar reveal a desire for a smoother first‑run experience.

## Developer Pain Points
- **Cache misses and token cost**: Users feel they’re burning tokens unnecessarily on repeated contextual work, leading to frustration over cost and speed.  
- **TUI freezing under load**: Even before the latest fixes, fanout scenarios made the interface unresponsive and frightening. Confidence in multi‑agent workflows is being rebuilt.  
- **Unrecoverable session states**: Long outputs or approval timeouts can permanently break a session, leaving users no choice but to restart and lose context.  
- **MCP authentication friction**: OAuth token management is fragile, with silent failures and no auto‑refresh, slowing adoption of secure MCP servers.  
- **UI glitches**: Simple bugs like the mouse‑scroll behaviour and modal text overflow erode the polished feel, especially for newcomers.  
- **Complex power‑user configuration**: While Hotbar is powerful, its default visibility confused users; similar complexity around constitution, tools, and provider docs leads to support load.

</details>