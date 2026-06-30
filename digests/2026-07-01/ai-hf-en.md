# Hugging Face Trending Models Digest 2026-07-01

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-30 16:24 UTC

---

### Hugging Face Trending Models Digest — July 1, 2026

**1. Today’s Highlights**
The Hugging Face trending list this week is dominated by multimodal models and quantized fine-tunes. Zhipu AI’s GLM-5.2, a large Mixture-of-Experts language model, tops the leaderboard in likes, signaling strong interest in new open-weight MoE architectures. Vision-language models continue to surge, with Baidu’s Unlimited-OCR for advanced image-to-text and NVIDIA’s LocateAnything-3B for precise visual grounding both attracting high engagement. The community shows an enormous appetite for efficient deployment through GGUF and NVFP4 quantizations, as seen in the massive download numbers for Nvidia’s Qwen3.6 NVFP4 and various Gemma-based agentic coding GGUF models. Uncensored multimodal fine-tunes like HauhauCS’s Qwen3.6-based model also gain traction, reflecting a demand for unrestricted creative and roleplay use. Overall, the ecosystem is moving fast toward open, multimodal, and locally deployable AI.

**2. Trending Models by Category**

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)
- [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2) — Author: zai-org | Likes: 3,007 | Downloads: 142,547  
  A state-of-the-art Mixture-of-Experts text-generation model from Zhipu AI with native conversational ability, trending as a major new open LLM release.
- [deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark) — Author: deepseek-ai | Likes: 244 | Downloads: 6,939  
  DeepSeek’s latest V4 Pro model with DSpark attention, delivering cutting-edge text generation performance and research interest.
- [deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark) — Author: deepseek-ai | Likes: 107 | Downloads: 4,446  
  A faster, Flash variant of the DeepSeek V4 series optimized for efficiency while retaining strong language capabilities.
- [LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M) — Author: LiquidAI | Likes: 162 | Downloads: 17,839  
  A compact 230M language model built on Liquid AI’s novel LFM2 architecture, drawing curiosity for non-Transformer design.

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)
- [baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR) — Author: baidu | Likes: 1,458 | Downloads: 429,056  
  A powerful image-text-to-text model for optical character recognition that pushes the boundaries of general-purpose OCR with high accuracy, trending due to its robust feature-extraction capabilities.
- [Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B) — Author: Qwen | Likes: 456 | Downloads: 28,480  
  An official Qwen multimodal MoE model designed as an agent world model, supporting image-text-to-text tasks and advancing embodied AI research.
- [krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo) — Author: krea | Likes: 415 | Downloads: 45,668  
  A fast text-to-image generation model from Krea, providing high-quality, stylized visuals in a turbo-charged inference pipeline.
