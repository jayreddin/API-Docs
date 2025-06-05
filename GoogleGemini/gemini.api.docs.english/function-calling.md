# Function Calling with the Gemini API

Function calling lets you connect models to external tools and APIs. Instead of generating text responses, the model understands when to call specific functions and provides the necessary parameters to execute real-world actions. This allows the model to act as a bridge between natural language and real-world actions and data. Function calling has 3 primary use cases:

- **Augment Knowledge:** Access information from external sources like databases, APIs, and knowledge bases.
- **Extend Capabilities:** Use external tools to perform computations and extend the limitations of the model, such as using a calculator or creating charts.
- **Take Actions:** Interact with external systems using APIs, such as scheduling appointments, creating invoices, sending emails, or controlling smart home devices

## How Function Calling Works

Function calling involves a structured interaction between your application, the model, and external functions. Here's a breakdown of the process:

1. **Define Function Declaration:** Define the function declaration in your application code. Function Declarations describe the function's name, parameters, and purpose to the model.

2. **Call LLM with function declarations:** Send user prompt along with the function declaration(s) to the model. It analyzes the request and determines if a function call would be helpful. If so, it responds with a structured JSON object.

3. **Execute Function Code (Your Responsibility):** The Model _does not_ execute the function itself. It's your application's responsibility to process the response and check for Function Call:
   - **Yes**: Extract the name and args of the function and execute the corresponding function in your application.  
   - **No:** The model has provided a direct text response to the prompt.

4. **Create User friendly response:** If a function was executed, capture the result and send it back to the model in a subsequent turn of the conversation. It will use the result to generate a final, user-friendly response that incorporates the information from the function call.

This process can be repeated over multiple turns, allowing for complex interactions and workflows. The model also supports calling multiple functions in a single turn (parallel function calling) and in sequence (compositional function calling).

## Function declarations

