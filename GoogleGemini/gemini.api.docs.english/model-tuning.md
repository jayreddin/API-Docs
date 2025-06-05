[Skip to main content](https://ai.google.dev/gemini-api/docs/model-tuning#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/model-tuning)
- [Deutsch](https://ai.google.dev/gemini-api/docs/model-tuning?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/model-tuning?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/model-tuning?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/model-tuning?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/model-tuning?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/model-tuning?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/model-tuning?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/model-tuning?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/model-tuning?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/model-tuning?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/model-tuning?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/model-tuning?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/model-tuning?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/model-tuning?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/model-tuning?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/model-tuning?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/model-tuning?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/model-tuning?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/model-tuning?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/model-tuning?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/model-tuning?hl=ko)

Sign in

- On this page
- [How fine-tuning works](https://ai.google.dev/gemini-api/docs/model-tuning#how-model)
- [Prepare your dataset](https://ai.google.dev/gemini-api/docs/model-tuning#prepare-dataset)
  - [Format](https://ai.google.dev/gemini-api/docs/model-tuning#format)
  - [Limitations](https://ai.google.dev/gemini-api/docs/model-tuning#dataset-limitations)
  - [Training data size](https://ai.google.dev/gemini-api/docs/model-tuning#size-recommendation)
- [Upload your tuning dataset](https://ai.google.dev/gemini-api/docs/model-tuning#upload-tuning)
- [Advanced tuning settings](https://ai.google.dev/gemini-api/docs/model-tuning#advanced-settings)
  - [Recommended configurations](https://ai.google.dev/gemini-api/docs/model-tuning#recommended-configurations)
- [Check the tuning job status](https://ai.google.dev/gemini-api/docs/model-tuning#check-tuning-status)
- [Troubleshoot errors](https://ai.google.dev/gemini-api/docs/model-tuning#troubleshoot-errors)
  - [Authentication](https://ai.google.dev/gemini-api/docs/model-tuning#authentication)
  - [Canceled models](https://ai.google.dev/gemini-api/docs/model-tuning#canceled-models)
- [Limitations of tuned models](https://ai.google.dev/gemini-api/docs/model-tuning#tuned-model-limitations)
- [What's next](https://ai.google.dev/gemini-api/docs/model-tuning#what's-next)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)



 Send feedback



# Fine-tuning with the Gemini API

- On this page
- [How fine-tuning works](https://ai.google.dev/gemini-api/docs/model-tuning#how-model)
- [Prepare your dataset](https://ai.google.dev/gemini-api/docs/model-tuning#prepare-dataset)
  - [Format](https://ai.google.dev/gemini-api/docs/model-tuning#format)
  - [Limitations](https://ai.google.dev/gemini-api/docs/model-tuning#dataset-limitations)
  - [Training data size](https://ai.google.dev/gemini-api/docs/model-tuning#size-recommendation)
- [Upload your tuning dataset](https://ai.google.dev/gemini-api/docs/model-tuning#upload-tuning)
- [Advanced tuning settings](https://ai.google.dev/gemini-api/docs/model-tuning#advanced-settings)
  - [Recommended configurations](https://ai.google.dev/gemini-api/docs/model-tuning#recommended-configurations)
- [Check the tuning job status](https://ai.google.dev/gemini-api/docs/model-tuning#check-tuning-status)
- [Troubleshoot errors](https://ai.google.dev/gemini-api/docs/model-tuning#troubleshoot-errors)
  - [Authentication](https://ai.google.dev/gemini-api/docs/model-tuning#authentication)
  - [Canceled models](https://ai.google.dev/gemini-api/docs/model-tuning#canceled-models)
- [Limitations of tuned models](https://ai.google.dev/gemini-api/docs/model-tuning#tuned-model-limitations)
- [What's next](https://ai.google.dev/gemini-api/docs/model-tuning#what's-next)

Prompt design strategies such as few-shot prompting may not always produce the
results you need. _Fine-tuning_ is a process that can improve your model's
performance on specific tasks or help the model adhere to specific output
requirements when instructions aren't sufficient and you have a set of examples
that demonstrate the outputs you want.

This page provides a conceptual overview of fine-tuning the text model behind
the Gemini API text service. When you're ready to start tuning, try the
[fine-tuning tutorial](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial). If you'd like
a more general introduction to customizing LLMs for specific use cases, check
out
[LLMs: Fine-tuning, distillation, and prompt engineering](https://developers.google.com/machine-learning/crash-course/llm/tuning)
in the
[Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course/).

## How fine-tuning works

The goal of fine-tuning is to further improve the performance of the model for
your specific task. Fine-tuning works by providing the model with a training
dataset containing many examples of the task. For niche tasks, you can get
significant improvements in model performance by tuning the model on a modest
number of examples. This kind of model tuning is sometimes referred to as
_supervised fine-tuning_, to distinguish it from other kinds of fine-tuning.

Your training data should be structured as examples with prompt inputs and
expected response outputs. You can also tune models using example data directly
in Google AI Studio. The goal is to teach the model to mimic the wanted behavior
or task, by giving it many examples illustrating that behavior or task.

When you run a tuning job, the model learns additional parameters that help it
encode the necessary information to perform the wanted task or learn the wanted
behavior. These parameters can then be used at inference time. The output of the
tuning job is a new model, which is effectively a combination of the newly
learned parameters and the original model.

## Prepare your dataset

Before you can start fine-tuning, you need a dataset to tune the model with. For
the best performance, the examples in the dataset should be of high quality,
diverse, and representative of real inputs and outputs.

### Format

The examples included in your dataset should match your expected production
traffic. If your dataset contains specific formatting, keywords, instructions,
or information, the production data should be formatted in the same way and
contain the same instructions.

For example, if the examples in your dataset include a `"question:"` and a
`"context:"`, production traffic should also be formatted to include a
`"question:"` and a `"context:"` in the same order as it appears in the dataset
examples. If you exclude the context, the model can't recognize the pattern,
even if the exact question was in an example in the dataset.

As another example, here's Python training data for an application that
generates the next number in a sequence:

```
training_data = [\
  {"text_input": "1", "output": "2"},\
  {"text_input": "3", "output": "4"},\
  {"text_input": "-3", "output": "-2"},\
  {"text_input": "twenty two", "output": "twenty three"},\
  {"text_input": "two hundred", "output": "two hundred one"},\
  {"text_input": "ninety nine", "output": "one hundred"},\
  {"text_input": "8", "output": "9"},\
  {"text_input": "-98", "output": "-97"},\
  {"text_input": "1,000", "output": "1,001"},\
  {"text_input": "10,100,000", "output": "10,100,001"},\
  {"text_input": "thirteen", "output": "fourteen"},\
  {"text_input": "eighty", "output": "eighty one"},\
  {"text_input": "one", "output": "two"},\
  {"text_input": "three", "output": "four"},\
  {"text_input": "seven", "output": "eight"},\
]

```

Adding a prompt or preamble to each example in your dataset can also help
improve the performance of the tuned model. Note, if a prompt or preamble is
included in your dataset, it should also be included in the prompt to the tuned
model at inference time.

### Limitations

**Note:** Fine-tuning datasets for Gemini 1.5 Flash have the following
limitations:

- The maximum input size per example is 40,000 characters.
- The maximum output size per example is 5,000 characters.

### Training data size

You can fine-tune a model with as little as 20 examples. Additional data
generally improves the quality of the responses. You should target between 100
and 500 examples, depending on your application. The following table shows
recommended dataset sizes for fine-tuning a text model for various common tasks:

| Task | No. of examples in dataset |
| --- | --- |
| Classification | 100+ |
| Summarization | 100-500+ |
| Document search | 100+ |

## Upload your tuning dataset

Data is either passed inline using the API or through files uploaded in Google
AI Studio.

To use the client library, provide the data file in the `createTunedModel` call.
File size limit is 4 MB. See the
[fine-tuning quickstart with Python](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python)
to get started.

To call the REST API using cURL, provide training examples in JSON format to the
`training_data` argument. See the
[tuning quickstart with cURL](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=rest)
to get started.

## Advanced tuning settings

When creating a tuning job, you can specify the following advanced settings:

- **Epochs:** A full training pass over the entire training set such that each
example has been processed once.
- **Batch size:** The set of examples used in one training [iteration](https://developers.google.com/machine-learning/glossary#iteration). The
batch size determines the number of examples in a batch.
- **Learning rate:** A floating-point number that tells the algorithm how
strongly to adjust the model parameters on each iteration. For example, a
learning rate of 0.3 would adjust weights and biases three times more
powerfully than a learning rate of 0.1. High and low learning rates have
their own unique trade-offs and should be adjusted based on your use case.
- **Learning rate multiplier:** The rate multiplier modifies the model's
original learning rate. A value of 1 uses the original learning rate of the
model. Values greater than 1 increase the learning rate and values between 1
and 0 lower the learning rate.

### Recommended configurations

The following table shows the recommended configurations for fine-tuning a
foundation model:

| Hyperparameter | Default value | Recommended adjustments |
| --- | --- | --- |
| Epoch | 5 | If the loss starts to plateau before 5 epochs, use a smaller value.<br>If the loss is converging and doesn't seem to plateau, use a higher value. |
| Batch size | 4 |  |
| Learning rate | 0.001 | Use a smaller value for smaller datasets. |

The loss curve shows how much the model's prediction deviates from the ideal
predictions in the training examples after each epoch. Ideally you want to stop
training at the lowest point in the curve right before it plateaus. For example,
the graph below shows the loss curve plateauing at about epoch 4-6 which means
you can set the `Epoch` parameter to 4 and still get the same performance.

![Line chart showing the loss curve for the model. The line spikes between the first and the second epochs, then sharply declines to almost 0 and levels out after three epochs.](https://ai.google.dev/static/docs/images/loss_curve.png)

## Check the tuning job status

You can check the status of your tuning job in Google AI Studio under the
**My Library** tab or using the `metadata` property of the tuned model in the
Gemini API.

## Troubleshoot errors

This section includes tips on how to resolve errors you may encounter while
creating your tuned model.

### Authentication

Tuning using the API and client library requires authentication. You can
set up authentication using either an API key (recommended) or using OAuth
credentials. For documentation on setting up an API key, see
[Set up API key](https://ai.google.dev/gemini-api/docs/quickstart#set-up-api-key).

If you see a `'PermissionDenied: 403 Request had insufficient authentication
scopes'` error, you may need to set up user authentication using OAuth
credentials. To configure OAuth credentials for Python, visit our
[the OAuth setup tutorial](https://ai.google.dev/gemini-api/docs/oauth).

### Canceled models

You can cancel a fine-tuning job any time before the job is finished. However,
the inference performance of a canceled model is unpredictable, particularly if
the tuning job is canceled early in the training. If you canceled because you
want to stop the training at an earlier epoch, you should create a new tuning
job and set the epoch to a lower value.

## Limitations of tuned models

**Note:** Tuned models have the following limitations:

- The input limit of a tuned Gemini 1.5 Flash model is 40,000 characters.
- JSON mode is not supported with tuned models.
- System instruction is not supported with tuned models.
- Only text input is supported.

## What's next

Get started with the fine-tuning tutorials:

- [Fine-tuning tutorial (Python)](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=python)
- [Fine-tuning tutorial (REST)](https://ai.google.dev/gemini-api/docs/model-tuning/tutorial?lang=rest)



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-04-16 UTC.