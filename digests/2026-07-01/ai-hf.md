# Hugging Face 热门模型日报 2026-07-01

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-30 16:24 UTC

---

# Hugging Face 热门模型日报
**日期：2026-07-01**

## 今日速览
GLM-5.2 以超 3 千点赞领跑本周趋势，英伟达迅速跟进发布 NVFP4 优化版，开源社区 quantized 热情高涨。多模态模型密集涌现：Ornith 系列与 Qwen-AgentWorld 争夺图像理解高地，百度 Unlimited-OCR 和英伟达 LocateAnything-3B 则重新定义视觉感知边界。另一边，无审查版 Qwen3.6 下载量突破 300 万，安全与编码专用模型通过 GGUF 格式加速分发，生态明显向「多模态 + 垂直微调 + 高效量化」并进。

## 热门模型

### 🧠 语言模型
- [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)  
  作者: zai-org | 👍 3,007 | ⬇️ 142,547  
  智谱最新旗舰对话模型，采用 MoE 架构，本周点赞最高，是当前最受关注的纯文本生成模型。

- [nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)  
  作者: nvidia | 👍 177 | ⬇️ 104,746  
  英伟达对 GLM-5.2 的官方 FP4 量化版，通过 Model Optimizer 大幅压缩显存，适合本地部署。

- [nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)  
  作者: nvidia | 👍 384 | ⬇️ 5,495,402  
  通义千问 3.6 的 NVFP4 优化版，下载量惊人，显示企业端对高效推理模型的强烈需求。

- [deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)  
  作者: deepseek-ai | 👍 244 | ⬇️ 6,939  
  DeepSeek V4 系列的专业版，新架构首次登上热榜，带来增强的推理与执行能力。

- [deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)  
  作者: deepseek-ai | 👍 107 | ⬇️ 4,446  
  V4 家族的轻量版，面向低延迟场景，与 Pro 形成高低搭配。

- [Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)  
  作者: Chunjiang-Intelligence | 👍 132 | ⬇️ 1,519  
  专注网络安全的 DeepSeek V4 社区微调，为垂直领域语言模型提供新范式。

- [LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)  
  作者: LiquidAI | 👍 162 | ⬇️ 17,839  
  Liquid 基础模型新成员，主打高效的小尺寸文本生成，探索非 Transformer 架构路线。

### 🎨 多模态与生成
- [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)  
  作者: baidu | 👍 1,458 | ⬇️ 429,056  
  百度推出的万能 OCR 模型，端到端图像文字提取，下载量近 43 万，实用性极强。

- [empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)  
  作者: empero-ai | 👍 581 | ⬇️ 99,359  
  以 Claude 神话风格微调的多模态 9B 模型，融合 Qwen3.5 视觉与推理能力。

- [Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)  
  作者: Qwen | 👍 456 | ⬇️ 28,480  
  阿里官方发布的世界模型 Agent，支持图像理解与复杂环境交互，多模态 AI 的前沿探索。

- [deepreinforce-ai/Ornith-1.0-9B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B)  
  作者: deepreinforce-ai | 👍 298 | ⬇️ 26,151  
  Ornith 系列多模态基座，9B 参数实现图像到文本生成，MIT 许可友好。

- [deepreinforce-ai/Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B)  
  作者: deepreinforce-ai | 👍 253 | ⬇️ 69,048  
  35B 多模态 MoE 版本，性能更强的同时保持可部署性。

- [deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)  
  作者: deepreinforce-ai | 👍 175 | ⬇️ 2,564  
  超大参数多模态模型，面向极致能力，适合研究场景。

- [nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)  
  作者: nvidia | 👍 2,508 | ⬇️ 800,597  
  英伟达视觉定位模型，小尺寸却能精准检测任意物体，本周多模态领域的最大亮点。

- [krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)  
  作者: krea | 👍 415 | ⬇️ 45,668  
  Krea 新一代图像生成模型的 Turbo 版，出图速度大幅提升。

