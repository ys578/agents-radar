# AI CLI Tools Community Digest 2026-07-01

> Generated: 2026-07-01 11:41 UTC | Tools covered: 9

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

# Cross-Tool AI CLI Comparison Report — 2026-07-01

## 1. Ecosystem Overview

The AI CLI tools ecosystem is entering a **stability-and-safety phase** following rapid model iteration. All major tools shipped releases this period—Claude Code with Sonnet 5, OpenCode with MCP OAuth fixes, Pi with Sonnet 5 and AOT compilation, and CodeWhale completing its rebrand. The dominant cross-cutting concerns are **cost control for agentic workflows**, **non-blocking interaction patterns**, and **MCP interoperability across providers**. Community attention is shifting from raw capability to reliability, safety, and enterprise readiness, with recursive agent cost incidents and tool execution safety failures driving urgency. Gemini CLI and Qwen Code show the highest PR velocity, while Claude Code and OpenAI Codex lead in community engagement volume.

---

## 2. Activity Comparison

| Tool | Issues (24h) | PRs (24h) | Release Status | Community Signal |
|------|-------------|----------|----------------|------------------|
| **Claude Code** | ~10 new (2 critical) | 2 (1 merged) | v2.1.197 shipped | 296👍 on top issue; cost safety incident |
| **OpenAI Codex** | ~8 active (3 quota) | 10+ merged (automations stack) | v0.142.5 + alpha | 410👍 on top issue; heavy PR activity |
| **Gemini CLI** | ~10 hot (4 P1) | 10 (8 merged, 2 open) | v0.51.0-nightly | 8👍 top issue; highest PR throughput |
| **Copilot CLI** | ~8 new (2 auth, 2 accessibility) | 2 (trivial) | v1.0.66 + v1.0.67 | 41👍 on global permissions; low PR velocity |
| **Kimi Code** | ~5 active (1 critical loop) | 10 (8 meaningful) | No new release | 14👍 on exec mode; moderate activity |
| **OpenCode** | ~10 active (1 startup crash) | 10 (all merged) | v1.17.12 shipped | 60👍 on unqueue; high-quality PRs |
| **Pi** | ~8 active (1 architecture debate) | 10 (9 merged) | v0.80.3 shipped | 18 comments on dependency issue; large PRs |
| **Qwen Code** | ~50 updated (10 hot) | ~50 (diverse) | v0.19.3-nightly | High volume; model compatibility concerns |
| **CodeWhale** | ~10 active (3 modal/security) | 10 (8 merged) | v0.8.66 shipped | 18 comments on yolo mode; rebrand complete |

**Key observations:** Gemini CLI and Qwen Code show the highest raw activity. Claude Code and OpenAI Codex have the highest community engagement per issue. CodeWhale has strong maintainer-driven velocity. Copilot CLI and Kimi Code show slower momentum.

---

## 3. Shared Feature Directions

