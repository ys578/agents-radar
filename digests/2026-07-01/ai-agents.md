# OpenClaw 生态日报 2026-07-01

> Issues: 33 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-06-30 16:24 UTC

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

## OpenClaw 项目深度报告

# OpenClaw 项目日报 | 2026-07-01

---

## 1. 今日速览

项目处于 **高度活跃但压力集中** 的状态。过去24小时新开/活跃 Issue 25 条、关闭 8 条，PR 流水线积压严重（455 条待合并 vs 45 条已合并/关闭），表明社区贡献动能强劲但审查吞吐能力成为瓶颈。今日发布了 **v2026.6.11** 版本，重点强化了频道控制（Slack relay、Mattermost 队列）与运营韧性。值得警惕的是，多个 P1 级回归问题在主线浮现，其中 SSE 缓冲区截断（#98197）和会话失忆（#98156）直接威胁消息可靠性，需优先排期。

---

## 2. 版本发布

### **v2026.6.11** — OpenClaw 2026.6.11

**核心更新：**

- **频道控制增强**：Slack relay 模式、Mattermost 原生 `/oc_queue` 命令、每 DM 模型覆盖能力现已可用（#94707, #95546, #95120）。贡献者：@sjf-oa, @amknight, @xydigit-zt, @thomaszta, @gandalf-at-lerian。
- **运营韧性改进**（信息截断，完整发布说明待补全）。

**迁移注意事项**：该版本为当前最新稳定版，建议升级前检查自定义频道配置与 DM 模型覆盖规则是否兼容。

---

## 3. 项目进展

今日已合并/关闭的 PR（45 条）中，可辨识的重大推进包括：

