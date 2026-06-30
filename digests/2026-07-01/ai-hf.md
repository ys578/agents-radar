# Hugging Face 热门模型日报 2026-07-01

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-30 17:11 UTC

---

好的，作为AI模型生态分析师，以下是根据您提供的2026年7月1日数据生成的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年7月1日**

#### **今日速览**

本周Hugging Face社区焦点集中于**混合专家模型（MoE）的全面爆发**，特别是以Qwen 3.5/3.6、GLM-5.2为代表的系列模型占据主导地位。在量化与部署领域，来自`empero-ai`和`yuxinlu1`的GGUF版本社区微调模型（如Qwythos和Gemma-4衍生版本）下载量巨大，显示出强大的本地部署需求。同时，以百度`Unlimited-OCR`和英伟达`LocateAnything-3B`为代表的多模态理解应用模型也取得了极高的人气。此外，`Krea-2`系列模型的发布标志着开源文本到图像生成进入新阶段，而`DeepSeek-V4`的多个变体也释放出前沿研究信号。

---

#### **热门模型**

##### 🧠 语言模型（LLM、对话、指令微调）

*   **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** - 作者: zai-org | 👍 3,009 | ⬇️ 142,547
    *   基于GLM架构的MoE模型，凭借极高的点赞数成为本周最受关注的预训练权重发布，代表了中文大模型在MoE方向的最新成果。

*   **[Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** - 作者: deepreinforce-ai | 👍 519 | ⬇️ 157,418
    *   Ornith-1.0系列的最大规模版本量化版，为社区提供了在消费级硬件上运行35B参数模型的可能性，下载量可观。

*   **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** - 作者: Qwen | 👍 459 | ⬇️ 28,480
    *   阿里Qwen团队发布的世界模型变体，使用3B激活参数（35B总参数），专注于Agent任务，标志着大模型向“具身智能”和“环境理解”的进化。

*   **[DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** - 作者: deepseek-ai | 👍 245 | ⬇️ 6,939
    *   深度求索最新一代模型的Pro版本，带有学术论文（arxiv:2606.19348）背书，代表前沿开源闭源混合研究的尖端水平。

*   **[Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** - 作者: deepreinforce-ai | 👍 176 | ⬇️ 2,564
    *   接近4000亿参数的超大MoE模型，虽下载量不高，但其存在本身就标志着一个雄心勃勃的开源模型预训练项目。

*   **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** - 作者: LiquidAI | 👍 164 | ⬇️ 17,839
    *   Liquid AI最新的液态基础模型系列，以极小参数（230M）实现优秀性能，是探索新架构（液态网络）方向的代表性模型。

*   **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** - 作者: WeiboAI | 👍 755 | ⬇️ 67,777
    *   基于Qwen2的微博AI微调模型，专门优化数学和逻辑推理能力，在中等规模模型（3B）中表现出色，人气很高。

##### 🎨 多模态与生成模型（图像、视频、文本到X）

*   **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** - 作者: baidu | 👍 1,461 | ⬇️ 429,056
    *   百度的通用OCR模型，支持图片到文字识别、提取，其在实用性和准确率上的突破使其获得了极高的社区普及度。

*   **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** - 作者: nvidia | 👍 2,508 | ⬇️ 800,597
    *   英伟达的“万物定位”模型，通过语言指令在图像中定位任何物体。3B参数设计使其兼具高效与高精度，是本周下载量最大的模型之一。

*   **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** - 作者: krea | 👍 416 | ⬇️ 45,668
    *   Krea AI第二代图像生成模型的Turbo版本，主打快速推理和高性能，代表着开源文生图在质量和速度上的新平衡。

*   **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** - 作者: fal | 👍 122 | ⬇️ 0
    *   LTX视频模型的最新LoRA组件，专注生成写实3D视觉效果，代表了社区在视频生成领域持续的细化和专业化。

##### 🔧 专用模型（代码、数学、医疗、安全）

*   **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** - 作者: yuxinlu1 | 👍 2,521 | ⬇️ 575,255
    *   Gemma-4 12B模型的代码优化版本，通过“fable”微调策略显著增强了代码生成与推理能力，是顶级代码辅助模型之一。

*   **[Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)** - 作者: Chunjiang-Intelligence | 👍 132 | ⬇️ 1,519
    *   在DeepSeek-V4基础上针对网络安全场景进行“Fable”微调的专用模型，体现了前沿模型向高价值垂直领域的快速演进。

*   **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** - 作者: BugTraceAI | 👍 91 | ⬇️ 253
    *   专注于网络攻防与安全审计的专用模型，使用Qwen3作为基底，反映了AI在网络安全自动化领域的深度应用。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

*   **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** - 作者: empero-ai | 👍 1,024 | ⬇️ 970,663
    *   基于Qwen3.5的社区微调模型，融合了风格化对话和推理能力，其GGUF版本以接近百万的下载量成为社区量化部署的绝对热门。

*   **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** - 作者: unsloth | 👍 476 | ⬇️ 180,394
    *   unsloth团队为GLM-5.2提供的高质量GGUF量化版，极大降低了运行门槛，是GLM模型在本地部署领域迅速普及的关键推手。

*   **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** - 作者: nvidia | 👍 385 | ⬇️ 5,495,402
    *   英伟达使用ModelOpt工具对Qwen3.6 MoE模型进行的4位浮点（NVFP4）量化版本，凭借最高达500万的下载量，表明企业级硬件（如NVIDIA GPU）对高效MoE推理的旺盛需求。

*   **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** - 作者: huihui-ai | 👍 84 | ⬇️ 65
    *   针对GLM-5.2的“去审查”（abliterated）社区微调版本，反映了部分社区用户对模型输出“无束缚”的持续探索。

---

#### **生态信号**

本周模型生态释放出强烈信号：**混合专家模型（MoE）已成为绝对主流**，从参数规模（GLM-5.2、Ornith-397B、Qwen-AgentWorld）到部署方案（各种GGUF/NVFP4量化），MoE全面渗透。**量化/微调社区异常活跃**，呈现两极化：一方面，大型组织（Nvidia、unsloth）提供官方级优化工具和部署方案；另一方面，个人开发者（yuxinlu1、empero-ai）通过定制微调和“去审查”，展现了强大的社区创造力。这表明**开源模型的竞争力已从单纯的“发布参数”转向“易用性 & 垂直场景适配”**。`DeepSeek-V4`系列与`GLM-5.2`的出现，预示开源势能与闭源前沿的差距正在缩小。

---

#### **值得探索**

*   **📌 [nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
    *   **理由**：英伟达出品，下载量及点赞数均极高。如需一个开箱即用、精确且高效的图像定位/推理工具，这是当前最佳选择。3B参数使其易于部署。

*   **📌 [yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
    *   **理由**：量化版中代码能力最强的模型之一。如果您是开发者，希望在本地的LLM上获得媲美顶尖闭源模型（如Claude/DeepSeek Coder）的代码体验，这个经过“Fable”微调的Gemma-4变体是性价比极高的选择。

*   **📌 [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
    *   **理由**：作为本周点赞最高的原始权重模型，它代表了中文语言模型的最新突破。无论是研究MoE架构，还是打造顶级的国产化对话应用，这都是一款值得深入研究的基座模型。

---
*本日报由 [agents-radar](https://github.com/ys578/agents-radar) 自动生成。*