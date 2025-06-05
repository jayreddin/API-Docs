# Gemini Thinking

The Gemini 2.5 series models use an internal "thinking process" during response generation. This process contributes to their improved reasoning capabilities and helps them use multi-step planning to solve complex tasks. This makes these models especially good at coding, advanced mathematics, data analysis, and other tasks that require planning or thinking.

This guide shows you how to work with Gemini's thinking capabilities using the Gemini API.

## Use thinking models

Models with thinking capabilities are available in Google AI Studio and through the Gemini API. Thinking is on by default in both the API and AI Studio because the 2.5 series models have the ability to automatically decide when and how much to think based on the prompt. For most use cases, it's beneficial to leave thinking on. But if you want to turn thinking off, you can do so by setting the `thinkingBudget` parameter to 0.

### Send a basic request

```python
from google import genai

client = genai.Client(api_key="GOOGLE_API_KEY")
prompt = "Explain the concept of Occam's Razor and provide a simple, everyday example."
response = client.models.generate_content(
    model="gemini-2.5-flash-preview-04-17",
    contents=prompt
)

print(response.text)
```

### Set budget on thinking models

The `thinkingBudget` parameter gives the model guidance on the number of thinking tokens it can use when generating a response. A greater number of tokens is typically associated with more detailed thinking, which is needed for solving more complex tasks. `thinkingBudget` must be an integer in the range 0 to 24576. Setting the thinking budget to 0 disables thinking.

Depending on the prompt, the model might overflow or underflow the token budget.

Example:
```python
from google import genai
from google.genai import types

client = genai.Client()

response = client.models.generate_content(
    model="gemini-2.5-flash-preview-04-17",
    contents="Explain the Occam's Razor concept and provide everyday examples of it",
    config=types.GenerateContentConfig(
        thinking_config=types.ThinkingConfig(thinking_budget=1024)
    ),
)

print(response.text)
```

## Use tools with thinking models

You can combine your use of the thinking models with any of Gemini's tools and capabilities to perform actions beyond generating text. This allows them to interact with external systems, execute code, or access real-time information, incorporating the results into their reasoning and final response.

- The search tool allows the model to query external search engines to find up-to-date information or information beyond its training data. This is useful for questions about recent events or highly specific topics.

- The code execution tool enables the model to generate and run Python code to perform calculations, manipulate data, or solve problems that are best handled algorithmically. The model receives the code's output and can use it in its response.

- With structured output, you can constrain Gemini to respond with JSON, a structured output format suitable for automated processing. This is particularly useful for integrating the model's output into applications.

- Function calling connects the thinking model to external tools and APIs, so it can reason around when to call the right function and what parameters to provide.

## Best practices

This section includes some guidance for using thinking models efficiently.

### Debugging and steering

- **Review reasoning**: When you're not getting your expected response from the thinking models, it can help to carefully analyze Gemini's reasoning process. You can see how it broke down the task and arrived at its conclusion, and use that information to correct towards the right results.

- **Provide Guidance in Reasoning**: If you're hoping for a particularly lengthy output, you may want to provide guidance in your prompt to constrain the amount of thinking the model uses. This lets you reserve more of the token output for your response.

### Task complexity

- **Easy Tasks (Thinking could be OFF):** For straightforward requests, complex reasoning isn't required such as straightforward fact retrieval or classification, thinking is not required. Examples include:
  - "Where was DeepMind founded?"
  - "Is this email asking for a meeting or just providing information?"

- **Medium Tasks (Default/Some Thinking):** Many common requests benefit from a degree of step-by-step processing or deeper understanding. Gemini can flexibly use thinking capability for tasks like:
  - Analogize photosynthesis and growing up.
  - Compare and contrast electric cars and hybrid cars.

- **Hard Tasks (Maximum Thinking Capability):** For truly complex challenges, the AI needs to engage its full reasoning and planning capabilities, often involving many internal steps before providing an answer. Examples include:
  - Solve problem 1 in AIME 2025: Find the sum of all integer bases b > 9 for which 17b is a divisor of 97b.
  - Write Python code for a web application that visualizes real-time stock market data, including user authentication. Make it as efficient as possible.