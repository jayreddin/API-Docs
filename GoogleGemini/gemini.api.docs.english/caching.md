[Skip to main content](https://ai.google.dev/gemini-api/docs/caching?lang=python#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/caching?lang=python)
- [Deutsch](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/caching?lang=python&hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fcaching%3Flang%3Dpython&prompt=select_account)

- On this page
- [When to use context caching](https://ai.google.dev/gemini-api/docs/caching?lang=python#when-to-use-caching)
- [How to use context caching](https://ai.google.dev/gemini-api/docs/caching?lang=python#how-to-use)
  - [Generate content using a cache](https://ai.google.dev/gemini-api/docs/caching?lang=python#generate-content)
  - [List caches](https://ai.google.dev/gemini-api/docs/caching?lang=python#list-caches)
  - [Update a cache](https://ai.google.dev/gemini-api/docs/caching?lang=python#update-cache)
  - [Delete a cache](https://ai.google.dev/gemini-api/docs/caching?lang=python#delete-cache)
- [How caching reduces costs](https://ai.google.dev/gemini-api/docs/caching?lang=python#cost-efficiency)
- [Additional considerations](https://ai.google.dev/gemini-api/docs/caching?lang=python#considerations)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# Context caching

- On this page
- [When to use context caching](https://ai.google.dev/gemini-api/docs/caching?lang=python#when-to-use-caching)
- [How to use context caching](https://ai.google.dev/gemini-api/docs/caching?lang=python#how-to-use)
  - [Generate content using a cache](https://ai.google.dev/gemini-api/docs/caching?lang=python#generate-content)
  - [List caches](https://ai.google.dev/gemini-api/docs/caching?lang=python#list-caches)
  - [Update a cache](https://ai.google.dev/gemini-api/docs/caching?lang=python#update-cache)
  - [Delete a cache](https://ai.google.dev/gemini-api/docs/caching?lang=python#delete-cache)
- [How caching reduces costs](https://ai.google.dev/gemini-api/docs/caching?lang=python#cost-efficiency)
- [Additional considerations](https://ai.google.dev/gemini-api/docs/caching?lang=python#considerations)

PythonJavaScriptGoREST

In a typical AI workflow, you might pass the same input tokens over and over to
a model. Using the Gemini API context caching feature, you can pass some content
to the model once, cache the input tokens, and then refer to the cached tokens
for subsequent requests. At certain volumes, using cached tokens is lower cost
than passing in the same corpus of tokens repeatedly.

When you cache a set of tokens, you can choose how long you want the cache to
exist before the tokens are automatically deleted. This caching duration is
called the _time to live_ (TTL). If not set, the TTL defaults to 1 hour. The
cost for caching depends on the input token size and how long you want the
tokens to persist.

Context caching varies from [model to model](https://ai.google.dev/gemini-api/docs/models).

## When to use context caching

Context caching is particularly well suited to scenarios where a substantial
initial context is referenced repeatedly by shorter requests. Consider using
context caching for use cases such as:

- Chatbots with extensive [system instructions](https://ai.google.dev/gemini-api/docs/system-instructions)
- Repetitive analysis of lengthy video files
- Recurring queries against large document sets
- Frequent code repository analysis or bug fixing

## How to use context caching

This section assumes that you've installed a Gemini SDK (or have curl installed)
and that you've configured an API key, as shown in the
[quickstart](https://ai.google.dev/gemini-api/docs/quickstart).

### Generate content using a cache

The following example shows how to generate content using a cached system
instruction and video file.

[Videos](https://ai.google.dev/gemini-api/docs/caching?lang=python#videos)[PDFs](https://ai.google.dev/gemini-api/docs/caching?lang=python#pdfs)More

```
import os
import pathlib
import requests
import time

from google import genai
from google.genai import types

client = genai.Client()

# Download video file
url = 'https://storage.googleapis.com/generativeai-downloads/data/SherlockJr._10min.mp4'
path_to_video_file = pathlib.Path('SherlockJr._10min.mp4')
if not path_to_video_file.exists():
  with path_to_video_file.open('wb') as wf:
    response = requests.get(url, stream=True)
    for chunk in response.iter_content(chunk_size=32768):
      wf.write(chunk)

# Upload the video using the Files API
video_file = client.files.upload(file=path_to_video_file)

# Wait for the file to finish processing
while video_file.state.name == 'PROCESSING':
  print('Waiting for video to be processed.')
  time.sleep(2)
  video_file = client.files.get(name=video_file.name)

print(f'Video processing complete: {video_file.uri}')

# You must use an explicit version suffix: "-flash-001", not just "-flash".
model='models/gemini-2.0-flash-001'

# Create a cache with a 5 minute TTL
cache = client.caches.create(
    model=model,
    config=types.CreateCachedContentConfig(
      display_name='sherlock jr movie', # used to identify the cache
      system_instruction=(
          'You are an expert video analyzer, and your job is to answer '
          'the user\'s query based on the video file you have access to.'
      ),
      contents=[video_file],
      ttl="300s",
  )
)

# Construct a GenerativeModel which uses the created cache.
response = client.models.generate_content(
  model = model,
  contents= (
    'Introduce different characters in the movie by describing '
    'their personality, looks, and names. Also list the timestamps '
    'they were introduced for the first time.'),
  config=types.GenerateContentConfig(cached_content=cache.name)
)

print(response.usage_metadata)

# The output should look something like this:
#
# prompt_token_count: 696219
# cached_content_token_count: 696190
# candidates_token_count: 214
# total_token_count: 696433

print(response.text)

```

```
from google import genai
from google.genai import types
import io
import httpx

client = genai.Client()

long_context_pdf_path = "https://www.nasa.gov/wp-content/uploads/static/history/alsj/a17/A17_FlightPlan.pdf"

# Retrieve and upload the PDF using the File API
doc_io = io.BytesIO(httpx.get(long_context_pdf_path).content)

document = client.files.upload(
  file=doc_io,
  config=dict(mime_type='application/pdf')
)

model_name = "gemini-2.0-flash-001"
system_instruction = "You are an expert analyzing transcripts."

# Create a cached content object
cache = client.caches.create(
    model=model_name,
    config=types.CreateCachedContentConfig(
      system_instruction=system_instruction,
      contents=[document],
    )
)

# Display the cache details
print(f'{cache=}')

# Generate content using the cached prompt and document
response = client.models.generate_content(
  model=model_name,
  contents="Please summarize this transcript",
  config=types.GenerateContentConfig(
    cached_content=cache.name
  ))

# (Optional) Print usage metadata for insights into the API call
print(f'{response.usage_metadata=}')

# Print the generated text
print('\n\n', response.text)

```

### List caches

It's not possible to retrieve or view cached content, but you can retrieve
cache metadata ( `name`, `model`, `display_name`, `usage_metadata`,
`create_time`, `update_time`, and `expire_time`).

To list metadata for all uploaded caches, use `CachedContent.list()`:

```
for cache in client.caches.list():
  print(cache)

```

To fetch the metadata for one cache object, if you know its name, use `get`:

```
client.caches.get(name=name)

```

### Update a cache

You can set a new `ttl` or `expire_time` for a cache. Changing anything else
about the cache isn't supported.

The following example shows how to update the `ttl` of a cache using
`client.caches.update()`.

```
from google import genai
from google.genai import types

client.caches.update(
  name = cache.name,
  config  = types.UpdateCachedContentConfig(
      ttl='300s'
  )
)

```

To set the expiry time, it will accepts either a `datetime` object
or an ISO-formatted datetime string ( `dt.isoformat()`, like
`2025-01-27T16:02:36.473528+00:00`). Your time must include a time zone
( `datetime.utcnow()` doesn't attach a time zone,
`datetime.now(datetime.timezone.utc)` does attach a time zone).

```
from google import genai
from google.genai import types
import datetime

# You must use a time zone-aware time.
in10min = datetime.datetime.now(datetime.timezone.utc) + datetime.timedelta(minutes=10)

client.caches.update(
  name = cache.name,
  config  = types.UpdateCachedContentConfig(
      expire_time=in10min
  )
)

```

### Delete a cache

The caching service provides a delete operation for manually removing content
from the cache. The following example shows how to delete a cache:

```
client.caches.delete(cache.name)

```

## How caching reduces costs

Context caching is a paid feature designed to reduce overall operational costs.
Billing is based on the following factors:

1. **Cache token count:** The number of input tokens cached, billed at a
reduced rate when included in subsequent prompts.
2. **Storage duration:** The amount of time cached tokens are stored (TTL),
billed based on the TTL duration of cached token count. There are no minimum
or maximum bounds on the TTL.
3. **Other factors:** Other charges apply, such as for non-cached input tokens
and output tokens.

For up-to-date pricing details, refer to the Gemini API [pricing\\
page](https://ai.google.dev/pricing). To learn how to count tokens, see the [Token\\
guide](https://ai.google.dev/gemini-api/docs/tokens).

## Additional considerations

Keep the following considerations in mind when using context caching:

- The _minimum_ input token count for context caching is 4,096, and the
_maximum_ is the same as the maximum for the given model. (For more on
counting tokens, see the [Token guide](https://ai.google.dev/gemini-api/docs/tokens)).
- The model doesn't make any distinction between cached tokens and regular
input tokens. Cached content is a prefix to the prompt.
- There are no special rate or usage limits on context caching; the standard
rate limits for `GenerateContent` apply, and token limits include cached
tokens.
- The number of cached tokens is returned in the `usage_metadata` from the
create, get, and list operations of the cache service, and also in
`GenerateContent` when using the cache.

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-04-24 UTC.

The new page has loaded.