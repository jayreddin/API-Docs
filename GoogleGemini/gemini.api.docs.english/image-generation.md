# Generate images

The Gemini API supports image generation using [Gemini 2.0 Flash Experimental](#gemini) and using [Imagen 3](#imagen). This guide helps you get started with both models.

For image prompting guidance, check out the [Imagen prompt guide](#imagen-prompt-guide) section.

### Before you begin

Before calling the Gemini API, ensure you have [your SDK of choice](https://ai.google.dev/gemini-api/docs/downloads) installed, and a [Gemini API key](https://ai.google.dev/gemini-api/docs/api-key) configured and ready to use.

## Generate images using Gemini 

Gemini 2.0 Flash Experimental supports the ability to output text and inline images. This lets you use Gemini to conversationally edit images or generate outputs with interwoven text (for example, generating a blog post with text and images in a single turn). All generated images include a [SynthID watermark](https://ai.google.dev/responsible/docs/safeguards/synthid), and images in Google AI Studio include a visible watermark as well.

The following example shows how to use Gemini 2.0 to generate text-and-image output:

```python
from google import genai
from google.genai import types
from PIL import Image
from io import BytesIO
import base64

client = genai.Client()

contents = ('Hi, can you create a 3d rendered image of a pig '
            'with wings and a top hat flying over a happy '
            'futuristic scifi city with lots of greenery?')

response = client.models.generate_content(
    model="gemini-2.0-flash-exp-image-generation",
    contents=contents,
    config=types.GenerateContentConfig(
      response_modalities=['TEXT', 'IMAGE']
    )
)

for part in response.candidates[0].content.parts:
  if part.text is not None:
    print(part.text)
  elif part.inline_data is not None:
    image = Image.open(BytesIO((part.inline_data.data)))
    image.save('gemini-native-image.png')
    image.show()
```

Depending on the prompt and context, Gemini will generate content in different modes (text to image, text to image and text, etc.). Here are some examples:

- Text to image 
  - **Example prompt:** "Generate an image of the Eiffel tower with fireworks in the background."
- Text to image(s) and text (interleaved)
  - **Example prompt:** "Generate an illustrated recipe for a paella."
- Image(s) and text to image(s) and text (interleaved)
  - **Example prompt:** (With an image of a furnished room) "What other color sofas would work in my space? can you update the image?"
- Image editing (text and image to image)
  - **Example prompt:** "Edit this image to make it look like a cartoon"
  - **Example prompt:** [image of a cat] + [image of a pillow] + "Create a cross stitch of my cat on this pillow."
- Multi-turn image editing (chat)
  - **Example prompts:** [upload an image of a blue car.] "Turn this car into a convertible." "Now change the color to yellow."

### Image editing with Gemini

To perform image editing, add an image as input. The following example demonstrates uploading base64 encoded images. For multiple images and larger payloads, check the [image input](https://ai.google.dev/gemini-api/docs/vision#image-input) section.

```python
from google import genai
from google.genai import types
from PIL import Image
from io import BytesIO

import PIL.Image

image = PIL.Image.open('/path/to/image.png')

client = genai.Client()

text_input = ('Hi, This is a picture of me.'
            'Can you add a llama next to me?',)

response = client.models.generate_content(
    model="gemini-2.0-flash-exp-image-generation",
    contents=[text_input, image],
    config=types.GenerateContentConfig(
      response_modalities=['TEXT', 'IMAGE']
    )
)

for part in response.candidates[0].content.parts:
  if part.text is not None:
    print(part.text)
  elif part.inline_data is not None:
    image = Image.open(BytesIO(part.inline_data.data))
    image.show()
```

### Limitations

- For best performance, use the following languages: EN, es-MX, ja-JP, zh-CN, hi-IN.
- Image generation does not support audio or video inputs.
- Image generation may not always trigger:
  - The model may output text only. Try asking for image outputs explicitly (e.g. "generate an image", "provide images as you go along", "update the image").
  - The model may stop generating partway through. Try again or try a different prompt.
- When generating text for an image, Gemini works best if you first generate the text and then ask for an image with the text.

## Choose a model

Which model should you use to generate images? It depends on your use case.

Gemini 2.0 is best for producing contextually relevant images, blending text + images, incorporating world knowledge, and reasoning about images. You can use it to create accurate, contextually relevant visuals embedded in long text sequences. You can also edit images conversationally, using natural language, while maintaining context throughout the conversation.

If image quality is your top priority, then Imagen 3 is a better choice. Imagen 3 excels at photorealism, artistic detail, and specific artistic styles like impressionism or anime. Imagen 3 is also a good choice for specialized image editing tasks like updating product backgrounds, upscaling images, and infusing branding and style into visuals. You can use Imagen 3 to create logos or other branded product designs.

## Generate images using Imagen 3

The Gemini API provides access to [Imagen 3](https://deepmind.google/technologies/imagen-3/), Google's highest quality text-to-image model, featuring a number of new and improved capabilities. Imagen 3 can do the following:

- Generate images with better detail, richer lighting, and fewer distracting artifacts than previous models
- Understand prompts written in natural language  
- Generate images in a wide range of formats and styles
- Render text more effectively than previous models

```python
from google import genai
from google.genai import types
from PIL import Image
from io import BytesIO

client = genai.Client(api_key='GEMINI_API_KEY')

response = client.models.generate_images(
    model='imagen-3.0-generate-002',
    prompt='Robot holding a red skateboard',
    config=types.GenerateImagesConfig(
        number_of_images= 4,
    )
)
for generated_image in response.generated_images:
  image = Image.open(BytesIO(generated_image.image.image_bytes))
  image.show()
```

### Imagen model parameters

(Naming conventions vary by programming language.)

- `numberOfImages`: The number of images to generate, from 1 to 4 (inclusive). The default is 4.
- `aspectRatio`: Changes the aspect ratio of the generated image. Supported values are `"1:1"`, `"3:4"`, `"4:3"`, `"9:16"`, and `"16:9"`. The default is `"1:1"`.
- `personGeneration`: Allow the model to generate images of people. The following values are supported:
  - `"DONT_ALLOW"`: Block generation of images of people.
  - `"ALLOW_ADULT"`: Generate images of adults, but not children. This is the default.

## Imagen prompt guide

This section shows you how modifying a text-to-image prompt can produce different results, along with examples of images you can create.

### Prompt writing basics 

A good prompt is descriptive and clear, and makes use of meaningful keywords and modifiers. Start by thinking of your **subject**, **context**, and **style**.

1. **Subject**: The first thing to think about with any prompt is the subject: the object, person, animal, or scenery you want an image of.

2. **Context and background:** Just as important is the background or context in which the subject will be placed. Try placing your subject in a variety of backgrounds. For example, a studio with a white background, outdoors, or indoor environments.

3. **Style:** Finally, add the style of image you want. Styles can be general (painting, photograph, sketches) or very specific (pastel painting, charcoal drawing, isometric 3D). You can also combine styles.

After you write a first version of your prompt, refine your prompt by adding more details until you get to the image that you want. Iteration is important. Start by establishing your core idea, and then refine and expand upon that core idea until the generated image is close to your vision.

Additional advice for Imagen prompt writing:

- **Use descriptive language**: Employ detailed adjectives and adverbs to paint a clear picture for Imagen 3.
- **Provide context**: If necessary, include background information to aid the AI's understanding.
- **Reference specific artists or styles**: If you have a particular aesthetic in mind, referencing specific artists or art movements can be helpful.
- **Use prompt engineering tools**: Consider exploring prompt engineering tools or resources to help you refine your prompts and achieve optimal results.
- **Enhancing the facial details in your personal and group images**:
  - Specify facial details as a focus of the photo (for example, use the word "portrait" in the prompt).

### Generate text in images

Imagen can add text into images, opening up more creative image generation possibilities. Use the following guidance to get the most out of this feature:

- **Iterate with confidence**: You might have to regenerate images until you achieve the look you want. Imagen's text integration is still evolving, and sometimes multiple attempts yield the best results.
- **Keep it short**: Limit text to 25 characters or less for optimal generation.
- **Multiple phrases**: Experiment with two or three distinct phrases to provide additional information. Avoid exceeding three phrases for cleaner compositions.
- **Guide Placement**: While Imagen can attempt to position text as directed, expect occasional variations. This feature is continually improving.
- **Inspire font style**: Specify a general font style to subtly influence Imagen's choices. Don't rely on precise font replication, but expect creative interpretations.
- **Font size**: Specify a font size or a general indication of size (for example, small, medium, large) to influence the font size generation.

### Photography modifiers

In the following examples, you can see several photography-specific modifiers and parameters. You can combine multiple modifiers for more precise control.

1. **Camera Proximity** - Close up, taken from far away

2. **Camera Position** - aerial, from below

3. **Lighting** - natural, dramatic, warm, cold

4. **Camera Settings** - motion blur, soft focus, bokeh, portrait

5. **Lens types** - 35mm, 50mm, fisheye, wide angle, macro

6. **Film types** - black and white, polaroid

### Photorealistic images

Different versions of the image generation model might offer a mix of artistic and photorealistic output. Use the following wording in prompts to generate more photorealistic output, based on the subject you want to generate.

| Use case | Lens type | Focal lengths | Additional details |
| --- | --- | --- | --- |
| People (portraits) | Prime, zoom | 24-35mm | black and white film, Film noir, Depth of field, duotone (mention two colors) |
| Food, insects, plants (objects, still life) | Macro | 60-105mm | High detail, precise focusing, controlled lighting |
| Sports, wildlife (motion) | Telephoto zoom | 100-400mm | Fast shutter speed, Action or movement tracking |
| Astronomical, landscape (wide-angle) | Wide-angle | 10-24mm | Long exposure times, sharp focus, long exposure, smooth water or clouds |

## What's next

- Check out the [Veo guide](https://ai.google.dev/gemini-api/docs/video) to learn how to generate videos with the Gemini API.
- To learn more about Gemini 2.0 models, see [Gemini models](https://ai.google.dev/gemini-api/docs/models/gemini) and [Experimental models](https://ai.google.dev/gemini-api/docs/models/experimental-models).