- [krea/Krea-2-Raw](https://huggingface.co/krea/Krea-2-Raw)  
  作者: krea | 👍 255 | ⬇️ 32,008  
  Krea-2 的原始权重，供社区微调与深入研究。

- [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)  
  作者: nvidia | 👍 751 | ⬇️ 87,115  
  英伟达语音识别小模型，专为流式 ASR 设计，端侧部署友好。

### 🔧 专用模型
- [WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)  
  作者: WeiboAI | 👍 755 | ⬇️ 67,777  
  3B 数学推理专用模型，轻量级但解题能力突出，适合教育资源与本地助手。

- [BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)  
  作者: BugTraceAI | 👍 91 | ⬇️ 253  
  网络安全与攻击性安全专用模型，Q6 量化，用于漏洞分析与安全研究。

- [yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)  
  作者: yuxinlu1 | 👍 2,521 | ⬇️ 575,255  
  基于 Gemma 4 的编程模型 GGU F版，点赞超 2500，社区对开源代码 LLM 的热情持续高涨。

- [yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)  
  作者: yuxinlu1 | 👍 874 | ⬇️ 257,216  
  同一作者的代理/终端控制模型，强调工具调用与自主推理，GGUF 分发。

- [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)  
  作者: HauhauCS | 👍 2,346 | ⬇️ 3,017,678  
  无审查版 Qwen3.6 多模态模型，下载量破 300 万，体现社区对内容自由度的巨大需求。

### 📦 微调与量化
- [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)  
  作者: empero-ai | 👍 1,020 | ⬇️ 970,663  
  Qwythos 9B 多模态模型的 GGUF 量化版，几乎百万下载，是 llama.cpp 生态的主力。

- [deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)  
  作者: deepreinforce-ai | 👍 517 | ⬇️ 157,418  
  Ornith 35B 的 GGUF 版，方便消费级硬件运行多模态大模型。

- [deepreinforce-ai/Ornith-1.0-9B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF)  
  作者: deepreinforce-ai | 👍 330 | ⬇️ 98,750  
  9B 参数的高效量化版，平衡性能与资源消耗。

- [unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)  
  作者: unsloth | 👍 476 | ⬇️ 180,394  
  Unsloth 对 GLM-5.2 的 GGUF 转换，延续其快速优化的口碑。

- [unsloth/Qwen-AgentWorld-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen-AgentWorld-35B-A3B-GGUF)  
  作者: unsloth | 👍 121 | ⬇️ 155,333  
  世界模型 Agent 的 GGUF 版本，让多模态智能体可在本地跑起来。

- [fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)  
  作者: fal | 👍 122 | ⬇️ 0  
  LTX 视频模型的三维真实感 LoRA，图像到视频的风格微调新作。

- [ilkerzgi/fal-Krea-2-Style-LoRAs](https://huggingface.co/ilkerzgi/fal-Krea-2-Style-LoRAs)  
  作者: ilkerzgi | 👍 88 | ⬇️ 0  
  Krea-2 图像模型的多风格 LoRA 索引，为 AI 绘画提供丰富风格库。

## 生态信号
GLM 与 Qwen 家族继续统治榜单，智谱和阿里交替发布 MoE 新作，英伟达则以 NVFP4 量化方案深度介入分发，强化了「官方优化权重」这一新模式。开源权重优势不可撼动，所有上榜模型均提供开放权重，但闭源 API 的影子仍在部分微调叙事中若隐若现。社区量化活动空前活跃：GGUF 已成为本地部署的事实标准，几乎每款主流模型都有 unsloth 或作者自转的 GGUF 版本，而 LoRA 微调从图像、视频蔓延到风格控制。专用模型赛道里，编程、数学和无审查对话三者下载量断崖式领先，说明用户正在从通用助手转向高可控、垂直优化的具体工具。多模态也不再是附庸——图像理解、视觉定位、OCR 模型已占据半壁江山。

## 值得探索
- **nvidia/LocateAnything-3B**：仅 3B 参数就在视觉定位任务上获得 2.5k 点赞、80 万下载，小模型的高精度令人兴奋，非常适合端侧与实时物体检测研究。
- **WeiboAI/VibeThinker-3B**：专注数学推理的轻量模型，3B 尺寸意味着能在笔记本上流畅运行，为教育 AI 和可解释推理提供新基线。
- **HauhauCS/Qwen3.6-35B-A3B-Uncensored**：下载量超 300 万的争议性模型，多模态 + 无审查的组合反映了用户对创作自由的渴望，同时值得研究安全与对齐的边界。