# Long Context

Gemini 2.0 Flash and Gemini 1.5 Flash come with a 1-million-token context window, and Gemini 1.5 Pro comes with a 2-million-token context window. Historically, large language models (LLMs) were significantly limited by the amount of text (or tokens) that could be passed to the model at one time. The Gemini 1.5 long context window, with near-perfect retrieval (>99%), unlocks many new use cases and developer paradigms.

## What is a context window?

The basic way you use the Gemini models is by passing information (context) to the model, which will subsequently generate a response. An analogy for the context window is short term memory. There is a limited amount of information that can be stored in someone's short term memory, and the same is true for generative models.

## Getting started with long context

Most generative models created in the last few years were only capable of processing 8,000 tokens at a time. Newer models pushed this further by accepting 32,000 tokens or 128,000 tokens. Gemini 1.5 is the first model capable of accepting 1 million tokens, and now 2 million tokens with Gemini 1.5 Pro.

In practice, 1 million tokens would look like:
- 50,000 lines of code (with the standard 80 characters per line)
- All the text messages you have sent in the last 5 years
- 8 average length English novels
- Transcripts of over 200 average length podcast episodes

## Long context use cases

### Long form text
Text-based use cases include:
- Summarizing large corpuses of text
- Question and answering
- Agentic workflows
- Many-shot in-context learning

### Long form video
Video-based use cases include:
- Video question and answering
- Video memory
- Video captioning
- Video recommendation systems
- Video customization
- Video content moderation
- Real-time video processing

### Long form audio
Audio-based use cases include:
- Real-time transcription and translation
- Podcast/video question and answering
- Meeting transcription and summarization
- Voice assistants

## Long context optimizations

The primary optimization when working with long context and the Gemini 1.5 models is to use context caching. Beyond the previous impossibility of processing lots of tokens in a single request, the other main constraint was the cost. Using context caching can significantly reduce costs while maintaining high performance.

## Long context limitations

While Gemini 1.5 models achieve high performance on single needle-in-a-haystack retrieval, performance can vary when looking for multiple specific pieces of information. There is an inherent tradeoff between retrieval accuracy and cost.

## FAQs

### Where is the best place to put my query in the context window?
In most cases, especially if the total context is long, put your query/question at the end of the prompt (after all the other context).

### Do I lose model performance when I add more tokens to a query?
Generally, avoid passing unnecessary tokens. However, the model is highly capable of extracting information from large token sets with up to 99% accuracy.

### How does Gemini 1.5 Pro perform on the standard needle-in-a-haystack test?
Gemini 1.5 Pro achieves 100% recall up to 530k tokens and >99.7% recall up to 1M tokens.

### How can I lower my cost with long-context queries?
Use context caching for reusing similar sets of tokens/context multiple times.

### How can I get access to the 2-million-token context window?
All developers now have access to the 2-million-token context window with Gemini 1.5 Pro.

### Does the context length affect the model latency?
Yes, longer queries generally have higher latency (time to first token).

### Do the long context capabilities differ between Gemini 1.5 Flash and Gemini 1.5 Pro?
Yes, Gemini 1.5 Pro is generally more performant on most long context use cases.