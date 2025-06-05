# Video understanding

Gemini models can process videos, enabling many frontier developer use cases that would have historically required domain specific models. Some of Gemini's vision capabilities include the ability to:

- Describe, segment, and extract information from videos up to 90 minutes long
- Answer questions about video content  
- Refer to specific timestamps within a video

Gemini was built to be multimodal from the ground up and we continue to push the frontier of what is possible. This guide shows how to use the Gemini API to generate text responses based on video inputs.

### Before you begin

Before calling the Gemini API, ensure you have [your SDK of choice](https://ai.google.dev/gemini-api/docs/downloads) installed, and a [Gemini API key](https://ai.google.dev/gemini-api/docs/api-key) configured and ready to use.

## Video input

You can provide videos as input to Gemini in the following ways:

- [Upload a video file](#upload-video) using the File API before making a request to `generateContent`. Use this method for files larger than 20MB, videos longer than approximately 1 minute, or when you want to reuse the file across multiple requests.
- [Pass inline video data](#inline-video) with the request to `generateContent`. Use this method for smaller files (<20MB) and shorter durations.
- [Include a YouTube URL](#youtube) directly in the prompt.

### Upload a video file {#upload-video}

You can use the [Files API](https://ai.google.dev/gemini-api/docs/files) to upload a video file. Always use the Files API when the total request size (including the file, text prompt, system instructions, etc.) is larger than 20 MB, the video duration is significant, or if you intend to use the same video in multiple prompts.

```python
from google import genai

client = genai.Client(api_key="GOOGLE_API_KEY")

myfile = client.files.upload(file="path/to/sample.mp4")

response = client.models.generate_content(
    model="gemini-2.0-flash", contents=[myfile, "Summarize this video. Then create a quiz with an answer key based on the information in this video."]
)

print(response.text)
```

To learn more about working with media files, see [Files API](https://ai.google.dev/gemini-api/docs/files).

### Pass video data inline {#inline-video}

Instead of uploading a video file using the File API, you can pass smaller videos directly in the request to `generateContent`. This is suitable for shorter videos under 20MB total request size.

Here's an example:

```python
# Only for videos of size <20Mb
video_file_name = "/path/to/your/video.mp4"
video_bytes = open(video_file_name, 'rb').read()

response = client.models.generate_content(
    model='models/gemini-2.0-flash',
    contents=types.Content(
        parts=[
            types.Part(
                inline_data=types.Blob(data=video_bytes, mime_type='video/mp4')
            ),
            types.Part(text='Please summarize the video in 3 sentences.')
        ]
    )
)
```

### Include a YouTube URL {#youtube}

The Gemini API and AI Studio support YouTube URLs as a file data `Part`. You can include a YouTube URL with a prompt asking the model to summarize, translate, or otherwise interact with the video content.

**Limitations:**

- You can't upload more than 8 hours of YouTube video per day
- You can upload only 1 video per request
- You can only upload public videos (not private or unlisted videos)

Example:

```python
response = client.models.generate_content(
    model='models/gemini-2.0-flash',
    contents=types.Content(
        parts=[
            types.Part(
                file_data=types.FileData(file_uri='https://www.youtube.com/watch?v=9hE5-98ZeCg')
            ),
            types.Part(text='Please summarize the video in 3 sentences.')
        ]
    )
)
```

## Refer to timestamps in the content

You can ask questions about specific points in time within the video using timestamps of the form `MM:SS`.

For example:
```python
prompt = "What are the examples given at 00:05 and 00:10 supposed to show us?"
```

## Transcribe video and provide visual descriptions

The Gemini models can transcribe and provide visual descriptions of video content by processing both the audio track and visual frames. For visual descriptions, the model samples the video at a rate of **1 frame per second**. This sampling rate may affect the level of detail in the descriptions, particularly for videos with rapidly changing visuals.

Example:
```python
prompt = "Transcribe the audio from this video, giving timestamps for salient events in the video. Also provide visual descriptions."
```

## Supported video formats

Gemini supports the following video format MIME types:

- `video/mp4`
- `video/mpeg`  
- `video/mov`
- `video/avi`
- `video/x-flv`
- `video/mpg`
- `video/webm`
- `video/wmv`
- `video/3gpp`

## Technical details about videos

- **Supported models & context**: All Gemini 2.0 and 2.5 models can process video data.
  - Models with a 2M context window can process videos up to 2 hours long, while models with a 1M context window can process videos up to 1 hour long.

- **File API processing**: When using the File API, videos are sampled at 1 frame per second (FPS) and audio is processed at 1Kbps (single channel). Timestamps are added every second.
  - These rates are subject to change in the future for improvements in inference.

- **Token calculation**: Each second of video is tokenized as follows:
  - Individual frames (sampled at 1 FPS): 258 tokens per frame
  - Audio: 32 tokens per second  
  - Metadata is also included
  - Total: Approximately 300 tokens per second of video

- **Timestamp format**: When referring to specific moments in a video within your prompt, use the `MM:SS` format (e.g., `01:15` for 1 minute and 15 seconds).

- **Best practices**:
  - Use only one video per prompt request for optimal results
  - If combining text and a single video, place the text prompt _after_ the video part in the `contents` array
  - Be aware that fast action sequences might lose detail due to the 1 FPS sampling rate. Consider slowing down such clips if necessary.

## What's next

- [System instructions](https://ai.google.dev/gemini-api/docs/system-instructions): System instructions let you steer the behavior of the model based on your specific needs and use cases.
- [Files API](https://ai.google.dev/gemini-api/docs/files): Learn more about uploading and managing files for use with Gemini.
- [File prompting strategies](https://ai.google.dev/gemini-api/docs/file-prompting-strategies): The Gemini API supports prompting with text, image, audio, and video data.
- [Safety guidance](https://ai.google.dev/gemini-api/docs/safety-guidance): Sometimes generative AI models produce unexpected outputs, such as outputs that are inaccurate, biased, or offensive. Post-processing and human evaluation are essential to limit the risk of harm from such outputs.