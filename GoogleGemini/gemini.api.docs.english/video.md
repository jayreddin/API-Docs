# Generate video using Veo

The Gemini API provides access to [Veo 2](https://deepmind.google/technologies/veo/), Google's most capable video generation model to date. Veo generates videos in a wide range of cinematic and visual styles, capturing prompt nuance to render intricate details consistently across frames.

This guide will help you get started with Veo using the Gemini API.

For video prompting guidance, check out the [Veo prompt guide](#prompt-guide) section.

### Before you begin

Before calling the Gemini API, ensure you have [your SDK of choice](https://ai.google.dev/gemini-api/docs/downloads) installed, and a [Gemini API key](https://ai.google.dev/gemini-api/docs/api-key) configured and ready to use.

To use Veo with the Google Gen AI SDKs, ensure that you have one of the following versions installed:

- [Python](https://pypi.org/project/google-genai/) v1.10.0 or later
- [TypeScript and JavaScript](https://www.npmjs.com/package/@google/genai) v0.8.0 or later
- [Go](https://pkg.go.dev/google.golang.org/genai) v1.0.0 or later

## Generate videos

This section provides code examples for generating videos [using text prompts](#generate-from-text) and [using images](#generate-from-images).

### Generate from text

You can use the following code to generate videos with Veo:

```python
import time
from google import genai
from google.genai import types

client = genai.Client()  # read API key from GOOGLE_API_KEY

operation = client.models.generate_videos(
    model="veo-2.0-generate-001",
    prompt="Panning wide shot of a calico kitten sleeping in the sunshine",
    config=types.GenerateVideosConfig(
        person_generation="dont_allow",  # "dont_allow" or "allow_adult"
        aspect_ratio="16:9",  # "16:9" or "9:16"
    ),
)

while not operation.done:
    time.sleep(20)
    operation = client.operations.get(operation)

for n, generated_video in enumerate(operation.response.generated_videos):
    client.files.download(file=generated_video.video)
    generated_video.video.save(f"video{n}.mp4")  # save the video
```

This code takes about 2-3 minutes to run, though it may take longer if resources are constrained. If you see an error message instead of a video, this means that resources are constrained and your request couldn't be completed. In this case, run the code again.

Generated videos are stored on the server for 2 days, after which they are removed. If you want to save a local copy of your generated video, you must run `result()` and `save()` within 2 days of generation.

### Generate from images 

You can also generate videos using images. First generate an image using [Imagen](https://ai.google.dev/gemini-api/docs/image-generation):

```python
prompt="Panning wide shot of a calico kitten sleeping in the sunshine",

imagen = client.models.generate_images(
    model="imagen-3.0-generate-002",
    prompt=prompt,
    config=types.GenerateImagesConfig(
      aspect_ratio="16:9",
      number_of_images=1
    )
)

imagen.generated_images[0].image
```

Then generate a video using the resulting image as the first frame:

```python
operation = client.models.generate_videos(
    model="veo-2.0-generate-001",
    prompt=prompt,
    image = imagen.generated_images[0].image,
    config=types.GenerateVideosConfig(
      # person_generation is not allowed for image-to-video generation
      aspect_ratio="16:9",  # "16:9" or "9:16"
      number_of_videos=2
    ),
)

# Wait for videos to generate
while not operation.done:
   time.sleep(20)
   operation = client.operations.get(operation)

for n, video in enumerate(operation.response.generated_videos):
    fname = f'with_image_input{n}.mp4'
    print(fname)
    client.files.download(file=video.video)
    video.video.save(fname)
```

## Veo model parameters

- `prompt`: The text prompt for the video. When present, the `image` parameter is optional.
- `image`: The image to use as the first frame for the video. When present, the `prompt` parameter is optional. 
- `negativePrompt`: Text string that describes anything you want to _discourage_ the model from generating
- `aspectRatio`: Changes the aspect ratio of the generated video. Supported values are `"16:9"` and `"9:16"`. The default is `"16:9"`.
- `personGeneration`: Allow the model to generate videos of people. The following values are supported:
  - Text-to-video generation:
    - `"dont_allow"`: Don't allow the inclusion of people or faces.
    - `"allow_adult"`: Generate videos that include adults, but not children.
  - Image-to-video generation: 
    - Not allowed; server will reject the request if parameter is used.
- `numberOfVideos`: Output videos requested, either `1` or `2`.
- `durationSeconds`: Length of each output video in seconds, between `5` and `8`.
- `enhance_prompt`: Enable or disable the prompt rewriter. Enabled by default.

## Specifications

| **Modalities** | - Text-to-video generation<br>- Image-to-video generation |
| **Request latency** | - Min: 11 seconds<br>- Max: 6 minutes (during peak hours) |
| **Variable length generation** | 5-8 seconds |
| **Resolution** | 720p |
| **Frame rate** | 24fps |
| **Aspect ratio** | - 16:9 - landscape<br>- 9:16 - portrait |
| **Input languages (text-to-video)** | English |

Videos created by Veo are watermarked using [SynthID](https://deepmind.google/technologies/synthid/), our tool for watermarking and identifying AI-generated content, and are passed through safety filters and memorization checking processes that help mitigate privacy, copyright and bias risks.

## Things to try

To get the most out of Veo, incorporate video-specific terminology into your prompts. Veo understands a wide range of terms related to:

- **Shot composition:** Specify the framing and number of subjects in the shot (e.g., "single shot," "two shot," "over-the-shoulder shot").
- **Camera positioning and movement:** Control the camera's location and movement using terms like "eye level," "high angle," "worms eye," "dolly shot," "zoom shot," "pan shot," and "tracking shot."
- **Focus and lens effects:** Use terms like "shallow focus," "deep focus," "soft focus," "macro lens," and "wide-angle lens" to achieve specific visual effects.
- **Overall style and subject:** Guide Veo's creative direction by specifying styles like "sci-fi," "romantic comedy," "action movie," or "animation." You can also describe the subjects and backgrounds you want, such as "cityscape," "nature," "vehicles," or "animals."

## Veo prompt guide {#prompt-guide}

This section contains examples of videos you can create using Veo, and shows you how to modify prompts to produce distinct results.

### Safety filters

Veo applies safety filters across Gemini to help ensure that generated videos and uploaded photos don't contain offensive content. Prompts that violate our [terms and guidelines](https://ai.google.dev/gemini-api/docs/usage-policies#abuse-monitoring) are blocked.

### Prompt writing basics

Good prompts are descriptive and clear. To get your generated video as close as possible to what you want, start with identifying your core idea, and then refine your idea by adding keywords and modifiers.

The following elements should be included in your prompt:

- **Subject**: The object, person, animal, or scenery that you want in your video.
- **Context**: The background or context in which the subject is placed.
- **Action**: What the subject is doing (for example, _walking_, _running_, or _turning their head_).
- **Style**: This can be general or very specific. Consider using specific film style keywords, such as _horror film_, _film noir_, or animated styles like _cartoon_ style.
- **Camera motion**: [Optional] What the camera is doing, such as _aerial view_, _eye-level_, _top-down shot_, or _low-angle shot_.
- **Composition**: [Optional] How the shot is framed, such as _wide shot_, _close-up_, or _extreme close-up_.
- **Ambiance**: [Optional] How the color and light contribute to the scene, such as _blue tones_, _night_, or _warm tones_.

#### More tips for writing prompts

- **Use descriptive language**: Use adjectives and adverbs to paint a clear picture for Veo.
- **Provide context**: If necessary, include background information to help your model understand what you want.
- **Reference specific artistic styles**: If you have a particular aesthetic in mind, reference specific artistic styles or art movements.
- **Utilize prompt engineering tools**: Consider exploring prompt engineering tools or resources to help you refine your prompts and achieve optimal results.
- **Enhance facial details**: Specify facial details as a focus of the photo like using the word _portrait_ in the prompt.

### Example prompts and output

#### Icicles
Close up shot (composition) of melting icicles (subject) on a frozen rock wall (context) with cool blue tones (ambiance), zoomed in (camera motion) maintaining close-up detail of water drips (action).

#### Film noir scene
A cinematic close-up shot follows a desperate man in a weathered green trench coat as he dials a rotary phone mounted on a gritty brick wall, bathed in the eerie glow of a green neon sign. The camera dollies in, revealing the tension in his jaw and the desperation etched on his face as he struggles to make the call. The shallow depth of field focuses on his furrowed brow and the black rotary phone, blurring the background into a sea of neon colors and indistinct shadows, creating a sense of urgency and isolation.

### Negative prompts

Negative prompts can be a powerful tool to help specify elements you _don't_ want in the video. Describe what you want to discourage the model from generating after the phrase "Negative prompt". Follow these tips:

- ❌ Don't use instructive language or words like _no_ or _don't_. For example, "No walls" or "don't show walls".
- ✅ Do describe what you don't want to see. For example, "wall, frame", which means that you don't want a wall or a frame in the video.

### Aspect ratios

Gemini Veo video generation supports two aspect ratios:

| **Aspect ratio** | **Description** |
| --- | --- |
| Widescreen (16:9) | The most common aspect ratio for televisions, monitors, and mobile phone screens (landscape). Use this when you want to capture more of the background, like in scenic landscapes. |
| Portrait (9:16) | Rotated widescreen. This aspect ratio has been popularized by short form video applications, such as Youtube shorts. Use this for portraits or tall objects with strong vertical orientations, such as buildings, trees, waterfall, or buildings. |

## What's next

- Gain more experience generating AI videos with the [Veo Colab](https://github.com/google-gemini/cookbook/blob/main/quickstarts/Get_started_Veo.ipynb)
- Check out examples using Veo 2 on the [Google DeepMind site](https://deepmind.google/technologies/veo/)