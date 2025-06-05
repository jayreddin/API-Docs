## [Tutorials](https://developer.puter.com/tutorials/)

# Free, Unlimited Claude API

Updated: April 8, 2025


This tutorial will show you how to use Puter.js to access Claude's advanced AI capabilities (both [Claude 3.7 Sonnet](https://developer.puter.com/encyclopedia/claude-3-7-sonnet/) and Claude 3.5 Sonnet) for free, without any API keys or usage restrictions. Using Puter.js, you can generate text with Claude for a wide range of tasks, from creative writing to code generation and more without worrying about usage limits or costs.

Puter is the pioneer of the ["User Pays" model](https://docs.puter.com/user-pays-model/), which allows developers to incorporate AI capabilities into their applications while users cover their own usage costs. This model enables developers to access advanced AI capabilities for free, without any API keys or server-side setup.

## Getting Started

Puter.js works without any API keys or sign-ups. To start using Puter.js, include the following script tag in your HTML file, either in the `<head>` or `<body>` section:

```html hljs language-xml
<script src="https://js.puter.com/v2/"></script>

```

You're now ready to use Puter.js for free access to Claude capabilities. No API keys or sign-ups are required.

## Example 1Basic Text Generation with Claude 3.7 Sonnet

To generate text using Claude, use the [`puter.ai.chat()`](https://docs.puter.com/AI/chat/) function with your preferred model. Here's a full code example using Claude 3.7 Sonnet:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        puter.ai.chat("Explain quantum computing in simple terms", {model: 'claude-3-7-sonnet'})
            .then(response => {
                puter.print(response.message.content[0].text);
            });
    </script>
</body>
</html>

```

## Example 2Streaming Responses for Longer Queries

For longer responses, use streaming to get results in real-time:

```javascript hljs
async function streamClaudeResponse(model = 'claude-3-7-sonnet') {
    const response = await puter.ai.chat(
        "Write a detailed essay on the impact of artificial intelligence on society",
        {model: model, stream: true}
    );

    for await (const part of response) {
        puter.print(part?.text);
    }
}

// Use Claude 3.7 Sonnet (default)
streamClaudeResponse();

// Or specify Claude 3.5 Sonnet
// streamClaudeResponse('claude-3-5-sonnet');

```

Here's the full code example with streaming:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        (async () => {
            const response = await puter.ai.chat(
                "Write a detailed essay on the impact of artificial intelligence on society",
                {model: 'claude-3-7-sonnet', stream: true}
            );

            for await (const part of response) {
                puter.print(part?.text);
            }
        })();
    </script>
</body>
</html>

```

## Example 3Using different Claude models

You can specify different Claude models using the `model` parameter, for example `claude-3-5-sonnet` or `claude-3-7-sonnet`:

```javascript hljs
// Using claude-3-5-sonnet model
puter.ai.chat(
    "Write a short poem about coding",
    { model: "claude-3-5-sonnet" }
).then(response => {
    puter.print(response);
});

// Using claude-3-7-sonnet model
puter.ai.chat(
    "Write a short poem about coding",
    { model: "claude-3-7-sonnet" }
).then(response => {
    puter.print(response);
});

```

Full code example:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        // Using claude-3-5-sonnet model
        puter.ai.chat(
            "Write a short poem about coding",
            { model: "claude-3-5-sonnet" }
        ).then(response => {
            puter.print("<h2>Using claude-3-5-sonnet model</h2>");
            puter.print(response);
        });

        // Using claude-3-7-sonnet model
        puter.ai.chat(
            "Write a short poem about coding",
            { model: "claude-3-7-sonnet" }
        ).then(response => {
            puter.print("<h2>Using claude-3-7-sonnet model</h2>");
            puter.print(response);
        });
    </script>
</body>
</html>

```

## Choosing Between Claude 3.5 Sonnet and Claude 3.7 Sonnet

- **Claude 3.5 Sonnet**: A good general-purpose model for most applications.
- **Claude 3.7 Sonnet**: The more advanced model, with better performance for complex reasoning tasks, agentic coding, and detailed content generation.

Both models are available without usage limits through Puter.js, so you can select the one that best fits your specific needs.

That's it! You now have free, unlimited access to Claude capabilities using Puter.js. This allows you to leverage Claude's advanced language understanding and generation abilities without worrying about API keys or usage limits.

## Related

- [Free, Unlimited OpenAI API](https://developer.puter.com/tutorials/free-unlimited-openai-api)
- [Free, Unlimited DeepSeek API](https://developer.puter.com/tutorials/free-unlimited-deepseek-api)
- [Free, Unlimited Gemini API](https://developer.puter.com/tutorials/free-gemini-api)
- [Free, Unlimited Llama API](https://developer.puter.com/tutorials/free-unlimited-llama-api)
- [Free, Unlimited OpenRouter API](https://developer.puter.com/tutorials/free-unlimited-openrouter-api)
- [Free, Unlimited Text-to-Speech API](https://developer.puter.com/tutorials/free-unlimited-text-to-speech-api)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)