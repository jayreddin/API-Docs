# Files API

The Gemini family of artificial intelligence (AI) models is built to handle various types of input data, including text, images, and audio. Since these models can handle more than one type or _mode_ of data, the Gemini models are called _multimodal models_ or explained as having _multimodal capabilities_.

This guide shows you how to work with media files using the Files API. The basic operations are the same for audio files, images, videos, documents, and other supported file types.

For file prompting guidance, check out the [File prompt guide](#file-prompting-strategies) section.

## Upload a file

You can use the Files API to upload a media file. Always use the Files API when the total request size (including the files, text prompt, system instructions, etc.) is larger than 20 MB.

The following code uploads a file and then uses the file in a call to `generateContent`.

```python
from google import genai

client = genai.Client(api_key="GOOGLE_API_KEY")

myfile = client.files.upload(file="path/to/sample.mp3")

response = client.models.generate_content(
    model="gemini-2.0-flash", contents=["Describe this audio clip", myfile]
)

print(response.text)
```

## Get metadata for a file

You can verify that the API successfully stored the uploaded file and get its metadata by calling `files.get`.

```python
myfile = client.files.upload(file='path/to/sample.mp3')
file_name = myfile.name
myfile = client.files.get(name=file_name)
print(myfile)
```

## List uploaded files

You can upload multiple files using the Files API. The following code gets a list of all the files uploaded:

```python
print('My files:')
for f in client.files.list():
    print(' ', f.name)
```

## Delete uploaded files

Files are automatically deleted after 48 hours. You can also manually delete an uploaded file:

```python
myfile = client.files.upload(file='path/to/sample.mp3')
client.files.delete(name=myfile.name)
```

## Usage info

You can use the Files API to upload and interact with media files. The Files API lets you store up to 20 GB of files per project, with a per-file maximum size of 2 GB. Files are stored for 48 hours. During that time, you can use the API to get metadata about the files, but you can't download the files. The Files API is available at no cost in all regions where the Gemini API is available.

## File prompting strategies

This section provides guidance and best practices for using media files with prompts for the Gemini API.

Being able to use various types of data in your prompts gives you more flexibility in terms of what tasks you can tackle with the Gemini API. For example, you can send the model a photo of a delicious meal and ask it to write a short blog about the meal.

You can improve your multimodal prompts by following these best practices:

### Be specific in your instructions

Prompts have the most success when they are clear and detailed. If you have a specific output in mind, it's better to include that requirement in the prompt to ensure you get the output you want.

### Add a few examples

The Gemini model can accept multiple inputs which it can use as examples to understand the output you want. Adding these examples can help the model identify the patterns and apply the relationship between the given images and responses to the new example. This is also called "few-shot" learning.

### Break it down step-by-step

For complex tasks like the ones that require both visual understanding and reasoning, it can be helpful to split the task into smaller, more straightforward steps. Alternatively, it could also be effective if you directly ask the model to "think step by step" in your prompt.

### Specify the output format

A common problem is the need for model output to be in a certain format (e.g. markdown, JSON, HTML), especially if the model output needs to be ingested by a downstream task. You can try to produce output in that format by instructing the model to do so within the prompt.

### Put your image first for single-image prompts

While Gemini can interpret image and text in any order within a prompt, placing a single image before the text prompt might lead to better results.

### Troubleshooting your multimodal prompt

You might need to troubleshoot your prompt if you are not getting a helpful response. Here are a few strategies you could try:

#### If the model is not drawing information from the relevant part of the image
Drop hints with which aspects of the image you want the prompt to draw information from.

#### If the model output is too generic
At the start of the prompt, try asking the model to describe the image(s) or video before providing the task instruction, or try asking the model to refer to what's in the image.

#### To troubleshoot which part failed
Ask the model to describe the image, or ask the model to explain its reasoning, to gauge the model's initial understanding.

#### If your prompt results in hallucinated content
Try dialing down the temperature setting or asking the model for shorter descriptions so that it's less likely to extrapolate additional details.

#### Tuning the sampling parameters
Experiment with different temperature settings and top-k selections to adjust the model's creativity.

## What's next

- Try writing your own multimodal prompts using [Google AI Studio](http://aistudio.google.com/).
- For information on using the Gemini Files API for uploading media files and including them in your prompts, see the [Vision](https://ai.google.dev/gemini-api/docs/vision), [Audio](https://ai.google.dev/gemini-api/docs/audio), and [Document processing](https://ai.google.dev/gemini-api/docs/document-processing) guides.
- For more guidance on prompt design, like tuning sampling parameters, see the [Prompt strategies](https://ai.google.dev/gemini-api/docs/prompting-strategies) page.