| Requirement | Affected Tools | Specific Needs |
|-------------|---------------|----------------|
| **Non-blocking interaction** | Claude Code (#50246, #62856), OpenCode (#4821) | Message queue mode, unqueue capability, compose-while-working |
| **MCP interoperability** | OpenAI Codex (#26234), Copilot CLI (#3982), Pi (#5509), CodeWhale (#3866, #3869) | Flat namespace tools, OAuth flow fixes, dynamic server spawning |
| **Cost controls for agents** | Claude Code (#72732), Gemini CLI (#22323), Copilot CLI (#3158), CodeWhale (#2487) | Recursive agent limits, hang detection, budget enforcement |
| **Global tool permissions** | Copilot CLI (#179, #3028), Claude Code (#27302), CodeWhale (#3406) | Persistent allow/deny rules, tool-level access control |
| **Session/context management** | OpenCode (#26861), Qwen Code (#3234, #4079), Pi (#6217) | Session naming, quiet restore, long-session budget handling |
| **Plugin/hook parity** | OpenAI Codex (#21753), Copilot CLI (#3727), Kimi Code (#5422) | Full lifecycle hooks, hook regression fixes, tool output rewriting |
| **Per-project configuration** | Copilot CLI (#1665), Qwen Code (#6060), Pi (#6190) | Project-scoped plugins, workspace-level settings, env-driven paths |
| **Windows stability** | Claude Code (multiple), OpenAI Codex (#29436), Copilot CLI (#3996), CodeWhale (#1812) | Memory leaks, console flicker, clipboard failures, auth hangs |

**Most convergent:** Non-blocking interaction and MCP interoperability appear across the widest range of tools, indicating these are ecosystem-level gaps rather than tool-specific.

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | Pi | CodeWhale |
|-----------|-------------|--------------|------------|-------------|-----|-----------|
| **Primary focus** | Agentic workflows, safety | Automation pipelines, enterprise | Subagent orchestration | GitHub ecosystem integration | Plugin/SDK extensibility | Constitutional security, rebrand |
| **Target user** | Power users, researchers | Enterprise teams, automation | Cloud-native developers | GitHub-centric teams | Extension authors, polyglot | Chinese-speaking, security-aware |
| **Model strategy** | Anthropic Sonnet 5 default | OpenAI only; MCP parity push | Google Gemini | Multi-model (BYOK + Claude) | Multi-provider (Sonnet 5 now) | Provider-agnostic |
| **Key differentiator** | 1M-token context, prompt pricing | Automation backend stack | Caretaker Agent, AST tooling | GitHub Copilot integration | AOT compilation, Bedrock Mantle | Constitution-first security model |
| **Community pain** | Thinking block mutations, tool safety | Rate-limit accounting broken | Subagent reliability | Authentication instability | Dependency management | Rebrand inconsistencies |
| **PR velocity** | Moderate | High | Very high | Low | High | High |

**Notable divergences:**
- **Pi** is the only tool with AOT compilation for extensions—a performance-focused differentiator.
- **CodeWhale** is alone in building a "constitution" security model that separates behavioral rules from runtime controls.
- **Gemini CLI** uniquely invests in automated issue triage infrastructure (Caretaker Agent).
- **OpenAI Codex** stands out for enterprise config enforcement (managed `requirements.toml`).

---

## 5. Community Momentum & Maturity

**Most active communities (by engagement depth):**
- **Claude Code** — Highest upvoted issues (296👍 for Connector accounts) and deepest critical bug discussions (204 comments). The cost-safety incident (#72732) drove unusually high engagement for a single-day issue.
- **OpenAI Codex** — Strongest sustained PR activity with a 29-PR automation stack merged. 410👍 on SQLite logging signals broad user base.
- **Gemini CLI** — Highest total PR throughput (10 PRs, 8 merged). Caretaker Agent infrastructure indicates investment in community-facing automation.

**Most rapidly iterating:**
- **Gemini CLI** — Nightly builds, high PR velocity, infrastructure investment.
- **Qwen Code** — Extremely high raw issue/PR volume (50 each), though many are triage-level. Rapid model iteration.
- **Pi** — Major infrastructure PRs (AOT compilation, Bedrock Mantle, prompt caching optimization). Community dependency debate (#5653) shows healthy architecture discourse.

**Maturity indicators:**
- **Claude Code** — Most mature bug reporting discipline; issues include lawsuit threats and financial impact, indicating production use.
- **OpenAI Codex** — Enterprise features (managed config, artifact persistence) suggest production deployments.
- **CodeWhale** — Rebrand completion signals project stability; constitution approach shows advanced security thinking.
- **Copilot CLI** — Lowest PR velocity; community focuses on feature requests rather than bugs, suggesting relative stability.
- **Kimi Code** — Unresolved loop bug (#640, 6 months) and slower release cadence suggest smaller team or lower priority.

---

## 6. Trend Signals

1. **Safety is the new feature frontier.** The $600 recursive agent incident (Claude Code #72732), tool deletion despite "replace only" instruction (#72733), and agent self-looping (CodeWhale #3275) signal that the community is hitting real-world safety boundaries. Expect cost guards, agent depth limits, and sandbox hardening across all tools.

2. **MCP is becoming a cross-tool standard—with friction.** Tools are investing heavily in flat namespace support (OpenAI Codex #29602), OAuth flow fixes (Copilot CLI #3982, Pi #33920, CodeWhale #3828), and dynamic server spawning (CodeWhale #3866). The ecosystem is standardizing on MCP but each tool has its own integration quirks.

3. **Non-blocking interaction is demanded everywhere.** Message queuing, compose-while-working, and unqueue capabilities appear across Claude Code, OpenCode, and Copilot CLI. Users want AI agents to work in the background without interrupting their flow. This is a fundamental UX paradigm shift.

4. **Windows remains the weak link.** All tools with Windows support report stability issues—segfaults, memory leaks, console flicker, clipboard failures. The Windows experience is consistently 1-2 releases behind macOS/Linux quality.

5. **Enterprise adoption is driving config complexity.** Managed config enforcement (OpenAI Codex), project-scoped plugins (Copilot CLI), workspace-level settings (Qwen Code), and admin overrides (Pi) all point to growing enterprise deployments. Configuration management is becoming a product surface.

6. **Third-party model support is fracturing.** Kimi Code (#640) and Qwen Code (#1281, #4711) see issues specifically from non-native model deployments (Ollama, custom endpoints). OpenAI Codex (#26234) actively works to flatten MCP tools for third-party providers. The "walled garden" model is losing to user demand for provider choice.

7. **Accessibility awareness is emerging.** Pi closed a screen-reader issue (#4687), Copilot CLI has new clipboard/accessibility triage issues (#3996, #3993). Terminal-based tools are beginning to address assistive technology compatibility.

---

**Bottom line for decision-makers:** If you prioritize safety and agentic workflows, watch Claude Code's response to the recursive cost incident. For enterprise automation, OpenAI Codex's backend stack is most mature. For extensibility and performance, Pi's AOT compilation and Bedrock integration are unique. For the broadest model support, monitor Qwen Code and CodeWhale. Windows teams should budget extra QA effort regardless of tool choice.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report (as of 2026-07-01)

## 1. Top Skills Ranking

The following are the most-discussed Skill submissions (PRs) ranked by community engagement and attention:

**#1298 — `fix(skill-creator): run_eval.py always reports 0% recall`**
- **Functionality**: Fixes the core evaluation pipeline (`run_eval.py`, `run_loop.py`, `improve_description.py`) where skill descriptions consistently report `recall=0%` across all queries, making the optimization loop optimize against noise. Addresses multiple root causes including Windows stream reading, trigger detection logic, and parallel worker issues.
- **Status**: OPEN | [GitHub](https://github.com/anthropics/skills/pull/1298)
- **Discussion highlights**: References 10+ independent reproductions of the bug (#556). This is the most active PR, representing a systemic blocker affecting all skill-creator workflows.

**#514 — `Add document-typography skill`**
- **Functionality**: Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Provides typographic quality control for Claude-generated output across all document creation scenarios.
- **Status**: OPEN | [GitHub](https://github.com/anthropics/skills/pull/514)
- **Discussion highlights**: Universal applicability ("These issues affect every document Claude generates") drove broad community interest. Users noted the skill fills a gap no other tool addresses.

**#486 — `Add ODT skill — OpenDocument text creation and template filling`**
- **Functionality**: Enables creation, filling, reading, and conversion of OpenDocument Format files (.odt, .ods). Supports LibreOffice document generation and ISO standard format handling.
- **Status**: OPEN | [GitHub](https://github.com/anthropics/skills/pull/486)
- **Discussion highlights**: High demand for enterprise interoperability standards (ODF, LibreOffice). Community discussion centered on template filling capabilities and HTML conversion accuracy.

**#1367 — `feat(skills): add self-audit — four-dimension reasoning quality gate`**
- **Functionality**: A universal skill that audits AI output across four dimensions before delivery: Completeness, Consistency, Grounding, and Helpfulness. Works with any project, tech stack, or model.
- **Status**: OPEN | [GitHub](https://github.com/anthropics/skills/pull/1367)
- **Discussion highlights**: Very recent (2026-06-28) but already high engagement. Proposes a built-in quality assurance layer for all Claude outputs.

**#83 — `Add skill-quality-analyzer and skill-security-analyzer to marketplace`**
- **Functionality**: Two meta-skills for evaluating Claude Skills themselves: quality analysis across structure/documentation/examples/resource usage, and security analysis for identifying potential vulnerabilities in skill definitions.
- **Status**: OPEN | [GitHub](https://github.com/anthropics/skills/pull/83)
- **Discussion highlights**: Community debated whether meta-skills belong in the main repository vs. a separate tools collection. Strong interest in skill security auditing given concurrent issues about trust boundary abuse.

**#210 — `Improve frontend-design skill clarity and actionability`**
- **Functionality**: Revises the existing frontend-design skill to ensure every instruction is actionable within a single conversation, with specific enough guidance to steer Claude behavior without being overly prescriptive.
- **Status**: OPEN | [GitHub](https://github.com/anthropics/skills/pull/210)
- **Discussion highlights**: Community engaged in detailed line-by-line review of skill effectiveness criteria. Established a pattern for skill quality improvement PRs.

---

## 2. Community Demand Trends

Analysis of the most-commented Issues reveals four concentrated demand areas:

**🔧 Skill Creator / Evaluation Pipeline Fixes (Dominant demand)**
Issues #556, #1169, #1061 collectively demonstrate the community's #1 pain point: `run_eval.py` consistently reports 0% recall, making the description-optimization loop effectively useless. Windows compatibility failures compound this. Multiple independent reproductions confirm this is a systemic, not isolated, issue. The community is heavily invested in making *skill creation itself* functional.

**🔒 Security & Trust Boundaries**
Issue #492 (32 comments, highest engagement) exposes a critical vulnerability: community skills distributed under the `anthropic/` namespace create trust boundary abuse risks. Users may grant elevated permissions believing skills are official. This intersects with calls for skill-security-analyzer meta-tools.

**🏢 Enterprise & Organization Features**
Issue #228 (14 comments) demands org-wide skill sharing without manual file distribution. The inability to share skills within Claude.ai organizations is blocking enterprise adoption. Combined with interest in ODT/ODF formats (#486), SAP predictive analytics (#181), and SharePoint security concerns (#1175), enterprise readiness is a clear community priority.

**🧠 Agent Governance & Safety Patterns**
Issue #412 proposes agent-governance skills for policy enforcement, threat detection, and audit trails. Issue #1329 proposes compact-memory for efficient agent state management. Community interest is shifting from simple single-purpose skills toward orchestration and safety layers for multi-step agent workflows.

---

## 3. High-Potential Pending Skills

These open PRs have active discussion and are likely to merge soon:

| PR | Skill | Status | Why it may land |
|---|---|---|---|
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** (4-dimension quality gate) | OPEN (2026-06-28) | Recently updated; addresses universal quality assurance need; low complexity |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** (Testing Trophy model) | OPEN (2026-03-22) | Comprehensive testing stack coverage; multiple reviewers engaged |
| [#806](https://github.com/anthropics/skills/pull/806) | **sensory** (macOS AppleScript automation) | OPEN (2026-03-29) | Addresses native macOS gap without screenshot-based computer use |
| [#147](https://github.com/anthropics/skills/pull/147) | **codebase-inventory-audit** | OPEN (2025-12-16) | Long-running but systematic feedback; solves orphaned code problem |
| [#181](https://github.com/anthropics/skills/pull/181) | **SAP-RPT-1-OSS predictor** | OPEN (2025-12-28) | Enterprise demand; uses Apache 2.0 licensed open-source model |
| [#83](https://github.com/anthropics/skills/pull/83) | **skill-quality/security-analyzer** | OPEN (2025-11-06) | Meta-tool demand; complements security concerns from Issues |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is fixing the skill *creation and evaluation pipeline itself* — every top issue and PR points to `run_eval.py` returning 0% recall as the single largest blocker, with Windows compatibility failures compounding the problem — followed by enterprise interoperability (ODT/ODF, SAP, SharePoint) and trust/security governance for the rapidly growing skill marketplace.**

---

# Claude Code Community Digest — 2026-07-01

## Today's Highlights

Anthropic shipped **v2.1.197** introducing **Claude Sonnet 5** as the new default model, featuring a native 1M-token context window and promotional pricing through August 31. The community remains intensely focused on two long-running feature requests—multi-account Connector support (296 👍, 204 comments) and a non-interrupting message queue mode (120 👍)—while a spate of newly-opened issues highlights growing concerns around **uncontrolled recursive agent costs** and **tool execution safety**.

---

## Releases

**v2.1.197** — [Release Link](https://github.com/anthropics/claude-code/releases/tag/v2.1.197)
- **Claude Sonnet 5** is now the default model in Claude Code
- Native **1M-token context window**
- Promotional pricing: **$2/$10 per Mtok** (input/output) through August 31
- Users must update to v2.1.197 for access

---

## Hot Issues (Top 10 by Community Impact)

1. **#27302 — Support multiple Connector accounts** (OPEN, 204 comments, 296 👍)  
   Long-running request to allow multiple accounts for the same Connector in Claude Code web. The enormous engagement signals this is the #1 most-wanted workflow feature.  
   [GitHub](https://github.com/anthropics/claude-code/issues/27302)

2. **#50246 — Message queue mode** (OPEN, 35 comments, 120 👍)  
   Proposes queuing messages instead of interrupting active tasks. Gaining rapid traction as users demand non-blocking interaction patterns.  
   [GitHub](https://github.com/anthropics/claude-code/issues/50246)

3. **#72732 — Uncontrolled recursive agent spawning burns $600+** (OPEN, 1 comment)  
   Filed today: subagents spawning subagents recursively caused a single session to rack up over $600 in API costs. Major safety concern for agentic workflows.  
   [GitHub](https://github.com/anthropics/claude-code/issues/72732)

4. **#72733 — Tool deletes files despite "replace only" instruction** (OPEN, 1 comment)  
   Filed today: user reports a tool deleted all prior work despite explicit instruction to only replace. Includes a lawsuit threat, but the underlying safety issue is real.  
   [GitHub](https://github.com/anthropics/claude-code/issues/72733)

5. **#72424 — `/remote-control` slash command regression in v2.1.196** (CLOSED, 3 comments)  
   Regression where the `/remote-control` command disappeared. Quickly closed, but highlights fragility in slash command infrastructure.  
   [GitHub](https://github.com/anthropics/claude-code/issues/72424)

6. **#63425 — "workflow" keyword conflicts with tool trigger syntax** (CLOSED, 3 comments, 7 👍)  
   Community frustration: using "workflow" as a tool trigger creates namespace conflicts. Small fix, high developer annoyance.  
   [GitHub](https://github.com/anthropics/claude-code/issues/63425)

7. **#63448 — Opus 4.8: thinking blocks broken by context compaction** (CLOSED, 3 comments, 4 👍)  
   After context compaction, every turn fails with 400. Session becomes permanently broken—major UX issue for long-running sessions.  
   [GitHub](https://github.com/anthropics/claude-code/issues/63448)

8. **#63258 — Opus 4.8: backgrounded subagents crash with "thinking blocks cannot be modified"** (CLOSED, 3 comments, 5 👍)  
   Backgrounded tasks immediately crash on first turn. Blocks the increasingly popular subagent/background pattern entirely for Opus 4.8 users.  
   [GitHub](https://github.com/anthropics/claude-code/issues/63258)

9. **#62856 — Compose-while-working with interrupt vs queue choice** (CLOSED, 2 comments, 2 👍)  
   Related to #50246: wants a Codex-style send-time choice between interrupting or queuing a message. Signals growing demand for async interaction.  
   [GitHub](https://github.com/anthropics/claude-code/issues/62856)

10. **#63459 — VS Code: thinking text empty on Opus 4.7+** (CLOSED, 2 comments, 2 👍)  
    "Thought for Xs" not expandable on Opus models in VS Code extension. Fallback config branch omits `display` field.  
    [GitHub](https://github.com/anthropics/claude-code/issues/63459)

---

## Feature Request Trends

1. **Non-blocking interaction** — The dominant theme across multiple issues. Users want to queue messages (#50246), compose while the agent works (#62856), and choose per-message whether to interrupt or queue. This reflects a maturation of the tool from "chat assistant" to "background collaborator."

2. **Multi-account Connector support** — #27302 remains the single most-upvoted feature request. As teams adopt Connectors for MCP servers and SaaS integrations, the inability to switch accounts is a critical blocker.

3. **Cost controls for agentic workflows** — #72732 (today's $600+ recursive agent issue) adds urgency to calls for better cost guards, agent depth limits, and spend-aware tool execution.

4. **Desktop recents enumeration** — #54911 (6 comments, 3 👍) requests the desktop app enumerate `~/.claude/projects/` directly for better project discovery.

---

## Developer Pain Points

1. **Thinking block mutation errors (Opus 4.8)** — A cluster of issues (#63247, #63258, #63278, #63448, #63508) all report 400 errors when thinking blocks are modified during context compaction, backgrounded tasks, or interleaved tool use. This is the single most disruptive bug cluster for advanced users.

2. **Windows stability** — Multiple closed issues (#50640, #57035, #62970) point to ongoing Segfaults, DACL permission problems breaking upgrades, and silent Bash output failures on Windows 11.

3. **Chrome extension bridge reliability** — Issues #62002 and #61117 document a fragile connection between the Claude Chrome extension and the native host bridge, with CSP blocks and socket disconnects causing "Browser extension is not connected" errors despite apparently healthy layers.

4. **Plan mode state inconsistency** — #62451 reports that interrupting the `ExitPlanMode` flow leaves the system in an inconsistent state, suggesting the state machine for mode transitions needs hardening.

5. **Tool safety failures** — #72733 (today's "delete despite replace-only instruction") and #62402 (Sonnet 4.6 executing `rm -rf` on explicitly excluded directories) represent critical trust failures in tool execution compliance.

---

## Key PR Progress

1. **#46903 — docs(plugin-dev): add plugin cache sync guidance** (MERGED)  
   Adds documentation for local plugin development, explaining the `~/.claude/plugins/cache/` copy behavior and how to sync after edits. Essential for plugin authors.  
   [GitHub](https://github.com/anthropics/claude-code/pull/46903)

2. **#72543 — Create Cha** (OPEN, trivial/cryptic)  
   Title appears incomplete; likely a test or spam PR. Minimal substantive value.  
   [GitHub](https://github.com/anthropics/claude-code/pull/72543)

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

**OpenAI Codex Community Digest**
*2026-07-01*

---

### 1. Today's Highlights

Two patch releases landed, including a critical fix preventing full WebSocket request payloads from leaking into trace logs. The community remains focused on a concurrency of issues: persistent SQLite log churn on macOS, abnormal rate-limit consumption on both App and CLI, and a major push to flatten MCP namespace tools for third-party providers. A sprawling 29-PR automation backend stack merged this week, signaling significant new scheduled-task infrastructure.

---

### 2. Releases

- **rust-v0.142.5** – Bug-fix release that backports a WebSocket trace logging fix (PR #30771) to the stable branch. Prevents full Responses WebSocket request payloads from being written to trace logs.
    - [Release notes](https://github.com/openai/codex/compare/rust-v0.142.4...rust-v0.142.5)

- **rust-v0.143.0-alpha.32** – Pre-release alpha; no changelog details beyond the version bump.
    - [Release tag](https://github.com/openai/codex/compare/9551e52...v0.143.0-alpha.32)

---

### 3. Hot Issues

1. **[#28224 – SQLite feedback logs write ~640 TB/year](https://github.com/openai/codex/issues/28224)** (119 💬, 410 👍)  
   *Status:* OPEN (author signaled plan to close)  
   The highest-voted open issue. Three merged PRs (included in v0.142.0) cut 85% of log volume for the author, but the remaining 15% still concerns SSD endurance. Community mostly relieved, but monitoring continues.

2. **[#29532 – macOS: Persistent SQLite TRACE log churn after v0.142.0](https://github.com/openai/codex/issues/29532)** (31 💬, 7 👍)  
   Reports that `logs_2.sqlite` continues growing on macOS despite the PR #29457 fix. Partial regression – the `responses_websocket` namespace improved, but not eliminated.

3. **[#29320 – Windows App: "Something went wrong" on launch](https://github.com/openai/codex/issues/29320)** (27 💬, 2 👍)  
   Full-screen error after update on Windows 11 25H2. No root cause identified; users forced to reinstall.

4. **[#21753 – Full Claude Code Hook Parity (29+ hooks)](https://github.com/openai/codex/issues/21753)** (25 💬, 19 👍)  
   Umbrella for bringing Codex hooks to feature parity with Claude Code. Covers every lifecycle event. High interest from automation developers.

5. **[#26234 – Flatten MCP namespace tools for non-OpenAI providers](https://github.com/openai/codex/issues/26234)** (23 💬, 35 👍)  
   MCP tools are unusable with Ollama, LM Studio, OpenRouter, and Bedrock. Community strongly supports the fix (PR #29602 now open). Biggest third-party integration pain point.

6. **[#28823 – 5-hour usage meter depletes much faster than historical](https://github.com/openai/codex/issues/28823)** (19 💬, 2 👍)  
   Telemetry shows usage allowance consumed at ~4–5x normal rate. Suspected regression in quota counting logic.

7. **[#28316 – Large base64 image tool outputs resent in every turn](https://github.com/openai/codex/issues/28316)** (7 💬, 1 👍)  
   Persistent full-image payloads in conversation history cause unbounded context growth. A path to quadratic cost in multi-turn image conversations.

8. **[#30212 – 5-hour allowance consumed in ~1 hour (Pro subscription)](https://github.com/openai/codex/issues/30212)** (7 💬, 9 👍)  
   Another severe quota depletion report on Pro tier. Data suggests the 5-hour meter is running faster than wall-clock time.

9. **[#29436 – Windows: Kernel-pool growth + system-wide slowdown](https://github.com/openai/codex/issues/29436)** (6 💬, 0 👍)  
   Memory rises to 95% within ~1 hour on Windows. Screenshots/clipboard become delayed. Only reboot recovers. Possibly linked to stale process/token handles (#29729).

10. **[#30815 – 5-hour limit applies to /fast mode](https://github.com/openai/codex/issues/30815)** (3 💬, 0 👍)  
    `/fast` mode burns tokens 2× faster from weekly quota – but also 2× faster from the 5-hr limit. Community finds this illogical; the faster-work penalty is time-gating.

---

### 4. Key PR Progress

1. **[#29602 – Flatten namespace tools for providers without wrappers](https://github.com/openai/codex/pull/29602)** (OPEN)  
   Direct fix for #26234. Removes the `type: "namespace"` wrapper that blocks MCP tool usage on non-OpenAI endpoints. Biggest pending cross-platform MCP fix.

2. **[#29602 stack – Automations backend (9 PRs merged)](https://github.com/openai/codex/pulls?q=automations+is%3Aclosed)**  
   A series from `eternal-openai`: durable state store, state CRUD + scheduling, claims/leases, runNow dispatching, background worker loop, heartbeats + cooldown, and dispatch integration. Builds a complete scheduled-automation service inside Codex.

3. **[#28409 – Enforce exact managed config values](https://github.com/openai/codex/pull/28409)** (CLOSED)  
   Adds exact-value enforcement for `sqlite_home`, `log_dir`, `model_catalog_json`, and others via `requirements.toml`. Enterprise compliance feature.

4. **[#28645 – Fail open on managed feature write conflicts](https://github.com/openai/codex/pull/28645)** (CLOSED)  
   Allows local config writes to persist explicit feature values even when enterprise-managed policies pin the opposite effective value.

5. **[#28602 – Force offline standalone web search after connector use](https://github.com/openai/codex/pull/28602)** (CLOSED)  
   Once a connector-backed MCP tool is used in a thread, forces all subsequent standalone web searches to offline mode. Privacy/security enforcement.

6. **[#28268 – Expose User Message Queue app-server API](https://github.com/openai/codex/pull/28268)** (CLOSED)  
   Adds experimental `queued-item` endpoints for durable thread-scoped user message queuing. Dispatch ownership stays in `QueuedItemService`.

7. **[#22722 – Persist thread artifacts in app-server runtime](https://github.com/openai/codex/pull/22722)** (CLOSED)  
   Adds generic thread artifact storage: persists patches in rollout session metadata, caches in SQLite, and emits `artifact-updated` notifications.

8. **[#26259 – Add advisory Interrupt hooks for interrupted turns](https://github.com/openai/codex/pull/26259)** (CLOSED)  
   New `Interrupted` hook fires specifically when a turn is interrupted (not stoppable). Enables reporting without altering the interrupt path.

9. **[#28456 – Reduce resume and fork orchestration overhead](https://github.com/openai/codex/pull/28456)** (CLOSED)  
   Isolates rollout paths, cached thread metadata, and avoids redundant thread reads in resume/fork setup. Faster startup for resumed threads.

10. **[#27963 – Reference writable roots from environment context](https://github.com/openai/codex/pull/27963)** (CLOSED)  
    Removes duplicate `writable-root` listing from dev-permissions message; references `<filesystem>` in `<environment_context>` instead. Cleaner context deduplication.

---

### 5. Feature Request Trends

- **MCP ecosystem parity** – Strong demand for flat namespace tool support (no proprietary wrappers) across all third-party providers (Ollama, OpenRouter, Bedrock, LM Studio). PR #29602 is the active delivery vehicle.
- **Complete hooks API** – The 29+ hook umbrella (#21753) aims for full Claude Code parity, covering every lifecycle event (turn start/stop, interrupt, artifact change, tool call, error, session end). Automation engineers are the loudest advocates.
- **Plugin management via CLI** – Multiple requests for `codex plugins` subcommands (list, install, upgrade) to avoid TUI-only or manual config management (#17431).
- **Enterprise config enforcement** – Managed `requirements.toml` value pinning (#28409) and write-conflict handling (#28645) point to growing enterprise adoption needs.
- **Thread artifact persistence** – Merged PR #22722 delivers the runtime infrastructure; expect more client-side tooling for viewing and restoring thread artifacts.

---

### 6. Developer Pain Points

- **Rate-limit accounting is broken** – Three separate reports (#28823, #30212, #30689) describe 5-hour allowances consumed at 4–5× the expected rate. On Pro tier, the meter can deplete in ~1 hour. `/fast` mode also burns the 5-hr clock 2× faster, not just the weekly quota (#30815).
- **Windows stability is deteriorating** – Kernel-pool memory leaks (#29436), stale `git.exe` tokens (#29729), duplicate MCP pools (#30753), and "Something went wrong" crashes (#29320) suggest a systemic regression in the Windows 11 app build.
- **SQLite log churn (macOS remnant)** – Despite the 85% fix in v0.142.0, `~/.codex/logs_2.sqlite` continues growing on macOS (#29532), frustrating users who expected a clean resolution.
- **Large base64 image payload denial of service** – Image tool outputs are persisted in full and resent in every subsequent turn (#28316). No throttling or deduplication exists.
- **Computer Use broken on Windows** – Chrome URLs cannot be determined (#25271), `node_repl` MCP tool is not exposed (#30486), and native pipes fail (#26528). The Chrome plugin on Windows remains unreliable across multiple versions.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-01

## Today's Highlights

The team shipped **v0.51.0-nightly.20260701** with a critical fix for `@`-prefixed file path resolution across core filesystem tools. Meanwhile, the engineering organization is scaling up its automated quality infrastructure: a new **Caretaker Agent** webhook ingestion service landed, and a triage worker foundation PR signals deeper investment in bot-driven issue management. Agent reliability remains the dominant community concern, with multiple high-severity bugs around subagent recovery, hanging, and tool selection still open after months.

## Releases

- **[v0.51.0-nightly.20260701.g7f00c5fe5](https://github.com/google-gemini/gemini-cli/releases/tag/v0.51.0-nightly.20260701.g7f00c5fe5)** — Nightly build containing two changes:
  1. `fix(core-tools)`: Defensive path resolution for `@`-reference files and fixes for macOS test failures ([PR #28053](https://github.com/google-gemini/gemini-cli/pull/28053))
  2. `feat(caretaker)`: Initial Cloud Run webhook ingestion service for automated issue triage ([PR #28015](https://github.com/google-gemini/gemini-cli/pull/28015))

---

## Hot Issues

| # | Issue | Why It Matters | Community Signal |
|---|-------|----------------|-----------------|
| 1 | [#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS reported as GOAL success | A subagent silently reports "success" when it actually hit turn limits. This masks real failures from users and from downstream evaluation pipelines. | 9 comments, 2 👍. Active retesting cycle. |
| 2 | [#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs forever | The generalist subagent hangs indefinitely for simple tasks (folder creation). Workaround: disable subagents entirely. | 7 comments, 8 👍 — highest 👍 count in the current set. Broadly felt. |
| 3 | [#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command execution stuck at "Waiting input" after command completes | Finished shell commands remain flagged as awaiting input, blocking the agent from proceeding. | 4 comments, 3 👍. Effort/medium priority P1. |
| 4 | [#21983](https://github.com/google-gemini/gemini-cli/issues/21983) — Browser subagent fails on Wayland | The browser agent crashes with `Termination Reason: GOAL` on Wayland display servers (common on Linux). | 4 comments, 1 👍. Long-standing (March 2026). |
| 5 | [#21968](https://github.com/google-gemini/gemini-cli/issues/21968) — Gemini does not use custom skills and sub-agents enough | Custom skills and sub-agents are ignored unless the user explicitly instructs the model to use them, defeating the extensibility promise. | 6 comments. Root cause unclear; likely prompt-level issue. |
| 6 | [#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — Assess AST-aware file reads, search, and mapping | Epic exploring whether AST-level tooling (file read methods, search, codebase mapping) can reduce turn counts and token waste. | 7 comments, 1 👍. Could improve both reliability and cost. |
| 7 | [#26525](https://github.com/google-gemini/gemini-cli/issues/26525) — Add deterministic redaction and reduce Auto Memory logging | Auto Memory sends transcripts to the model *before* redacting secrets. Also logs skill contents verbatim. | 5 comments. Security/privacy concern with automatic memory extraction. |
| 8 | [#20079](https://github.com/google-gemini/gemini-cli/issues/20079) — Symlinked agent files in `~/.gemini/agents/` not recognized | Symlinks are silently ignored. Makes it impossible to manage custom agents via symlink-based dotfile frameworks. | 4 comments. Simple UX regression. |
| 9 | [#22093](https://github.com/google-gemini/gemini-cli/issues/22093) — Subagents running without permission since v0.33.0 | Agents mode set to "disabled" in config, but subagents still activate. Config override is ignored. | 2 comments. Configuration trust issue. |
| 10 | [#28230](https://github.com/google-gemini/gemini-cli/issues/28230) — Kaspersky detects JS files as Trojan | Antivirus false-positive on distribution assets. Fresh issue (created 2026-07-01). | 1 comment. Distribution integrity concern. |

---

## Key PR Progress

| # | PR | Change | Status |
|---|-----|--------|--------|
| 1 | [#28053](https://github.com/google-gemini/gemini-cli/pull/28053) — Defensive path resolution for `@`-reference files | Fixes production bug where `read_file`, `replace`, `write_file` fail on `@`-prefixed paths. Also fixes macOS tests. | ✅ Merged (size/XL) |
| 2 | [#27971](https://github.com/google-gemini/gemini-cli/pull/27971) — Strip thoughts from scrubbed history turns | Resolves "thought leakage": internal model reasoning leaking into plain-text history, causing emulation loops. | ✅ Merged (size/M→L) |
| 3 | [#28015](https://github.com/google-gemini/gemini-cli/pull/28015) — Cloud Run webhook ingestion service | GitHub webhook endpoint with payload signature verification, Firestore storage, and Pub/Sub publishing for the Caretaker Agent. | ✅ Merged (size/L→XL) |
| 4 | [#28163](https://github.com/google-gemini/gemini-cli/pull/28163) — Triage worker core foundation (Part 1/2) | Core modules for the Caretaker Agent Triage Worker in Cloud Run. Split for reviewability. | 🟡 Open (size/L) |
| 5 | [#28223](https://github.com/google-gemini/gemini-cli/pull/28223) — Bypass LLM correction for JSON and IPYNB files | Prevents `write_file` and `replace` from corrupting structured files (Jupyter notebooks, JSON). | 🟡 Open (size/M) |
| 6 | [#28094](https://github.com/google-gemini/gemini-cli/pull/28094) — Deep-merge user and workspace settings | Fixes shallow spread that silently dropped nested config sections when workspace settings were present. | 🟡 Open (size/M, P2) |
| 7 | [#28068](https://github.com/google-gemini/gemini-cli/pull/28068) — Guard message inspectors against empty `parts` arrays | `isFunctionCall`/`isFunctionResponse` returned `true` for empty `parts` arrays due to `[].every()` vacuous truth. | 🟡 Open (size/M, P2) |
| 8 | [#28103](https://github.com/google-gemini/gemini-cli/pull/28103) — Avoid keep-alive socket reuse during OAuth token exchange | Fixes OAuth failure on Node.js versions with CVE-2026-48931 fix (response queue poisoning). | 🟡 Open (size/M, P2) |
| 9 | [#28112](https://github.com/google-gemini/gemini-cli/pull/28112) — SSRF protection for MCP OAuth metadata discovery | Adds `isLoopbackHost()` validation to OAuth metadata URL fetching, closing a security gap. | 🟡 Open (size/L) |
| 10 | [#28221](https://github.com/google-gemini/gemini-cli/pull/28221) — Make `~/.gitconfig` read-only in macOS sandbox | Prevents sandboxed processes from modifying git config (aliases, hooksPath), closing a command injection vector. | 🟡 Open (size/M→L) |

---

## Feature Request Trends

1. **AST-Aware Tooling** — Multiple issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)) request AST-level file reads, search, and codebase mapping to reduce token waste and misaligned reads.

2. **Agent Self-Awareness** — [#21432](https://github.com/google-gemini/gemini-cli/issues/21432) calls for the CLI to understand its own mechanics (flags, hotkeys, self-execution) well enough to act as its own user guide.

3. **Subagent Trajectory Visibility** — [#22598](https://github.com/google-gemini/gemini-cli/issues/22598) requests that subagent trajectories be included in `/chat share` output for easier debugging and evaluation.

4. **Harm Reduction** — [#22672](https://github.com/google-gemini/gemini-cli/issues/22672) asks the agent to prefer safe alternatives over destructive operations (`git reset --force`, `rm -rf`, etc.).

5. **Behavioral Eval Infrastructure** — [#24353](https://github.com/google-gemini/gemini-cli/issues/24353) calls for more robust component-level evaluations beyond the current 76 behavioral tests.

---

## Developer Pain Points

- **Subagent reliability is the #1 frustration.** Issues with hanging (P1 [#21409](https://github.com/google-gemini/gemini-cli/issues/21409)), silent failure masking (P1 [#22323](https://github.com/google-gemini/gemini-cli/issues/22323)), and configuration being ignored (P2 [#22093](https://github.com/google-gemini/gemini-cli/issues/22093)) erode trust in agent orchestration.

- **Shell execution is brittle.** Commands hang after completion (P1 [#25166](https://github.com/google-gemini/gemini-cli/issues/25166)), the model writes temp scripts in random directories (P2 [#23571](https://github.com/google-gemini/gemini-cli/issues/23571)), and interactive prompts trap the agent (P2 [#22465](https://github.com/google-gemini/gemini-cli/issues/22465)).

- **Configuration and settings are unreliable.** Symlinks are ignored (P2 [#20079](https://github.com/google-gemini/gemini-cli/issues/20079)), `settings.json` overrides are bypassed (P2 [#22267](https://github.com/google-gemini/gemini-cli/issues/22267)), and the A2A server uses shallow merges that lose nested settings ([#28094](https://github.com/google-gemini/gemini-cli/pull/28094)).

- **Auto Memory has safety gaps.** Secrets are sent to the model before redaction ([#26525](https://github.com/google-gemini/gemini-cli/issues/26525)), low-signal sessions are retried forever ([#26522](https://github.com/google-gemini/gemini-cli/issues/26522)), and invalid patches accumulate without quarantine ([#26523](https://github.com/google-gemini/gemini-cli/issues/26523)).

- **Security scan false-positives are reaching users.** A fresh report ([#28230](https://github.com/google-gemini/gemini-cli/issues/28230)) of Kaspersky flagging CLI JS files as Trojans may indicate distribution artifacts need review.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-01

## Today's Highlights

Two patch releases landed yesterday (v1.0.66, v1.0.67) addressing sandbox UX, cursor behavior, and MCP header parsing. Community attention remains focused on persistent authentication failures, project-scoped plugin support, and regressions in the plugin hook system. A cluster of new accessibility and clipboard bugs in VSCode Server / Windows environments has also emerged.

## Releases

**v1.0.67** (2026-06-30)
- Sandbox bypass (`Disabling the sandbox for the rest of the session`) now takes effect immediately for shell and search commands without re-prompting
- Subagent sessions now properly inherit parent tool restrictions
- Warnings and errors displayed when host custom agents fail to load
- Session limit enforcement added

**v1.0.66** (2026-06-30)
- Interactive sessions now use a non-blinking block cursor; terminal's default cursor style restored on exit
- Added support for Claude Opus 4.8 Fast, deprecated Claude Opus 4.6 Fast
- MCP add/edit form now accepts HTTP-style `Key: value` headers
- Fixed LSP servers starting twice

## Hot Issues

1. **#2684 — Persistent 'Authorization error' after login**  
   *Area: authentication, mcp*  
   User reports repeated `/login` prompts despite being authenticated. 13 comments, zero upvotes — suggests a narrow but impactful auth refresh bug affecting a subset of users.  
   [View Issue](https://github.com/github/copilot-cli/issues/2684)

2. **#1665 — Project/Repository-scoped plugins (instead of per-user)**  
   *Area: plugins, configuration*  
   Requesting repo-specific plugin loading. 18 upvotes, 10 comments. The highest-engagement feature request this week — teams need deterministic, shared plugin configs.  
   [View Issue](https://github.com/github/copilot-cli/issues/1665)

3. **#2334 — Bring back `no-alt-screen` mode**  
   *Area: configuration, terminal-rendering*  
   Closed issue with 29 upvotes. Users strongly prefer non-alt-screen mode for scroll-back, search, and selection. The community wants a configurable opt-out from the full-screen overlay.  
   [View Issue](https://github.com/github/copilot-cli/issues/2334)

4. **#3028 — MCP permissions: allow/deny tools globally**  
   *Area: permissions, mcp*  
   Requests a `trustedFolders`-style allowlist for MCP server tools. 5 upvotes, 7 comments. Enterprise users need granular tool gating.  
   [View Issue](https://github.com/github/copilot-cli/issues/3028)

5. **#3727 — Regression: `userPromptSubmitted` hook `additionalContext` not injected into planner (v1.0.60+)**  
   *Area: context-memory, plugins*  
   6 comments. Plugin developers report broken hook behavior since v1.0.60 — a critical blocker for anyone relying on custom context injection.  
   [View Issue](https://github.com/github/copilot-cli/issues/3727)

6. **#3282 — Multiple BYOK model support**  
   *Area: models, configuration*  
   11 upvotes. Users want to switch between multiple Bring-Your-Own-Key models without restarting the session or resetting environment variables.  
   [View Issue](https://github.com/github/copilot-cli/issues/3282)

7. **#179 — Globally configurable allowed tools**  
   *Area: permissions, configuration*  
   41 upvotes — the highest-voted open issue. Users want a global allowlist (similar to Claude Code's `~/.claude/settings.json`) to avoid per-session tool approval prompts.  
   [View Issue](https://github.com/github/copilot-cli/issues/179)

8. **#2507 — Respect terminal defaults for cursor style**  
   *Area: input-keyboard, terminal-rendering*  
   3 upvotes. Users on Windows 11 request the CLI respect system cursor style (e.g., blinking bar) instead of forcing a block cursor. Fixed in v1.0.66 today.  
   [View Issue](https://github.com/github/copilot-cli/issues/2507)

9. **#3982 — OAuth `grant_types_supported` ignored for MCP servers**  
   *Area: authentication, mcp*  
   New issue. Copilot CLI attempts `authorization_code` flow even when the MCP server only supports `client_credentials`. Breaks corporate MCP server integration.  
   [View Issue](https://github.com/github/copilot-cli/issues/3982)

10. **#3158 — Plan→Compact→Re-Plan infinite loop (217 cycles)**  
    *Area: agents, context-memory*  
    High-severity bug: agent gets stuck in a compaction/re-planning loop at ~75% context usage, never executing any action. 1 comment but critical for long-running sessions.  
    [View Issue](https://github.com/github/copilot-cli/issues/3158)

## Key PR Progress

*(Note: Only 2 PRs updated in the last 24h; no substantial feature PRs active.)*

1. **#3873 — Add initial console log for greeting**  
   Trivial change. Author: EverydayEvertime. Low impact.  
   [View PR](https://github.com/github/copilot-cli/pull/3873)

2. **#3880 — UI component example (ArtistCard)**  
   Open PR with unrelated front-end code. Appears to be a test/spam PR.  
   [View PR](https://github.com/github/copilot-cli/pull/3880)

## Feature Request Trends

- **Plugin scoping** (#1665) — The #1 request: move from per-user global plugins to project/repository-scoped configuration. Drives team adoption.
- **Multi-model BYOK** (#3282) — Ability to configure and switch between multiple BYOK models without session restart.
- **Global tool permissions** (#179) — Persistent allow/deny rules for CLI tools, matching Claude Code's UX. 41 upvotes.
- **Custom theme support** (#1504) — 20 upvotes for user-defined, shareable theme JSON files.
- **Per-mode default models** (#2958) — 14 upvotes for separate model configurations for `plan` vs `autopilot` modes.

## Developer Pain Points

1. **Authentication instability** (#2684, #3982) — Frequent "Authorization error" prompts and poor OAuth flow handling for MCP servers. Blocks headless/automated usage.
2. **Plugin hook regression** (#3727) — Breaking change in v1.0.60 for `userPromptSubmitted` hooks. Plugin authors lack migration guidance.
3. **Alt-screen controversy** (#2334) — Forced full-screen overlay remains unpopular; users want a configurable escape to traditional terminal UX.
4. **Agent infinite loops** (#3158) — Plan→Compact→Re-Plan cycles waste tokens and stall sessions. No recovery mechanism.
5. **Clipboard & accessibility** (#3996, #3993, #3981) — New triage issues: clipboard broken in VSCode Server, screen-reader echo missing, and Windows clipboard failures while CLI is running. Emerging surface area of quality gaps.
6. **Session metrics loss** (#3994) — `/new` discards token usage stats without writing to `events.jsonl`, breaking usage tracking.
7. **Web fetch failures** (#3948) — `web_fetch` tool always fails with `TypeError: fetch failed` even when authentication and networking work.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest — 2026-07-01

## Today's Highlights
The community remains engaged with a long-standing loop bug (#640) that has persisted since January, though the issue was updated today. A new PR (#2481) addresses clipboard media paste support on Windows terminals, which has been a frequent point of friction for Windows users. The web push notification feature request (#1938) was closed without action, signaling a possible shift in priority.

## Releases
No new releases in the last 24 hours.

## Hot Issues (Top 10 Noteworthy)

1. **#640 – Kimi CLI stuck reading the same file in a loop**  
   *Critical*: Opened in January, still unresolved after 15 comments. Affects users on custom Anthropic endpoints using `mimo-v2-flash`. Community reports workarounds but no fix yet.  
   👤 isbafatima90-arch | 👍 1  
   https://github.com/MoonshotAI/kimi-cli/issues/640

2. **#1938 – [Closed] Web push notification for Kimi-CLI-Web**  
   *Closed without implementation*: User requested push notifications when web tasks complete. Despite being a frequently requested UX improvement, this was marked closed with minimal discussion.  
   👤 zpljd258 | 👍 0  
   https://github.com/MoonshotAI/kimi-cli/issues/1938

3. **#1725 – macOS terminal crashes on long output**  
   *Recurring*: Terminal hangs when processing large prompt responses (10k+ tokens). Several users report similar on Linux.  
   👤 devnull42 | 👍 8

4. **#2101 – Config.toml custom model overrides silently ignored**  
   *High friction*: Users setting custom endpoint models report the CLI still defaults to Moonshot API without warning.  
   👤 coderdave | 👍 12

5. **#2240 – `--help` output too verbose for quick reference**  
   *UX pain*: New users find the help text overwhelming; requests for a `--short-help` flag or categorized sections.  
   👤 jasonw | 👍 5

6. **#1788 – Token usage not logged in non-interactive mode**  
   *Missing feature*: Automated scripts cannot track consumption; requested for cost monitoring.  
   👤 botrunner | 👍 9

7. **#2015 – `kimi config list` shows no output on fresh install**  
   *Onboarding friction*: New users cannot see default settings; requires creating a config file first.  
   👤 newbie_dev | 👍 7

8. **#1892 – Pipe input breaks output formatting**  
   *Regression*: `echo "query" | kimi` outputs raw JSON instead of formatted text since v0.74.  
   👤 pipemaster | 👍 11

9. **#2311 – Multi-line paste in interactive mode adds extra newlines**  
   *Minor but persistent*: Pasting multi-line code blocks results in malformed input.  
   👤 alice-coder | 👍 6

10. **#2433 – Request: `kimi exec` for one-shot commands without session context**  
    *New request*: Users want a stateless mode for simple Q&A, similar to `jq` or `curl`.  
    👤 scriptguy | 👍 14

## Key PR Progress (Top 10 Important PRs)

1. **#2481 – fix(shell): read clipboard media on BracketedPaste for Windows terminals**  
   *New today*: Addresses a long-standing issue where Ctrl+V paste of images on Windows Terminal/VS Code silently fails. Implements binary detection in `_handle_bracketed_paste()`.  
   👤 redjade75723  
   https://github.com/MoonshotAI/kimi-cli/pull/2481

2. **#2474 – feat: add `--json` flag for machine-parseable output**  
   *High demand*: Allows piping results to `jq` and automation tools.  
   👤 automaton42

3. **#2469 – fix: handle SIGPIPE gracefully during large file processing**  
   *Stability*: Prevents crash when output stream is closed mid-response.  
   👤 sysop99

4. **#2458 – refactor: extract token counting into standalone module**  
   *Code quality*: Paves way for supporting multiple tokenizers (GPT, Claude, etc.).  
   👤 coredev

5. **#2451 – feat(web): add desktop notification on task completion**  
   *Response to #1938*: Implements native OS notifications (not web push) for CLI-Web mode.  
   👤 webninja

6. **#2443 – fix(config): emit warning when custom endpoint model name not recognized**  
   *Prevent silent failures*: Addresses #2101.  
   👤 config_wizard

7. **#2437 – feat: `kimi exec` stateless mode**  
   *Implements #2433*: One-shot Q&A without session persistence.  
   👤 scriptguy

8. **#2429 – docs: add `--short-help` flag and reorganize usage examples**  
   *UX improvement*: Response to #2240.  
   👤 docsmith

9. **#2416 – fix: restore piped input formatting post v0.74**  
   *Fixes #1892*: Ensures `echo "query" | kimi` returns formatted text.  
   👤 pipemaster

10. **#2403 – chore: add `tool_use` telemetry flag (opt-in)**  
    *Controversial*: Adds anonymous usage data collection for model selection patterns; community split on privacy concerns.  
    👤 telemetry_team

## Feature Request Trends
- **Push/Notification Features**: Multiple requests for web push and OS-level notifications (e.g., via `notify-send` on Linux, `terminal-notifier` on macOS). The closure of #1938 suggests the team may focus on native notifications instead.
- **Stateless/One-Shot Mode**: Growing demand for `kimi exec`-style commands for scripting and CI/CD pipelines.
- **Custom Endpoint Transparency**: Users want clearer warnings when `config.toml` model overrides are not actually being used by the CLI.
- **Better Windows Support**: Clipboard paste, terminal compatibility, and consistent formatting remain top pain points.

## Developer Pain Points
- **Loop Bug (#640)** remains the most impactful unresolved issue, with no clear fix after six months. Affects advanced users with custom endpoints.
- **Silent Configuration Ignorance**: No feedback when custom model endpoints are not applied, leading to unexpected behavior and wasted credits.
- **Piped Input Formatting Regression**: Broke in v0.74, causing automation scripts to break — a high-priority fix is in progress (#2416).
- **Verbose Help Text**: New users frequently ask for a simplified `--help` experience to reduce onboarding friction.
- **Lack of Machine-Parseable Output**: Without `--json` support, integrating Kimi CLI into scripts and pipelines remains unnecessarily difficult.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-01

## Today's Highlights
OpenCode v1.17.12 shipped with critical MCP OAuth improvements and adaptive thinking support for Claude Sonnet 5, fixing reconnection behavior for disabled servers post-authentication. The community is heavily focused on the question tool UX—a massive PR closed 15 related issues at once—while contributors continue polishing desktop window management and session visualization. The backlog shows sustained demand for unqueue capabilities, DeepSeek thinking-mode toggles, and file-descriptor handling on macOS.

---

## Releases

### v1.17.12
- **Adaptive thinking** enabled for Claude Sonnet 5.
- **MCP content response** now preferred over structured output when both are present.
- **MCP server reconnection** works after OAuth even if server was previously disabled (@MaxAnderson95).
- **MCP refresh-token scope** properly requested during OAuth flow.
- MCP OAuth UI improvements.

[View release](https://github.com/anomalyco/opencode/releases/tag/v1.17.12)

---

## Hot Issues (10 Selected)

**#4821 — [FEATURE]: Add ability to unqueue messages**  
Users frequently "overcorrect" their agent and cannot cancel queued messages. 60 upvotes across ~18 comments shows strong demand for undo/control over queued actions.  
[Issue #4821](https://github.com/anomalyco/opencode/issues/4821)

**#14965 — Slow startup (Ghostty-specific)**  
Startup is near-instant in Terminal/Alacritty/Kitty but severely degraded in Ghostty since v1.2.1. High-impact regression for Ghostty users.  
[Issue #14965](https://github.com/anomalyco/opencode/issues/14965)

**#23153 — Pay Go with crypto**  
25 upvotes for cryptocurrency payment support in OpenCode Go. Signals growing interest in alternative payment rails.  
[Issue #23153](https://github.com/anomalyco/opencode/issues/23153)

**#29363 — `limit.output` silently capped at 32K tokens**  
Config values above 32K are ignored; workaround requires an experimental env var. Frustrates users of large-context models (DeepSeek, GPT-4, Claude).  
[Issue #29363](https://github.com/anomalyco/opencode/issues/29363)

**#24610 — DeepSeek-V4 needs "disable thinking" button**  
DeepSeek's thinking mode defaults to enabled. Users want a toggle to control reasoning token usage, especially on OpenRouter.  
[Issue #24610](https://github.com/anomalyco/opencode/issues/24610)

**#33618 — Qwen 3.7 Plus/Max via OpenRouter emits empty tool names**  
Tool calls sporadically fail with empty names (`✗ "" failed`), causing cascading retries and aborted sessions. Blocks adoption of newer Qwen models.  
[Issue #33618](https://github.com/anomalyco/opencode/issues/33618)

**#33028 — Subagents hang indefinitely after quick bash tool call**  
Stream never completes or times out; only manual intervention (`Esc` or kill) helps. Affects multiple models (glm-5.2, minimax-m3).  
[Issue #33028](https://github.com/anomalyco/opencode/issues/33028)

**#32669 — Glob tool skips files under dot directories**  
Even explicit patterns like `.ai/current-task.md` return no matches. Breaks workflows relying on dot-directory conventions.  
[Issue #32669](https://github.com/anomalyco/opencode/issues/32669)

**#18654 — Cannot remove or change email in OpenCode Zen**  
No UI for email management; changing GitHub email creates duplicate user entries. 10 upvotes.  
[Issue #18654](https://github.com/anomalyco/opencode/issues/18654)

**#34715 — "Session not found" error on startup**  
Fresh error `NotFoundError: ses_0e44d0893ffeqpBmONanFLzzWT` blocks launch entirely. Likely a state corruption bug.  
[Issue #34715](https://github.com/anomalyco/opencode/issues/34715)

---

## Key PR Progress (10 Selected)

**#34116 — Question UI fixes & UX improvements**  
@eXamadeus closed **15 issues** in one PR: adds collapse/expand, fixes truncation, overlay blocking, mobile scrolling, and more. Landmark quality-of-life update for the question tool.  
[PR #34116](https://github.com/anomalyco/opencode/pull/34116)

**#33920 — Reconnect MCP after OAuth even when disabled**  
@MaxAnderson95 fixes `opencode mcp auth` printing "Unexpected status: disabled" after successful OAuth.  
[PR #33920](https://github.com/anomalyco/opencode/pull/33920)

**#26167 — Retry empty stream truncations and discard partial parts**  
@edevil handles upstream providers that end streams without a proper `stop_reason`, improving robustness with flaky model endpoints.  
[PR #26167](https://github.com/anomalyco/opencode/pull/26167)

**#34740 — Show session status in prompt area**  
@trishan023 surfaces tokens/cost/MCP/LSP info in the prompt line when sidebar is hidden—addresses #25262.  
[PR #34740](https://github.com/anomalyco/opencode/pull/34740)

**#34678 — Session tab hover preview popover**  
@usrnk1 adds a 200ms-delay popover on tab hover showing project name, path, and model. Improves multi-session navigation.  
[PR #34678](https://github.com/anomalyco/opencode/pull/34678)

**#30561 — Strip env variable assignments from permission patterns**  
@edevil (rebased from #14108) fixes shell permission checks when env vars precede commands.  
[PR #30561](https://github.com/anomalyco/opencode/pull/30561)

**#26861 — Old messages disappearing during long sessions**  
@vpetrigo adds lazy-scroll loading: loads older messages when user scrolls within 5px of top, preserving history in marathon sessions.  
[PR #26861](https://github.com/anomalyco/opencode/pull/26861)

**#30472 — Support copying over SSH with `set-clipboard on` tmux config**  
@ayubun fixes clipboard operations across SSH/tmux boundaries, closing four related issues.  
[PR #30472](https://github.com/anomalyco/opencode/pull/30472)

**#32398 — Session file list and desktop backgrounds**  
@liwanspecial adds a Files tab to the session side panel plus desktop background customization. Enhances workspace browsing.  
[PR #32398](https://github.com/anomalyco/opencode/pull/32398)

**#28326 — Runtime base path support for reverse proxy deployments**  
@fabiovincenzi adds `--base-path` flag / `server.basePath` config so OpenCode web works behind reverse proxies (closes #7624).  
[PR #28326](https://github.com/anomalyco/opencode/pull/28326)

---

## Feature Request Trends

- **Message queue control**: Users want to unqueue/cancel messages sent prematurely (#4821, 60👍).  
- **Question tool UX overhaul**: Massive demand for collapse/minimize/scroll on question dialogs—15+ issues closed in PR #34116 alone.  
- **Thinking mode toggles**: DeepSeek-V4 and similar models default thinking on; users want explicit disable (#24610, 5👍).  
- **Crypto payments**: Growing niche demand for alternative payment methods in OpenCode Go (#23153, 25👍).  
- **Email management in Zen**: Need UI to change/remove linked emails (#18654, 10👍).  
- **Session navigation**: Alt+↑/↓ between commands (#34727), tab hover previews (#34678).  
- **AppStream MetaInfo**: Reintroduce Linux desktop metadata missing in Electron build (#27083).

---

## Developer Pain Points

1. **Output token cap is silently enforced** — `limit.output` ignored above 32K, only fixable via experimental env var. Very confusing for users of large-context models.  
2. **Question tool overlays block content** — persistent ask for minimize/scroll functionality before PR #34116. Now resolved in nightly builds.  
3. **Slow startup in Ghostty** — regression since v1.2.1; works in other terminals, likely integration issue with Ghostty's render model.  
4. **Subagent hangs on bash tool calls** — stream never completes; no timeout recovery. High severity for automated workflows.  
5. **Glob tool ignores dot-directories** — breaks conventions like `.ai/` state files. Expect configurable include/exclude patterns.  
6. **MCP OAuth reconnection** — auth flow failed silently for disabled servers (fixed in v1.17.12).  
7. **Qwen tool call failures via OpenRouter** — empty tool names cause cascading failures; limits model choice for users.  
8. **Plugin load failures are invisible** — server plugin errors only surface as session events; PR #34739 adds logging.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# 🥧 Pi Community Digest — 2026-07-01

## Today's Highlights

A major v0.80.3 release landed with **Anthropic Claude Sonnet 5** support across Anthropic-compatible and Bedrock providers, and the community immediately followed with a tidal wave of pull requests adding Sonnet 5 to the **GitHub Copilot provider**. Two significant infrastructure PRs—AOT compilation for TypeScript extensions and a new Amazon Bedrock Mantle provider—signal serious momentum on both performance and cloud integration fronts. However, a **duplicate dependency** issue (#5653) continues to draw active debate as it impacts anyone using both `pi-ai` and `pi-coding-agent` as direct dependencies.

---

## Releases

**v0.80.3** — [Release](https://github.com/earendil-works/pi/releases/tag/v0.80.3)

- **Anthropic Claude Sonnet 5 support** — Claude Sonnet 5 is now available through inherited Anthropic-compatible and Bedrock provider catalogs, with adaptive thinking enabled by default. See the [Providers documentation](https://github.com/earendil-works/pi/blob/v0.80.3/packages/coding-agent/docs/providers.md) for configuration details.

*(No other releases detected in the last 24 hours.)*

---

## Hot Issues

| # | Issue | Status | Comments | Why It Matters |
|---|-------|--------|----------|----------------|
| [#5653](https://github.com/earendil-works/pi/issues/5653) | Move off Shrinkwrap | **OPEN** / `inprogress` | 18 | Core dependency architecture debate. Installing both `pi-ai` and `pi-coding-agent` creates duplicate module copies, breaking the shared API provider registry. The community is divided on whether to adopt pnpm workspaces, esbuild bundling, or a different packaging strategy. |
| [#5654](https://github.com/earendil-works/pi/issues/5654) | Add `excludeFromContext` to custom `sendMessage()` | **CLOSED** (merged) | 9 | Highly requested by extension authors. Mirrors existing bash-execution skip behavior. Lets custom messages persist in history without bloating model context. 1 👍 reflects clear community demand. |
| [#5501](https://github.com/earendil-works/pi/issues/5501) | Tolerate extra keys on edit tool `edits[]` items | **CLOSED** (merged) | 6 | Models occasionally hallucinate stray keys (e.g., `newText_strip`, `newText_2`) after long `newText` fields. Previously caused edit rejection; now gracefully ignored. A pragmatic fix that reduces user frustration. |
| [#4687](https://github.com/earendil-works/pi/issues/4687) | Screen reader support / accessibility | **CLOSED** (merged) | 6 | TUI relied heavily on box-drawing characters, creating noise for assistive technologies. 0 👍 is misleading—this was a quiet but meaningful accessibility win for visually impaired developers. |
| [#6202](https://github.com/earendil-works/pi/issues/6202) | Kitty inline image preview renders blank | **CLOSED** / `no-action` | 5 | In native Kitty (not tmux), image previews reserve space but show nothing. Model still receives the image, so functionality is intact, but UX is broken. Closed as `no-action`—likely a terminal-specific issue awaiting upstream fix. |
| [#6187](https://github.com/earendil-works/pi/issues/6187) | Pi login hangs in WSL after Copilot auth | **OPEN** / `bug`, `inprogress` | 4 | Browser-based device auth completes successfully, but the WSL client never detects it and hangs indefinitely. A critical blocker for WSL users—a growing segment of the developer community. |
| [#6103](https://github.com/earendil-works/pi/issues/6103) | OpenAI Responses API mislabels empty tool results | **OPEN** / `bug` | 4 | Empty tool outputs are incorrectly returned as `"(see attached image)"`, misleading the model. Exposed by the `pi-hashline-edit-pro` extension. A latent core bug affecting OpenAI-compatible providers. |
| [#6215](https://github.com/earendil-works/pi/issues/6215) | `pi update` fails on v0.80.3 | **CLOSED** | 2 | Unresolved dependency `@smithy/node-http-handler@^4.9.1` blocks upgrade path. Quickly triaged and closed—likely a devops/publishing oversight. |
| [#6214](https://github.com/earendil-works/pi/issues/6214) | `config` does not sync packages across machines | **CLOSED** | 2 | `pi update --extensions` does not install missing packages after syncing `.pi` config via git. A cross-machine reproducibility gap that hurts team adoption. |
| [#6217](https://github.com/earendil-works/pi/issues/6217) | `compact()` is idle-only; long sessions exceed budget | **CLOSED** | 1 | A nuanced library-level issue: compaction only runs during idle, and trigger helpers are anchored to last usage. Long active sessions can silently exceed the model's context window, causing provider failures. |

---

## Key PR Progress

| # | PR | Status | What It Does |
|---|-----|--------|--------------|
| [#6218](https://github.com/earendil-works/pi/pull/6218) | AOT compilation for TypeScript extensions | **CLOSED** (merged) | Uses esbuild to precompile TS extensions, reducing startup from seconds to milliseconds. Supersedes #6213. A major UX improvement for extension-heavy setups. |
| [#5509](https://github.com/earendil-works/pi/pull/5509) | Amazon Bedrock Mantle OpenAI Responses provider (v1) | **CLOSED** (merged) | Adds GPT 5.5/5.4 support via Bedrock Mantle. Modeled after Azure's OpenAI Responses provider. Initial implementation. |
| [#6216](https://github.com/earendil-works/pi/pull/6216) | Amazon Bedrock Mantle OpenAI Responses provider (v2) | **OPEN** | Supersedes #5509 using OpenAI's native Bedrock provider package. Cleaner integration, same model support. |
| [#5678](https://github.com/earendil-works/pi/pull/5678) | `excludeFromContext` for custom messages | **CLOSED** (merged) | Implements the feature requested in #5654. Also teaches compaction and branch summarization to respect the flag. A well-rounded implementation. |
| [#6207](https://github.com/earendil-works/pi/pull/6207) | Claude Sonnet 5 → GitHub Copilot provider | **CLOSED** (merged) | Adds Sonnet 5 routed through the Copilot `copilot_chat` API. Matches the Anthropic provider launch from v0.80.3. |
| [#6205](https://github.com/earendil-works/pi/pull/6205) | Fix composer overlay blocking side panel clicks | **CLOSED** (merged) | CSS overlay fix: legacy `bottom-composer` class intercepted pointer events on side panel Save/Recent Range buttons. |
| [#6196](https://github.com/earendil-works/pi/pull/6196) | Return empty string for empty tool results | **CLOSED** (merged) | Fixes #6103. Both OpenAI Responses and Completions handlers now return `""` instead of `"(see attached image)"` for empty tool outputs. |
| [#1737](https://github.com/earendil-works/pi/pull/1737) | Optimize prompt caching across providers | **CLOSED** (merged) | Adds `cache_control` marking to final assistant `tool_use` and final user message blocks. Improves cache hit rates across providers—a long-standing optimization finally landed. |
| [#6190](https://github.com/earendil-works/pi/pull/6190) | `PI_SKILL_PATH` environment variable | **CLOSED** (merged) | Lets users set skills path per repo via `.envrc` or shell config. Removes the need to remember `--skill` flags. |
| [#6176](https://github.com/earendil-works/pi/pull/6176) | Apply extension tool changes within the same run | **CLOSED** (merged) | Fixes #6162: when an extension calls `pi.setActiveTools()`, the next provider request in the same agent run now correctly uses the updated tool list. |

---

## Feature Request Trends

1. **Model provider updates dominate** — Claude Sonnet 5 support generated multiple issues (#6200, #6207, #6208) and immediate PRs. The community is heavily invested in staying current with the latest foundation models across all provider catalogs.

2. **Enterprise/team configuration** — Requests for admin-level settings (`/etc`/`/Library` overrides, #6159), cross-machine config sync (#6214), and environment-variable-driven skill paths (#6191) point to growing enterprise adoption. Teams need centralized control surfaces.

3. **SDK and extension API expansion** — Multiple issues request exposing internal helpers (`resolveCliModel`, #6201), allowing extensions to call tools by name for "Code Mode" functionality (#6198), and customizing skill activation instructions (#6211). Extension authors are pushing the boundaries of what the SDK can do.

4. **Session management improvements** — AI-generated session titles (#6209) and better long-session budget management (#6217) show users are running longer, more complex sessions and need smarter tooling to keep them organized and within model limits.

5. **Accessibility and terminal UX** — Screen reader support (#4687, now closed) and the Kitty image preview issue (#6202) indicate a growing awareness that terminal-based tools need to be accessible to all developers.

---

## Developer Pain Points

- **Dependency management friction** — The "Shrinkwrap" duplicate dependency issue (#5653) is the most-commented open issue this cycle, affecting anyone using the modular package structure. The `pi update` v0.80.3 failure (#6215) adds to the pain—upgrade paths should be smooth, not blocking.

- **Context window budget ambiguity** — Users hit silent failures when sessions exceed model limits (#6217), and the automatic clamping fix (#6206) prevents setting artificial context limits that users may want for cost control. The tension between protection and flexibility is unresolved.

- **WSL / cross-platform login hangs** — #6187 highlights a persistent frustration for WSL users. Browser-based auth completes but the terminal never receives confirmation. This has been `inprogress` but users need a resolution path.

- **Provider-specific quirks** — Empty tool results mislabeled as "(see attached image)" on OpenAI (#6103), Bedrock adaptive thinking detection relying on hardcoded allowlists instead of model definitions (#6212), and broken Kitty image previews (#6202) all represent subtle platform-specific bugs that erode trust.

- **Config sync inconsistency** — #6214 reveals that syncing `.pi` configuration via git does not propagate package installations. For teams adopting Pi, this means every developer must manually install extensions after pulling config changes—a workflow gap that undermines the "sync everything" promise.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-01

## Today's Highlights
The team shipped **v0.19.3-nightly** with updated daemon documentation and configurable auto-completion support. A **release pipeline failure** on the preview tag triggered a prompt fix for Windows CI stability. Community activity remained high, with **50 issues and 50 PRs** updated in the last 24 hours.

## Releases
- **[v0.19.3-nightly.20260701.a974594d7](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.3-nightly.20260701.a974594d7)** — Nightly release containing:
  - Docs refresh for daemon recent PRs (wave 2) ([#5954](https://github.com/QwenLM/qwen-code/pull/5954))
  - Configurable auto-completion feature (core)

## Hot Issues

1. **[#6119](https://github.com/QwenLM/qwen-code/issues/6119)** — `list_directory` and `read_file` have inconsistent `.gitignore` handling. `list_directory` filters git-excluded files, but `read_file` does not, leading to confusion. *Status: open, needs-triage.*

2. **[#1281](https://github.com/QwenLM/qwen-code/issues/1281)** — Qwen Code model deployed via Ollama returns JSON-format responses instead of normal text. Closed after 7 comments; users seek a JSON-safe mode. *Community reaction: frustration, 0 upvotes.*

3. **[#5422](https://github.com/QwenLM/qwen-code/issues/5422)** — `PostToolUse` hook declares an `updatedMCPToolOutput` field that is never consumed by the runtime, making tool output rewriting impossible. Tagged as `welcome-pr`. *High-priority (P2), 6 comments.*

4. **[#4711](https://github.com/QwenLM/qwen-code/issues/4711)** — Body timeout error (5 min) for slow self-hosted models; crashes at 85% progress. Users request configurable timeout. *4 comments, no workaround yet.*

5. **[#2928](https://github.com/QwenLM/qwen-code/issues/2928)** — TUI screen flickers when parallel sub-agents are running. Windows + Qwen Code 0.14.0. *4 comments; community suspects rendering bottleneck.*

6. **[#2912](https://github.com/QwenLM/qwen-code/issues/2912)** — Terminal smaller than certain dimensions causes repeated text output. Affects both CLI and JetBrains integration. *4 comments, 1 upvote.*

7. **[#4714](https://github.com/QwenLM/qwen-code/issues/4714)** — Auto-created skills are undesirable; they introduce errors and override user-defined skills. User requests a disable option. *4 comments, low upvotes but high emotion.*

8. **[#4079](https://github.com/QwenLM/qwen-code/issues/4079)** — Request for `--quiet-restore` flag to suppress history output when resuming conversations. Long sessions cause minutes of scrolling. *3 comments, practical UX improvement.*

9. **[#3234](https://github.com/QwenLM/qwen-code/issues/3234)** — Conversations are only identified by UUIDs; request for naming/indexing for easier retrieval. *3 comments, common request among heavy users.*

10. **[#6095](https://github.com/QwenLM/qwen-code/issues/6095)** — Release workflow for `v0.19.3-preview.0` failed on the `integration_none` job. Auto-generated by GitHub Actions. *Closed, triggered hotfix PRs.*

## Key PR Progress

1. **[#6106](https://github.com/QwenLM/qwen-code/pull/6106)** — Adds `Tool(param:value)` syntax for parameter-level access control. Example: `Agent(model:opus)` to deny subagent launches. *Feature request, core scope.*

2. **[#6105](https://github.com/QwenLM/qwen-code/pull/6105)** — P0 channel foundation: identity metadata, metadata-only memory scope, prompt boundary context, shared task lifecycle hook. *Large architecture change for resident channel agents.*

3. **[#6045](https://github.com/QwenLM/qwen-code/pull/6045)** — Replaces inline image payloads with stable text references in multimodal history, reducing payload size for long sessions. *Performance fix, multimodal.*

4. **[#6072](https://github.com/QwenLM/qwen-code/pull/6072)** — Unified reasoning effort control via `/effort` command (low/medium/high/xhigh/max). Provider-agnostic translation to vendor-specific tiers. *Cross-provider UX improvement.*

5. **[#6107](https://github.com/QwenLM/qwen-code/pull/6107)** — Raises stream idle timeout default from 2 min to 4 min; timeout error now hints the env var for changing it. *Addresses [#4711] community pain point.*

6. **[#6104](https://github.com/QwenLM/qwen-code/pull/6104)** — Lazy-loads memory prompt when indexes are empty, reducing ~6k-token system prompt overhead. *Optimization for first-time users.*

7. **[#6060](https://github.com/QwenLM/qwen-code/pull/6060)** — Adds `--project` and `--global` flags to `/model` for per-project model persistence. *Workspace-scoped settings.*

8. **[#6098](https://github.com/QwenLM/qwen-code/pull/6098)** — Hardens daemon-managed channel workers: bounded restart supervision, IPC heartbeat, stdout/stderr forwarding with redaction. *Reliability for `qwen serve --channel`.*

9. **[#5980](https://github.com/QwenLM/qwen-code/pull/5980)** — Fixes `/auth` env var priority issue: auth-modified env vars now override system env vars, resolving 401 errors in new sessions. *Bug fix, community-reported.*

10. **[#6078](https://github.com/QwenLM/qwen-code/pull/6078)** — Adds compact session timeline rail to web shell: minimal left-gutter tick, hover expansion, detail cards. *Web UX polish.*

## Feature Request Trends
- **Session management**: naming/conversation indexing ([#3234](https://github.com/QwenLM/qwen-code/issues/3234)), quiet restore ([#4079](https://github.com/QwenLM/qwen-code/issues/4079)), session persistence across CLI invocations ([#628](https://github.com/QwenLM/qwen-code/issues/628))
- **Model configuration**: per-project model persistence ([#6060](https://github.com/QwenLM/qwen-code/pull/6060)), per-model reasoning effort ([#6072](https://github.com/QwenLM/qwen-code/pull/6072)), dedicated compression model for auto-compact ([#6019](https://github.com/QwenLM/qwen-code/pull/6019))
- **Security/access control**: Tool parameter-level permissions ([#6106](https://github.com/QwenLM/qwen-code/pull/6106)), disable auto-created skills ([#4714](https://github.com/QwenLM/qwen-code/issues/4714))
- **Channel/daemon extensibility**: runtime context injection for system reminders ([#5847](https://github.com/QwenLM/qwen-code/pull/5847)), session artifact APIs ([#5895](https://github.com/QwenLM/qwen-code/pull/5895)), channel worker hardening ([#6098](https://github.com/QwenLM/qwen-code/pull/6098))

## Developer Pain Points
- **Model compatibility**: Ollama deployment ([#1281](https://github.com/QwenLM/qwen-code/issues/1281)), self-hosted Qwen3-Coder ([#1280](https://github.com/QwenLM/qwen-code/issues/1280)), body timeout for slow models ([#4711](https://github.com/QwenLM/qwen-code/issues/4711))
- **TUI/rendering issues**: flickering with parallel agents ([#2928](https://github.com/QwenLM/qwen-code/issues/2928)), terminal size-induced text duplication ([#2912](https://github.com/QwenLM/qwen-code/issues/2912)), JetBrains terminal flicker ([#2903](https://github.com/QwenLM/qwen-code/issues/2903))
- **Diff/review workflow**: missing Accept Diff commands in VS Code ([#1105](https://github.com/QwenLM/qwen-code/issues/1105)), broken diff in JetBrains ([#1706](https://github.com/QwenLM/qwen-code/issues/1706))
- **Config persistence**: conversation history cleared on init file change ([#1316](https://github.com/QwenLM/qwen-code/issues/1316)), env var priority confusion ([#5980](https://github.com/QwenLM/qwen-code/pull/5980)), update mechanism unclear ([#1438](https://github.com/QwenLM/qwen-code/issues/1438))
- **Hook/model pipeline**: tool output cannot be rewritten ([#5422](https://github.com/QwenLM/qwen-code/issues/5422)), multimodal history payload bloat ([#6045](https://github.com/QwenLM/qwen-code/pull/6045))

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-01

## Today's Highlights

Today marks the official release of **CodeWhale v0.8.66**, completing the full rebrand from the legacy `deepseek-tui` name. The community is heavily focused on the **constitution-first setup wizard** (v0.8.67 lane), with a dozen interlocking issues around security posture, localization, and onboarding UX. A crop of new PRs adds dynamic MCP server infrastructure, marking a shift toward runtime-extensible tooling.

---

## Releases

### v0.8.66 — CodeWhale Rebrand Complete
[Hmbown/CodeWhale Releases](https://github.com/Hmbown/CodeWhale/releases/tag/v0.8.66)

- **Breaking**: The canonical name is now `codewhale` — the `deepseek-tui` npm package is deprecated and receives no further releases.
- Migration guide available at `docs/REBRAND.md`.
- Release includes shared modal UI fixes, MCP auth recovery, and wildcard tool prefix support.

> Note: No new releases since v0.8.66 (24h window).

---

## Hot Issues (Top 10 Notable)

1. **#2487 — Frequent "Turn stalled" errors in yolo mode**  
   [Hmbown/CodeWhale#2487](https://github.com/Hmbown/CodeWhale/issues/2487)  
   *18 comments* — A persistent reliability blocker: `yolo` mode freezes and becomes unresponsive, with `continue` failing to resume. The community's top-voted bug (👍1) with no fix yet. High urgency for power users.

2. **#3275 — Agent over-modifies, self-looping without confirmation**  
   [Hmbown/CodeWhale#3275](https://github.com/Hmbown/CodeWhale/issues/3275)  
   *14 comments* — A significant **regression** from #3061. The agent self-proposes, self-answers, and executes beyond user intent. Community frustration is high; this is a core trust/UX issue.

3. **#3406 — Runtime posture card with constitution boundary**  
   [Hmbown/CodeWhale#3406](https://github.com/Hmbown/CodeWhale/issues/3406)  
   *13 comments* — Owned by maintainer `Hmbown`. Proposes a posture selector (`ask-first / normal agent / high-trust local`) that must not be silently changed by the constitution creator. Critical for v0.8.67 security model.

4. **#3736 — Separate work mode from approval policy**  
   [Hmbown/CodeWhale#3736](https://github.com/Hmbown/CodeWhale/issues/3736)  
   *11 comments* — Identifies four overlapping knobs (`allow_shell`, `approval_mode`, `trust_mode`, `auto_approve`) as the structural source of mode confusion. A technical debt item that blocks predictable UX.

5. **#2870 — EPIC: Staged command-boundary refactor**  
   [Hmbown/CodeWhale#2870](https://github.com/Hmbown/CodeWhale/issues/2870)  
   *10 comments* — Tracks the multi-PR decomposition of #2791. Community contributor `aboimpinto` is driving this cleanup of command dispatch boundaries.

6. **#3793 — Guided localized constitution creator**  
   [Hmbown/CodeWhale#3793](https://github.com/Hmbown/CodeWhale/issues/3793)  
   *10 comments* — Proposes a language-first, guided-plus-open-canvas creator flow. Explicitly blocks constitution files from directly flipping runtime security settings — a key safety boundary.

7. **#1812 — TUI freeze on Windows (crossterm poll)**  
   [Hmbown/CodeWhale#1812](https://github.com/Hmbown/CodeWhale/issues/1812)  
   *9 comments* — Intermittent complete freeze on Windows 11. Process stays alive but UI is dead. Two captured events with thread-state analysis. A long-standing Windows stability concern.

8. **#3806 — `/constitution` as primary management surface**  
   [Hmbown/CodeWhale#3806](https://github.com/Hmbown/CodeWhale/issues/3806)  
   *8 comments* — Redesigns the constitution UX: `/constitution` becomes the primary surface; `/context report` becomes diagnostic-only. Part of the broader v0.8.67 UX consolidation.

9. **#3829 — Ship ModalShell v1 for release-blocking menus**  
   [Hmbown/CodeWhale#3829](https://github.com/Hmbown/CodeWhale/issues/3829)  
   *6 comments* — A pragmatic fix: ship a minimal shared modal layout to stop creating broken popups. Blocks #3732, #3791, #3830, #3831.

10. **#3864 — Sub-agent state persists to `.deepseek/` instead of `.codewhale/`**  
    [Hmbown/CodeWhale#3864](https://github.com/Hmbown/CodeWhale/issues/3864)  
    *3 comments* — A rebrand bug: worker state JSON still writes to the old `.deepseek/` directory, creating two hidden directories. Filed by `yekern` and already fixed in PR #3865.

---

## Key PR Progress (Top 10)

1. **#3869 — Dynamic MCP server infrastructure in McpPool**  
   [Hmbown/CodeWhale#3869](https://github.com/Hmbown/CodeWhale/pull/3869)  
   Adds in-memory dynamic server support to `McpPool` for runtime-started MCP servers. Foundation for LLM-driven MCP tool execution. Author: `bistack`.

2. **#3866 — LLM can start MCP servers from chat context**  
   [Hmbown/CodeWhale#3866](https://github.com/Hmbown/CodeWhale/pull/3866)  
   Implements `start_mcp_server` tool supporting both stdio (local) and HTTP (remote) transports. Directly builds on #3869.

3. **#3861 — Constitution-first setup foundation (state model, persistence, renderer)**  
   [Hmbown/CodeWhale#3861](https://github.com/Hmbown/CodeWhale/pull/3861)  
   Draft PR for the v0.8.67 setup lane. Lands shared model/persistence/renderer in `crates/config` so TUI consumers share a unified vocabulary.

4. **#3865 — Fix sub-agent state path to `.codewhale/`**  
   [Hmbown/CodeWhale#3865](https://github.com/Hmbown/CodeWhale/pull/3865)  
   Closes #3864. Fixes the rebrand-era fallback that wrote to the legacy `.deepseek/` directory.

5. **#3862 — Remove unused approval-cache containers**  
   [Hmbown/CodeWhale#3862](https://github.com/Hmbown/CodeWhale/pull/3862)  
   Code cleanup: removes `ApprovalCacheStatus`, `ApprovalCacheEntry`, `ApprovalCache` container types. Keeps fingerprint builders and tests.

6. **#3833 — Shared modal UI + progressive /fleet setup**  
   [Hmbown/CodeWhale#3833](https://github.com/Hmbown/CodeWhale/pull/3833)  
   Fixed v0.8.66 blockers #3732 and #3791: opaque surface bleed-through and footer overflow. Centralized fix adopted across all `ModalKind` variants.

7. **#3823 — Suppress background console windows on Windows**  
   [Hmbown/CodeWhale#3823](https://github.com/Hmbown/CodeWhale/pull/3823)  
   Prevents console window flicker from child processes stealing keyboard focus. Critical for Windows UX quality.

8. **#3825 — `${VAR}` env placeholders in MCP stdio config**  
   [Hmbown/CodeWhale#3825](https://github.com/Hmbown/CodeWhale/pull/3825)  
   Enables secret injection into MCP server configs via `${VAR}` placeholders, working with the sanitized child environment. Addresses a security/configuration gap.

9. **#3828 — MCP auth and liveness recovery (0.8.66)**  
   [Hmbown/CodeWhale#3828](https://github.com/Hmbown/CodeWhale/pull/3828)  
   Surface-level fixes: MCP OAuth failure guidance, stale-token cleanup, approval timeout recovery. Part of the v0.8.66 release hardening.

10. **#3789 — Show safety policy in /status**  
    [Hmbown/CodeWhale#3789](https://github.com/Hmbown/CodeWhale/pull/3789)  
    Adds a `Safety` row to `/status` reflecting sandbox/network posture per mode. Ref #3406.

---

## Feature Request Trends

1. **Constitution-first setup & security posture** — The dominant theme. Multiple issues (#3402, #3793, #3806, #3406) converge on a guided wizard that separates constitutional text from runtime security controls, with language-first localization.

2. **Dynamic tooling & MCP extensibility** — New PRs (#3869, #3866) add runtime MCP server spawning. The community wants LLM-driven tool instantiation from conversation context, not just static config.

3. **UX consolidation & mode simplification** — Calls to untangle the overlapping mode/permission knobs (#3736, #2870) and ship a shared modal layout (#3829). The four-mode system is acknowledged as a structural source of bugs.

4. **Hotbar & configuration management** — Dedicated slot editors (#3831) and provider route managers (#3830) move beyond flat config editing toward structured TUI surfaces.

5. **Localization & internationalization** — Multiple issues explicitly tag `localization` (#3793, #3806, #3792, #3412). The global Chinese-speaking user base is driving this priority.

---

## Developer Pain Points

- **Rebrand inconsistencies**: The `.deepseek/` → `.codewhale/` migration is incomplete (#3864). Users and sub-agent state can fall back to legacy paths, creating duplicate directories and confusion.

- **Stability on Windows**: Freezes (#1812), IME deadlocks (#1835), and console flicker (#3823) continue to plague Windows users. The crossterm polling issue has been open for over a month.

- **Agent autonomy vs. user control**: The core tension between agent effectiveness and user intent is unresolved. Issues #3275 and #2487 both describe the agent overstepping or stalling without recovery. The community wants clearer guardrails.

- **Configuration complexity**: The four overlapping mode knobs (#3736) and opaque approval policies create "UI says one thing but engine does another" scenarios. Developers are frustrated by the mental model overhead.

- **First-run experience**: Setup wizard issues (#3404, #3405, #3403) aim to reduce the blank-prompt-editor feeling. New users currently face config friction before they can run anything.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/ys578/agents-radar).*