When you implement function calling in a prompt, you create a `tools` object, which contains one or more _`function declarations`_. You define functions using JSON, specifically with a [select subset](https://ai.google.dev/api/caching#Schema) of the [OpenAPI schema](https://spec.openapis.org/oas/v3.0.3#schemawr) format. A single function declaration can include the following parameters:

- `name` (string): A unique name for the function (`get_weather_forecast`, `send_email`). Use descriptive names without spaces or special characters (use underscores or camelCase).
- `description` (string): A clear and detailed explanation of the function's purpose and capabilities. This is crucial for the model to understand when to use the function. Be specific and provide examples if helpful ("Finds theaters based on location and optionally movie title which is currently playing in theaters.").
- `parameters` (object): Defines the input parameters the function expects.
  - `type` (string): Specifies the overall data type, such as `object`.
  - `properties` (object): Lists individual parameters, each with:
    - `type` (string): The data type of the parameter, such as `string`, `integer`, `boolean, array`.
    - `description` (string): A description of the parameter's purpose and format. Provide examples and constraints ("The city and state, e.g., 'San Francisco, CA' or a zip code e.g., '95616'.").
    - `enum` (array, optional): If the parameter values are from a fixed set, use "enum" to list the allowed values instead of just describing them in the description. This improves accuracy ("enum": ["daylight", "cool", "warm"]).
  - `required` (array): An array of strings listing the parameter names that are mandatory for the function to operate.

## Parallel Function Calling

In addition to single turn function calling, you can also call multiple functions at once. Parallel function calling lets you execute multiple functions at once and is used when the functions are not dependent on each other. This is useful in scenarios like gathering data from multiple independent sources, such as retrieving customer details from different databases or checking inventory levels across various warehouses or performing multiple actions such as converting your apartment into a disco.

## Compositional Function Calling

Gemini 2.0 supports compositional function calling, meaning the model can chain multiple function calls together. For example, to answer "Get the temperature in my current location", the Gemini API might invoke both a `get_current_location()` function and a `get_weather()` function that takes the location as a parameter.

## Function calling modes

The Gemini API lets you control how the model uses the provided tools (function declarations). Specifically, you can set the mode within the `function_calling_config`.

- `AUTO (Default)`: The model decides whether to generate a natural language response or suggest a function call based on the prompt and context. This is the most flexible mode and recommended for most scenarios.
- `ANY`: The model is constrained to always predict a function call and guarantee function schema adherence. If `allowed_function_names` is not specified, the model can choose from any of the provided function declarations. If `allowed_function_names` is provided as a list, the model can only choose from the functions in that list. Use this mode when you require a function call in response to every prompt (if applicable).
- `NONE`: The model is _prohibited_ from making function calls. This is equivalent to sending a request without any function declarations. Use this to temporarily disable function calling without removing your tool definitions.

## Automatic Function Calling (Python Only)

When using the Python SDK, you can provide Python functions directly as tools. The SDK automatically converts the Python function to declarations, handles the function call execution and response cycle for you. The Python SDK then automatically:

1. Detects function call responses from the model.
2. Call the corresponding Python function in your code.
3. Sends the function response back to the model.
4. Returns the model's final text response.

### Automatic Function schema declaration

Automatic schema extraction from Python functions doesn't work in all cases. For example: it doesn't handle cases where you describe the fields of a nested dictionary-object. The API is able to describe any of the following types:

```python
AllowedType = (int | float | bool | str | list['AllowedType'] | dict[str, AllowedType])
```

## Multi-tool use: Combine Native Tools with Function Calling 

With Gemini 2.0, you can enable multiple tools combining native tools with function calling at the same time. For example, you can combine Grounding with Google Search, code execution, and custom function declarations.

## Use Model Context Protocol (MCP)

[Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) is an open standard to connect AI applications with external tools, data sources, and systems. MCP provides a common protocol for models to access context, such as functions (tools), data sources (resources), or predefined prompts. You can use models with MCP server using their tool calling capabilities.

MCP servers expose the tools as JSON schema definitions, which can be used with Gemini compatible function declarations. This lets you to use a MCP server with Gemini models directly.

## Supported Models

| Model | Function Calling | Parallel Function Calling | Compositional Function Calling<br>(Live API only) |
| --- | --- | --- | --- |
| Gemini 2.0 Flash | ✔️ | ✔️ | ✔️ |
| Gemini 2.0 Flash-Lite | X | X | X |
| Gemini 1.5 Flash | ✔️ | ✔️ | ✔️ |
| Gemini 1.5 Pro | ✔️ | ✔️ | ✔️ |

## Best Practices

- **Function and Parameter Descriptions:** Be extremely clear and specific in your descriptions. The model relies on these to choose the correct function and provide appropriate arguments.
- **Naming:** Use descriptive function names (without spaces, periods, or dashes).
- **Strong Typing:** Use specific types (integer, string, enum) for parameters to reduce errors. If a parameter has a limited set of valid values, use an enum.
- **Tool Selection:** While the model can use an arbitrary number of tools, providing too many can increase the risk of selecting an incorrect or suboptimal tool. For best results, aim to provide only the relevant tools for the context or task, ideally keeping the active set to a maximum of 10-20. Consider dynamic tool selection based on conversation context if you have a large total number of tools.
- **Prompt Engineering:**
  - Provide context: Tell the model its role (e.g., "You are a helpful weather assistant.").
  - Give instructions: Specify how and when to use functions (e.g., "Don't guess dates; always use a future date for forecasts.").
  - Encourage clarification: Instruct the model to ask clarifying questions if needed.
- **Temperature:** Use a low temperature (e.g., 0) for more deterministic and reliable function calls.
- **Validation:** If a function call has significant consequences (e.g., placing an order), validate the call with the user before executing it.
- **Error Handling**: Implement robust error handling in your functions to gracefully handle unexpected inputs or API failures. Return informative error messages that the model can use to generate helpful responses to the user.
- **Security:** Be mindful of security when calling external APIs. Use appropriate authentication and authorization mechanisms. Avoid exposing sensitive data in function calls.
- **Token Limits:** Function descriptions and parameters count towards your input token limit. If you're hitting token limits, consider limiting the number of functions or the length of the descriptions, break down complex tasks into smaller, more focused function sets.

## Notes and Limitations

- Only a [subset of the OpenAPI schema](https://ai.google.dev/api/caching#FunctionDeclaration) is supported.
- Supported parameter types in Python are limited.
- Automatic function calling is a Python SDK feature only.