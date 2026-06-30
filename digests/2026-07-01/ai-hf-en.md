# Hugging Face Trending Models Digest 2026-07-01

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-30 17:11 UTC

---

# Hugging Face Trending Models Digest — 2026-07-01

## 1. Today's Highlights

This week's trending models reveal a strong push toward **multimodal MoE architectures** and **agentic code-specialized models**. GLM-5.2 emerges as the most-liked model with 3,009 weekly likes, while NVIDIA's LocateAnything-3B (2,508 likes) demonstrates surging demand for grounded vision-language tools. The ecosystem is seeing a wave of community GGUF quantization activity, with Ornith-1.0 spawning four separate quantized variants in the top 30. Notably, Qwen's model family continues to dominate the MoE landscape, with Qwen3.6 derivatives appearing across multiple trending entries.

## 2. Trending Models

### 🧠 Language Models

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** by zai-org • 3,009 likes • 142,547 downloads  
  A top-liked MoE-DSA architecture model optimized for conversational text generation, likely benefiting from strong Chinese-language performance and efficient sparse activation.

- **[Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B)** by deepreinforce-ai • 253 likes • 69,048 downloads  
  Full-precision 35B MoE model from a rising new family, with GGUF, 9B, and 397B variants all trending simultaneously.

- **[DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** by deepseek-ai • 245 likes • 6,939 downloads  
  Latest DeepSeek generation with a new "DSpark" inference acceleration method, supported by an arXiv paper (2606.19348).

- **[Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** by HauhauCS • 2,349 likes • 3,017,678 downloads  
  The highest-download model this week — a community uncensored finetune of Qwen3.6 MoE with aggressive system prompt tuning for maximum creativity.

- **[VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** by WeiboAI • 755 likes • 67,777 downloads  
  A compact 3B math-specialized model built on Qwen2, demonstrating that small reasoning models continue to attract strong interest.

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** by LiquidAI • 164 likes • 17,839 downloads  
  Ultra-efficient 230M parameter model from Liquid AI's LFM2.5 series, targeting edge deployment with liquid neural network architecture.

- **[DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)** by Chunjiang-Intelligence • 132 likes • 1,519 downloads  
  A cybersecurity-focused fine-tune of DeepSeek-V4, showing increasing niche specialization in safety and security domains.

### 🎨 Multimodal & Generation

- **[Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** by baidu • 1,461 likes • 429,056 downloads  
  Baidu's unlimited-scope OCR model for image-text-to-text tasks, likely used for document processing and scene text recognition.

- **[Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** by krea • 416 likes • 45,668 downloads  
  Accelerated text-to-image diffusion model building on Krea-2-Raw, optimized for fast generation while maintaining quality.

- **[Krea-2-Raw](https://huggingface.co/krea/Krea-2-Raw)** by krea • 255 likes • 32,008 downloads  
  Base Krea-2 model with open license, serving as foundation for community LoRAs and finetunes.

- **[LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** by fal • 122 likes • 0 downloads  
  Just-released LoRA adapter for LTX-2.3 enabling 3D-realistic video generation from single images.

### 🔧 Specialized Models

- **[LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** by nvidia • 2,508 likes • 800,597 downloads  
  NVIDIA's grounded object detection and segmentation model — the second most-liked model, showing massive demand for generalist vision tools.

- **[Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** by Qwen • 459 likes • 28,480 downloads  
  Task-oriented MoE model for agentic world modeling, supporting both text and vision inputs.

- **[BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** by BugTraceAI • 91 likes • 253 downloads  
  Qwen3-based quantized model specializing in offensive and defensive cybersecurity analysis.

### 📦 Fine-tunes & Quantizations

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** by yuxinlu1 • 878 likes • 257,216 downloads  
  Heavily customized Gemma-4 quantized variant with "agentic fable" storytelling optimization and terminal integration.

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** by yuxinlu1 • 2,521 likes • 575,255 downloads  
  The third most-liked model — Gemma-4-12B fine-tuned for code generation and reasoning, quantized for local deployment.

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** by unsloth • 476 likes • 180,394 downloads  
  Unsloth's efficient GGUF quantization of GLM-5.2, making the large MoE model accessible on consumer hardware.

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** by nvidia • 177 likes • 104,746 downloads  
  NVIDIA's ModelOpt-optimized 4-bit floating point version of GLM-5.2 for enterprise deployment.

- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** by nvidia • 385 likes • 5,495,402 downloads  
  The highest-download model overall — NVIDIA's FP4 quantized Qwen3.6 MoE for efficient inference on Blackwell hardware.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** by empero-ai • 1,024 likes • 970,663 downloads  
  Claude-Mythos fine-tune of Qwen3.5 in GGUF format, blending Anthropic-inspired reasoning with open model accessibility.

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** by huihui-ai • 84 likes • 65 downloads  
  "Abliterated" variant of GLM-5.2 with safety guardrails removed for unrestricted use cases.

## 3. Ecosystem Signal

**MoE dominance accelerates.** The top 30 is increasingly dominated by Mixture-of-Experts models: GLM-5.2's MoE-DSA, Qwen3.5/3.6 MoE variants, and the Ornith-1.0 family (all MoE-based) represent over half of trending language models. This signals that **sparse activation has become the default architecture** for competitive LLM releases.

**Quantization is now infrastructure, not an afterthought.** Unsloth and NVIDIA are racing to provide optimized inference formats — unsloth's GGUF variants and NVIDIA's NVFP4 both appear multiple times. The Qwen3.6-35B-A3B-NVFP4's staggering 5.5M downloads suggests **enterprise-scale FP4 adoption is accelerating**, likely driven by NVIDIA Blackwell GPU compatibility.

**Agentic and specialized fine-tuning is exploding.** Models targeting "agentic," "fable," "composer," and "security" use cases show that the community is moving beyond generic chat to task-specific deployments. The Gemma-4 ecosystem, in particular, is being heavily customized for coding and agent workflows.

**Open-weight momentum is sustained.** All 30 trending models are open-weight with permissive licenses. Even "proprietary-inspired" models like Qwythos (Claude-Mythos style) are remixed into open formats, indicating the open ecosystem is absorbing and reinterpreting closed-source advances.

## 4. Worth Exploring

1. **[LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — NVIDIA's vision grounding model at just 3B parameters is the v2 of their detection/masking work. With 800K downloads and 2.5K likes, it's likely the most practical vision tool this week for developers needing zero-shot object localization without heavy compute.

2. **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — The third most-liked model represents a fascinating trend: deeply customized Gemma-4 variants for specialized use cases. Worth studying for anyone interested in how fine-tuning can dramatically shift base model behavior for coding or creative writing.

3. **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** — With 5.5 million downloads, this is **the model to watch** for production MoE deployment. NVIDIA's FP4 quantization on Qwen3.6 MoE represents the cutting edge of enterprise inference efficiency — a must-study for teams deploying LLMs at scale.

---
*This digest is auto-generated by [agents-radar](https://github.com/ys578/agents-radar).*