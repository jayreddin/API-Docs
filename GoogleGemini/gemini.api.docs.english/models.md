# Gemini models

## Model variants

The Gemini API offers different models that are optimized for specific use cases. Here's a brief overview of Gemini variants that are available:

| Model variant | Input(s) | Output | Optimized for |
| --- | --- | --- | --- |
| Gemini 2.5 Flash Preview 04-17 | Audio, images, videos, and text | Text | Adaptive thinking, cost efficiency |
| Gemini 2.5 Pro Preview | Audio, images, videos, and text | Text | Enhanced thinking and reasoning, multimodal understanding, advanced coding, and more |
| Gemini 2.0 Flash | Audio, images, videos, and text | Text, images (experimental), and audio (coming soon) | Next generation features, speed, thinking, realtime streaming, and multimodal generation |
| Gemini 2.0 Flash-Lite | Audio, images, videos, and text | Text | Cost efficiency and low latency |
| Gemini 1.5 Flash | Audio, images, videos, and text | Text | Fast and versatile performance across a diverse variety of tasks |
| Gemini 1.5 Flash-8B | Audio, images, videos, and text | Text | High volume and lower intelligence tasks |
| Gemini 1.5 Pro | Audio, images, videos, and text | Text | Complex reasoning tasks requiring more intelligence |
| Gemini Embedding | Text | Text embeddings | Measuring the relatedness of text strings |
| Imagen 3 | Text | Images | Most advanced image generation model |
| Veo 2 | Text, images | Video | High quality video generation |
| Gemini 2.0 Flash Live | Audio, video, and text | Text, audio | Low-latency bidirectional voice and video interactions |

## Detailed Model Information

### Gemini 2.5 Flash Preview 04-17
- Best model in terms of price-performance
- Input token limit: 1,048,576
- Output token limit: 65,536
- Capabilities: Code execution, Function calling, Search, Structured outputs, Thinking
- Latest update: April 2025
- Knowledge cutoff: January 2025

### Gemini 2.5 Pro Preview
- State-of-the-art thinking model
- Input token limit: 1,048,576
- Output token limit: 65,536
- Capabilities: Structured outputs, Caching, Function calling, Code execution, Search grounding, Thinking
- Latest update: March 2025
- Knowledge cutoff: January 2025

### Gemini 2.0 Flash
- Next-gen features and improved capabilities
- Input token limit: 1,048,576
- Output token limit: 8,192
- Capabilities: Structured outputs, Caching, Function calling, Code execution, Search, Image generation (experimental), Audio generation (coming soon), Live API, Thinking (experimental)
- Latest update: February 2025
- Knowledge cutoff: August 2024

[Additional models and details omitted for brevity]

## Model Version Name Patterns

Gemini models are available in either preview, stable, or experimental versions:

- **Latest stable:** `<model>-<generation>-<variation>` (e.g., `gemini-2.0-flash`)
- **Stable:** `<model>-<generation>-<variation>-<version>` (e.g., `gemini-2.0-flash-001`)
- **Preview:** `<model>-<generation>-<variation>-<version>` (e.g., `gemini-2.5-pro-preview-03-25`)
- **Experimental:** `<model>-<generation>-<variation>-<version>` (e.g., `gemini-2.0-pro-exp-02-05`)

## Supported Languages

Gemini models support 43 languages including:
- English (en)
- Chinese simplified and traditional (zh)
- French (fr)
- German (de)
- Japanese (ja)
- Spanish (es)
[And many more...]

*Note: A token is equivalent to about 4 characters for Gemini models. 100 tokens are about 60-80 English words.*