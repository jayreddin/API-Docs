## [Tutorials](https://developer.puter.com/tutorials/)

# Free, Unlimited o3-mini API

This tutorial will show you how to use Puter.js to access OpenAI's o3-mini capabilities for free, without any API keys or usage restrictions. Using Puter.js, you can leverage o3-mini's impressive efficiency and capabilities for various tasks from content generation to complex problem solving, all without worrying about usage limits or costs.

Puter is the pioneer of the ["User Pays" model](https://docs.puter.com/user-pays-model/), which allows developers to incorporate AI capabilities into their applications while users cover their own usage costs. This model enables developers to access advanced AI capabilities for free, without any API keys or server-side setup.

## Getting Started

Puter.js works without any API keys or sign-ups. To start using Puter.js, include the following script tag in your HTML file, either in the `<head>` or `<body>` section:

```hljs xml
<script src="https://js.puter.com/v2/"></script>

```

You're now ready to use Puter.js for free access to o3-mini capabilities. No API keys or sign-ups are required.

## Example 1Basic Text Generation with o3-mini

Let's start with a simple example showing how to use o3-mini for basic text generation:

```html hljs language-xml
<html>
<body>
    <script src="https://js.puter.com/v2/"></script>
    <script>
        // Generate text with o3-mini
        puter.ai.chat(
            "Explain how electric cars work in simple terms.",
            {model: 'openrouter:openai/o3-mini'}
        ).then(response => {
            document.body.innerHTML = response.message.content;
        });
    </script>
</body>
</html>

```

This basic example demonstrates how to use o3-mini to generate a straightforward explanation. The model is efficient for these kinds of informational queries and produces clear, concise text.

## Example 2Stream Responses for Better User Experience

For a more interactive experience, you can stream the responses as they're generated:

```html hljs language-xml
<html>
<body>
    <div id="response" style="font-family: Arial, sans-serif; max-width: 800px; margin: 20px auto; line-height: 1.6;"></div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        (async () => {
            const responseDiv = document.getElementById('response');
            responseDiv.textContent = "Generating response...";

            const response = await puter.ai.chat(
                "Write a short story about artificial intelligence becoming self-aware.",
                {
                    model: 'openrouter:openai/o3-mini',
                    stream: true
                }
            );

            responseDiv.textContent = ""; // Clear the loading message
            for await (const part of response) {
                if (part?.text) {
                    responseDiv.textContent += part.text
                }
            }
        })();
    </script>
</body>
</html>

```

This example shows how to implement streaming with o3-mini, which creates a better user experience by displaying content as it's generated rather than making users wait for the complete response.

## Example 3Create a Smart Recipe Generator

Now let's build a more practical application that helps users generate recipes based on ingredients they have available:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 0 auto; font-family: Arial, sans-serif;">
        <h1>Smart Recipe Generator</h1>
        <p>Enter ingredients you have (comma separated)</p>
        <textarea id="ingredients" rows="3" style="width: 100%; padding: 8px;"></textarea>
        <div style="margin: 10px 0;">
            <label>
                <input type="checkbox" id="vegetarian"> Vegetarian
            </label>
            <select id="meal-type">
                <option value="any">Any meal type</option>
                <option value="breakfast">Breakfast</option>
                <option value="lunch">Lunch</option>
                <option value="dinner">Dinner</option>
                <option value="dessert">Dessert</option>
            </select>
            <button id="generate-btn" style="padding: 8px 16px;">Generate Recipe</button>
        </div>
        <div id="loading" style="display: none;">Thinking of a delicious recipe...</div>
        <div id="recipe-output" style="margin-top: 20px; white-space: pre-wrap;"></div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        document.getElementById('generate-btn').addEventListener('click', async () => {
            const ingredientsList = document.getElementById('ingredients').value;
            const isVegetarian = document.getElementById('vegetarian').checked;
            const mealType = document.getElementById('meal-type').value;
            const outputDiv = document.getElementById('recipe-output');
            const loadingDiv = document.getElementById('loading');

            if (!ingredientsList.trim()) {
                outputDiv.textContent = "Please enter some ingredients.";
                return;
            }

            outputDiv.textContent = "";
            loadingDiv.style.display = 'block';

            const dietaryRestriction = isVegetarian ? "The recipe must be vegetarian." : "";
            const mealTypeReq = mealType !== 'any' ? `This should be a ${mealType} recipe.` : "";

            const prompt = `Create a recipe using these ingredients: ${ingredientsList}.
${dietaryRestriction}
${mealTypeReq}
Format the recipe with a title, ingredients list with measurements, and clear step-by-step instructions.`;

            try {
                const response = await puter.ai.chat(prompt, {
                    model: 'openrouter:openai/o3-mini',
                    stream: true
                });

                for await (const part of response) {
                    if (part?.text) {
                        outputDiv.textContent += part.text;
                    }
                }
            } catch (error) {
                outputDiv.textContent = "Error generating recipe: " + error.message;
            } finally {
                loadingDiv.style.display = 'none';
            }
        });
    </script>
</body>
</html>

```

This example creates a practical recipe generator that takes ingredients the user already has and generates a suitable recipe. It also allows users to specify dietary preferences and meal types for more targeted results.

## Example 2Interactive Study Assistant

Let's create an educational tool that helps students understand complex concepts through interactive explanations:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 0 auto; font-family: Arial, sans-serif; padding: 20px;">
        <h1>Interactive Study Assistant</h1>

        <div style="display: flex; gap: 10px; margin-bottom: 20px;">
            <select id="subject-select" style="padding: 8px;">
                <option value="math">Mathematics</option>
                <option value="science">Science</option>
                <option value="history">History</option>
                <option value="literature">Literature</option>
                <option value="computer-science">Computer Science</option>
            </select>

            <select id="level-select" style="padding: 8px;">
                <option value="beginner">Beginner</option>
                <option value="intermediate">Intermediate</option>
                <option value="advanced">Advanced</option>
            </select>
        </div>

        <input type="text" id="question-input" placeholder="Ask a question about your subject..."
               style="width: 100%; padding: 10px; font-size: 16px; margin-bottom: 10px;">

        <div style="display: flex; gap: 10px; margin-bottom: 20px;">
            <button id="ask-btn" style="padding: 8px 16px; background: #4285f4; color: white; border: none; border-radius: 4px;">
                Ask Question
            </button>

            <button id="simplify-btn" style="padding: 8px 16px;" disabled>
                Simplify Explanation
            </button>

            <button id="example-btn" style="padding: 8px 16px;" disabled>
                Give Me Examples
            </button>
        </div>

        <div id="loading" style="display: none; margin: 20px 0;">Thinking...</div>

        <div id="response-container" style="background: #f5f5f5; padding: 20px; border-radius: 8px; margin-top: 20px; display: none;">
            <h3 id="question-display"></h3>
            <div id="answer-display" style="line-height: 1.6;"></div>
        </div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        let currentQuestion = '';
        let currentAnswer = '';

        document.getElementById('ask-btn').addEventListener('click', async () => {
            const question = document.getElementById('question-input').value.trim();
            if (!question) return;

            currentQuestion = question;
            await generateResponse(question);
        });

        document.getElementById('simplify-btn').addEventListener('click', async () => {
            if (!currentQuestion) return;

            const prompt = `Please simplify the following explanation in simpler terms for a beginner:

${currentAnswer}`;

            await generateResponse(prompt, true);
        });

        document.getElementById('example-btn').addEventListener('click', async () => {
            if (!currentQuestion) return;

            const prompt = `Regarding this concept:

${currentQuestion}

Please provide 2-3 real-world examples that illustrate this concept clearly.`;

            await generateResponse(prompt, true);
        });

        async function generateResponse(prompt, isFollowUp = false) {
            const subject = document.getElementById('subject-select').value;
            const level = document.getElementById('level-select').value;
            const loadingDiv = document.getElementById('loading');
            const responseContainer = document.getElementById('response-container');
            const questionDisplay = document.getElementById('question-display');
            const answerDisplay = document.getElementById('answer-display');

            loadingDiv.style.display = 'block';

            let fullPrompt = prompt;
            if (!isFollowUp) {
                fullPrompt = `I'm studying ${subject} at a ${level} level. ${prompt}

Please explain this concept thoroughly but clearly. Use analogies where helpful.`;
            }

            try {
                answerDisplay.innerHTML = '';
                const response = await puter.ai.chat(fullPrompt, {
                    model: 'openrouter:openai/o3-mini',
                    stream: true
                });

                let fullResponse = '';
                for await (const part of response) {
                    if (part?.text) {
                        answerDisplay.innerHTML += part.text;
                        fullResponse += part.text;
                    }
                }

                currentAnswer = fullResponse;
                document.getElementById('simplify-btn').disabled = false;
                document.getElementById('example-btn').disabled = false;

                if (!isFollowUp) {
                    questionDisplay.textContent = currentQuestion;
                }

                responseContainer.style.display = 'block';
            } catch (error) {
                answerDisplay.innerHTML = "Error generating response: " + error.message;
            } finally {
                loadingDiv.style.display = 'none';
            }
        }

        // Enter key to submit
        document.getElementById('question-input').addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                document.getElementById('ask-btn').click();
            }
        });
    </script>
</body>
</html>

```

This example creates an interactive study assistant that helps students learn by providing explanations tailored to their educational level. It includes additional buttons to request simplified explanations or concrete examples, making it a valuable learning tool.

## Example 4Business Content Generator

Here's a tool that generates professional business content for various purposes:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 0 auto; font-family: Arial, sans-serif; padding: 20px;">
        <h1>Business Content Generator</h1>

        <div style="margin-bottom: 20px;">
            <label for="content-type">Content Type:</label>
            <select id="content-type" style="padding: 8px; width: 100%; margin-top: 5px;">
                <option value="email">Professional Email</option>
                <option value="proposal">Business Proposal Summary</option>
                <option value="marketing">Marketing Copy</option>
                <option value="social">Social Media Post</option>
                <option value="job">Job Description</option>
            </select>
        </div>

        <div style="margin-bottom: 20px;">
            <label for="industry">Industry:</label>
            <input type="text" id="industry" placeholder="e.g., Technology, Healthcare, Finance"
                   style="padding: 8px; width: 100%; margin-top: 5px;">
        </div>

        <div style="margin-bottom: 20px;">
            <label for="details">Key Points/Details:</label>
            <textarea id="details" rows="5" placeholder="Enter key information to include in the content..."
                      style="padding: 8px; width: 100%; margin-top: 5px;"></textarea>
        </div>

        <div style="margin-bottom: 20px;">
            <label>Tone:</label>
            <div style="display: flex; gap: 10px; margin-top: 5px;">
                <label><input type="radio" name="tone" value="formal" checked> Formal</label>
                <label><input type="radio" name="tone" value="conversational"> Conversational</label>
                <label><input type="radio" name="tone" value="persuasive"> Persuasive</label>
                <label><input type="radio" name="tone" value="enthusiastic"> Enthusiastic</label>
            </div>
        </div>

        <button id="generate-btn" style="padding: 10px 20px; background: #0078D7; color: white; border: none; border-radius: 4px; cursor: pointer;">
            Generate Content
        </button>

        <div id="loading" style="margin-top: 20px; display: none;">
            Generating professional content...
        </div>

        <div id="output-container" style="margin-top: 20px; display: none;">
            <h3>Generated Content</h3>
            <div id="output" style="background: #f8f8f8; padding: 20px; border: 1px solid #ddd; border-radius: 4px; white-space: pre-wrap;"></div>

            <div style="margin-top: 15px;">
                <button id="copy-btn" style="padding: 8px 12px;">Copy to Clipboard</button>
                <button id="regenerate-btn" style="padding: 8px 12px; margin-left: 10px;">Regenerate</button>
            </div>
        </div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        function getSelectedTone() {
            const toneRadios = document.getElementsByName('tone');
            for (const radio of toneRadios) {
                if (radio.checked) {
                    return radio.value;
                }
            }
            return 'formal';
        }

        async function generateContent() {
            const contentType = document.getElementById('content-type').value;
            const industry = document.getElementById('industry').value || 'general business';
            const details = document.getElementById('details').value;
            const tone = getSelectedTone();

            const loadingDiv = document.getElementById('loading');
            const outputContainer = document.getElementById('output-container');
            const outputDiv = document.getElementById('output');

            if (!details.trim()) {
                alert('Please provide some details for your content.');
                return;
            }

            loadingDiv.style.display = 'block';
            outputContainer.style.display = 'none';

            let contentDescription;
            switch (contentType) {
                case 'email':
                    contentDescription = 'a professional email';
                    break;
                case 'proposal':
                    contentDescription = 'a business proposal summary';
                    break;
                case 'marketing':
                    contentDescription = 'marketing copy';
                    break;
                case 'social':
                    contentDescription = 'a social media post';
                    break;
                case 'job':
                    contentDescription = 'a job description';
                    break;
            }

            const prompt = `Generate ${contentDescription} for the ${industry} industry with a ${tone} tone.

Include the following key points/details:
${details}

Make sure the content is professional, well-structured, and ready to use.`;

            try {
                outputDiv.textContent = '';
                const response = await puter.ai.chat(prompt, {
                    model: 'openrouter:openai/o3-mini',
                    stream: true
                });

                for await (const part of response) {
                    if (part?.text) {
                        outputDiv.textContent += part.text;
                    }
                }

                outputContainer.style.display = 'block';
            } catch (error) {
                outputDiv.textContent = 'Error generating content: ' + error.message;
                outputContainer.style.display = 'block';
            } finally {
                loadingDiv.style.display = 'none';
            }
        }

        document.getElementById('generate-btn').addEventListener('click', generateContent);
        document.getElementById('regenerate-btn').addEventListener('click', generateContent);

        document.getElementById('copy-btn').addEventListener('click', () => {
            const outputText = document.getElementById('output').textContent;
            navigator.clipboard.writeText(outputText)
                .then(() => alert('Content copied to clipboard!'))
                .catch(err => alert('Failed to copy: ' + err));
        });
    </script>
</body>
</html>

```

This example creates a versatile business content generator that can produce professional emails, marketing copy, job descriptions, and more with customizable industry focus and tone.

## Example 5Data Analysis Assistant

Let's create a tool that helps users understand and interpret data:

```html hljs language-xml
<html>
<body>
    <div style="max-width: 800px; margin: 0 auto; font-family: Arial, sans-serif; padding: 20px;">
        <h1>Data Analysis Assistant</h1>

        <div style="margin-bottom: 20px;">
            <h3>Enter Your Data</h3>
            <p>Paste your data in CSV format or as a table of numbers/text:</p>
            <textarea id="data-input" rows="10" style="width: 100%; font-family: monospace; padding: 8px;"></textarea>
        </div>

        <div style="margin-bottom: 20px;">
            <h3>Analysis Options</h3>
            <div style="display: flex; flex-wrap: wrap; gap: 10px;">
                <label><input type="checkbox" id="summarize" checked> Summarize Data</label>
                <label><input type="checkbox" id="trends"> Identify Trends</label>
                <label><input type="checkbox" id="correlations"> Find Correlations</label>
                <label><input type="checkbox" id="anomalies"> Detect Anomalies</label>
                <label><input type="checkbox" id="recommendations"> Provide Recommendations</label>
            </div>
        </div>

        <div style="margin-bottom: 20px;">
            <label for="context">Additional Context (optional):</label>
            <textarea id="context" rows="3" placeholder="Add any context about your data that might help with analysis..."
                      style="width: 100%; padding: 8px;"></textarea>
        </div>

        <button id="analyze-btn" style="padding: 10px 20px; background: #4CAF50; color: white; border: none; border-radius: 4px;">
            Analyze Data
        </button>

        <div id="loading" style="display: none; margin-top: 20px;">
            Analyzing your data...
        </div>

        <div id="analysis-output" style="margin-top: 20px; line-height: 1.6;"></div>
    </div>

    <script src="https://js.puter.com/v2/"></script>
    <script>
        document.getElementById('analyze-btn').addEventListener('click', async () => {
            const dataInput = document.getElementById('data-input').value.trim();
            if (!dataInput) {
                alert('Please enter some data to analyze.');
                return;
            }

            const summarize = document.getElementById('summarize').checked;
            const trends = document.getElementById('trends').checked;
            const correlations = document.getElementById('correlations').checked;
            const anomalies = document.getElementById('anomalies').checked;
            const recommendations = document.getElementById('recommendations').checked;
            const context = document.getElementById('context').value;

            const analysisOptions = [];
            if (summarize) analysisOptions.push('Provide a summary of the data');
            if (trends) analysisOptions.push('Identify any trends or patterns');
            if (correlations) analysisOptions.push('Find potential correlations between variables');
            if (anomalies) analysisOptions.push('Detect any anomalies or outliers');
            if (recommendations) analysisOptions.push('Suggest next steps or recommendations based on the data');

            if (analysisOptions.length === 0) {
                alert('Please select at least one analysis option.');
                return;
            }

            const prompt = `Analyze the following data:

${dataInput}

${context ? 'Additional context: ' + context + '\n\n' : ''}

Please perform the following analysis:
${analysisOptions.map(option => '- ' + option).join('\n')}

Provide your analysis in a clear, structured format with headings for each section.`;

            const loadingDiv = document.getElementById('loading');
            const outputDiv = document.getElementById('analysis-output');

            loadingDiv.style.display = 'block';
            outputDiv.innerHTML = '';

            try {
                const response = await puter.ai.chat(prompt, {
                    model: 'openrouter:openai/o3-mini',
                    stream: true
                });

                for await (const part of response) {
                    if (part?.text) {
                        outputDiv.innerHTML += part.text;
                    }
                }
            } catch (error) {
                outputDiv.innerHTML = 'Error analyzing data: ' + error.message;
            } finally {
                loadingDiv.style.display = 'none';
            }
        });
    </script>
</body>
</html>

```

This data analysis assistant helps users gain insights from their numerical or tabular data by providing summary statistics, identifying trends, finding correlations, and offering recommendations.

## Best Practices for Using o3-mini

When using o3-mini through Puter.js, consider these best practices:

1. **Optimize prompt structure**: o3-mini produces better results with well-structured prompts that clearly state the desired output format.

2. **Use streaming for longer outputs**: Enable streaming for a better user experience, especially for content generation tasks.

3. **Provide specific instructions**: Be explicit about requirements such as tone, length, or format to get more targeted results.

4. **Include error handling**: Always implement proper error handling to provide feedback if requests fail.

5. **Consider user context**: The model works best when given relevant context about the user's needs or situation.


That's it! You now have free, unlimited access to OpenAI's o3-mini model using Puter.js. This allows you to leverage powerful AI capabilities for your applications without worrying about API keys or usage limits.

## Related

- [Free, Unlimited Claude API](https://developer.puter.com/tutorials/free-unlimited-claude-35-sonnet-api)
- [Free, Unlimited OpenRouter API](https://developer.puter.com/tutorials/free-unlimited-openrouter-api)
- [Free, Unlimited o1-mini API](https://developer.puter.com/tutorials/free-unlimited-o1-mini-api)
- [Free, Unlimited OpenAI API](https://developer.puter.com/tutorials/free-unlimited-openai-api)
- [Free, Unlimited Gemini API](https://developer.puter.com/tutorials/free-gemini-api)
- [Serverless AI: Forever Free for Developers](https://developer.puter.com/tutorials/serverless-ai-forever-free-for-developers)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)