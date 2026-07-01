# Hugging Face Trending Models Digest 2026-07-01

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-01 11:41 UTC

---

Here is the **Hugging Face Trending Models Digest** for **2026-07-01**.

---

## 1. Today’s Highlights

This week’s trending models signal a clear shift toward **quantized, multimodal MoE architectures** and **specialized agentic/coding fine-tunes**. The **GLM-5.2 family** (by Zhipu AI) leads in raw likes, while **NVIDIA’s NVFP4-optimized Qwen3.6 variants** dominate downloads with a staggering 5.7M pulls—indicating strong enterprise demand for memory-efficient inference. Community fine-tuning is hyper-active around **Qwen3.5/3.6** and **DeepSeek-V4**, with multiple GGUF and abliterated variants trending. Notably, **NVIDIA’s LocateAnything-3B** (vision grounding) and **baidu/Unlimited-OCR** (image-text-to-text) show that multimodal utility models are gaining mainstream traction alongside large language models.

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org | 3,108 likes, 160K downloads  
  *Zhipu AI’s latest MoE-DSA conversational model, trending for its strong Chinese-English performance and high community engagement.*

- **[Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** — Qwen | 482 likes, 34K downloads  
  *A 35B MoE agent-oriented world model from the Qwen team, built for interactive reasoning and simulation tasks.*

- **[DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — deepseek-ai | 264 likes, 7.6K downloads  
  *An advanced DeepSeek-V4 variant with sparse attention (DSpark) for long-context reasoning, accompanied by an arXiv paper.*

- **[DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)** — deepseek-ai | 119 likes, 13K downloads  
  *A faster, lighter sibling of the V4 Pro, optimized for speed with the same DSpark long-context mechanism.*

- **[DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)** — Chunjiang-Intelligence | 136 likes, 1.8K downloads  
  *A cybersecurity-focused fine-tune of DeepSeek-V4 for narrative and threat analysis tasks.*

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — InternScience | 111 likes, 511 downloads  
  *An agent-oriented model built on Qwen3.5-MoE, designed for tool use and multi-step planning.*

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** — LiquidAI | 174 likes, 22K downloads  
  *A tiny (230M) but efficient liquid foundation model, trending for on-device and edge LLM deployment.*

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu | 1,534 likes, 630K downloads  
  *Baidu’s universal OCR model for image-to-text extraction, trending due to high utility and enterprise-grade performance.*

- **[Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)** — empero-ai | 603 likes, 114K downloads  
  *A multimodal Qwen3.5-based fine-tune blending large context windows and vision understanding, highly popular for creative chat.*

- **[Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — krea | 431 likes, 57K downloads  
  *A fast distilled text-to-image model built on Krea-2-Raw, favored for real-time creative generation.*

- **[Krea-2-Raw](https://huggingface.co/krea/Krea-2-Raw)** — krea | 260 likes, 40K downloads  
  *The base Diffusers model for the Krea-2 image generation series, available under a permissive license.*

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — nvidia | 2,533 likes, 896K downloads  
  *A 3B vision grounding model that can localize any object in an image; trending for robotics and multimodal RAG.*

- **[Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 2,367 likes, 3.06M downloads  
  *An uncensored, vision-capable MoE model with aggressive alignment; massively downloaded for exploratory use.*

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** — fal | 132 likes, 0 downloads  
  *A LoRA adapter for the LTX-2.3 video model enabling 3D-realistic video generation from images.*

- **[Comfy-Org/Krea-2](https://huggingface.co/Comfy-Org/Krea-2)** — Comfy-Org | 215 likes, 10 downloads  
  *A ComfyUI node integration for Krea-2, facilitating local image generation workflows.*

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[Ornith-1.0-9B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B) / [Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B) / [Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** — deepreinforce-ai | 318 / 274 / 183 likes  
  *A family of Qwen3.5-MoE fine-tunes spanning 9B to 397B parameters, optimized for agentic and reasoning-heavy tasks.*

- **[Meituan-LongCat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)** — meituan-longcat | 118 likes, 0 downloads  
  *Meituan’s long-context model for extended reasoning, likely used in search/recommendation; minimal public downloads yet.*

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — yuxinlu1 | 2,542 likes, 597K downloads  
  *A GGUF quant of a highly specialized Gemma-4 coding variant; the most liked gemma-4 community release this week.*

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 | 902 likes, 289K downloads  
  *Second Gemma-4 GGUF fine-tune with agentic and terminal capabilities; strong community adoption.*

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** — unsloth | 487 likes, 212K downloads  
  *Unsloth’s optimized GGUF quant of GLM-5.2, enabling fast local inference with the MoE-DSA architecture.*

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** — huihui-ai | 107 likes, 901 downloads  
  *An abliterated (uncensored) GGUF variant of GLM-5.2, appealing to users wanting reduced safety constraints.*

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** — nvidia | 191 likes, 137K downloads  
  *NVIDIA’s ModelOpt 4-bit quantization of GLM-5.2 for efficient deployment on NVIDIA hardware.*

- **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4) / [Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** — nvidia | 134 / 397 likes, 2.7K / 5.77M downloads  
  *NVFP4-quantized Qwen3.6 models; the 35B MoE is the most downloaded model overall this week, signaling massive enterprise interest in memory-savvy MoE inference.*

- **[Ornith GGUF variants](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF) / [Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai | 356 / 576 likes, 191K / 234K downloads  
  *GGUF quants of the Ornith models, making heavy MoE models accessible on consumer hardware via llama.cpp.*

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai | 1,103 likes, 1.11M downloads  
  *Highly downloaded GGUF quant of the multimodal Qwythos-9B, optimized for local creative text-image chat.*

- **[unsloth/Qwen-AgentWorld-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen-AgentWorld-35B-A3B-GGUF)** — unsloth | 125 likes, 196K downloads  
  *Unsloth GGUF of the Qwen agent world model, making agentic simulation accessible on CPU/edge.*

## 3. Ecosystem Signal

The current landscape shows a clear **triumph of Mixture-of-Experts (MoE)** architecture as the dominant paradigm for both proprietary and open-weight models. The **Qwen3.5/3.6** family (with A3B active parameters) and **GLM-5.2** (MoE-DSA) are the two most active ecosystems—both spawning dozens of community fine-tunes and quantizations. **NVIDIA’s NVFP4** quantization is becoming the default enterprise deployment path, with the Qwen3.6-35B-A3B-NVFP4 pulling 5.7M downloads—likely driven by internal or cloud deployments of MoE models requiring minimal VRAM. **Unsloth** remains the dominant third-party quantizer for GGUF, while **deepreinforce-ai** and **empero-ai** lead the “agentic-coder” fine-tune niche. On the multimodal side, **LocateAnything-3B** signals a shift toward capable, small vision models for grounding tasks, while **Unlimited-OCR** proves that utility models can go viral purely on function. Open-weight momentum is strong, but NVIDIA’s proprietary quantization layer is creating a new middle ground: open model weights + optimized proprietary runtime.

## 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — If you work in robotics, visual RAG, or image understanding, this 3B grounding model is a standout: small, fast, and highly capable. Recent demos show it performing comparably to much larger models on open-vocabulary localization.

2. **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — Representing the highest-quality Gemma-4 coding fine-tune, this GGUF is perfect for local code assistant workflows. Its unique “Composer” architecture and strong reasoning benchmarks make it a top pick for developer-local agents.

3. **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** — With 5.7M downloads, this is the model the ecosystem is betting on. It combines Qwen’s state-of-the-art MoE with NVIDIA’s optimized 4-bit inference. A must-study for anyone deploying large MoE models in production.

---
*This digest is auto-generated by [agents-radar](https://github.com/ys578/agents-radar).*