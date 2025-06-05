[Skip to main content](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart)
- [Deutsch](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart?hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fai-studio-quickstart&prompt=select_account)

- On this page
- [Prompts and model tuning](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#prompts-and)
- [Chat prompt example: Build a custom chat application](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#chat_example)
  - [Step 1 - Create a chat prompt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-1-chat)
  - [Step 2 - Teach your bot to chat better](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-2-chat)
  - [Step 3 - Next steps](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-3-chat)
- [Structured prompt example: Build a product copy generator](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#structured_example)
  - [Step 1 - Create a structured prompt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step_1_sp)
  - [Step 2 - Add examples](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-2-structured)
  - [Step 3 - Test your prompt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-3-structured)
  - [Step 4 - Next steps](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-4-structured)
- [Further reading](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#further-reading)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# Google AI Studio quickstart

- On this page
- [Prompts and model tuning](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#prompts-and)
- [Chat prompt example: Build a custom chat application](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#chat_example)
  - [Step 1 - Create a chat prompt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-1-chat)
  - [Step 2 - Teach your bot to chat better](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-2-chat)
  - [Step 3 - Next steps](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-3-chat)
- [Structured prompt example: Build a product copy generator](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#structured_example)
  - [Step 1 - Create a structured prompt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step_1_sp)
  - [Step 2 - Add examples](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-2-structured)
  - [Step 3 - Test your prompt](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-3-structured)
  - [Step 4 - Next steps](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#step-4-structured)
- [Further reading](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#further-reading)

[Google AI Studio](https://aistudio.google.com/) lets you quickly try out
models and experiment with different prompts. When you're ready to build, you
can select "Get code" and your preferred programming language to
use the [Gemini API](https://ai.google.dev/gemini-api/docs/quickstart).

## Prompts and model tuning

Google AI Studio provides several interfaces for prompts that are designed for
different use cases:

- **Chat prompts:** Use chat prompts to build conversational experiences. This
prompting technique allows for multiple input and response turns to generate
output. You can learn more with our [chat prompt example\\
below](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#chat_example).
- **Structured prompts:** This prompting technique lets you guide model output
by providing a set of example requests and replies. Use this approach when
you need more control over the structure of model output. You can learn more
with our [structured prompt example below](https://ai.google.dev/gemini-api/docs/ai-studio-quickstart#structured_example).

Google AI Studio also lets you to change the behavior of a model, using a
technique called _tuning_:

- **Tuned model:** Use this advanced technique to improve a model's responses
for a specific task by providing more examples. Visit our documentation on
[fine-tuning a model](https://ai.google.dev/gemini-api/docs/model-tuning) to learn more.

## Chat prompt example: Build a custom chat application

If you've used a general-purpose chatbot like
[Gemini](https://gemini.google.com/), you've experienced first-hand how powerful
generative AI models can be for open-ended dialog. While these general-purpose
chatbots are useful, often they need to be tailored for particular use cases.
For example, maybe you want to build a customer service chatbot that only
supports conversations that talk about a company's product. You might want to
build a chatbot that speaks with a particular tone or style: a bot that cracks
lots of jokes, rhymes like a poet, or uses lots of emoji in its answers.

This example shows you how to use Google AI Studio to build a friendly chatbot
that communicates as if it is an alien living on one of Jupiter's moons, Europa.

### Step 1 - Create a chat prompt

To build a chatbot, you need to provide examples of interactions between a user
and the chatbot to guide the model to provide the responses you're looking for.

To create a chat prompt:

1. Open [Google AI Studio](https://aistudio.google.com/).

2. Click **Create new prompt**..

3. Click the expand\_more expander arrow to
expand the **System Instructions** section. Paste the following into the
text input field:








```
You are an alien that lives on Europa, one of Jupiter's moons.

```


After you've added the system instructions, start testing your application by
chatting with the model.

To test the chatbot behavior:

1. In the text input boxed labeled **Type something**, type in a question or
observation that a user might make. For example:

_User_:








```
What's the weather like?

```

2. Click the **Run** button or press `Enter` to get a response from
the chatbot. This response may be something like the following:

_Model_:








```
As always, it is a frigid day on Europa. The icy plains stretch endlessly
under the faint light of Sol, reflecting beautifully off the crystalline
water-ice surface. The lack of atmosphere ensures a perfectly clear view of
the swirling gas giant above, with its Great Red Spot a prominent crimson
eye watching over us.

```


### Step 2 - Teach your bot to chat better

By providing a single instruction, you were able to build a basic Europa alien
chatbot. However, a single instruction is usually not enough to ensure
consistency and quality in the model's responses. Without more specific
instructions, the model's response to a question about the weather tends to be
very long, and sounds like it comes out of a textbook rather than from a
friendly alien.

Customize the tone of your chatbot by adding to the system instructions:

1. Start a new chat prompt. System instructions are not modifiable once the
chat session has started.

2. In the **System Instructions** section, change the instructions you already
have to the following:








```
You are Tim, an alien that lives on Europa, one of Jupiter's moons.

Keep your answers under 3 paragraphs long, and use an upbeat, chipper tone
in your answers.

```

3. Re-enter your question ( `What's the weather like?`) and click the **Run**
button or press `Enter`. Now your response should look something
like this:

_Model:_








```
Well, it's a bit nippy today! It's -170 degrees Celsius, but that's pretty
average for Europa. We get a lot of snow, but it's not like the fluffy stuff
you have. It's more like tiny ice pebbles.

If you ever come visit, make sure you pack a warm jacket!

```


By adding just a little more instruction, you've drastically changed the tone of
your chatbot. Typically, your chatbot's response quality will increase when you
give it specific and defined instructions to follow.

You can use this approach to add additional depth to the chatbot. Ask more
questions, edit the answers, and improve the quality of your chatbot. Continue
to add or modify the instructions and test how they change your chatbot's
behavior.

### Step 3 - Next steps

Similar to the other prompt types, once you have your prompt prototyped to your
satisfaction, you can use the **Get code** button to start coding or save your
prompt to work on later and share with others.

## Structured prompt example: Build a product copy generator

Structured prompts in Google AI Studio help you combine instructions with
examples to show the model the kind of output you want, rather than just telling
it what to do. This kind of prompting, called [_few-shot_\\
_prompting_](https://ai.google.dev/gemini-api/docs/models/generative-models#prompt-types), is useful
when you want the model to stick to a consistent output format (i.e. structured
JSON) or when it's difficult to describe in words what you want the model to do
(i.e. write in a particular style). In this section, you'll see how to create
structured prompts in Google AI Studio.

### Step 1 - Create a structured prompt

In this example, you'll create a structured prompt that generates advertising
copy for products. To start, you'll define the structure for the prompt by
creating two columns: a **Product** input column and a **Product copy** output
column.

To create the structured prompt:

1. Open [Google AI Studio](https://aistudio.google.com/).

2. Click **Tune a Model**.

3. Click **Create a Structured prompt**.

4. In the text input box labeled **Optional tone and style instructions for the**
**model**, paste the following:








```
You are a product marketer targeting a Gen Z audience. Create exciting and
fresh advertising copy for products and their simple description. Keep copy
under a few sentences long.

```

5. Replace the default **Input** header text ( `input:`) with `Product:`.

6. Replace the default **Output** header text ( `output:`) with `Product copy:`.


### Step 2 - Add examples

Now that you've named your columns, provide some example rows. These rows should
contain example inputs (product names for this example) and example outputs
(corresponding product descriptions). By providing the model a couple of example
product descriptions, you can guide it to replicate a similar style when
generating its own outputs. You can enter examples manually or import from a
file using the import data menu.

To manually enter examples:

1. In the top examples data table, select the field below the
**Product:** header and type a product description.

2. Select the field below the **Product copy:** header and type marketing copy
for this product.


Here's an example of input and output values for this prompt:

| Product: | Product copy: |
| --- | --- |
| Old-school sneaker | Let's lace up! These kicks bring an iconic look and a one of a kind<br> color palette, while supporting you in style and function like no other<br> shoe before. |
| Supersoft hoodie | Stay cozy and stylish in our new unisex hoodie! Made from 100% cotton,<br> this hoodie is soft and comfortable to wear all day long. The semi-brushed<br> inside will keep you warm on even the coldest days. |

(Optional) To import examples from a file:

1. In the top, right corner of the examples table, click **Actions > Import**
**examples**.

2. In the dialog, select a CSV or Google Sheets file in your Google Drive, or
upload one from your computer.

3. In the import examples dialog, choose which columns to import and which to
leave out. The dialog also lets you specify which data column imports to
which table column in your structured prompt.


### Step 3 - Test your prompt

Once you have the examples that show the model what you want, test your prompt
with new input in the **Test your prompt** table at the bottom.

For example, you could enter something like `Vintage baseball cap` in the input
column, click the
spark **Run** button or press `Enter`, and see what the model outputs.

#### Review how examples are sent to the model

Under the hood, Google AI Studio constructs a prompt by combining the
instructions with the examples you provide. As you add more examples, these get
added to the text sent to the model. Depending on how long your examples are,
you may start hitting the model's token limit. All generative AI models have a
token limit, which is the maximum length of the text they can accept as input.

### Step 4 - Next steps

Once you're happy with your prompt, you can save your project to Google Drive by
clicking the **Save** button, or export it to code by clicking the **Get code**
button.

You can also export the individual few-shot examples to a CSV file or Google
Sheet. Click **Export examples** in the **Action** menu to export your examples.

## Further reading

- If you're ready to move on to code, see the [API\\
quickstarts](https://ai.google.dev/gemini-api/docs/quickstart).
- To learn how to craft better prompts, check out the [Prompt design\\
guidelines](https://ai.google.dev/gemini-api/docs/prompting-intro).

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-02-25 UTC.