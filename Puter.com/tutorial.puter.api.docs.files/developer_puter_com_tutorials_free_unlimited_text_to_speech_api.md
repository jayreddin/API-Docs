## [Tutorials](https://developer.puter.com/tutorials/)

# Free, Unlimited Text-to-Speech API with Puter.js

This tutorial will show you how to use Puter.js to access text-to-speech capabilities similar to Amazon Polly for free, without any API keys or usage restrictions. Using Puter.js, you can convert text to speech for a wide range of applications without worrying about usage limits or costs.

## Getting Started

Using puter.js does not require any API keys or sign-ups. You can start using Puter.js by including the following script tag in your HTML file, either in the `<head>` or `<body>` section:

```hljs xml
<script src="https://js.puter.com/v2/"></script>

```

That's all you need to start using Puter.js for free text-to-speech conversion! No API keys or sign-ups required.

## Example 1Use Puter.js for text-to-speech conversion

To convert text to speech using Puter.js, use the [`puter.ai.txt2speech()`](https://docs.puter.com/AI/chat/) function:

```javascript hljs
puter.ai.txt2speech("Hello, world! This is text-to-speech using Puter.js.")
    .then((audio) => {
        audio.play();
    });

```

Here's a complete example with a text input and a button to trigger the text-to-speech conversion:

```html hljs language-xml
<html>
<body>
    <textarea id="text-input" rows="4" cols="50">Hello, world! This is text-to-speech using Puter.js.</textarea>
    <br>
    <button id="speak-button">Speak</button>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        document.getElementById('speak-button').addEventListener('click', () => {
            const text = document.getElementById('text-input').value;
            puter.ai.txt2speech(text)
                .then((audio) => {
                    audio.play();
                })
                .catch((error) => {
                    console.error('Error:', error);
                });
        });
    </script>
</body>
</html>

```

## Example 2Customize the voice

Puter.js supports multiple languages and voices. You can specify the language when calling the [`txt2speech`](https://docs.puter.com/AI/txt2speech/) function:

```javascript hljs
puter.ai.txt2speech("Bonjour, le monde!", "fr-FR")
    .then((audio) => {
        audio.play();
    });

```

Here's an example that allows users to select different languages:

```html hljs language-xml
<html>
<body>
    <textarea id="text-input" rows="4" cols="50">Hello, world!</textarea>
    <br>
    <select id="language-select">
        <option value="en-US">English (US)</option>
        <option value="fr-FR">French</option>
        <option value="de-DE">German</option>
        <option value="es-ES">Spanish</option>
        <option value="it-IT">Italian</option>
    </select>
    <button id="speak-button">Speak</button>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        document.getElementById('speak-button').addEventListener('click', () => {
            const text = document.getElementById('text-input').value;
            const language = document.getElementById('language-select').value;
            puter.ai.txt2speech(text, language)
                .then((audio) => {
                    audio.play();
                })
                .catch((error) => {
                    console.error('Error:', error);
                });
        });
    </script>
</body>
</html>

```

That's it! You now have a free alternative to the Amazon Polly API using Puter.js. This allows you to add text-to-speech capabilities to your web applications without worrying about API keys or usage limits.

## Additional Features

Puter.js offers many more features, including cloud storage, hosting static websites, and AI-powered image generation. Explore the [Puter.js documentation](https://docs.puter.com/) to discover all the possibilities and start building powerful, serverless web applications with ease!

## Related

- [Free, Unlimited Claude API](https://developer.puter.com/tutorials/free-unlimited-claude-35-sonnet-api)
- [Free, Unlimited OpenAI API](https://developer.puter.com/tutorials/free-unlimited-openai-api)
- [Free, Unlimited OCR API](https://developer.puter.com/tutorials/free-unlimited-ocr-api)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)