| 领域 | 进展 | 相关 PR/Issue |
|------|------|-------------|
| 安全审计稳定性 | 修复 `openclaw security audit --deep` 假死问题 | [#83075] |
| 会话可靠性 | 修复回退模型回复未能投递到频道（Feishu 通道） | [#98194] |
| iOS 语音 | 修复 Gateway Default TTS 配置被忽略，错误回退到 Realtime Voice | [#98154] |
| 文档准确性 | 修正 macOS launchd 日志路径文档与实际行为不符 | [#98199] |
| 服务稳定性 | 修复 Molty 托管工作区 "Rose is moving in…" 无限等待 | [#98179] |
| PII 安全 | 新增用户自定义实体词典双向 PII 脱敏功能请求 | [#98157] |

整体来看，近期合并更偏向 **缺陷修复与稳定性和安全门加固**，大的功能特性仍在审查管线中。

---

## 4. 社区热点

### 讨论最热烈的议题

1. **[#48003] Steer mode does not inject messages mid-turn for main sessions** (14 评论, 👍3)
   - 自 3 月起持续讨论，核心诉求是 `steer` 队列模式应在工具边界注入用户消息，而非等待回合完成。涉及 `KeyedAsyncQueue` 引入的回归，影响实时交互体验。

2. **[#38327] "Cannot convert undefined or null to object" with google-vertex/gemini-3.1-pro-preview** (9 评论, 👍3)
   - 3 月报告至今未修复，Google Vertex 路径在特定模型下引发崩溃循环。用户持续等待修复，反映长尾 Provider 兼容性维护压力。

3. **[#94228] Native Anthropic path: replaying historical `thinking` blocks bricks long tool-use threads** (8 评论, 👍1)
   - 6 月 17 日报告，长期多轮工具调用会话会因签名验证失败永久卡死。对重度 Anthropic 用户影响极大。

**热力指标**：评论数和反应量集中在 **消息投递可靠性** 和 **会话状态管理** 两类问题，用户核心痛点是"消息丢失"和"会话僵死"。

---

## 5. Bug 与稳定性

### 🔴 P1 严重问题（待修复）

| Issue | 问题摘要 | 是否有 Fix PR |
|-------|---------|-------------|
| [#98197] | **gpt-5.5 SSE 缓冲区截断**：64 KiB 限制拒绝合法大事件，回归自 #96989，阻塞 6.11 发布 | 待确认 |
| [#98156] | **会话失忆**：abort settle 超时触发 `SessionTakeoverError`，导致完整上下文丢失 | ❌ |
| [#98204] | **子代理回复静默丢弃**：可见文本嵌套在结果负载字段内时被抑制 | ❌ |
| [#98209] | **iOS Talk 将 SecretRef 密钥视作缺失**：ElevenLabs 配置失效 | ✅ [#98210] |
| [#98153] | **iOS Talk 将 Gateway TTS 错认为 realtime voice** | ✅ [#98214] |
| [#48003] | **Steer 模式无法在回合中途注入消息** | ⏳ 长期跟踪 |
| [#94228] | **Anthropic thinking 块重放导致会话永久卡死** | ⏳ 待复现 |

### 🟡 P2 持续关注

| Issue | 问题摘要 | 是否有 Fix PR |
|-------|---------|-------------|
| [#97314] | **Google LLM 路径不轮换 API 密钥** | ❌ |
| [#77093] | **Gmail Pub/Sub 推送在 Docker+Tailscale 下不被处理** | ❌ |
| [#97738] | **Voice Call xAI 转录 Provider 被 OpenAI 运行时覆盖** | ❌ |
| [#93908] | **Feishu 插件报告错误版本号导致跳过发现** | ❌ |
| [#89247] | **Feishu DM 反复泄露内部失败横幅给用户** | ❌ |
| [#79252] | **globalCircuitBreakerThreshold 按工具类型计数而非会话全局** | ❌ |
| [#98166] | **NO_REPLY 哨兵带前导标点时泄漏到频道** | ❌ |
| [#58775] | **google-vertex 在 2026.3.28 被错误合并到 Google AI 传输路径（回归）** | ❌ |

**趋势判断**：6 月最后一周新开 P1 Issue 密度偏高（至少 6 个），且部分涉及主线合并引入的回归，提示预发布测试覆盖需加强。

---

## 6. 功能请求与路线图信号

### 社区驱动的高价值功能 PR

1. **[#97508] feat(durable): add opt-in agent coordination kernel**
   - 面向长时间多代理协作的内核设计，打通 sessions/background tasks/Task Flow/Workboard/subagents。XL 规模，已通过概念验证，处于 "ready for maintainer look"。

2. **[#97485] feat(agents): add iteration budget for agent loop safety**
   - 为 LLM 工具调用轮次增加显式硬预算，解决生产环境中代理无限循环问题。XL 规模，P2，已通过充分证明。

3. **[#95787] fix(cron): add opt-in billing guard probes**
   - 为定时任务引入可选计费保护探针，防止意外费用飙升。

4. **[#95951] fix(google): add google-gemini-cli auth alias and expand model runtime bindings**
   - 修复从其他 Provider 重新上船到 Gemini CLI 后无响应的问题。

5. **[#72129] feat(huggingface): add text-to-image generation**
   - 通过 HF Inference Providers 路由添加文生图能力，含充分证明。

6. **[#69039] add option for MCP apps support**
   - 支持 MCP Apps UI 元数据/资源，补齐 MCP 生态集成短板。XL 规模，P1，等待作者。

**路线图信号**：代理安全加固（循环预算）、持久化协调内核、MCP 生态深化是下一阶段最可能落地的方向。

---

## 7. 用户反馈摘要

### 痛点提炼

- **消息丢失焦虑**：多个 Issue（#98156、#98204、#98194、#77093）均涉及消息静默丢失，用户定期遇到"回复生成了但从未出现在频道"的故障模式，对生产环境信任度造成侵蚀。
- **iOS 语音配置摩擦**：用户抱怨 Gateway 语音 TTS 配置在 iOS 端被错误映射为 realtime voice（#98153、#98154），且 SecretRef 密钥不兼容（#98209），导致多端体验割裂。
- **Feishu 通道质量退化**：#89247 和 #93908 反映 Feishu 直接对话反复向用户泄漏内部错误信息，插件版本检测也存在回归，影响企业 IM 用户的使用信心。
- **Google Provider 长尾维护困难**：#38327（3 月至今未修复）、#58775（Vertex 路径回归）、#97314（密钥不轮换）构成 Google 生态用户的三重打击。
- **正面信号**：社区贡献热情旺盛（455 个开放 PR），且多个修复 PR 附带了充分证明材料（screenshot/video/codex proof），质量意识在提升。

---

## 8. 待处理积压

### ⚠️ 超长待办（>30 天未解决的核心 Issue）

| Issue | 标题 | 报告日期 | 最后更新 | 严重度 |
|-------|------|---------|---------|-------|
| [#48003] | Steer mode 不注入中途消息 | 2026-03-16 | 2026-06-30 | P1 |
| [#38327] | Google Vertex 崩溃循环 "Cannot convert undefined or null" | 2026-03-06 | 2026-06-30 | P1 |
| [#58775] | google-vertex 传输路径合并回归 | 2026-04-01 | 2026-06-30 | P2 |

### ⚠️ 积压 PR（检查数>30 天未合并）

| PR | 标题 | 报告日期 | 状态 |
|----|------|---------|------|
| [#66444] | fix(systemd): reconcile managed-env unit migrations | 2026-04-14 | ⏳ waiting on author |
| [#68129] | Fix delivery-ready verification blockers | 2026-04-17 | 📣 needs proof |
| [#68236] | test(auth): add oauth e2e regression coverage | 2026-04-17 | ⏳ waiting on author |
| [#68843] | fix(acp): treat missing cwd as stale bound session | 2026-04-19 | ⏳ waiting on author |
| [#68967] | feat(googlechat): sessionThread option | 2026-04-19 | ⏳ waiting on author |
| [#69039] | MCP apps support | 2026-04-19 | ⏳ waiting on author |

**提醒**：`等待作者` 状态的 PR 积压量较大，建议维护者批量检查是否需要关闭或接手，避免无限期搁置对贡献者积极性造成打击。455 条开放 PR 的规模本身也提示 **PR 审查管道需扩容或流程调整**。

---

*日报生成：基于 OpenClaw/openclaw 仓库截至 2026-07-01 的公开数据。*

[#48003]: https://github.com/openclaw/openclaw/issues/48003
[#38327]: https://github.com/openclaw/openclaw/issues/38327
[#94228]: https://github.com/openclaw/openclaw/issues/94228
[#98197]: https://github.com/openclaw/openclaw/issues/98197
[#98156]: https://github.com/openclaw/openclaw/issues/98156
[#98204]: https://github.com/openclaw/openclaw/issues/98204
[#98209]: https://github.com/openclaw/openclaw/issues/98209
[#98210]: https://github.com/openclaw/openclaw/pull/98210
[#98153]: https://github.com/openclaw/openclaw/issues/98153
[#98214]: https://github.com/openclaw/openclaw/pull/98214
[#98154]: https://github.com/openclaw/openclaw/issues/98154
[#98194]: https://github.com/openclaw/openclaw/issues/98194
[#98179]: https://github.com/openclaw/openclaw/issues/98179
[#98157]: https://github.com/openclaw/openclaw/issues/98157
[#83075]: https://github.com/openclaw/openclaw/issues/83075
[#98199]: https://github.com/openclaw/openclaw/issues/98199
[#97508]: https://github.com/openclaw/openclaw/pull/97508
[#97485]: https://github.com/openclaw/openclaw/pull/97485
[#95787]: https://github.com/openclaw/openclaw/pull/95787
[#95951]: https://github.com/openclaw/openclaw/pull/95951
[#72129]: https://github.com/openclaw/openclaw/pull/72129
[#69039]: https://github.com/openclaw/openclaw/pull/69039
[#97314]: https://github.com/openclaw/openclaw/issues/97314
[#77093]: https://github.com/openclaw/openclaw/issues/77093
[#97738]: https://github.com/openclaw/openclaw/issues/97738
[#93908]: https://github.com/openclaw/openclaw/issues/93908
[#89247]: https://github.com/openclaw/openclaw/issues/89247
[#79252]: https://github.com/openclaw/openclaw/issues/79252
[#98166]: https://github.com/openclaw/openclaw/issues/98166
[#58775]: https://github.com/openclaw/openclaw/issues/58775
[#66444]: https://github.com/openclaw/openclaw/pull/66444
[#68129]: https://github.com/openclaw/openclaw/pull/68129
[#68236]: https://github.com/openclaw/openclaw/pull/68236
[#68843]: https://github.com/openclaw/openclaw/pull/68843
[#68967]: https://github.com/openclaw/openclaw/pull/68967

---

## 横向生态对比

## 个人 AI 助手 / 自主智能体开源生态横向对比分析报告（2026-07-01）

### 1. 生态全景
当前 AI 智能体开源生态正处于**高活跃、快迭代、强分化**的阶段。主流项目普遍进入“生产可用→稳定加固”的转折期，今日多个项目集中修复消息可靠性、会话状态管理与安全漏洞，表明交付质量正在取代功能堆叠成为核心议题。同时，渠道与平台的碎片化催生了大量适配类贡献（钉钉、飞书、Telegram、Matrix等），模型提供商兼容性（OpenAI/ Anthropic/Google/国产模型）仍是跨项目的通用痛点。OpenClaw 作为头部参照物，面临审查吞吐瓶颈；NanoBot、CoPaw 等中小型项目则展现出敏捷的修复与社区响应能力，整体生态呈现“一超多强、百花齐放”的格局。

### 2. 各项目今日活跃度对比

| 项目 | Issues（新/活/关） | PR（合/开） | 版本发布 | 健康度评估 |
|------|------------------|-------------|---------|-----------|
| **OpenClaw** | 25/8（活跃） | 45/455 | v2026.6.11 | ⚠️ 高压：审查积压严重，P1回归多发 |
| **NanoBot** | 14（新+活） | 35/32 | 无 | ✅ 健康：高修复密度，多条线并行 |
| **Hermes Agent** | 13（新+活） | 3/47 | 无 | ⚠️ 关注：积压PR多，质量加固期 |
| **PicoClaw** | 7（新+活） | 2/5 | nightly | 🔶 温和：快速迭代，兼容性痛点突出 |
| **NanoClaw** | 3（新2+关1） | 1/8 | 无 | ✅ 健康：安全修复快速，生态扩展积极 |
| **NullClaw** | 1（新） | 4/0 | 无 | 🔶 稳定：功能集成收尾，低互动 |
| **IronClaw** | 7（新） | 23/27 | 无 | ✅ 活跃：密集打磨，CI/稳定性并行 |
| **LobsterAI** | 8（新+活） | 14/2 | v2026.6.30 | 🔶 良好：快速收敛，性能问题待解 |
| **CoPaw** | 16（新12+关4） | 22/28 | 无 | ✅ 高活跃：大量修复与特性并进 |
| **ZeroClaw** | 6（新4+关2） | 4/46 | 无 | ⚠️ 积压：审核压力大，重要修复合入 |
| **Moltis** | 0 | 1（自动）/0 | 无 | 🔷 低活跃：纯依赖维护 |
| **TinyClaw** | 0 | 0 | 无 | 🔷 无活动 |
| **ZeptoClaw** | 0 | 0 | 无 | 🔷 无活动 |

*注：PR 合/开 表示今日合并或关闭/仍开放的数量；健康度评估综合活跃度、积压、安全性及稳定风险。*

### 3. OpenClaw 在生态中的定位
OpenClaw 是生态中**事实上的旗舰参照物**。其优势在于：

- **社区规模与贡献量领先**：455条开放PR、单日25+活跃Issue，社区动能远超其他项目。
- **全栈覆盖深度**：频道控制（Slack/Mattermost/飞书）、安全审计、PII脱敏等企业级特性完备。
- **技术路线成熟**：已进入微版本迭代（v2026.6.11），关注运营韧性与回归修复。

与同类相比，OpenClaw 的代价是**运维与审查瓶颈**：PR审查管线严重积压，P1级回归（SSE截断、会话失忆）直接冲击核心体验。NanoBot/CoPaw 等中坚项目在特定领域（如代理可靠性、多通道消息投递）修复速度更快，但整体完整度与生态影响力仍有差距。OpenClaw 的更早起步和更大安装基数使其成为标准制定者，但这也要求其必须尽快解决审查吞吐与预发布测试覆盖率问题，以防被敏捷跟进者蚕食优势。

### 4. 共同关注的技术方向
多个项目在以下方向出现共振：

- **消息投递可靠性与会话状态管理**  
  OpenClaw（#98156/#98194/#98204）、Hermes（飞书/Telegram重复消息）、CoPaw（钉钉送达反馈）、NanoClaw（WhatsApp附件静默丢失）、LobsterAI（多文件选择丢失附件）均面对“消息生成了但没送到”问题，表明**确定性投递与状态恢复**是跨项目一级痛点。

- **多通道/多平台适配与附件处理**  
  从飞书、钉钉到 Matrix/DeltaChat/微信，几乎所有活跃项目都在扩展渠道。附件处理方面，NanoClaw 的 Discord 适配器无法下载图片、CoPaw 的聊天附件免文字触发等反映出**富媒体内容的统一处理抽象**已成为必要建设。

- **代理循环安全与资源控制**  
  OpenClaw 的代理迭代预算（PR #97485）、NanoBot 的代理可靠性层（PR #4534）、CoPaw 的 Loop Engineering Gate（PR #5665）等共同指向**无限循环防护与执行预算管理**，皆因生产环境中代理失控会导致成本与伤害，社区正将其从“可选增强”提升为“必备能力”。

- **安全加固（SSRF、沙箱、凭据泄露）**  
  NanoBot DNS重绑定漏洞（#4611）、PicoClaw 的 ISATAP 绕过（PR #3143）、ZeroClaw zip炸弹防护（#8554）、Hermes 子进程凭据剥离（PR #55709）等，形成密集的安全防线修补，表明智能体的网络访问与文件操作正面临更严格的安全威胁模型。

### 5. 差异化定位分析

| 维度 | OpenClaw | NanoBot | Hermes | CoPaw | ZeroClaw | 其他 |
|------|----------|---------|--------|-------|----------|------|
| **功能侧重** | 全栈AI助手/自主智能体+企业频道 | 轻量级多功能代理框架 | 桌面AI助手+多窗口体验 | 多通道Agent平台+自动化 | 网关级多Agent管理与插件生态 | PicoClaw(边缘轻量)/NanoClaw(安全附件)/NullClaw(专注cron)/IronClaw(Cloud Native) |
| **目标用户** | 开发者+企业团队 | 个人/小团队开发者 | 桌面重度用户 | 国内企业IM用户（钉钉/飞书为主） | 分布式多Agent场景开发者 | 特定垂直场景 |
| **技术架构** | 单仓库全栈，高度集成 | 轻量级，模块化，易读懂 | Electron桌面+多平台Backend | 注重前端体验与自动化 | 插件化Wasm运行时(拟迁移wasmtime) | 异构 |
| **社区特点** | 贡献极旺但核心审查过载 | 敏捷修复，新手友好 | 桌面交互细节挑剔 | 国内渠道反馈密集 | 架构演化（Wasm选型）驱动 | 部分项目社区沉寂 |

OpenClaw 与 ZeroClaw 分别代表“大集成”与“网关插件”两条路线；NanoBot 以轻量和可读性获得开发者青睐；CoPaw 深耕钉钉/飞书生态，形成区域优势；Hermes 聚焦桌面多窗口差异；其余项目则在边缘、cron、安全附件等细分领域寻找空间。

### 6. 社区热度与成熟度分层
根据今日动态，可分为三个梯队：

- **快速迭代梯队**：OpenClaw、CoPaw、IronClaw、NanoBot  
  高频提交、高Issue/PR流速，快速吸收反馈并修复，但同时伴有审查积压或测试覆盖率压力。这一梯队决定了生态主流方向。

- **质量巩固梯队**：Hermes、LobsterAI、PicoClaw、NanoClaw、NullClaw  
  正集中处理稳定性与UX细节（附件、白屏、空闲超时、体验摩擦），新特性节奏放缓，更侧重于让现有功能达到生产级。部分项目如NullClaw已进入功能收尾。

- **低活跃/观望梯队**：Moltis、TinyClaw、ZeptoClaw  
  今日近乎无社区互动或仅依赖更新，可能处于维护者缺口或战略转移期，需后续观察。

从成熟度看，OpenClaw 处于“成熟但瓶颈期”，其发布频率和P1回归数暗示需要一次重大的预发布测试流程改进；IronClaw、NanoBot 则展现出健康的中等规模效率。

### 7. 值得关注的趋势信号
1. **从“功能交付”到“信任交付”**：社区对消息丢失、会话僵死、白屏等异常的容忍度急剧降低，任何影响基础通信可靠性的Bug都会被标为P1并引发用户流失焦虑。智能体框架的竞争已转向 SLA（服务可靠性）感知。
2. **安全成为准入门槛**：SSRF、zip炸弹、凭据泄漏、DNS重绑定等攻防正在从“增值审计”变为社区日常提交，缺乏内建安全机制的项目将迅速丧失开发者信任。
3. **多模态附件处理标准化**：Discord、WhatsApp、飞书、腾讯IM等渠道的媒体类型差异暴露出“附件处理抽象层”缺失，未来统一的多媒体下载、安全扫描、格式转换中间层可能成为关键组件。
4. **代理预算与 Loop 控制的标配化**：多个项目同时推进代理迭代上限、循环门控、心跳开销控制，说明**成本治理+安全熔断**是自主智能体迈向无人值守的必要条件，有望在半年内形成事实标准。
5. **标准化API与模型切换需求**：ZeroClaw 出现要求 OpenAI 兼容端点的请求，NanoBot 大量 PR 实现模型热切换，CoPaw 遇到转发兼容问题，表明用户不希望被锁定在某一模型或封闭接口，开放兼容层将成为差异化卖点。
6. **国产模型与本土通道生态深度整合**：豆包工具调用泄露、GLM thinking 模式修复、DeepSeek V4 兼容性、9router 转发问题等高频出现，暗示中国市场的智能体项目正独立构建供需闭环，可能催生与国际主生态的分叉版本。

对 AI 智能体开发者而言，上述信号指明两点行动建议：**立刻加固消息管道与安全边界，将可靠性视为一阶需求；** **同时设计模型与通道的抽象层，保持对未来半年内快速变化的模型市场和渠道标准的适应力。**

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot 项目日报（2026-07-01）

## 今日速览
过去 24 小时 NanoBot 项目保持高活跃度：新增/更新 Issues 14 个，Pull Requests 激增至 67 个（其中 35 个已合并或关闭，32 个等待审查）。社区在功能增强、稳定性修复、安全加固和内存管理等多条线上并行推进。主要维护者和社区贡献者正快速消化积压，多项长期存在的痛点（如心跳结果路由、OAuth 配置、安装脚本崩溃）被集中解决，项目健康度良好。

## 项目进展
今日合并/关闭的重要 PR 推动了以下方向：

- **WebUI 空闲压缩行为修复**：`#4609` 避免空闲会话压缩意外刷新会话时间戳，修复了自动压缩误触发问题，改善了 WebUI 会话列表排序逻辑。  
- **CLI OAuth 登录体验优化**：`#4573` 允许用户在 OAuth 登录后直接将其设置为主提供者，解决了初学者因配置缺失而卡住的问题。  
- **心跳任务结果投递修复**：关闭已久的 `#4418` 请求被实现，心跳任务现在能将结果回传到任务添加的原始频道，而非最近活跃频道。  
- **其他重要关闭**：修复了安装脚本的 TUI 崩溃（`#4599`）、OAuth 令牌未持久化（`#1023`）、以及流式文件编辑器中工具调用 ID 错误覆盖导致的会话污染问题（`#4595`）。

这些修复使代理执行可靠性、安装体验和多渠道协作能力获得提升。

## 社区热点
以下是今日讨论最活跃的 Issues/PRs：

1. **PR #4534 – 代理可靠性、验证与执行服务全面改进**  
   该 PR 为代理循环增加了通用可靠性层，覆盖 Codex 集成、验证反馈、长输出处理及运行时预算收敛，直击实际评估中发现的任务丢失痛点，属于 P1 优先级重构，受关注度高。

2. **Issue #4611 – DNS 重绑定 TOCTOU 安全漏洞**  
   `validate_url_target` 在 SSRF 校验中未锁定解析 IP，存在时间竞争窗口。由外部安全研究者提交，获 1 个 👍，属于高优先级安全议题，目前暂无对应修复 PR。

3. **Issue #4604 – 请求支持 Anthropic OAuth**  
   社区希望增加对 Anthropic 的 OAuth 认证支持，此请求源自讨论区，已获得 2 条评论，反映出跨模型提供商集成是用户的强烈需求。

4. **Issue #4418（已关闭）– 心跳任务回传原频道**  
   该功能请求在关闭前累计 4 条评论，解决了心跳任务结果投递错乱的常见困扰，关闭带来了明确的功能交付，用户反响积极。

## Bug 与稳定性
| 严重度 | Issue | 描述 | 状态 | 关联修复 PR |
|--------|-------|------|------|-------------|
| 高 | `#4611` | DNS 重绑定导致 SSRF 绕过 | 开放，无修复 | 无 |
| 中 | `#4513` | Windows 服务模式下 /restart 导致端口占用或幽灵进程 | 已关闭 | 疑似已修复 |
| 中 | `#4595` | 流式文件编辑导致工具调用 ID 被覆盖，引发永久性会话污染 | 已关闭 | 未公开对应 PR |
| 低 | `#4599` | 安装脚本在 TUI 阶段崩溃 | 已关闭 | 已修复 |
| 低 | `#4592` | ExecTool 在 “=” 后无法提取绝对路径，限制工作区边界检查 | 开放，无修复 | 无 |

> 关注：`#4611` 虽无直接利用公开，但影响所有启用 Web 工具的场景，建议维护者优先评估。

## 功能请求与路线图信号
今日新增功能请求，部分已有开放 PR 呼应：

- **多模型灵活配置**：请求支持 OpenAI Response API（`#4612`）、Anthropic OAuth（`#4604`），同时  `#4549`、`#4555`、`#4556` 等 PR 分别实现心跳、会话、Dream 的模型覆盖，表明“模型热切换”正成为路线重点。  
- **代理间协作与外部触发**：需求包括外部脚本触发代理动作（`#4605`）及原生 A2A 委托（PR `#4571`），后者已提交实现，有望进入下一版本。  
- **WebUI 体验提升**：导出 Markdown（`#4587`）、显示会话时间戳（`#4586`）等功能已通过 PR 提交，对应讨论 `#4579` 被积极跟进。  
- **成本与上下文优化**：PR `#4581` 通过精简上下文内容减少 tokens 消耗，与用户长期希望降低使用成本的愿望一致。  
- **安全加固**：`#4603` 重构工具调用 ID 以分离 WebUI 进度关联和提供者协议，避免了数据污染风险，符合架构健康方向。

综上，下一次版本可能会重点强化模型切换、Agent 间协作以及 WebUI 导出能力。

## 用户反馈摘要
- **正面评价**：有用户在 `#4605` 中称赞项目“轻量级代码库易于阅读和理解”，并成功将其用于 Gmail 智能分类，显示出对开发者体验的认可。  
- **核心痛点**：Windows 服务守护（`#4513`）、OAuth 配置复杂（`#4573` 修复前）、心跳结果混乱（`#4418`）等易用性问题反复出现，好在本轮迭代多数已解决。  
- **安全担忧**：`#4611` 的报告者以详细技术描述指出 SSRF 防护薄弱，诉求是“修复 DNS 解析的 TOCTOU”，虽非最终用户，但代表了安全审计社区的关切。  
- **集成诉求**：多个请求要求接入 GitHub Copilot Enterprise、OpenAI Response API、Anthropic OAuth，反映用户希望 NanoBot 成为企业内部统一 AI 网关的期待。

## 待处理积压
- **高优安全 Issue**：`#4611` 尽管刚创建，但影响范围广，需尽快评估或指定维护者响应。  
- **有待跟进的架构改进**：`#4603` 重构工具调用 ID 直接影响协议合规性，虽已有 PR 草案但尚未合并，建议列入后续里程碑。  
- **无对应 PR 的功能请求**：`#4612`（OpenAI Response API）、`#4605`（外部触发代理）目前无开发者认领，可能成为社区贡献的契机。  
- **潜在回归风险**：`#4592` ExecTool 路径提取缺陷可能让已启用工作区限制的用户面临绕过风险，虽严重度较低，但久未修复可能累积隐患。

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent 项目日报 | 2026-07-01

## 今日速览
今日项目活跃度极高，过去24小时共新增/活跃13条Issue、50个Pull Request，其中47个PR待审核，3个已完成合并/关闭。社区聚焦于桌面多窗口体验、机器人自身学习幻觉修复、飞书/Telegram消息可靠性、以及一系列边界场景的稳定性改进。无新版本发布，但大量修复PR已提交，反映出社区贡献节奏加快，项目正经历一次集中的质量加固期。

## 项目进展
今日有3个PR被合并/关闭（具体内容未在截取范围内显示），推测修复了某些问题或实现了小功能。待合并队列中大量PR直接关联已知Bug，若合入将显著提升多个平台的稳定性和安全性：

- **安全边界修复** PR #55709 要求将子进程环境变量通过集中式凭据剥离辅助函数传递，避免API密钥泄漏，优先级P1。
- **飞书体验优化** PR #55759 将Markdown表格渲染为CardKit v2卡片，PR #55750 修复DM引用回复不被引用的问题。
- **Telegram/浏览器/Windows 稳定性** PR #55761 去重短文本消息，PR #55760 解决macOS下headless Chrome破坏正常窗口，PR #55753 修复Windows子进程标志缺失。
- **核心Agent逻辑** PR #55756 修复尾部保护token估算遗漏推理项，PR #55757 修正`read_file`末行计数，PR #55758 支持CJK语言的intent确认继续对话。
- **内存与文件工具** PR #55729 修复全息记忆检索计数遗漏，PR #55751 拒绝零间隔cron调度。

这些PR一旦合并，将修复十余个已报告的缺陷，并堵住一处潜在安全边界。

## 社区热点
**最受关注的议题**  
- **多窗口桌面支持** Issue #40394 获得4个👍和2条评论，用户希望在独立的桌面窗口中并行运行相同配置文件的多路会话，当前Electron实现禁用了多窗口，限制了大量并行工作流。
- **自我改进技能补丁幻觉** Issue #55647 指出后台自动改进流程可能对未读取的技能文件进行“补丁”，引发写入不一致，属于P1级别的核心Agent缺陷，已引起立即讨论。

**功能主张集中的方向**  
今天的Issue列表里用户密集提出架构优化需求，例如强制中间循环提示缓存失效（#55743）、统一内存提供者抽象（#55744）、消除变更检测快照测试（#55745）、隐私遥测选择加入（#55747）等，反映出社区对底层可扩展性、成本与隐私合规的强烈关切。

## Bug 与稳定性
今日报告的Bug按严重程度排序：

| 严重等级 | Issue | 描述 | 已有修复 PR |
|---------|-------|------|-------------|
| **P1** | #55647 | 后台自改进技能补丁幻觉，违反“先读后写”不变式 | 无 |
| **P1** (安全) | PR #55709 | 子进程环境变量泄漏API密钥 | ✅ #55709 |
| **P2** | #55750 | 飞书DM引用回复以普通消息发送，不跟随被引用消息 | 部分（#55750为Issue，PR待查） |
| **P2** | #55761 | Telegram短文本消息重复发送（流预览+网关终送） | 无 |
| **P2** | #55760 | macOS下browser-cdp LaunchAgent使用普通Chrome导致可见窗口异常 | 无 |
| **P2** | (多个) | 钉钉会话密钥编码导致重启丢失会话、Bedrock空图片URL崩溃等 | ✅ #55740, #55752, #55754 |
| **P3** | #55755 | memory工具收到无效动作字符串时返回‘Unknown action None’错误信息不友好 | 无 |
| **P3** | #55762 | 项目模式零会话时Sidebar空白 | 无 |

大量P2/P3 Bug已有对应修复PR（如Bedrock、Cron、文件读取、CJK确认等），项目缺的是一次集成回合。P1安全PR #55709 需要优先审阅。

## 功能请求与路线图信号
今日涌现大量中期特性请求，已与进行中的PR形成呼应：

- **桌面多窗口 / 增强辅助窗口** #40394, #55764 → 目前尚无直接PR，但桌面端的早期工作可能为其铺路。
- **学习时间线** PR #55555 将桌面已有的记忆图谱功能带入终端CLI/TUI，有望丰富纯终端用户的技能与记忆浏览体验。
- **新平台集成** PR #3335 (Zulip)、#25186 (TrueConf) 仍在开放状态，新增 #55742 (Google Vertex AI provider) 表明企业多云AI接入需求旺盛。
- **架构与成本治理** #55743 (强制缓存失效)、#55746 (弃用教学工具分页) 透露社区希望降低大语言模型成本。
- **内存系统重构** #55744 提出统一Memory Provider ABC，与正在修正的 #55729 全息记忆计数修复形成互补，预计下一版本内存扩展性将得到体系化改善。

结合PR队列，Google Vertex AI、Journey CLI 等功能已具备较成熟实现，较大概率会纳入下一阶段。

## 用户反馈摘要
- **多窗口痛点**：用户 `maxonliu` 希望像使用IDE一样同时开启多个Hermes对话窗口，当前限制让重度并行使用者工作流受阻。
- **飞书集成**：`UIYES` 发现引用回复体验割裂，消息容易遗失；`luochonglie` 提供了卡片化表格修复方案，表明飞书用户群体活跃且对消息呈现质量有高要求。
- **自我学习机制风险**：`binarybasher` 警告后台“补丁”会破坏现有技能内容，呼吁严格遵守先读后写。
- **macOS 桌面冲突**：`WalterClawSoftware` 描述browser-cdp sidecar占用普通Chrome导致日常使用受影响，反映出自动化浏览器对桌面用户的入侵性。
- **Telegram 重复消息**：`Midnightblue23` 发现短文本会出现两条完全相同的消息，影响对话整洁度。
- **空白侧边栏**：`Hayston1001` 在项目模式下创建工作树后导航消失，说明无会话状态的边角情况尚未被良好覆盖。

总体而言，用户对Hermes的多窗口、技能幻觉、消息可靠性和平台适配性存在强烈期待。

## 待处理积压
以下重要PR长时间未获响应，建议核心维护者关注：

- **Zulip 集成** PR #3335 (2026-03-27创建) 已提交3个月，新增大型消息平台支持未获审阅。
- **TrueConf 网关适配器** PR #25186 (2026-05-13创建) 为东欧消息服务扩展。
- **TUI 远程图片上传校验** PR #41496 (2026-06-07) 提升安全门槛，但停滞近1个月。

此外，部分P1/P2 Bug（如 #55647、#55750、#55760）尚未附带修复，建议提升其优先级以防止在下一个版本中蔓延。

---  
*本日报基于公开GitHub数据自动生成，所有链接可点击追溯。*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目日报 | 2026-07-01**

---

### 1. 今日速览
过去 24 小时社区活跃度中等偏上：共产生 7 条 Issues 更新（其中 5 条为新开/活跃）和 7 条 Pull Requests 更新（其中 5 条待合并）。一个新 nightly 版本发布（`v0.3.1-nightly.20260630`）继续推进主线功能集成，但同时暴露出不少兼容性痛点——尤其是 iOS Safari 的兼容问题、模型供应商连接错误以及 OAuth 登录失败等。整体上，项目在功能扩展（如 DeltaChat 网关、远程 WebSocket 模式）与健壮性修补之间快速迭代，但问题积压与长期未关闭的“stale”项需要关注。

---

### 2. 版本发布
- **Nightly Build: v0.3.1-nightly.20260630.52320f48**  
  自动构建的每日版本，基于主分支最新提交（对应全量变更日志：`v0.3.1...main`）。此版本可能不稳定，仅供测试和尝鲜，无正式 release note。注意：包含近期所有合并/未合并 PR 的改动，建议测试者关注可能的回归，尤其是 Web 面板的兼容性和新模型供应商连接逻辑。  
  链接：https://github.com/sipeed/picoclaw/releases/tag/nightly

---

### 3. 项目进展
今日关闭的重要 PR 如下：
- **[PR #3198] fix(providers): surface friendly auth error messages**  
  已合并/关闭，改进了供应商认证错误处理，为用户返回结构化 `HTTPError` 和更友好的错误提示，显著提升了模型接入时的故障诊断体验。  
  链接：https://github.com/sipeed/picoclaw/pull/3198  
- **[PR #3143] fix(web): block private IPv4 embeds in ISATAP literals**  
  已关闭的 SSRF 防护补丁，修补了 `web_fetch` 功能中通过 ISATAP IPv6 字面量包含内网/回环 IPv4 地址的绕过问题，增强了安全性。  
  链接：https://github.com/sipeed/picoclaw/pull/3143

此外，有 5 个 PR 保持开放待合并，涉及：
- 新增 DeltaChat 网关（#3063）
- 远程 Pico WebSocket 模式（#3118）
- 工具输出中 data URL 误判修复（#3115）
- AWS Bedrock 提示缓存支持（#3163）
- 每次对话轮次 token 用量事件（#3156）

这些进展表明项目正同时向多网关、远程部署、成本可见性和安全加固方向迈进。

---

### 4. 社区热点
- **Issue #3093 [Feature] I need SimpleX or tox**  
  要求增加 SimpleX、Wire 或 Tox 作为通信网关，反映了用户对去中心化/隐私优先通知渠道的强烈需求。评论数 4，点赞 1，且标签为 `stale`，近期可能需维护者关注方向性。  
  链接：https://github.com/sipeed/picoclaw/issues/3093  
- **Issue #3153 [BUG] Volcengine Doubao Seed tool calls leak raw text**  
  使用豆包模型时工具调用泄露原始 XML 文本给用户，而非执行工具，影响较大，已有多条评论讨论。  
  链接：https://github.com/sipeed/picoclaw/issues/3153  
- **PR #3063 feat: add deltachat gateway**  
  已开放近一个月仍有活动（更新 2026-06-30），可能因功能受欢迎但尚需完善，成为社区讨论焦点之一。  
  链接：https://github.com/sipeed/picoclaw/pull/3063

这些热点揭示了用户对隐私通信网关和专业模型适配的迫切期待。

---

### 5. Bug 与稳定性
按严重程度排列的重要 Bug：
1. **Issue #3195 – OpenAI GPT 在 NanoKVM 上默认配置无效**（严重）  
   新硬件集成场景下完全无法使用，涉 gpt-5.4 配置，用户依照官方文档操作仍失败。尚无 fix PR。  
   链接：https://github.com/sipeed/picoclaw/issues/3195  
2. **Issue #3153 – 豆包模型工具调用泄露原始 XML**（较高）  
   直接暴露底层 seed:tool_call 文本，破坏对话体验。暂无明确 PR 修复。  
   链接：https://github.com/sipeed/picoclaw/issues/3153  
3. **Issue #3199 – 自定义供应商无法连接本地 OpenAI 兼容端点**（较高）  
   无法使用 `http://127.0.0.1:16001/v1`，而其他客户端工作正常，疑似 PicoClaw 侧限制或 bug。已关闭但未说明如何解决。  
   链接：https://github.com/sipeed/picoclaw/issues/3199  
4. **Issue #3090 – Safari iOS <16.4 上面板不工作**（已关闭，需验证）  
   低版本 iOS Safari 兼容性问题已关闭，但可能未修复，只是 close 策略。  
   链接：https://github.com/sipeed/picoclaw/issues/3090  
5. **Issue #3196 / #3197 – Codex 和 Antygravity OAuth 登录失败**（中等）  
   两个重复问题，直接影响依赖这些认证方式的用户。目前开放无 PR。  
   链接：https://github.com/sipeed/picoclaw/issues/3196 | https://github.com/sipeed/picoclaw/issues/3197

---

### 6. 功能请求与路线图信号
- **通信网关扩展**：SimpleX / Tox / Wire 的支持（Issue #3093）与正在开发中的 DeltaChat 网关（PR #3063）高度相关，可能推动项目构建模块化网关框架。  
- **远程与分布式部署**：PR #3118 (远程 WebSocket 模式) 若合并，将极大扩展部署场景；与之配合的 PR #3156 (token 用量事件) 则为远程模式下成本监控提供基础。  
- **云服务优化**：PR #3163 为 AWS Bedrock 添加提示缓存，体现了对商业模型的深度集成意图，可能被纳入下一版本。  
- **稳定性与多平台支持**：iOS Safari 兼容性 (Issue #3090) 和 NanoKVM 支持 (Issue #3195) 指向边缘计算/轻量设备场景的重要性，未来可能催生更多针对 ARM/RISC-V 设备的适配 PR。

---

### 7. 用户反馈摘要
- **痛点多集中在模型供应商的易用性**：用户反馈“看到官方文档操作仍然失败”（#3195）、“同样的端点其他客户端能用，PicoClaw 不行”（#3199），说明提高首次配置成功率是急切需求。  
- **对去中心化与隐私的诉求**：需要 Tox/SimpleX 网关的呼声加上 DeltaChat 的 PR，反映了非大型云服务依赖的用户群体。  
- **跨设备体验割裂**：iOS 低版本不能使用面板（#3090），虽关闭但可能未解决根源，伤害了移动监控场景。  
- **积极信号**：用户愿意在 GitHub 积极报告 bug 并提供环境信息（例如 NanoKVM 2.4.0、豆包模型详情），显示核心社区仍有较强的参与意愿。

---

### 8. 待处理积压
- **Issue #3093 (SimpleX/Tox 网关)** 已被标记 `stale` 但持续有更新，距首次创建已 21 天，建议维护者明确表态（接受方向或短期不会实现）。  
  链接：https://github.com/sipeed/picoclaw/issues/3093  
- **PR #3063 (DeltaChat 网关)** 开放 23 天仍在活动，积压较久，可能存在复杂的合并冲突或设计探讨，需推动评审。  
  链接：https://github.com/sipeed/picoclaw/pull/3063  
- **PR #3156 (token 用量事件)** 和 **PR #3115 (data URL 修复)** 均接近两周未合并，可能需提升优先级以减少技术债务。  
  链接：https://github.com/sipeed/picoclaw/pull/3156 | https://github.com/sipeed/picoclaw/pull/3115  

---

**项目健康度小结**：PicoClaw 处于快速演进期，每日合并/关闭 PR 保证核心修复落地，但新增的兼容性问题与积压的功能请求反映出维护压力。建议集中精力解决 NanoKVM 和自定义供应商连接等瓶颈，并明确热点功能请求的路线图，以保持社区信任与参与度。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw 项目日报 | 2026-07-01

## 1. 今日速览
今日项目无新版本发布，但代码合并与社区互动保持活跃。在过去的24小时内，共有3个Issue更新（2个新开，1个安全漏洞被关闭），9个Pull Request活动（1个安全修复已合并关闭，8个新特性/修复等待审核）。社区焦点集中在多渠道附件传输稳定性（Discord/WhatsApp）与安全加固，同时多个功能增强型PR集中提交，显示项目正朝着更安全、更具多通道支持及开发者体验的方向演进。

## 2. 版本发布
无新版本发布。

## 3. 项目进展
- **安全修复合并**：PR #2880 已关闭，修复了 Issue #2828 描述的严重安全漏洞——A2A附件转发可能通过收件箱符号链接逃逸，实现任意主机文件写入。该修复同时加固了入口文件写入的容器化限制，提升了多代理协作场景下的隔离安全性。  
  [PR #2880](https://github.com/nanocoai/nanoclaw/pull/2880) | [Issue #2828](https://github.com/nanocoai/nanoclaw/issues/2828)

此合并标志着项目在安全模型方面的重大加固，为后续多代理间文件交换提供了更严密的基础。

## 4. 社区热点
今日讨论热度最高的为**安全漏洞#2828**（获2👍）及**Discord附件丢失问题#2888**。安全研究者YLChen-007提交的漏洞报告促使快速修复，体现出社区对多代理环境下文件操作安全的关注。Discord适配器无法获取图片/文件内容（仅存元数据）引发日常用户的不便，评论中透露出对附件处理一致性的迫切需求。  
- [#2828 安全漏洞详情](https://github.com/nanocoai/nanoclaw/issues/2828) （已关闭）  
- [#2888 Discord附件缺失讨论](https://github.com/nanocoai/nanoclaw/issues/2888)

此外，WhatsApp媒体静默丢失问题（#2894）与对应的修复PR #2895 同时出现，反映社区在积极推动聊天平台多媒体体验的完整性。

## 5. Bug 与稳定性
| 严重程度 | Issue | 描述 | 应对 |
|--------|------|------|------|
| **高** | [#2828 (已关闭)](https://github.com/nanocoai/nanoclaw/issues/2828) | A2A附件转发可能写入任意主机路径 | PR #2880 已合入 |
| **高** | [#2894](https://github.com/nanocoai/nanoclaw/issues/2894) | WhatsApp适配器CDN获取失败时静默丢弃所有入站媒体（图片/视频/文档） | 已有修复 PR #2895 待审核 |
| **中** | [#2888](https://github.com/nanocoai/nanoclaw/issues/2888) | Discord及其他仅URL型适配器丢失附件内容，代理仅收到文件名 | 尚无对应PR，需排查 `chat-sdk-bridge.ts` 中的数据下载逻辑 |

无崩溃或回归问题报告。

## 6. 功能请求与路线图信号
大量功能增强型PR集中提交，预示下一阶段项目将大幅扩展能力：
- **多媒体与文档处理**：PR #2893 新增基于安全容器的文档渲染工具 `render_document`，将LaTeX/Chromium等重型工具链隔离执行，提升代理处理文档的安全性。  
- **渠道生态扩展**：PR #2844 实现了Matrix原生端到端加密适配器，PR #2889 增加了微信（WeChat）适配器及每日新闻代理，PR #2891 为渠道接口添加了名称解析能力，PR #2892 则开启了Telegram线程支持。  
- **开发者体验**：PR #2890 引入代理模板加载器，支持从本地、Git仓库加载可复用代理蓝图，降低配置门槛；PR #2886 修复了单提供商安装下新建代理的401错误。
这些PR表明项目路线图正围绕**全渠道覆盖**、**智能代理脚手架**及**安全丰富的工具链**展开。

## 7. 用户反馈摘要
- **附件可靠性质疑**：用户eagansilverpathmarketing在Discord使用中反馈“代理只能看到文件名，完全无法处理图片/截图”，与Telegram的顺利体验形成鲜明对比，暴露了适配器在附件内容下载上的差异处理。
- **静默故障困扰**：报告WhatsApp问题时，用户echarrod指出“媒体直接丢失，没有任何提示”，要求补全 `reuploadRequest` 恢复链路，反映出其对生产环境中消息可靠性的严格要求。
- **安全敬畏**：安全漏洞#2828收到积极回应，社区认可快速封堵攻击面的做法，增强了信任。

## 8. 待处理积压
- **PR #2844**（Matrix原生E2EE适配器）已开放7天（自06-24），尚未有评审记录，需关注以防止适配器开发滞后。  
  [PR #2844](https://github.com/nanocoai/nanoclaw/pull/2844)
- **Discord附件丢失问题 (#2888)** 暂无对应修复PR，可能导致高使用率渠道体验退化，建议尽早排期处理。  
  [Issue #2888](https://github.com/nanocoai/nanoclaw/issues/2888)

整体而言，项目健康度良好，安全响应迅速，功能迭代活跃，但部分新渠道缺陷仍需加快跟进。

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw 项目日报 — 2026-07-01

## 1. 今日速览
过去 24 小时项目进入功能集成收尾阶段，共关闭 4 个重要 PR，其中包含一项大型 cron 子代理引擎的实现。社区报告唯一一个新 bug 涉及 Telegram 频道长时间空闲后无响应，当前尚无评论与修复方案。整体活跃度中等，无新版本发布，维护者主要精力集中在审查与合入累积 PR。

## 2. 项目进展
当天关闭/合并的 4 个 PR 显著提升了 cron 子系统的完整性与健壮性，并修复了智谱 AI 提供商的长期响应异常：

- **feat(cron): cron subagent, run history, JSON output, security hardening** [#783](https://github.com/nullclaw/nullclaw/pull/783)  
  引入数据库驱动的 cron 子代理引擎，包含运行历史记录、工作队列、原子化调度、安全加固等。所有 cron 任务类型（技能/代理/Shell）均支持时区偏移、投递路由和操作员告警；CLI 新增 `--json` 结构化输出选项，使 cron 任务的调试与自动化集成大幅改善。这是近期最大幅度的功能推进。

- **fix(providers): fix GLM/ZhipuAI thinking mode and native tool_calls** [#641](https://github.com/nullclaw/nullclaw/pull/641)  
  修复智谱/GLM 提供商三个关联问题：强制思考模式导致响应循环、原生工具调用缺失 `tool_calls` 字段、以及参数兼容性，保障了国产模型接入的稳定性。

- **fix(cron): allow agent jobs to omit command field in cron.json** [#643](https://github.com/nullclaw/nullclaw/pull/643)  
  允许代理任务在 cron 配置中省略冗余的 `command` 字段，修复了因 `command` 为 `null` 而被静默跳过导致所有代理 cron 任务在网关重启后消失的严重缺陷。

- **fix(cron): add --account flag to cron add-agent CLI** [#645](https://github.com/nullclaw/nullclaw/pull/645)  
  为 `cron add-agent` 命令补全 `--account` 选项，让用户可以直接通过 CLI 指定投递账户（如 Telegram 机器人号），无需手动编辑配置文件。

这些 PR 的合入使 cron 模块从“基本可用”跃迁到“生产可用”，同时消除了智谱模型接入的隐患，项目整体可靠性向前迈进一大步。

## 3. 社区热点
今日社区交互量整体偏低。唯一的开放式 Issue [#972](https://github.com/nullclaw/nullclaw/issues/972) 尚无讨论，而所有关闭的 PR 均未观察到公开评论。从提交历史看，yanggf8 作为核心贡献者持续聚焦 cron 与模型适配，其密集合并动作本身构成了今日的开发热点。社区潜在关注点很可能集中在 cron 子代理这一新能力如何在实际信道（如 Telegram）中稳定工作。

## 4. Bug 与稳定性
- **Telegram 频道在长时间空闲后停止响应** [#972](https://github.com/nullclaw/nullclaw/issues/972)  
  **严重程度：中等**（服务中断但后端进程正常）  
  作者报告 Telegram 信道在空闲一夜或更长时间后停止应答，`nullclaw agent -m "ping"` 后端工作正常，表明问题可能出在 Telegram 连接保活、消息轮询或信道恢复逻辑层面。  
  目前无评论、无指定负责人，尚无修复 PR 关联。

## 5. 功能请求与路线图信号
今日无新功能请求 Issue。但从已合并 PR 的特征可判断下一版本路线图重点：
- **cron 子代理引擎** 的落地，意味着定时自动化任务能力已就绪，预期会在后续版本正式发布并撰写文档。
- **Telegram 故障修复** 可能触发对信道可靠性（连接健康监测、自动重连、心跳保活）的进一步需求，建议关注 Issue [#972](https://github.com/nullclaw/nullclaw/issues/972) 的后续讨论。

## 6. 用户反馈摘要
唯一可获取的用户声音来自 Issue [#972](https://github.com/nullclaw/nullclaw/issues/972)：生产环境中部署的 Telegram 频道在无人值守一段时间后“哑火”，而排障时发现后端 agent 正常，反映出用户对长时间运行稳定性的预期与实际表现存在落差。这揭示了机器人长期在线场景下的脆弱性，可能影响依赖该信道进行定时推送的用户体验。

## 7. 待处理积压
今日仅新增 1 个待处理项，无超过 30 天未响应的积压 Issue 或 PR。建议维护者优先处理：
- **[Bug] Telegram channel stop respond after some idle time** [#972](https://github.com/nullclaw/nullclaw/issues/972) — 虽为新报告，但因触及生产可用性，应尽早诊断，避免用户持续遇到服务中断。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw 项目日报 — 2026年7月1日

## 1. 今日速览
过去24小时项目活跃度维持高位：共产生 **7 条新 Issue** 和 **50 条 PR 更新**（其中 23 条已合并/关闭，27 条待审查）。工作重心明显集中在 **Reborn 自动化与 WebUI 的稳定性修复、CI/CD 流水线疏通，以及 LLM 上下文成本优化** 三个方向。无新版本发布，但大量卫语句级和功能级 PR 的快速合并反映出工程团队正在为下一个里程碑做密集的打磨与收敛。

## 2. 版本发布
今日无新版本（Release）发布。

## 3. 项目进展
今日共有 23 个 PR 被合并或关闭，关键进展包括：

- **WebUI 测试覆盖与项目设置**：`#5375` 完成了 Reborn WebUI 在项目、设置搜索、技能与工具权限等页面的浏览器自动化测试覆盖，弥补了交互测试缺口。
- **资源调控与压测优化**：`#5447` 为资源调控器增加了“无限额度”快速路径，使压力测试 `ironclaw_stress` 可绕过配额检查，便于调优；配合 `#5444` 新增的提供者延迟压力模式，可量化模型延迟表现。
- **出站投递鲁棒性**：`#5445` 使缺失的出站投递目标变为模型可感知的失败信息，而非底层错误，改善了自动化任务投递时的错误恢复能力。
- **工具能力修复**：`#5438` 修复了 `builtin.time` 的时区偏移参数校验，并将 GitHub Search API 的 422 响应归类为无效输入，避免将用户参数错误误报为系统故障。
- **依赖更新**：`#5410` 等 dependabot PR 批量升级了 `agent-client-protocol`、`webpki-roots` 等多个关键依赖，保障供应链及时性。

> PR 链接： [#5375](https://github.com/nearai/ironclaw/pull/5375) | [#5447](https://github.com/nearai/ironclaw/pull/5447) | [#5444](https://github.com/nearai/ironclaw/pull/5444) | [#5445](https://github.com/nearai/ironclaw/pull/5445) | [#5438](https://github.com/nearai/ironclaw/pull/5438)

## 4. 社区热点
今日社区讨论体量较小，唯一获得直接评论的议题是 **#5420**（1 条评论），而多个核心待审 PR 因解决痛展现出较高关注。

- **鲁棒性争论** — Issue [#5420](https://github.com/nearai/ironclaw/issues/5420)：用户发现 Routine（自动化）的投递目标是基于**用户维度的全局默认值**，而非每个 Routine 独立设定。为某个 Routine 设置 Slack 投递会导致该账号下**所有**已触发的 Routine（包括原本只发邮件的摘要任务）都重定向到 Slack。评论可能指向自动化行为的可预期性危机。
- **CI 阻塞修复** — PR [#5448](https://github.com/nearai/ironclaw/pull/5448)（核心贡献者，未合并但 tag 为重要修复）：它修复了因静态资源未正确 gitignore 导致 `release-plz` 失败的主分支阻塞问题，直接关系到持续发布流程的健康，预计将引发快速审查。
- **头通知功能** — PR [#5441](https://github.com/nearai/ironclaw/pull/5441) 为自动化审批添加 Header 通知铃，对应特性请求 Issue [#5443](https://github.com/nearai/ironclaw/issues/5443)，属于高频交互需求，虽然评论数未显，但从双向联动可见社区与贡献者已聚焦于此。

## 5. Bug 与稳定性
今日报出的缺陷覆盖从环境配置、核心功能到测试基础设施多个层面：

| 严重程度 | Issue | 描述 | 已有修复 PR |
| :--- | :--- | :--- | :--- |
| **严重** | [#5420](https://github.com/nearai/ironclaw/issues/5420) | Routine 投递全局默认覆盖，导致无关 Routine 错误投递到 Slack | [#5445](https://github.com/nearai/ironclaw/pull/5445) 改善失败处理，但未修复根因 |
| **高** | [#5426](https://github.com/nearai/ironclaw/issues/5426) | 在 hosted-staging 环境中无法创建 Routine，报“system drive is not available” | 暂无 |
| **中** | [#5429](https://github.com/nearai/ironclaw/issues/5429) | 使用 NEAR AI Inference 的 Web Search 要求云 API token，多租户/SSO 用户不可用 | [#5439](https://github.com/nearai/ironclaw/pull/5439) 尝试解决 MCP 令牌解析，尚未合并 |
| **低（测试）** | [#5428](https://github.com/nearai/ironclaw/issues/5428) | 模拟 MCP 测试层存在三个遗留缺陷，仅影响测试代码 | 无（特意从 [#5427](https://github.com/nearai/ironclaw/pull/5427) 中推迟） |
| **长期积压** | [#4108](https://github.com/nearai/ironclaw/issues/4108) | Nightly E2E 定时任务于 5 月 27 日起持续失败，至今未恢复 | 无 |

## 6. 功能请求与路线图信号
- **自动化通知**：Issue [#5443](https://github.com/nearai/ironclaw/issues/5443) 提出为触发的新自动化任务添加 Header 通知，避免用户错过结果。对应 PR [#5441](https://github.com/nearai/ironclaw/pull/5441) 已实现审批通知，极大概率纳入下一版本。
- **路线图推进**：PR [#5431](https://github.com/nearai/ironclaw/pull/5431) 按 Tier 0 路线图重新启用 `spawn_subagent` 表面测试（T0-SPAWN），[#5430](https://github.com/nearai/ironclaw/pull/5430) 为 Reborn 后端添加 `cargo-llvm-cov` 覆盖率作业（T0-COV），表明覆盖率与子代理特性正在从预览走向正式。
- **上下文成本优化**：PR [#5435](https://github.com/nearai/ironclaw/pull/5435)（可覆盖的压缩上下文预算）和 [#5450](https://github.com/nearai/ironclaw/pull/5450)（精减工具输出以减少跨轮次携带内容）直指 LLM 多轮对话的成本与质量平衡，属于架构级性能需求，可能在后续版本中实验性合入。

## 7. 用户反馈摘要
从 QA 与早期使用者的 Issue 中可提炼出两类突出痛点：
- **环境集成配置不可见**：测试人员 `sergeiest` 在 staging 环境中遭遇 Routine 创建直接失败（#5426）和 Web Search 功能因缺少令牌而拒绝服务（#5429），反映出在非本地部署场景下，功能引导与凭据注入仍存在断裂，新用户难以自行排查。
- **自动化行为意外耦合**：用户 `thisisjoshford` 指出 Routine 投递的“全局默认”设计背离了每个 Routine 独立配置的直觉（#5420），一度导致电子邮件摘要也被推送到 Slack，这暴露了配置模型过于粗糙，容易造成数据泄露风险和使用者困惑。

开发团队通过 PR [#5445](https://github.com/nearai/ironclaw/pull/5445) 和 [#5439](https://github.com/nearai/ironclaw/pull/5439) 快速响应了部分反馈，但对创建失败本身仍缺乏直接修复。

## 8. 待处理积压
- **\[5周\] 夜间端到端失败** — [#4108](https://github.com/nearai/ironclaw/issues/4108) 自 2026-05-27 起每日失败，无人评论或分配，可能已被忽略，建议维护者明确此流水线是否仍在维护范围，避免虚假健康信号。
- **\[新开\] 测试基础设施债** — [#5428](https://github.com/nearai/ironclaw/issues/5428) 标记了三个 mock-MCP 测试的遗留缺陷，虽然不直接影响生产，但若长期不清理会持续损害测试的可信度，建议在相近重构中附带修复。

---

*数据截止 2026-07-01 00:00 UTC，由 IronClaw 项目分析器自动生成。*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI 项目日报 | 2026-07-01

## 1. 今日速览
过去 24 小时项目活跃度较高，共产生 8 条 Issue 更新与 16 条 PR 更新，并发布了 **LobsterAI 2026.6.30** 版本。社区主要关注点集中在 用户体验细节、Cowork 会话稳定性与性能波动，同时维护团队通过密集的 PR 合并强化了可观测性与核心流程修复。今天关闭了 14 个 PR，待合并 PR 仅剩 2 个，项目整体推进节奏健康。

## 2. 版本发布
**LobsterAI 2026.6.30** 已于 2026-06-30 正式发布。本版本主要包含以下变更：
- **可观测性增强**：为 Cowork 和 OpenClaw 流程增加诊断日志，便于生产环境排障 ([feat(logging): add diagnostics for Cowork and OpenClaw flows · #2229](https://github.com/netease-youdao/LobsterAI/pull/2229))
- **OpenClaw 修复**：为已知的 Anthropic 格式提供者增加内置 maxTokens 回退逻辑，防止目录不可读时出现空限制 ([fix(openclaw): fallback catalog max token limits · #2232](https://github.com/netease-youdao/LobsterAI/pull/2232))
- **定时任务稳定性**：修复调度任务列表/历史因 OpenClaw 网关客户端未初始化导致的空结果问题 ([fix(scheduled-task): restore gateway-backed run history · #2231](https://github.com/netease-youdao/LobsterAI/pull/2231))

版本未引入已知破坏性变更，可直接升级。详细变更列表可见发布 PR [#2237](https://github.com/netease-youdao/LobsterAI/pull/2237)。

## 3. 项目进展
今日合并/关闭的重要 PR 推动了多项修复与优化落地：
- **Cowork 会话体验修复**：一系列 PR 修复了会话边栏提示预览问题，包括清理计划模式标签、增加预览长度、修复悬停时边栏宽度异常等 (#2226, #2218, #2222, #2223, #2224, #2225)。这些变更合并后显著提升了多会话导航的可用性。
- **UI 与布局优化**：修复了 Cowork 详情区在调整工件尺寸时与提示工具栏重叠的问题 (#2235)，并优化了模型编辑界面 (#2236)。
- **分析数据安全**：移除了提示事件中的意图类型、子类型和关键词字段，避免上报敏感推断信息 (#2233)。
- **定时任务与 OpenClaw 可靠性**：除上节提到的 #2231、#2232 外，还有针对 cron 子代理最终化阶段的修复，解决了子代理完成事件无法驱动父代理继续执行的问题 (#2234，仍处于 Open 状态待最终合入)。

整体上，项目在会话导航、定时任务、可观测性和 UX 细节方面均有实质性推进。

## 4. 社区热点
今日新开放的 Issue [#2230](https://github.com/netease-youdao/LobsterAI/issues/2230)（**同一个模型在 LobsterAI 比 CodeBuddy 慢很多**）在开发者群体中获得关注。作者提供了详细的量化对比：相同提示词下，CodeBuddy 耗时 2 分 24 秒消耗 67k Token，而 LobsterAI 耗时 25 分钟消耗 60M Token，差距巨大。该反馈直指模型调用链路的性能优化痛点，若无有效改善，可能造成用户流失。

此外，多个长期存在的 [stale] Issues（如 #1382 红色提示混淆、#1381 定时任务会话堆积）虽评论数不高，但反映出社区对日常使用流畅度的持续期待。

## 5. Bug 与稳定性
今日新报告或重新活跃的 Bug 按照影响程度排列如下：
1. **性能回归/异常**：[#2230](https://github.com/netease-youdao/LobsterAI/issues/2230) 模型响应极慢，Token 消耗异常。尚未有关联修复 PR。
2. **会话附件丢失**：[#1384](https://github.com/netease-youdao/LobsterAI/issues/1384) 会话中多文件选择仅保留最后一个。对应修复 PR [#1372](https://github.com/netease-youdao/LobsterAI/pull/1372) 已由社区提交但长期处于 Open 状态，至今未合并。
3. **微信机器人消息同步异常**：[#1383](https://github.com/netease-youdao/LobsterAI/issues/1383) 手机微信重复消息在电脑端仅同步一条，[#1385](https://github.com/netease-youdao/LobsterAI/issues/1385) 删除微信会话后历史记录未被清理。均为 [stale] 状态，暂无修复 PR。
4. **技能重复添加无提示**：[#1427](https://github.com/netease-youdao/LobsterAI/issues/1427) 曾允许重复添加同名技能，已于今日自动关闭（原因为 [stale] 过期），但无明确修复记录；相关 UX 问题 [#1426](https://github.com/netease-youdao/LobsterAI/issues/1426) 也已关闭。
5. **定时任务会话堆积**：[#1381](https://github.com/netease-youdao/LobsterAI/issues/1381) 每次 cron 触发创建新会话导致大量重复窗口，暂无解决方案。

## 6. 功能请求与路线图信号
社区提出的功能诉求集中在两个方面：
- **交互提示优化**：[#1382](https://github.com/netease-youdao/LobsterAI/issues/1382) 建议导出日志时避免使用红色（用户通常认为红色代表失败），属于低成本高收益的 UX 改进，尚未进入开发。
- **定时任务体验改进**：[#1381](https://github.com/netease-youdao/LobsterAI/issues/1381) 请求将定时任务结果合并到同一会话中，避免窗口泛滥。此需求与目前定时任务机制的会话处理逻辑相关，可能需要较大的架构调整。

已有关闭 PR [#1428](https://github.com/netease-youdao/LobsterAI/pull/1428) 曾尝试实现「后台会话完成/报错时推送系统通知」功能，该功能可弥补一部分状态感知需求，目前进度不明朗。以上需求为下一版本迭代提供了明确方向。

## 7. 用户反馈摘要
从 Issues 评论中提炼出以下几类真实痛点：
- **性能焦虑**：用户横向对比同类工具，对 LobsterAI 的响应速度和 Token 消耗反馈强烈（#2230）。需尽快定位并释放性能优化成果。
- **操作误导与不可预期行为**：红色日志提示（#1382）、多文件只保留最后一个（#1384）、微信消息同步残缺（#1383, #1385）等均属于“做了操作，结果与预期不符”，直接拉低信任感。
- **日常使用摩擦**：定时任务每次打开新会话（#1381）让用户感到“堆积”，技能添加流程缺乏反馈（#1426/1427）暴露了功能闭环缺失。

## 8. 待处理积压
以下 Issue/PR 长期处于 [stale] 状态或未获响应，需维护者关注：
- **PR [#1372](https://github.com/netease-youdao/LobsterAI/pull/1372)**：修复多文件选择仅保留一个文件的 Bug，已提交超过 3 个月，包含 8 个单元测试，待审核合并。
- **Issue [#1381](https://github.com/netease-youdao/LobsterAI/issues/1381)**：定时任务同一会话需求，2026-04-03 创建，无明确进展。
- **Issue [#1382](https://github.com/netease-youdao/LobsterAI/issues/1382)**：导出日志红色提示优化，同样长期搁置。
- **Issue [#1384](https://github.com/netease-youdao/LobsterAI/issues/1384)**：核心附件功能缺陷，影响文件交互场景，关联 PR 未合并。
- **Issue [#1383](https://github.com/netease-youdao/LobsterAI/issues/1383) / [#1385](https://github.com/netease-youdao/LobsterAI/issues/1385)**：微信机器人同步问题，涉及端到端数据一致性。

建议在后续迭代中优先处理积压的缺陷修复，避免社区信任流失。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis 项目日报 – 2026 年 7 月 1 日

## 今日速览
今日项目代码仓库活跃度偏低，主要活动全部来自自动化依赖项更新。过去 24 小时内无新的 Issue 提出或讨论，无版本发布，仅产生 3 条 Pull Request 动态（1 条新开启，2 条被关闭）。整体开发节奏处于平缓期，核心贡献者无新代码合入，项目健康度正常，但缺乏功能层面的推进。

## 项目进展
### 已关闭的 PR
- **#1134 – 升级 astro 与 undici 依赖**  
  [moltis-org/moltis#1134](https://github.com/moltis-org/moltis/pull/1134)  
  Dependabot 自动提交的跨目录依赖升级，涉及 `/docs` 目录中的 `astro` 从 6.3.3 升级至 6.4.8，以及 `/website` 目录中的 `undici`。该 PR 创建于 6 月 20 日，于 6 月 30 日被关闭，未合入主分支。
- **#1121 – 升级 esbuild 开发依赖**  
  [moltis-org/moltis#1121](https://github.com/moltis-org/moltis/pull/1121)  
  同样为 Dependabot 提交，计划将 `/crates/web/ui` 下的 `esbuild` 从 0.25.12 升至 0.28.1。创建于 6 月 14 日，关闭于 6 月 30 日，未合并。

> 分析：这两个 PR 的关闭很可能是被更新的 #1141 所取代。#1141 汇总了跨 3 个目录的多项升级，维护者可能倾向于一次性完成更新，因此关闭了较早的分散 PR。项目实际未通过这些 PR 获得实质功能推进。

### 待合并的 PR
- **#1141 – 批量升级 npm_and_yarn 组依赖（esbuild、vite 等）**  
  [moltis-org/moltis#1141](https://github.com/moltis-org/moltis/pull/1141)  
  Dependabot 今天（6 月 30 日）新开启，涵盖了 `/crates/web/ui` 和 `/docs` 目录中多个依赖的版本提升，包括 `esbuild` 和 `vite`。目前处于开放状态，等待审阅与合并。

## 社区热点
今日仓库无任何活跃讨论，所有 PR 均由 `dependabot[bot]` 自动创建，无社区成员评论或点赞。项目社区互动度极低，可能受时区或工作日末期影响，无值得追踪的热点诉求。

## Bug 与稳定性
未发现新的 Bug 报告或稳定性问题，今日无相关 Issue 提出。现有依赖升级 PR（#1141）仅涉及常规版本迭代，未标注修复已知漏洞或崩溃，当前分支应处于较稳定状态。

## 功能请求与路线图信号
无新增功能请求，亦无 Feature PR 出现。从 PR 积压情况看，项目当前专注于依赖维护，未显示下一版本的特性规划信号。

## 用户反馈摘要
今日无用户通过 Issue 或 PR 评论提交反馈，无法提炼真实用户痛点或满意度信息。

## 待处理积压
- **[dependencies] #1141 – 批量依赖升级待合并**  
  [moltis-org/moltis#1141](https://github.com/moltis-org/moltis/pull/1141)  
  该 PR 为当前唯一开放项，已等待合并约 1 日。建议维护者确认 CI 通过后及时合入，以减少与其他自动 PR 的冲突风险。此为常规 npm_and_yarn 安全更新，若不处理，未来可能堆积更多重复更新。
- **长期未关闭的旧自动 PR 已被清理**  
  #1134 与 #1121 的关闭表明维护者主动清理了过时自动 PR，积压现象得到改善，无需额外干预。

---

*数据来源：GitHub Moltis 仓库事件，统计区间 2026-06-30 00:00 至 2026-07-01 00:00 UTC。*

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

## CoPaw (QwenPaw) 项目日报 — 2026-07-01

### 1. 今日速览
过去24小时，项目仓库（agentscope-ai/QwenPaw）保持极高活跃度：共更新16条Issue（新开/活跃12条，关闭4条），PR更新50条（22条已合并或关闭，28条仍处于开放或审查状态）。前端崩溃、自动化任务稳定性、记忆检索增强与多通道通知等核心问题受到集中关注，多个修复PR快速跟进。未发布新版本，但迭代节奏密集，社区贡献与维护者响应均显积极。

### 2. 版本发布
今日无新版本发布。

### 3. 项目进展
今日合并/关闭的重要PR，推动了以下关键能力：

- **钉钉消息@提及支持与送达反馈修复**  
  PR #5590（feat(channels): support dingtalk mentions）及 PR #5654（fix(channels): surface DingTalk delivery failures）已被合并或关闭，补齐了`/messages/send`、`qwenpaw channels send`、Cron文本推送等主动发送路径中的@能力，同时修复了钉钉无可用token时静默失败的问题，并抑制了空消息导致的无意义通知。  
  关联 Issue: #5564（已关闭）, #5566（Open）

- **聊天附件免文本发送与去抖控制**  
  PR #5659（fix(chat): allow sending attachments without text）及 Issue #5663（已关闭）推进了无文字仅附件即可触发Agent的行为，解除了此前“必须输入文字”的限制，并计划提供前端开关供用户控制。

- **侧边栏滚动体验与UI样式修复**  
  PR #5656（fix(layouts): isolate sidebar session list scrolling）已关闭，优化了Simplified模式下的会话列表滚动；PR #5151（fix GitPanel tabs样式）仍在开放，持续改进前端细节。

- **技能自动同步与Plugin Market版本过滤**  
  PR #5639（feat(skill): Add skill auto sync）已关闭，实现了技能池至工作区的自动同步；PR #5661（feat: filter plugin market by QwenPaw version）正在审查，将带来插件兼容性过滤。

- **Windows原生沙箱、计算机使用自动化等重型特性**  
  PR #5525（feat(sandbox): windows native sandbox）、PR #5187（feat(computer-use): Windows desktop GUI automation）持续迭代，但尚未合并。

### 4. 社区热点
今日讨论最活跃的Issue（按评论数排序）：

- [#5401 前端渲染大工具历史会话崩溃]（6条评论，已关闭）  
  因后端将`tool_use`/`tool_result`块转换为`type: "data"`导致前端无法渲染，引发白屏。该Bug凸显了大量工具调用会话的稳定性和前端数据模型兼容性问题。

- [#5403 模型配置页搜索框被浏览器自动填充劫持]（5条评论，Open）  
  浏览器将搜索输入误识别为用户名字段，弹出自动填充弹窗，干扰操作。反映出前端表单标签标准问题，用户强烈希望修复。

- [#5588 记忆搜索支持Reranker实现两阶段检索]（4条评论，Open）  
  用户提出当前仅靠embedding的召回精度下降，要求集成`qwen3-rerank`精排或启用LLM-based rerank，并已有PR #5669跟进。

- [#5573 DeepSeek V4 thinking模式400错误]（4条评论，已关闭）  
  OpenAI兼容端点下`reasoning_content`缺失及工具Schema`null`类型未清洗导致请求失败，修复方案已合并。

- [#5564 钉钉@mention支持]（3条评论，已关闭）  
  多Agent协作场景中的@需求强烈，已在PR #5590中完成并关闭。

此外，PR #5665（Loop Engineering Gate架构）虽无公开讨论，但因其“可组合门控”设计可能影响后续Agent行为控制，值得关注。

### 5. Bug 与稳定性
今日报告的Bug及稳定性问题（按严重程度降序）：

1. **前端崩溃：大工具历史会话白屏**  
   Issue #5401（已关闭，已有修复） — 后端数据块类型转换导致前端渲染崩溃。  
   修复方案：后端API调整模型转换逻辑。

2. **DeepSeek V4兼容性400错误**  
   Issue #5573（已关闭，已有修复） — 流式推理无`reasoning_content`兜底、工具Schema`null`值未过滤，影响通过中转站使用非官方端点用户。

3. **Cron任务静默执行与通知可送达性**  
   Issue #5566（Open，PR #5654 open） — 空回复仍产生通知，`channels send`在后台脚本中不可达。PR已做初步修复（跳过空白消息，抛出无可用token异常），但仍需综合方案。

4. **模型配置页搜索框自动填充劫持**  
   Issue #5403（Open，尚无明确修复PR） — 需调整HTML属性避免浏览器误识别，影响用户体验。

5. **无法连接9router转发的模型请求**  
   Issue #5658（Open，新） — 一直存在的连接问题，可能与`if content`校验相关，尚未有修复PR。

6. **Qwen-Image Tool安装错误**  
   Issue #5587（Open） — 具体错误信息待补全，暂无PR。

7. **自动化任务莫名终止**  
   Issue #5616（Open） — 缺少明确复现步骤，需进一步诊断。

### 6. 功能请求与路线图信号
今日涌现的新功能需求及对应的潜在路线图推进：

- **记忆搜索两阶段检索**（#5588） ⇨ PR #5669（feat(memory): add qwen3-rerank）已开放，若通过将提升长记忆场景下的搜索精度。
- **Loop检测与可组合门控**（#5657） ⇨ PR #5665（feat: Loop Engineering Gate Architecture）提出从后端到前端的完整循环控制方案，有望进入下一版本。
- **取消输入框字符限制**（#5670） ⇨ 尚无直接PR，但呼声较高，可能推动前端调整。
- **Telegram自定义BaseURL**（#5630） ⇨ 面向特定地区或私有部署用户，PR未出现。
- **工作区文件浏览器入口**（#5667） ⇨ 提升Agent输出可发现性，无对应PR。
- **Linux AppImage构建**（#5668） ⇨ 基于Tauri打包，已有构建基础，无PR。

此外，PR #5661（插件市场版本过滤）和PR #5653（架构文档）进一步提升了项目可扩展性与可理解性。

### 7. 用户反馈摘要
从Issue评论与需求中提炼的真实用户声音：

- **“大工具调用历史直接白屏，完全无法查看”**（#5401） — 用户在监控类会话中积累大量`tool_use`记录后，前端崩溃严重影响分析。
- **“每5分钟一条空白通知，太打扰了”**（#5566） — Cron任务即使回复空字符串也会产生钉钉消息，用户希望静默运行。
- **“复制粘贴长文本只能放文件里，丧失便利性”**（#5670） — 开发者、研究员需要直接粘贴整篇文档，现有10k限制制约了大模型能力。
- **“用9router转发QwenPaw模型一直400，升了好几个版本也没修”**（#5658） — 特定转发链路用户长期受困，期待根本性修复。
- **“自动填充老是弹出来，没法正常搜模型”**（#5403） — 用户体验细节问题，但影响配置流程顺畅度。
- **“需要让Agent在群里@另一个人，否则协作记录看不全”**（#5564） — 钉钉群内多Agent协作的典型需求，获得快速支持并感谢。

整体上，用户对响应速度（如钉钉@能力）表示满意，对长期存在的边缘稳定性问题（如转发连接、大历史会话崩溃）积累了一些挫败感。

### 8. 待处理积压
以下重要Issue或PR近期未获回应，可能需维护者关注：

- **v2.0.0预发布问题集中跟踪**（#5273，创建于6月17日） — 虽为核心跟踪issue，但最新更新仍为6月30日，需确保所有回归都已分流。
- **计算机使用Windows桌面自动化**（PR #5187，创建于6月14日） — 大型特性，状态仍为Open，缺乏近期评审反馈。
- **侧边栏聊天输入队列session迁移修复**（PR #5514，6月25日） — 涉及核心运行时，尚未合并，可能影响会话连续性。
- **GitPanel Tab样式修复**（PR #5151，6月12日） — 近20天未处理，简单的前端问题，建议尽快合并。
- **安全设置Shield图标垂直居中**（PR #5097，6月11日） — 类似微小UI修复，积压较久。

鉴于PR待合并数量较多（28 open），建议维护者按模块进行批量Review，避免贡献堆积。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**ZeroClaw 项目日报 — 2026-07-01**

---

### 1. 今日速览
今日项目处于**高度活跃的迭代期**，无新版本发布但代码空间非常忙碌：过去24小时有6个Issue更新（4个新开，2个关闭）和50个PR状态变化，其中4个PR完成合并或关闭，46个PR仍在评审队列。社区贡献主要集中在稳定性修复（网关重命名/删除代理的持久化问题）、安全增强（技能包解压防护、审计日志错误链完善）以及Web体验提升（秘密字段状态显示）。整体上项目冲刺向前，但大量PR堆积提示维护者审核压力较大。

### 2. 版本发布
今日无新版本发布。

### 3. 项目进展
今日成功合并/关闭了2个针对网关关键缺陷的修复PR，显著提升了代理生命周期管理的可靠性：
- **#8018** 修复代理重命名后，因持久化与状态更新顺序问题导致的“分裂脑”无法收敛的警告，改为重新发起回合制收敛流程，使系统能自动恢复，无需运维人工介入。
- **#8017** 修复代理删除操作先归档工作区再持久化配置的问题，避免在持久化失败时，代理名下状态（记忆、cron、会话）已被移除但配置仍留在系统中，造成不一致。
这两项修复进一步加固了ZeroClaw在分布式网关场景下的数据一致性和故障自愈能力。

### 4. 社区热点
今日讨论最活跃的内容集中在架构决策与重大特性方向：
- **RFC #6943**（已关闭，4条评论）：提出用直接宿主wasmtime组件模型替代Extism，并将插件构建目标改为`wasm-wasip2`，以解决当前插件系统目标冲突（FND-001）和实现简化。社区背后的诉求是希望有一套单一、标准的运行时绑定，避免维护多套互斥方案。
- **PR #8033**（仍开放，大量标签、XL规模）：实现端到端的智能体入职双路径（LLM + 确定性），并通过RPC和CLI暴露可遍历的状态树，这是核心体验落地的关键PR，吸引了大量关注。
- **新功能请求 #8550**（新开）：要求增加OpenAI兼容的chat completions端点，反映出社区希望用标准客户端（Open WebUI、LobeChat）直接对接ZeroClaw的强烈需求，可能影响后续接口抽象。

### 5. Bug 与稳定性
今日报告了2个安全与功能缺陷，暂未见对应的修复PR出现：
- **S1 - 流程阻断 #8553**：当智能体试图使用环境变量（如`SLACK_BOT_TOKEN`）作为`http_request`工具的密钥时，找不到任何可用路径，导致自动化工作流完全被阻断。这直接影响依赖外部服务认证的Agent。
- **S2 - 行为退化 #8554**：技能包解压器`extract_zip_secure`只检查压缩后大小和路径穿越，未限制解压条目数、膨胀比及最终解压大小，在技能市场下载场景下存在zip炸弹攻击风险，可能耗尽资源。

### 6. 功能请求与路线图信号
用户侧提出的新需求开始形成清晰的演进方向：
- **秘密字段状态可视化 #8556** 已有对应的实现PR **#8557**，将在Web配置界面区分“已设置”和“未设置”状态，不再始终显示空密码框，提升配置管理体验，大概率进入下一版本。
- **OpenAI兼容端点 #8550** 直接反映了接入标准工具链的诉求，目前无关联PR，但在社区中呼声较高，可能成为网关API层面的路线图优先项。
- 已关闭的RFC **#6943** 标志着Wasm运行时选型方向已定，未来插件生态将基于wasmtime component model演进，对后续技能开发范式有深远影响。

### 7. 用户反馈摘要
从近期Issue评论与描述中可提炼以下典型痛点与期望：
- **环境认证不便**：多个场景要求Agent调用带Token的API，但当前只能使用预设的秘密后端，无法自然引用进程环境变量，导致开发者在CI/CD和本地测试中的集成体验割裂（见 #8553）。
- **安全配置不可见**：用户打开Web配置时，无法判断某个密钥字段是否已填写，容易误操作覆盖，要求直观的已设置状态提示（#8556）。
- **供应链安全担忧**：技能包安装时缺少对压缩包膨胀的严格限制，有用户明确提出需要按条目数、比例和最大解压体积三重防护（#8554），表明社区对安全沙箱的预期在提高。
- **标准化接入呼声**：出现独立的请求要求提供OpenAI兼容API，显示部分用户希望在不修改现有客户端的前提下直接使用ZeroClaw作为后端，降低迁移成本。

### 8. 待处理积压
以下重要条目长期处于开放状态，建议维护者纳入近期冲刺：
- **PR #6297**：为WhatsApp/Signal频道添加投票及交互式回复事件支持，同时暴露`Channel::send_choice`，已从5月3日开放至今逾2个月，风险高、规模大，且经过多次刷新，承载了多通道对话能力关键升级，长期积压可能造成分支合并冲突。
- **PR #8428**：实现缺失插件建议功能，基于离线注册表缓存提升技能环境自愈能力，6月28日创建，虽不陈旧但涉及技能和运行时核心模块，宜尽快评审以跟上插件系统变更节奏。

---

*本日报基于公开的仓库活动自动生成，仅反映截至2026-07-01 00:00 UTC的数据快照。*

</details>