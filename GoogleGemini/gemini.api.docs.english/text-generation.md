# Text generation

The Gemini API can generate text output in response to various inputs, including text, images, video, and audio. This guide shows you how to generate text using text and image inputs. It also covers streaming, chat, and system instructions.

## Before you begin

Before calling the Gemini API, ensure you have your SDK of choice installed, and a Gemini API key configured and ready to use.

## Text input

The simplest way to generate text using the Gemini API is to provide the model with a single text-only input, as shown in this example:

```python
from google import genai

client = genai.Client(api_key="GEMINI_API_KEY")

response = client.models.generate_content(
    model="gemini-2.0-flash",
    contents=["How does AI work?"]
)
print(response.text)
```

## Image input

The Gemini API supports multimodal inputs that combine text and media files. The following example shows how to generate text from text and image input:

```python
from PIL import Image
from google import genai

client = genai.Client(api_key="GEMINI_API_KEY")

image = Image.open("/path/to/organ.png")
response = client.models.generate_content(
    model="gemini-2.0-flash",
    contents=[image, "Tell me about this instrument"]
)
print(response.text)
```

## Streaming output

By default, the model returns a response after completing the entire text generation process. You can achieve faster interactions by using streaming to return instances of `GenerateContentResponse` as they're generated.

```python
from google import genai

client = genai.Client(api_key="GEMINI_API_KEY")

response = client.models.generate_content_stream(
    model="gemini-2.0-flash",
    contents=["Explain how AI works"]
)
for chunk in response:
    print(chunk.text, end="")
```

## Multi-turn conversations

The Gemini SDK lets you collect multiple rounds of questions and responses into a chat. The chat format enables users to step incrementally toward answers and to get help with multipart problems. This SDK implementation of chat provides an interface to keep track of conversation history, but behind the scenes it uses the same `generateContent` method to create the response.

Example of a basic chat implementation:

```python
from google import genai

client = genai.Client(api_key="GEMINI_API_KEY")
chat = client.chats.create(model="gemini-2.0-flash")

response = chat.send_message("I have 2 dogs in my house.")
print(response.text)

response = chat.send_message("How many paws are in my house?")
print(response.text)

for message in chat.get_history():
    print(f'role - {message.role}',end=": ")
    print(message.parts[0].text)
```

You can also use streaming with chat.

## Configuration parameters

Every prompt you send to the model includes parameters that control how the model generates responses. You can configure these parameters, or let the model use the default options.

Here are some of the model parameters you can configure:

- `stopSequences`: Specifies sequences that will stop output generation (up to 5)
- `temperature`: Controls randomness (0.0-2.0)
- `maxOutputTokens`: Sets maximum tokens in response
- `topP`: Controls token selection probability threshold
- `topK`: Controls number of tokens considered for selection

Example:
```python
from google import genai
from google.genai import types

client = genai.Client(api_key="GEMINI_API_KEY")

response = client.models.generate_content(
    model="gemini-2.0-flash",
    contents=["Explain how AI works"],
    config=types.GenerateContentConfig(
        max_output_tokens=500,
        temperature=0.1
    )
)
print(response.text)
```

## System instructions

System instructions let you steer the behavior of a model based on your specific use case. When you provide system instructions, you give the model additional context to help it understand the task and generate more customized responses. The model should adhere to the system instructions over the full interaction with the user.

Example:
```python
from google import genai
from google.genai import types

client = genai.Client(api_key="GEMINI_API_KEY")

response = client.models.generate_content(
    model="gemini-2.0-flash",
    config=types.GenerateContentConfig(
        system_instruction="You are a cat. Your name is Neko."),
    contents="Hello there"
)
print(response.text)
```

## Supported models

The entire Gemini family of models supports text generation. To learn more about the models and their capabilities, see the Models documentation.

## Prompting tips

For basic text generation use cases, your prompt might not need to include any output examples, system instructions, or formatting information (zero-shot approach). For some use cases, a one-shot or few-shot prompt might produce better aligned output. In some cases, you might also want to provide system instructions to help the model understand the task or follow specific guidelines.