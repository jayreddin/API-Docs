## [Tutorials](https://developer.puter.com/tutorials/)

# Free, Unlimited o1-mini API

This tutorial will show you how to use Puter.js to access OpenAI's o1-mini capabilities for free, without any API keys or usage restrictions. Using Puter.js, you can leverage o1-mini's impressive reasoning abilities for various tasks from problem-solving to content generation, all without worrying about usage limits or costs.

Puter is the pioneer of the ["User Pays" model](https://docs.puter.com/user-pays-model/), which allows developers to incorporate AI capabilities into their applications while users cover their own usage costs. This model enables developers to access advanced AI capabilities for free, without any API keys or server-side setup.

## Getting Started

Puter.js works without any API keys or sign-ups. To start using Puter.js, include the following script tag in your HTML file, either in the `<head>` or `<body>` section:

```hljs xml
<script src="https://js.puter.com/v2/"></script>

```

You're now ready to use Puter.js for free access to o1-mini capabilities. No API keys or sign-ups are required.

## Example 1Basic Reasoning with o1-mini

Let's start with a simple example showing how to use o1-mini's reasoning capabilities:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        puter.ai.chat("Solve this logic puzzle: A man has to cross a river with a wolf, a goat, and a cabbage. The boat can only hold the man and one other item. If left unattended, the wolf will eat the goat, and the goat will eat the cabbage. How can he get all three across safely?", {model: 'openrouter:openai/o1-mini'})
            .then(response => {
                document.body.innerHTML = response.message.content;
            });
    </script>
</body>
</html>

```

This example demonstrates o1-mini's ability to solve complex logic problems through careful reasoning. The model will break down the steps needed to safely transport all items across the river.

## Example 2Stream Responses for Math Problems

For mathematical reasoning, it's often helpful to see the model's step-by-step thinking. Here's how to use streaming to display the reasoning process in real-time:

```html hljs language-xml
<html>
<body>
    <div id="output"></div>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        async function solveWithStreaming() {
            const outputDiv = document.getElementById('output');
            outputDiv.innerHTML = "Solving problem...<br>";

            const response = await puter.ai.chat(
                "Calculate the indefinite integral of x²sin(x). Show your work step by step.",
                {model: 'openrouter:openai/o1-mini', stream: true}
            );

            outputDiv.innerHTML = "";
            for await (const part of response) {
                if (part?.text) {
                    outputDiv.innerHTML += part.text;
                }
            }
        }

        solveWithStreaming();
    </script>
</body>
</html>

```

This example showcases o1-mini's mathematical reasoning abilities by tackling a calculus problem. Using streaming provides a better user experience for complex problems where seeing the step-by-step reasoning is valuable.

## Example 3Interactive Learning Assistant

Here's how to create a simple interactive learning assistant that provides explanations on various topics:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 20px auto; font-family: Arial, sans-serif;">
        <h1>o1-mini Learning Assistant</h1>
        <div>
            <select id="topic-select">
                <option value="physics">Physics</option>
                <option value="chemistry">Chemistry</option>
                <option value="biology">Biology</option>
                <option value="math">Mathematics</option>
                <option value="computer-science">Computer Science</option>
            </select>
            <input type="text" id="question-input" placeholder="Enter your question here..." style="width: 60%; padding: 8px; margin: 10px 0;">
            <button onclick="askQuestion()" style="padding: 8px 16px;">Ask</button>
        </div>
        <div id="loading" style="display: none;">Thinking...</div>
        <div id="response-container" style="margin-top: 20px; padding: 15px; border: 1px solid #ddd; border-radius: 5px; display: none;">
            <h3 id="question-display"></h3>
            <div id="answer-display"></div>
        </div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        async function askQuestion() {
            const topic = document.getElementById('topic-select').value;
            const question = document.getElementById('question-input').value;

            if (!question) return;

            // Show loading indicator
            document.getElementById('loading').style.display = 'block';
            document.getElementById('response-container').style.display = 'none';

            // Construct the prompt
            const prompt = `I'm studying ${topic} and have the following question: ${question}.
            Please provide a clear, educational explanation appropriate for a student.`;

            try {
                const response = await puter.ai.chat(prompt, {model: 'openrouter:openai/o1-mini'});

                // Display the response
                document.getElementById('question-display').textContent = question;
                document.getElementById('answer-display').innerHTML = response.message.content.replace(/\n/g, '<br>');
                document.getElementById('response-container').style.display = 'block';
            } catch (error) {
                console.error('Error:', error);
                document.getElementById('answer-display').innerHTML = 'Sorry, there was an error processing your request.';
                document.getElementById('response-container').style.display = 'block';
            } finally {
                document.getElementById('loading').style.display = 'none';
            }
        }

        // Allow sending question with Enter key
        document.getElementById('question-input').addEventListener('keypress', (e) => {
            if (e.key === 'Enter') askQuestion();
        });
    </script>
</body>
</html>

```

This example creates an interactive learning assistant that leverages o1-mini's knowledge across various academic subjects. Students can select a topic and ask specific questions to receive explanations tailored to their educational needs.

## Example 4Decision Tree Generator

Here's an example of using o1-mini to create a decision tree for complex decision-making scenarios:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 20px auto; font-family: Arial, sans-serif;">
        <h1>Decision Tree Generator</h1>
        <div>
            <textarea id="scenario-input" rows="4" style="width: 100%; margin: 10px 0;" placeholder="Describe a decision-making scenario (e.g., 'Should I buy a house or continue renting?')"></textarea>
            <button onclick="generateTree()" style="padding: 8px 16px;">Generate Decision Tree</button>
        </div>
        <div id="loading" style="display: none; margin-top: 20px;">Generating decision tree...</div>
        <div id="result" style="margin-top: 20px; white-space: pre-wrap;"></div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        async function generateTree() {
            const scenario = document.getElementById('scenario-input').value;
            if (!scenario) return;

            const resultDiv = document.getElementById('result');
            const loadingDiv = document.getElementById('loading');

            loadingDiv.style.display = 'block';
            resultDiv.innerHTML = '';

            const prompt = `
Generate a decision tree for the following scenario: "${scenario}"

Format the decision tree with the following:
1. State the core decision as the main node
2. Identify 2-3 primary branches (options)
3. For each option, list:
   - Key considerations
   - Potential outcomes
   - Secondary decisions that might arise
4. Include a brief analysis of the trade-offs for each major branch

Present the decision tree in a structured, easy-to-follow format.`;

            try {
                const response = await puter.ai.chat(prompt, {
                    model: 'openrouter:openai/o1-mini',
                    stream: true
                });

                for await (const part of response) {
                    if (part?.text) {
                        resultDiv.innerHTML += part.text;
                    }
                }
            } catch (error) {
                resultDiv.innerHTML = 'Error generating decision tree: ' + error.message;
            } finally {
                loadingDiv.style.display = 'none';
            }
        }
    </script>
</body>
</html>

```

This example showcases o1-mini's ability to analyze complex scenarios and create structured decision frameworks. The generator helps users break down difficult decisions by identifying key options, considerations, and potential outcomes.

## Best Practices

When using o1-mini through Puter.js, keep these best practices in mind:

1. **Be specific with prompts**: o1-mini performs best when given clear, specific instructions
2. **Use streaming for complex reasoning**: When the model needs to work through multi-step problems, streaming provides a better user experience
3. **Structure your prompts**: For complex tasks, structure your prompts with clear sections or numbered points
4. **Request step-by-step reasoning**: When solving problems, explicitly ask for step-by-step explanations to leverage o1-mini's reasoning capabilities
5. **Handle errors gracefully**: Always implement error handling to provide feedback if the API request fails

That's it! You now have free, unlimited access to OpenAI's o1-mini model using Puter.js. This allows you to leverage powerful reasoning capabilities for your applications without worrying about API keys or usage limits.

## Related

- [Free, Unlimited OpenAI API](https://developer.puter.com/tutorials/free-unlimited-openai-api)
- [Free, Unlimited o3-mini API](https://developer.puter.com/tutorials/free-unlimited-o3-mini-api)
- [Free, Unlimited Claude API](https://developer.puter.com/tutorials/free-unlimited-claude-35-sonnet-api)
- [Free, Unlimited Gemini API](https://developer.puter.com/tutorials/free-gemini-api)
- [Serverless AI: Forever Free for Developers](https://developer.puter.com/tutorials/serverless-ai-forever-free-for-developers)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)