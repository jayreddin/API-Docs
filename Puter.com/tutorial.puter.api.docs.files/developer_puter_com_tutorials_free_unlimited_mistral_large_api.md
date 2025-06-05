## [Tutorials](https://developer.puter.com/tutorials/)

# Free, Unlimited Mistral Large API

Mistral Large is a powerful large language model known for its strong performance across a wide range of tasks. In this tutorial, we'll show you how to use Mistral Large through Puter.js, completely free and without any API keys.

Puter is the pioneer of the ["User Pays" model](https://docs.puter.com/user-pays-model/), which allows developers to incorporate AI capabilities into their applications while each user will cover their own usage costs. This model enables developers to access advanced AI capabilities for free, without any API keys or server-side setup.

## Prerequisites

None! You just need to include the Puter.js library in your HTML file:

```html hljs language-xml
<script src="https://js.puter.com/v2/"></script>

```

## Using Mistral Large

To use Mistral Large, you'll use the [`puter.ai.chat()`](https://docs.puter.com/AI/chat/) function with the `model` parameter set to `'mistral-large-latest'`. Here's a basic example:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        // Chat with Mistral Large
        puter.ai.chat(
            "What are the key differences between classical and quantum computing?",
            {model: 'mistral-large-latest'}
        ).then(response => {
            document.body.innerHTML = response.text;
        });
    </script>
</body>
</html>

```

## Streaming Responses

For a more interactive experience, you can stream the responses from Mistral Large as they're generated:

```html hljs language-xml
<html>
<body>
    <div id="response"></div>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        (async () => {
            const response = await puter.ai.chat(
                "Explain the concept of quantum entanglement.",
                {
                    model: 'mistral-large-latest',
                    stream: true
                }
            );

            const responseDiv = document.getElementById('response');
            for await (const part of response) {
                responseDiv.innerHTML += part.text;
            }
        })();
    </script>
</body>
</html>

```

## Building a Simple Chat Interface

Here's how to create a simple chat interface using Mistral Large:

```html hljs language-xml
<html>
<body>
    <div id="chat-container" style="max-width: 600px; margin: 20px auto;">
        <div id="messages" style="height: 400px; border: 1px solid #ccc; overflow-y: auto; padding: 10px; margin-bottom: 10px;"></div>
        <div style="display: flex; gap: 10px;">
            <input type="text" id="user-input" style="flex-grow: 1; padding: 5px;" placeholder="Type your message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        const messagesDiv = document.getElementById('messages');
        const userInput = document.getElementById('user-input');

        async function sendMessage() {
            const message = userInput.value;
            if (!message) return;

            // Add user message
            messagesDiv.innerHTML += `<p><strong>You:</strong> ${message}</p>`;
            userInput.value = '';
            messagesDiv.scrollTop = messagesDiv.scrollHeight;

            // Add AI response
            messagesDiv.innerHTML += `<p><strong>AI:</strong> <span id="ai-response"></span></p>`;
            const responseSpan = document.getElementById('ai-response');

            const response = await puter.ai.chat(message, {
                model: 'mistral-large-latest',
                stream: true
            });

            for await (const part of response) {
                responseSpan.innerHTML += part.text;
                messagesDiv.scrollTop = messagesDiv.scrollHeight;
            }
        }

        // Allow sending message with Enter key
        userInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') sendMessage();
        });
    </script>
</body>
</html>

```

Mistral Large through Puter.js provides a powerful, free, and easy-to-use AI solution for your web applications. With features like streaming responses and function calling, you can create sophisticated AI-powered applications without worrying about API keys or usage limits.

Remember that each user of your application will use their own Puter account, so you don't have to worry about costs or rate limits - it's all handled automatically!

## Related Resources

- [Getting Started with Puter.js](https://developer.puter.com/tutorials/getting-started-with-puterjs)
- [Free, Unlimited OpenAI API](https://developer.puter.com/tutorials/free-unlimited-openai-api)
- [Free, Unlimited Claude API](https://developer.puter.com/tutorials/free-unlimited-claude-35-sonnet-api)
- [Free, Unlimited Codestral API](https://developer.puter.com/tutorials/free-unlimited-codestral-api)
- [Free, Unlimited Grok API](https://developer.puter.com/tutorials/free-unlimited-grok-api)
- [Serverless AI: Forever Free for Developers](https://developer.puter.com/tutorials/serverless-ai-forever-free-for-developers)

## External Links

- [Puter.js Documentation](https://docs.puter.com/)
- [Puter.js GitHub Repository](https://github.com/HeyPuter/puter)
- [Join our Discord Community](https://discord.com/invite/PQcx7Teh8u)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)