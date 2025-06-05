# Gemini API quickstart

This quickstart shows you how to install your SDK of choice from the new Google Gen AI SDK, and then make your first Gemini API request.

## Install the Gemini API library

Using [Python 3.9+](https://www.python.org/downloads/), install the [`google-genai` package](https://pypi.org/project/google-genai/) using the following [pip command](https://packaging.python.org/en/latest/tutorials/installing-packages/):

```
pip install -q -U google-genai
```

## Make your first request

[Get a Gemini API key in Google AI Studio](https://aistudio.google.com/app/apikey)

Use the [`generateContent`](https://ai.google.dev/api/generate-content#method:-models.generatecontent) method to send a request to the Gemini API.

```python
from google import genai

client = genai.Client(api_key="YOUR_API_KEY")

response = client.models.generate_content(
    model="gemini-2.0-flash", contents="Explain how AI works in a few words"
)
print(response.text)
```

## What's next

Now that you made your first API request, you might want to explore the following guides that show Gemini in action:

- [Text generation](https://ai.google.dev/gemini-api/docs/text-generation)
- [Vision](https://ai.google.dev/gemini-api/docs/vision)
- [Long context](https://ai.google.dev/gemini-api/docs/long-context)