- [krea/Krea-2-Raw](https://huggingface.co/krea/Krea-2-Raw) — Author: krea | Likes: 255 | Downloads: 32,008  
  The base raw output version of Krea-2 for text-to-image generation, giving users full control over the creative process.
- [Comfy-Org/Krea-2](https://huggingface.co/Comfy-Org/Krea-2) — Author: Comfy-Org | Likes: 200 | Downloads: 10  
  A ComfyUI workflow/node for seamless integration of Krea-2 text-to-image models into the popular ComfyUI ecosystem.
- [nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B) — Author: nvidia | Likes: 2,508 | Downloads: 800,597  
  A compact 3B vision-language model that excels at open-vocabulary object localization and visual feature extraction, widely adopted for its utility.
- [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) — Author: HauhauCS | Likes: 2,346 | Downloads: 3,017,678  
  An uncensored, aggressive fine-tune of Qwen3.6 MoE with vision capabilities, surging in popularity for unrestricted creative and conversational AI.
- [fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA) — Author: fal | Likes: 122 | Downloads: 0  
  A LoRA adapter for LTX 2.3 image-to-video model that enhances 3D realism and consistency in generated videos.
- [nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b) — Author: nvidia | Likes: 751 | Downloads: 87,115  
  A tiny 0.6B Nemotron-based automatic speech recognition model optimized for streaming, offering strong performance in a lightweight package.

#### 🔧 Specialized Models (code, math, medical, embeddings)
- [WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B) — Author: WeiboAI | Likes: 755 | Downloads: 67,777  
  A math-focused 3B model based on Qwen2 that demonstrates strong reasoning abilities, making it a top choice for educational and problem-solving applications.
- [Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable) — Author: Chunjiang-Intelligence | Likes: 132 | Downloads: 1,519  
  A DeepSeek V4 fine-tune specialized in cybersecurity, offering advanced capabilities for security analysis and threat detection.
- [BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6) — Author: BugTraceAI | Likes: 91 | Downloads: 253  
  A 27B GGUF-quantized model tailored for offensive and defensive cybersecurity tasks, built on Qwen3 to automate vulnerability research.

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)
- [empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M) — Author: empero-ai | Likes: 581 | Downloads: 99,359  
  A 9B Qwen3.5-based model merged with Claude-style reasoning, creating a “mythos” persona for creative and philosophical dialogue.
- [empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) — Author: empero-ai | Likes: 1,020 | Downloads: 970,663  
  The GGUF-quantized version of Qwythos-9B, enabling local CPU/edge inference of this reasoning model with extremely high adoption.
- [deepreinforce-ai/Ornith-1.0-9B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B) — Author: deepreinforce-ai | Likes: 298 | Downloads: 26,151  
  A permissively licensed (MIT) 9B language model fine-tuned from Qwen3.5 with image-text capabilities, serving as a strong general-purpose LLM.
- [deepreinforce-ai/Ornith-1.0-9B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF) — Author: deepreinforce-ai | Likes: 330 | Downloads: 98,750  
  The GGUF quantized variant of Ornith-1.0-9B, facilitating easy local deployment.
- [deepreinforce-ai/Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B) — Author: deepreinforce-ai | Likes: 253 | Downloads: 69,048  
  A larger 35B MoE Ornith model with MIT license, balancing power and accessibility for advanced text and multimodal tasks.
- [deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF) — Author: deepreinforce-ai | Likes: 517 | Downloads: 157,418  
  The GGUF quantization of the Ornith 35B MoE, making the large model more practical for consumer hardware.
- [deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B) — Author: deepreinforce-ai | Likes: 175 | Downloads: 2,564  
  A massive 397B MoE model continuing the Ornith series at frontier scale, attracting interest despite limited downloads due to hardware demands.
- [yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF) — Author: yuxinlu1 | Likes: 874 | Downloads: 257,216  
  A merged and fine-tuned Gemma 4 12B model with agentic and terminal-use coding skills, distributed as GGUF for easy local execution.
- [yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF) — Author: yuxinlu1 | Likes: 2,521 | Downloads: 575,255  
  An exceptionally popular GGUF coding model based on Gemma 4 12B, delivering state-of-the-art code generation and reasoning capabilities.
- [unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF) — Author: unsloth | Likes: 476 | Downloads: 180,394  
  Unsloth’s GGUF conversion of GLM-5.2, enabling efficient local use of Zhipu’s MoE model.
- [unsloth/Qwen-AgentWorld-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen-AgentWorld-35B-A3B-GGUF) — Author: unsloth | Likes: 121 | Downloads: 155,333  
  A GGUF quantized version of Qwen’s AgentWorld model, bringing the agentic vision model to consumer devices.
- [nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4) — Author: nvidia | Likes: 177 | Downloads: 104,746  
  NVIDIA’s FP4 quantized version of GLM-5.2 using ModelOpt, significantly reducing memory footprint while preserving quality.
- [nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4) — Author: nvidia | Likes: 384 | Downloads: 5,495,402  
  The NVFP4 quantization of Qwen3.6 35B MoE, achieving massive adoption with over 5.4 million downloads due to extreme efficiency.
- [ilkerzgi/fal-Krea-2-Style-LoRAs](https://huggingface.co/ilkerzgi/fal-Krea-2-Style-LoRAs) — Author: ilkerzgi | Likes: 88 | Downloads: 0  
  A collection of style LoRAs for the fal.ai Krea-2 text-to-image model, offering diverse artistic styles for image generation.

**3. Ecosystem Signal**
The Hugging Face model ecosystem is clearly leaning into two major forces: multimodal LLMs and extreme quantization for local deployment. Mixture-of-Experts architectures have become mainstream, with Zhipu AI’s GLM-5.2, Qwen 3.6, and DeepSeek V4 all using MoE to scale capability while managing inference cost. NVIDIA’s NVFP4 quantization for both GLM-5.2 and Qwen3.6 models, alongside the ever-popular GGUF format from unsloth and community members, demonstrates that the community prioritizes on-device, efficient inference. The staggering 5.5 million downloads for the Qwen3.6 NVFP4 model highlights how fast these optimized weights spread. There is also a notable wave of agentic and coding fine-tunes, especially on Gemma 4 and Qwen architectures, with creators merging reasoning and tool-use capabilities into compact 12B–35B models. Open-weight releases from DeepSeek, Qwen, NVIDIA, Liquid AI, and Zhipu AI keep the ecosystem highly competitive and transparent, while a niche demand for uncensored multimodal models (e.g., HauhauCS) signals a user base seeking less restricted creative outputs. Overall, 2026 shows a mature open-source AI supply chain: powerful base models, fast fine-tunes, and instant quantizations all trending simultaneously.

**4. Worth Exploring**
1. **zai-org/GLM-5.2** — The latest MoE conversational model from a major Chinese AI lab, combining cutting-edge text generation with native safetensors and strong community adoption (3k likes). It’s a must-try for evaluating the new wave of open-weight MoE LLMs.
2. **nvidia/LocateAnything-3B** — With 2,500 likes and 800k downloads, this compact vision-language model redefines open-vocabulary localization in a tiny footprint. Ideal for developers building real-world applications needing precise visual understanding.
3. **baidu/Unlimited-OCR** — A breakthrough in general-purpose OCR that goes beyond traditional pipelines, offering robust feature extraction and high accuracy. Its popularity (1.4k likes) suggests it could become the go-to for document digitization and image-to-text tasks.