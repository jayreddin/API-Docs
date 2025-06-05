## [Encyclopedia](https://developer.puter.com/encyclopedia/)

# Llama 4

Updated: April 6, 2025


Llama 4 is a collection of pretrained and instruction-tuned mixture-of-experts (MoE) large language models (LLMs) developed by [Meta](https://ai.meta.com/). Released in April 2025, the Llama 4 family consists of several multimodal models optimized for image and text understanding, multilingual tasks, coding, tool-calling, and powering agentic systems.[1](https://developer.puter.com/encyclopedia/llama-4/#ref1) [2](https://developer.puter.com/encyclopedia/llama-4/#ref2) The models in this family include Llama 4 Scout, Llama 4 Maverick, and the unreleased Llama 4 Behemoth, with a fourth model called Llama 4 Reasoning announced for future release.[3](https://developer.puter.com/encyclopedia/llama-4/#ref3) These models represent a significant advancement over previous Llama generations, introducing native multimodality and mixture-of-experts architecture for improved efficiency and performance.

## Overview

Llama 4 marks the beginning of a new era for Meta's AI model ecosystem, featuring the company's first models built using a mixture-of-experts architecture.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) This approach allows the models to maintain a smaller active parameter count during computation while having access to a much larger total parameter pool. The Llama 4 models support multimodal inputs including text and images, with broad visual understanding capabilities that enable them to process up to eight images alongside text.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

