## [Tutorials](https://developer.puter.com/tutorials/)

# Free, Unlimited Grok API

Updated: April 10, 2025


Grok is xAI's latest large language model, known for its unique approach to problem-solving and witty responses. In this tutorial, we'll show you how to use Grok through Puter.js to create engaging and intelligent applications.

Puter is the pioneer of the ["User Pays" model](https://docs.puter.com/user-pays-model/), which allows developers to incorporate AI capabilities into their applications while each user will cover their own usage costs. This model enables developers to access advanced AI capabilities for free, without any API keys, usage costs, or server-side setup.

## Prerequisites

Just include the Puter.js library in your HTML file:

```html hljs language-xml
<script src="https://js.puter.com/v2/"></script>

```

## Example 1Use Grok 3 Beta

To use Grok 3 Beta, you'll use the [`puter.ai.chat()`](https://docs.puter.com/AI/chat/) function with the `model` parameter set to `x-ai/grok-3-beta`. Here's a basic example:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        // Chat with Grok 3 Beta
        puter.ai.chat(
            "Explain quantum computing in a witty and engaging way.",
            {model: 'x-ai/grok-3-beta'}
        ).then(response => {
            puter.print(response.message.content);
        });
    </script>
</body>
</html>

```

## Example 2Streaming responses

For a more interactive experience, you can stream the responses from Grok as they're generated:

```html hljs language-xml
<html>
<body>
    <div id="response"></div>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        (async () => {
            const response = await puter.ai.chat(
                "Tell me a funny story about artificial intelligence.",
                {
                    model: 'x-ai/grok-3-beta',
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

## Example 3Interactive Q&A interface

Here's how to create an engaging Q&A interface using Grok 3 Beta:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 20px auto; font-family: Arial, sans-serif;">
        <h1>Ask Grok Anything</h1>
        <div id="chat-container" style="margin: 20px 0;">
            <div id="messages" style="height: 400px; border: 1px solid #ccc; overflow-y: auto; padding: 20px; margin-bottom: 20px; border-radius: 8px;"></div>
            <div style="display: flex; gap: 10px;">
                <input type="text" id="user-input"
                    style="flex-grow: 1; padding: 10px; border: 1px solid #ccc; border-radius: 4px;"
                    placeholder="Ask me anything...">
                <button onclick="askQuestion()"
                    style="padding: 10px 20px; background: #0066cc; color: white; border: none; border-radius: 4px; cursor: pointer;">
                    Ask
                </button>
            </div>
        </div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        const messagesDiv = document.getElementById('messages');
        const userInput = document.getElementById('user-input');

        async function askQuestion() {
            const question = userInput.value;
            if (!question) return;

            // Add user question
            messagesDiv.innerHTML += `
                <div style="margin-bottom: 15px;">
                    <strong style="color: #0066cc;">You:</strong><br>
                    ${question}
                </div>
            `;
            userInput.value = '';
            messagesDiv.scrollTop = messagesDiv.scrollHeight;

            // Add Grok's response container
            const responseContainer = document.createElement('div');
            responseContainer.style.marginBottom = '15px';
            responseContainer.innerHTML = `
                <strong style="color: #009933;">Grok:</strong><br>
                <span></span>
            `;
            messagesDiv.appendChild(responseContainer);
            const responseSpan = responseContainer.querySelector('span');

            // Get streaming response from Grok
            const response = await puter.ai.chat(question, {
                model: 'x-ai/grok-3-beta',
                stream: true
            });

            for await (const part of response) {
                responseSpan.innerHTML += part.text;
                messagesDiv.scrollTop = messagesDiv.scrollHeight;
            }
        }

        // Allow sending message with Enter key
        userInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') askQuestion();
        });

        // Add initial greeting
        window.onload = () => {
            messagesDiv.innerHTML = `
                <div style="margin-bottom: 15px;">
                    <strong style="color: #009933;">Grok:</strong><br>
                    Hi there! I'm Grok, your witty AI assistant. I'm here to help you with anything you'd like to know about. What's on your mind?
                </div>
            `;
        };
    </script>
</body>
</html>

```

## Example 4Multi-turn conversations

Grok excels at maintaining context in conversations. Here's how to implement a context-aware chat:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        // Keep track of conversation history
        let conversationHistory = [];

        async function continueConversation(userMessage) {
            // Add user message to history
            conversationHistory.push({
                role: "user",
                content: userMessage
            });

            // Get response from Grok
            const response = await puter.ai.chat(conversationHistory, {
                model: 'x-ai/grok-3-beta'
            });

            // Add Grok's response to history
            conversationHistory.push({
                role: "assistant",
                content: response.message.content
            });

            return response.message.content;
        }

        // Example usage
        async function demonstrateConversation() {
            let response;

            response = await continueConversation("What's the most interesting thing about space?");
            document.body.innerHTML += `<p><strong>You:</strong> What's the most interesting thing about space?</p>`;
            document.body.innerHTML += `<p><strong>Grok:</strong> ${response}</p>`;

            response = await continueConversation("Tell me more about that!");
            document.body.innerHTML += `<p><strong>You:</strong> Tell me more about that!</p>`;
            document.body.innerHTML += `<p><strong>Grok:</strong> ${response}</p>`;
        }

        demonstrateConversation();
    </script>
</body>
</html>

```

## Example 5Using Grok for creative writing

Grok is particularly good at creative and engaging writing. Here's an example of using it for story generation:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 20px auto; font-family: Arial, sans-serif;">
        <h1>Story Generator</h1>
        <div style="margin: 20px 0;">
            <h3>Story Parameters</h3>
            <input type="text" id="genre" placeholder="Genre (e.g., sci-fi, fantasy)" style="width: 100%; margin-bottom: 10px; padding: 5px;">
            <input type="text" id="theme" placeholder="Theme (e.g., friendship, adventure)" style="width: 100%; margin-bottom: 10px; padding: 5px;">
            <input type="text" id="setting" placeholder="Setting (e.g., space station, medieval castle)" style="width: 100%; margin-bottom: 10px; padding: 5px;">
            <button onclick="generateStory()" style="padding: 10px 20px;">Generate Story</button>
        </div>
        <div id="story" style="white-space: pre-wrap; line-height: 1.6;"></div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        async function generateStory() {
            const genre = document.getElementById('genre').value || 'sci-fi';
            const theme = document.getElementById('theme').value || 'adventure';
            const setting = document.getElementById('setting').value || 'space station';

            const prompt = `
Write a short story with the following parameters:
- Genre: ${genre}
- Theme: ${theme}
- Setting: ${setting}

Make it engaging, witty, and memorable. Include some clever dialogue and unexpected twists.`;

            const storyDiv = document.getElementById('story');
            storyDiv.innerHTML = 'Generating your story...';

            const response = await puter.ai.chat(prompt, {
                model: 'x-ai/grok-3-beta',
                stream: true
            });

            storyDiv.innerHTML = '';
            for await (const part of response) {
                storyDiv.innerHTML += part.text;
            }
        }
    </script>
</body>
</html>

```

Grok 3 Beta through Puter.js provides a unique and engaging AI experience, combining technical capability with wit and creativity. Whether you're building a chatbot, a creative writing tool, or any other AI-powered application, Grok can help make it more engaging and fun for users.

## Related Resources

- [Getting Started with Puter.js](https://developer.puter.com/tutorials/getting-started-with-puterjs)
- [Free, Unlimited OpenAI API](https://developer.puter.com/tutorials/free-unlimited-openai-api)
- [Free, Unlimited Claude API](https://developer.puter.com/tutorials/free-unlimited-claude-35-sonnet-api)
- [Free, Unlimited Llama API](https://developer.puter.com/tutorials/free-unlimited-llama-api)
- [Free, Unlimited Mistral Large API](https://developer.puter.com/tutorials/free-unlimited-mistral-large-api)
- [Free, Unlimited Text-to-Speech API](https://developer.puter.com/tutorials/free-unlimited-text-to-speech-api)
- [Serverless AI: Forever Free for Developers](https://developer.puter.com/tutorials/serverless-ai-forever-free-for-developers)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)