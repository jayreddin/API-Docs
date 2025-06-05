[Skip to main content](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python)
- [Deutsch](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python&hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fmodel-tuning%2Ftutorial%3Flang%3Dpython&prompt=select_account)

- On this page
- [Limitations](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#limitations)
  - [Fine-tuning datasets](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#fine-tuning-datasets)
  - [Tuned models](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#tuned-models)
- [List tuned models](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#list-tuned-models)
- [Create a tuned model](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#create-tuned-model)
- [Try the model](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#try-model)
- [Not implemented](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#not-implemented)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# Fine-tuning tutorial

- On this page
- [Limitations](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#limitations)
  - [Fine-tuning datasets](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#fine-tuning-datasets)
  - [Tuned models](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#tuned-models)
- [List tuned models](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#list-tuned-models)
- [Create a tuned model](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#create-tuned-model)
- [Try the model](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#try-model)
- [Not implemented](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python#not-implemented)

PythonREST

This tutorial will help you get started with the Gemini API tuning service
using either the Python SDK or the REST API using
[curl](https://curl.se/). The examples show how to tune the text model behind
the Gemini API text generation service.

### Before you begin

Before calling the Gemini API, ensure you have [your SDK of choice](https://ai.google.dev/gemini-api/docs/downloads)
installed, and a [Gemini API key](https://ai.google.dev/gemini-api/docs/api-key) configured and ready to use.

|     |     |     |
| --- | --- | --- |
| [![](https://ai.google.dev/static/site-assets/images/docs/notebook-site-button.png)View on ai.google.dev](https://ai.google.dev/gemini-api/docs/model-tuning/python) | [![](https://www.tensorflow.org/images/colab_logo_32px.png)Try a Colab notebook](https://colab.research.google.com/github/google/generative-ai-docs/blob/main/site/en/gemini-api/docs/model-tuning/python.ipynb) | [![](https://www.tensorflow.org/images/GitHub-Mark-32px.png)View notebook on GitHub](https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/docs/model-tuning/python.ipynb) |

## Limitations

Before tuning a model, you should be aware of the following limitations:

### Fine-tuning datasets

Fine-tuning datasets for Gemini 1.5 Flash have the following limitations:

- The maximum input size per example is 40,000 characters.
- The maximum output size per example is 5,000 characters.
- Only input-output pair examples are supported. Chat-style multi-turn
conversations are not supported.

### Tuned models

Tuned models have the following limitations:

- The input limit of a tuned Gemini 1.5 Flash model is 40,000 characters.
- JSON mode is not supported with tuned models.
- Only text input is supported.

## List tuned models

You can check your existing tuned models with the
[`tunedModels.list`](https://ai.google.dev/api/tuning#method:-tunedmodels.list) method.

```
from google import genai
from google.genai import types
client = genai.Client() # Get the key from the GOOGLE_API_KEY env variable

for model_info in client.models.list():
    print(model_info.name)

```

## Create a tuned model

To create a tuned model, you need to pass your [dataset](https://ai.google.dev/api/tuning#Dataset) to
the model in the [`tunedModels.create`](https://ai.google.dev/api/tuning#method:-tunedmodels.create)
method.

For this example, you will tune a model to generate the next number in the
sequence. For example, if the input is `1`, the model should output `2`. If the
input is `one hundred`, the output should be `one hundred one`.

```
# create tuning model
training_dataset =  [\
    ["1", "2"],\
    ["3", "4"],\
    ["-3", "-2"],\
    ["twenty two", "twenty three"],\
    ["two hundred", "two hundred one"],\
    ["ninety nine", "one hundred"],\
    ["8", "9"],\
    ["-98", "-97"],\
    ["1,000", "1,001"],\
    ["10,100,000", "10,100,001"],\
    ["thirteen", "fourteen"],\
    ["eighty", "eighty one"],\
    ["one", "two"],\
    ["three", "four"],\
    ["seven", "eight"],\
]
training_dataset=types.TuningDataset(
        examples=[\
            types.TuningExample(\
                text_input=i,\
                output=o,\
            )\
            for i,o in training_dataset\
        ],
    )
tuning_job = client.tunings.tune(
    base_model='models/gemini-1.5-flash-001-tuning',
    training_dataset=training_dataset,
    config=types.CreateTuningJobConfig(
        epoch_count= 5,
        batch_size=4,
        learning_rate=0.001,
        tuned_model_display_name="test tuned model"
    )
)

# generate content with the tuned model
response = client.models.generate_content(
    model=tuning_job.tuned_model.model,
    contents='III',
)

print(response.text)

```

The optimal values for epoch count, batch size, and learning rate are dependent
on your dataset and other constraints of your use case. To learn more about
these values, see
[Advanced tuning settings](https://ai.google.dev/gemini-api/docs/model-tuning#advanced-settings) and
[Hyperparameters](https://ai.google.dev/api/tuning#Hyperparameters).

## Try the model

You can use the
[`tunedModels.generateContent`](https://ai.google.dev/api/tuning#method:-tunedmodels.generatecontent)
method and specify the name of the tuned model to test its performance.

```
response = client.models.generate_content(
    model=tuning_job.tuned_model.model,
    contents='III'
)

```

## Not implemented

Some features (progress reporting, updating the description, and
deleting tuned models) has not yet been implemented in the new SDK.

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-04-28 UTC.

The new page has loaded.