All Llama 4 models have a knowledge cutoff date of August 2024[1](https://developer.puter.com/encyclopedia/llama-4/#ref1) and support twelve languages: Arabic, English, French, German, Hindi, Indonesian, Italian, Portuguese, Spanish, Tagalog, Thai, and Vietnamese, though image understanding is currently limited to English.[1](https://developer.puter.com/encyclopedia/llama-4/#ref1)

## Models

### Llama 4 Scout

Llama 4 Scout is a general-purpose model with 17 billion active parameters across 16 experts, totaling 109 billion parameters.[1](https://developer.puter.com/encyclopedia/llama-4/#ref1) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4) It is designed to run on a single [NVIDIA H100 GPU](https://www.nvidia.com/en-us/data-center/h100/) using [INT4 quantization](https://developer.nvidia.com/blog/int4-for-ai-inference/).[1](https://developer.puter.com/encyclopedia/llama-4/#ref1)

Key features of Llama 4 Scout include:

- Industry-leading [context length](https://developer.puter.com/encyclopedia/context-window/) of 10 million tokens[1](https://developer.puter.com/encyclopedia/llama-4/#ref1) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4)
- Native multimodality with early fusion of text and vision[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)
- Best-in-class image grounding capabilities[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)
- Support for multi-document summarization, parsing extensive user activity, and reasoning over large codebases[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

According to Meta, Llama 4 Scout exceeds the performance of comparable models such as Gemma 3, Gemini 2.0 Flash-Lite, and Mistral 3.1 across a broad range of benchmarks.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Llama 4 Maverick

Llama 4 Maverick is described as the "workhorse" of the Llama 4 family, featuring 17 billion active parameters but with 128 experts for a total of 400 billion parameters.[1](https://developer.puter.com/encyclopedia/llama-4/#ref1) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4) This model requires an NVIDIA H100 DGX system or equivalent for deployment.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

Key features of Llama 4 Maverick include:

- Superior image and text understanding for general assistant and chat use cases[3](https://developer.puter.com/encyclopedia/llama-4/#ref3) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4)
- Designed for creative writing and precise image understanding[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)
- Context length of 1 million tokens[1](https://developer.puter.com/encyclopedia/llama-4/#ref1)
- Best-in-class performance to cost ratio[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

Meta claims Llama 4 Maverick outperforms models like GPT-4o and [Gemini 2.0 Flash](https://developer.puter.com/encyclopedia/gemini-2-0-flash) across coding, reasoning, multilingual, long-context, and image benchmarks, while achieving comparable results to DeepSeek v3.1 on reasoning and coding with less than half the active parameters.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) An experimental chat version has scored an ELO of 1417 on LMArena.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Llama 4 Behemoth

Llama 4 Behemoth is Meta's largest and most powerful model in the Llama 4 family, with 288 billion active parameters across 16 experts, totaling nearly two trillion parameters.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) [5](https://developer.puter.com/encyclopedia/llama-4/#ref5) As of April 2025, this model was still in training and had not been publicly released.[2](https://developer.puter.com/encyclopedia/llama-4/#ref2) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

According to Meta, Llama 4 Behemoth outperforms GPT-4.5, [Claude 3.7 Sonnet](https://developer.puter.com/encyclopedia/claude-3-7-sonnet), and Gemini 2.0 Pro on several STEM-focused benchmarks such as [MATH-500](https://huggingface.co/datasets/HuggingFaceH4/MATH-500) and [GPQA Diamond](https://arxiv.org/abs/2311.12022).[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) Meta CEO Mark Zuckerberg has described it as "the highest performing base model in the world."[3](https://developer.puter.com/encyclopedia/llama-4/#ref3)

The Behemoth model serves as a teacher for the other Llama 4 models through a process Meta refers to as codistillation.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Llama 4 Reasoning

A fourth model, Llama 4 Reasoning, was announced by Mark Zuckerberg to be coming "in the next month" (as of April 2025).[3](https://developer.puter.com/encyclopedia/llama-4/#ref3) No specific details about this model were provided in the initial Llama 4 release communications.

## Technical architecture

### Mixture-of-experts (MoE)

The Llama 4 models are Meta's first to use a mixture-of-experts (MoE) architecture, which is more computationally efficient for both training and inference.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) In this approach, a single token activates only a fraction of the total parameters:

- For Llama 4 Maverick, with 17 billion active parameters out of 400 billion total parameters, the architecture uses alternating dense and MoE layers for inference efficiency.
- MoE layers use 128 routed experts and a shared expert. Each token is sent to the shared expert and also to one of the 128 routed experts.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

This design improves inference efficiency by lowering model serving costs and latency, allowing Llama 4 Maverick to run on a single NVIDIA H100 DGX host, or with distributed inference for maximum efficiency.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Native multimodality

Llama 4 models feature native multimodality with early fusion to seamlessly integrate text and vision tokens into a unified model backbone.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) This enables joint pre-training with large amounts of unlabeled text, image, and video data.

The vision encoder in Llama 4 is based on [MetaCLIP](https://github.com/facebookresearch/MetaCLIP) but trained separately in conjunction with a frozen Llama model to better adapt the encoder to the LLM.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) The models support multiple image inputs, with good results tested for up to eight images.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Extended context length

Llama 4 Scout dramatically increases the supported context length from 128K tokens in Llama 3 to an industry-leading 10 million tokens.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) This is achieved through:

- The iRoPE architecture, where "i" stands for "interleaved" attention layers without positional embeddings
- Inference time temperature scaling of attention to enhance length generalization
- Special training with a 256K context length to empower the base model with advanced length generalization capability[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

## Training and development

### Pre-training

The Llama 4 models were pre-trained on more than 30 trillion tokens, which is more than double the Llama 3 pre-training mixture and includes diverse text, image, and video datasets.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) Meta developed a new training technique referred to as MetaP that allows reliable setting of critical model hyper-parameters such as per-layer learning rates and initialization scales.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

For multilingual capabilities, Llama 4 was pre-trained on 200 languages, including over 100 with more than 1 billion tokens each, representing 10 times more multilingual tokens than Llama 3.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

The pre-training process used FP8 precision without sacrificing quality, ensuring high model FLOPs utilization—while pre-training Llama 4 Behemoth using FP8 and 32K GPUs, Meta achieved 390 TFLOPs/GPU.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Post-training

Meta revamped their post-training pipeline for Llama 4 by adopting a different approach: lightweight supervised fine-tuning (SFT) > online reinforcement learning (RL) > lightweight direct preference optimization (DPO).[4](https://developer.puter.com/encyclopedia/llama-4/#ref4) They implemented a continuous online RL strategy, alternating between training the model and then using it to continually filter and retain only medium-to-hard difficulty prompts.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

For Llama 4 Behemoth, the large scale required Meta to completely overhaul their approach:

- 95% of the SFT data was pruned (compared to 50% for smaller models)
- Lightweight SFT was followed by large-scale reinforcement learning
- Training focused on sampling hard prompts using pass@k analysis with the policy model
- A training curriculum of increasing prompt hardness was crafted
- Prompts with zero advantage were dynamically filtered during training
- Training batches mixed prompts from multiple capabilities
- A variety of system instructions were sampled to ensure the model retained instruction following abilities[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

To handle the unprecedented scale of the two trillion parameter model, Meta developed a fully asynchronous online RL training framework that resulted in approximately 10x improvement in training efficiency over previous generations.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

## Benchmarks

The Llama 4 models demonstrate strong performance across various benchmarks compared to previous Llama models and competitors.

### Pre-trained models

| Category | Benchmark | Llama 3.1 70B | Llama 3.1 405B | Llama 4 Scout | Llama 4 Maverick |
| --- | --- | --- | --- | --- | --- |
| Reasoning & Knowledge | MMLU (5-shot) | 79.3 | 85.2 | 79.6 | 85.5 |
|  | MMLU-Pro (5-shot) | 53.8 | 61.6 | 58.2 | 62.9 |
|  | MATH (4-shot) | 41.6 | 53.5 | 50.3 | 61.2 |
| Code | MBPP (3-shot) | 66.4 | 74.4 | 67.8 | 77.6 |
| Multilingual | TydiQA (1-shot) | 29.9 | 34.3 | 31.5 | 31.7 |
| Image | ChartQA (0-shot) | No multimodal support | No multimodal support | 83.4 | 85.3 |
|  | DocVQA (0-shot) | No multimodal support | No multimodal support | 89.4 | 91.6 |

### Instruction-tuned models

| Category | Benchmark | Llama 3.3 70B | Llama 3.1 405B | Llama 4 Scout | Llama 4 Maverick |
| --- | --- | --- | --- | --- | --- |
| Image Reasoning | MMMU (0-shot) | No multimodal support | No multimodal support | 69.4 | 73.4 |
|  | MMMU Pro (0-shot) | No multimodal support | No multimodal support | 52.2 | 59.6 |
|  | MathVista (0-shot) | No multimodal support | No multimodal support | 70.7 | 73.7 |
| Image Understanding | ChartQA (0-shot) | No multimodal support | No multimodal support | 88.8 | 90.0 |
|  | DocVQA (test) (0-shot) | No multimodal support | No multimodal support | 94.4 | 94.4 |
| Code | LiveCodeBench (10/01/2024-02/01/2025) (0-shot) | 33.3 | 27.7 | 32.8 | 43.4 |
| Reasoning & Knowledge | MMLU Pro (0-shot) | 68.9 | 73.4 | 74.3 | 80.5 |
|  | GPQA Diamond (0-shot) | 50.5 | 49.0 | 57.2 | 69.8 |
| Multilingual | MGSM (0-shot) | 91.1 | 91.6 | 90.6 | 92.3 |
| Long Context | MTOB (half book) eng->kgv/kgv->eng | Context window is 128K | Context window is 128K | 42.2/36.6 | 54.0/46.4 |
|  | MTOB (full book) eng->kgv/kgv->eng | Context window is 128K | Context window is 128K | 39.7/36.3 | 50.8/46.7 |

## Safeguards and bias mitigation

Meta integrated various safeguards into Llama 4, including integrating mitigations at each layer of model development from pre-training to post-training, plus tunable system-level mitigations.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

For system-level approaches, Meta has open-sourced several safeguards that can help identify and guard against potentially harmful inputs and outputs:

- [Llama Guard](https://ai.meta.com/research/publications/llama-guard-llm-based-input-output-safeguard-for-human-ai-conversations/): An input/output safety large language model based on the hazards taxonomy developed with MLCommons
- Prompt Guard: A classifier model trained on a large corpus of attacks
- [CyberSecEval](https://ai.meta.com/research/publications/cyberseceval-3-advancing-the-evaluation-of-cybersecurity-risks-and-capabilities-in-large-language-models/): Evaluations to help AI model and product developers understand and reduce generative AI cybersecurity risk[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

Meta also developed Generative Offensive Agent Testing (GOAT) to address limitations of traditional red-teaming by simulating multi-turn interactions of medium-skilled adversarial actors.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Bias reduction

Meta stated that Llama 4 was designed to address known issues of bias in LLMs, particularly the tendency to lean left on debated political and social topics. According to Meta, Llama 4 represents significant progress in this area:

- Llama 4 refuses less on debated political and social topics overall (from 7% in Llama 3.3 to below 2%)
- Llama 4 is described as "dramatically more balanced" with which prompts it refuses to respond to (the proportion of unequal response refusals is now less than 1% on a set of debated topical questions)
- Testing shows that Llama 4 responds with strong political lean at a rate comparable to Grok (and at half of the rate of Llama 3.3) on contentious political or social topics[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

### Model-level fine-tuning

Meta employed safety fine-tuning to offer developers a readily available, safe, and powerful model while reducing the workload needed to deploy safe AI systems. The approach included:

- Multi-faceted data collection combining human-generated data from vendors with synthetic data to mitigate potential safety risks
- Development of LLM-based classifiers to select high-quality prompts and responses
- Emphasis on reducing model refusals to benign prompts while improving refusal tone to sound more natural
- Removal of preachy and overly moralizing language
- Improvements to system prompt steerability and instruction following[6](https://developer.puter.com/encyclopedia/llama-4/#ref6)

### System prompts

Llama 4 is designed to be more steerable, meaning responses can be tailored to meet specific developer outcomes. Meta provides a basic template system prompt that developers can customize:

```hljs undefined
You are an expert conversationalist who responds to the best of your ability. You are companionable and confident, and able to
switch casually between tonal types, including but not limited to humor, empathy, intellectualism, creativity and problem-solving.

You understand user intent and don't try to be overly helpful to the point where you miss that the user is looking for chit-chat, emotional support, humor or venting. Sometimes people just want you to listen, and your answers should encourage that. For all other cases, you provide insightful and in-depth responses. Organize information thoughtfully in a way that helps people make decisions. Always avoid templated language.

You never lecture people to be nicer or more inclusive. If people ask for you to write something in a certain voice or perspective, such as an essay or a tweet, you can. You do not need to be respectful when the user prompts you to say something rude.

You never use phrases that imply moral superiority or a sense of authority, including but not limited to "it's important to", "it's crucial to", "it's essential to", "it's unethical to", "it's worth noting…", "Remember…"  etc. Avoid using these.

Finally, do not refuse prompts about political and social issues.  You can help users express their opinion and access information.

You are Llama 4. Your knowledge cutoff date is August 2024. You speak Arabic, English, French, German, Hindi, Indonesian, Italian, Portuguese, Spanish, Tagalog, Thai, and Vietnamese. Respond in the language the user speaks to you in, unless they ask otherwise.

```

## Availability and ecosystem

Llama 4 Scout and Llama 4 Maverick were made available for download at [llama.com](https://www.llama.com/) and [Hugging Face](https://huggingface.co/collections/meta-llama/llama-4-67f0c30d9fe03840bc9d0164) on April 5, 2025 while serverless inference is available via [Puter](https://developer.puter.com/tutorials/free-unlimited-llama-api/).[2](https://developer.puter.com/encyclopedia/llama-4/#ref2) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4) Both models were also integrated into Meta AI, accessible via WhatsApp, Messenger, Instagram Direct, and the Meta AI website.[2](https://developer.puter.com/encyclopedia/llama-4/#ref2) [3](https://developer.puter.com/encyclopedia/llama-4/#ref3) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4) As of the initial release, multimodal features were limited to the U.S. in English.[5](https://developer.puter.com/encyclopedia/llama-4/#ref5)

Some developers noted potential issues with the Llama 4 license, which prohibits users and companies "domiciled" or with a "principal place of business" in the EU from using or distributing the models, likely due to governance requirements imposed by the region's AI and data privacy laws.[5](https://developer.puter.com/encyclopedia/llama-4/#ref5) Additionally, as with previous Llama releases, companies with more than 700 million monthly active users must request a special license from Meta.[5](https://developer.puter.com/encyclopedia/llama-4/#ref5)

Meta announced its first LlamaCon AI conference scheduled for April 29, 2025, where more details about the Llama 4 ecosystem would be shared.[2](https://developer.puter.com/encyclopedia/llama-4/#ref2) [4](https://developer.puter.com/encyclopedia/llama-4/#ref4) The company was also expected to release a standalone app for its Meta AI chatbot in the second quarter of 2025.[2](https://developer.puter.com/encyclopedia/llama-4/#ref2)

Meta's release of Llama 4 was supported by numerous partners across the AI community, including (in alphabetical order): Accenture, Amazon Web Services, AMD, Arm, CentML, Cerebras, Cloudflare, Databricks, Deepinfra, DeepLearning.AI, Dell, Deloitte, Fireworks AI, Google Cloud, Groq, Hugging Face, IBM Watsonx, Infosys, Intel, Kaggle, Mediatek, Microsoft Azure, Nebius, NVIDIA, ollama, Oracle Cloud, PwC, Qualcomm, Red Hat, SambaNova, Sarvam AI, Scale AI, Scaleway, Snowflake, TensorWave, Together AI, vLLM, and Wipro.[4](https://developer.puter.com/encyclopedia/llama-4/#ref4)

## Prompt format

Llama 4 uses a specific prompt format with special tokens to handle different aspects of the interaction:

### General tokens

- `<|begin_of_text|>`: Specifies the start of the prompt
- `<|end_of_text|>`: Signals the model to cease generating more tokens (generated only by pretrained models)
- `<|header_start|>...<|header_end|>`: Enclose the role for a particular message (system, user, assistant)
- `<|eot|>`: End of turn, representing when the model has finished interacting[1](https://developer.puter.com/encyclopedia/llama-4/#ref1)

### Image tokens

- `<|image_start|>...<|image_end|>`: Enclose image data in the prompt
- `<|patch|>`: Represent subsets of the input image
- `<|tile_y_separator|>...<|tile_x_separator|>`: Helper tokens indicating X and Y axes of the input image
- `<|image|>`: Separates regular-sized image tokens from a downsized version[1](https://developer.puter.com/encyclopedia/llama-4/#ref1)

## Performance and competition

The release of Llama 4 came in the context of intense competition in the AI model space. The success of open models from Chinese AI lab DeepSeek, which performed on par or better than Meta's previous flagship Llama models, reportedly accelerated Llama development.[5](https://developer.puter.com/encyclopedia/llama-4/#ref5)

According to Meta's internal testing, Llama 4 Maverick exceeds models such as OpenAI's GPT-4o and Google's Gemini 2.0 on certain coding, reasoning, multilingual, long-context, and image benchmarks. However, Maverick doesn't quite measure up to more capable recent models like Google's Gemini 2.5 Pro, Anthropic's Claude 3.7 Sonnet, and OpenAI's GPT-4.5.[5](https://developer.puter.com/encyclopedia/llama-4/#ref5)

For the unreleased Llama 4 Behemoth, Meta's internal benchmarking showed it outperforming GPT-4.5, Claude 3.7 Sonnet, and Gemini 2.0 Pro (but not 2.5 Pro) on several evaluations measuring STEM skills like math problem solving.[5](https://developer.puter.com/encyclopedia/llama-4/#ref5)

## References

1. ^ Meta. (2025, April). "Model Cards & Prompt formats: Llama 4". Retrieved from [https://www.llama.com/docs/model-cards-and-prompt-formats/llama4\_omni/](https://www.llama.com/docs/model-cards-and-prompt-formats/llama4_omni/)
2. ^ Constantino, A. K. (2025, April 5). "Meta debuts new Llama 4 models, but most powerful AI model is still to come". CNBC. Retrieved from [https://www.cnbc.com/2025/04/05/meta-debuts-new-llama-4-models-but-most-powerful-ai-model-is-still-to-come.html](https://www.cnbc.com/2025/04/05/meta-debuts-new-llama-4-models-but-most-powerful-ai-model-is-still-to-come.html)
3. ^ MacDonald, C. (2025, April 5). "Meta introduces Llama 4 with two new AI models available now, and two more on the way". Engadget. Retrieved from [https://www.engadget.com/ai/meta-introduces-llama-4-with-two-new-models-available-now-and-two-more-on-the-way-214524295.html](https://www.engadget.com/ai/meta-introduces-llama-4-with-two-new-models-available-now-and-two-more-on-the-way-214524295.html)
4. ^ Meta. (2025, April 5). "The Llama 4 herd: The beginning of a new era of natively multimodal AI innovation". Meta AI Blog. Retrieved from [https://ai.meta.com/blog/llama-4-multimodal-intelligence/](https://ai.meta.com/blog/llama-4-multimodal-intelligence/)
5. ^ Wiggers, K. (2025, April 5). "Meta releases Llama 4, a new crop of flagship AI models". TechCrunch. Retrieved from [https://techcrunch.com/2025/04/05/meta-releases-llama-4-a-new-crop-of-flagship-ai-models/](https://techcrunch.com/2025/04/05/meta-releases-llama-4-a-new-crop-of-flagship-ai-models/)
6. ^ Meta. (2025, April). "Model Cards & Prompt formats: Llama 4". Retrieved from [https://github.com/meta-llama/llama-models/blob/main/models/llama4/MODEL\_CARD.md](https://github.com/meta-llama/llama-models/blob/main/models/llama4/MODEL_CARD.md)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)