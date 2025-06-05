[Skip to main content](https://ai.google.dev/gemini-api/docs/embeddings#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/embeddings)
- [Deutsch](https://ai.google.dev/gemini-api/docs/embeddings?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/embeddings?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/embeddings?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/embeddings?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/embeddings?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/embeddings?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/embeddings?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/embeddings?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/embeddings?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/embeddings?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/embeddings?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/embeddings?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/embeddings?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/embeddings?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/embeddings?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/embeddings?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/embeddings?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/embeddings?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/embeddings?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/embeddings?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/embeddings?hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fembeddings&prompt=select_account)

- On this page
- [What are embeddings?](https://ai.google.dev/gemini-api/docs/embeddings#what-are-embeddings)
- [Generate embeddings](https://ai.google.dev/gemini-api/docs/embeddings#generate-embeddings)
- [Task types](https://ai.google.dev/gemini-api/docs/embeddings#task-types)
  - [Supported task types](https://ai.google.dev/gemini-api/docs/embeddings#supported-task-types)
- [Use cases](https://ai.google.dev/gemini-api/docs/embeddings#use-cases)
- [Embedding models](https://ai.google.dev/gemini-api/docs/embeddings#embeddings-models)
- [What's next](https://ai.google.dev/gemini-api/docs/embeddings#whats-next)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# Embeddings

- On this page
- [What are embeddings?](https://ai.google.dev/gemini-api/docs/embeddings#what-are-embeddings)
- [Generate embeddings](https://ai.google.dev/gemini-api/docs/embeddings#generate-embeddings)
- [Task types](https://ai.google.dev/gemini-api/docs/embeddings#task-types)
  - [Supported task types](https://ai.google.dev/gemini-api/docs/embeddings#supported-task-types)
- [Use cases](https://ai.google.dev/gemini-api/docs/embeddings#use-cases)
- [Embedding models](https://ai.google.dev/gemini-api/docs/embeddings#embeddings-models)
- [What's next](https://ai.google.dev/gemini-api/docs/embeddings#whats-next)

The Gemini API supports several embedding models that generate embeddings for
words, phrases, code, and sentences. The resulting embeddings can then be used
for tasks such as semantic search, text classification, and clustering, among
many others.

## What are embeddings?

Embeddings are numerical representations of text (or other media formats) that
capture relationships between inputs. Text embeddings work by converting text
into arrays of floating point numbers, called _vectors_. These vectors are
designed to capture the meaning of the text. The length of the embedding array
is called the vector's _dimensionality_. A passage of text might be represented
by a vector containing hundreds of dimensions.

Embeddings capture semantic meaning and context, which results in text with
similar meanings having "closer" embeddings. For example, the sentence "I took
my dog to the vet" and "I took my cat to the vet" would have embeddings that are
close to each other in the vector space.

You can use embeddings to compare different texts and understand how they
relate. For example, if the embeddings of the text "cat" and "dog" are close
together you can infer that these words are similar in meaning, context, or
both. This enables a variety of
[common AI use cases](https://ai.google.dev/gemini-api/docs/embeddings#use-cases).

### Before you begin

Before calling the Gemini API, ensure you have [your SDK of choice](https://ai.google.dev/gemini-api/docs/downloads)
installed, and a [Gemini API key](https://ai.google.dev/gemini-api/docs/api-key) configured and ready to use.

## Generate embeddings

Use the `embedContent` method to generate text embeddings:

[Python](https://ai.google.dev/gemini-api/docs/embeddings#python)[JavaScript](https://ai.google.dev/gemini-api/docs/embeddings#javascript)[Go](https://ai.google.dev/gemini-api/docs/embeddings#go)[REST](https://ai.google.dev/gemini-api/docs/embeddings#rest)More

```
from google import genai

client = genai.Client(api_key="GEMINI_API_KEY")

result = client.models.embed_content(
        model="gemini-embedding-exp-03-07",
        contents="What is the meaning of life?")

print(result.embeddings)

```

```
import { GoogleGenAI } from "@google/genai";

async function main() {

    const ai = new GoogleGenAI({ apiKey: "GEMINI_API_KEY" });

    const response = await ai.models.embedContent({
        model: 'gemini-embedding-exp-03-07',
        contents: 'What is the meaning of life?',
    });

    console.log(response.embeddings);
}

main();

```

```
package main

import (
    "context"
    "encoding/json"
    "fmt"
    "log"

    "google.golang.org/genai"
)

func main() {
    ctx := context.Background()
    client, err := genai.NewClient(ctx, &genai.ClientConfig{
        APIKey: "GOOGLE_API_KEY",
        Backend: genai.BackendGeminiAPI,
    })
    if err != nil {
        log.Fatal(err)
    }

    contents := []*genai.Content{
        genai.NewContentFromText("What is the meaning of life?", genai.RoleUser),
    }
    result, err := client.Models.EmbedContent(ctx,
        "gemini-embedding-exp-03-07",
        contents,
        nil,
    )
    if err != nil {
        log.Fatal(err)
    }

    embeddings, err := json.MarshalIndent(result.Embeddings, "", "  ")
    if err != nil {
        log.Fatal(err)
    }
    fmt.Println(string(embeddings))
}

```

```
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-embedding-exp-03-07:embedContent?key=$GEMINI_API_KEY" \
-H 'Content-Type: application/json' \
-d '{"model": "models/gemini-embedding-exp-03-07",
     "content": {
     "parts":[{\
     "text": "What is the meaning of life?"}]}
    }'

```

You can also generate embeddings for multiple chunks at once by passing them in
as a list of strings.

## Task types

When building Retrieval Augmented Generation (RAG) systems, a common design is
to use text embeddings to perform a similarity search. In some cases this can
lead to degraded quality, because questions and their answers are not semantically
similar. For example, a question like "Why is the sky blue?" and its answer
"The scattering of sunlight causes the blue color," have distinctly different
meanings as statements, which means that a RAG system won't automatically recognize
their relation.

Task types enable you to generate optimized embeddings for specific tasks,
saving you time and cost and improving performance.

[Python](https://ai.google.dev/gemini-api/docs/embeddings#python)[JavaScript](https://ai.google.dev/gemini-api/docs/embeddings#javascript)[REST](https://ai.google.dev/gemini-api/docs/embeddings#rest)More

```
from google import genai
from google.genai import types

client = genai.Client(api_key="GEMINI_API_KEY")

result = client.models.embed_content(
        model="gemini-embedding-exp-03-07",
        contents="What is the meaning of life?",
        config=types.EmbedContentConfig(task_type="SEMANTIC_SIMILARITY")
)
print(result.embeddings)

```

```
import { GoogleGenAI } from "@google/genai";

async function main() {

    const ai = new GoogleGenAI({ apiKey: "GEMINI_API_KEY" });

    const response = await ai.models.embedContent({
        model: 'gemini-embedding-exp-03-07',
        contents: 'What is the meaning of life?',
        config: {
            taskType: "SEMANTIC_SIMILARITY",
        }
    });

    console.log(response.embeddings);
}

main();

```

```
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-embedding-exp-03-07:embedContent?key=$GEMINI_API_KEY" \
-H 'Content-Type: application/json' \
-d '{"model": "models/gemini-embedding-exp-03-07",
     "content": {
     "parts":[{\
     "text": "What is the meaning of life?"}]},
     "taskType": "SEMANTIC_SIMILARITY"
    }'

```

### Supported task types

| Task type | Description |
| --- | --- |
| `SEMANTIC_SIMILARITY` | Used to generate embeddings that are optimized to assess text similarity. |
| `CLASSIFICATION` | Used to generate embeddings that are optimized to classify texts according to preset labels. |
| `CLUSTERING` | Used to generate embeddings that are optimized to cluster texts based on their similarities. |
| `RETRIEVAL_DOCUMENT`, `RETRIEVAL_QUERY`, `QUESTION_ANSWERING`, and `FACT_VERIFICATION` | Used to generate embeddings that are optimized for document search or information retrieval. |
| `CODE_RETRIEVAL_QUERY` | Used to retrieve a code block based on a natural language query, such as sort an array or reverse a linked list. Embeddings of the code blocks are computed using `RETRIEVAL_DOCUMENT`. |

## Use cases

Text embeddings are used in a variety of common AI use cases, such as:

- **Information retrieval:** You can use embeddings to retrieve semantically
similar text given a piece of input text.

[Document search tutorialtask](https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/tutorials/document_search.ipynb)

- **Clustering:** Comparing groups of embeddings can help identify hidden trends.

[Embedding clustering tutorialbubble\_chart](https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/tutorials/clustering_with_embeddings.ipynb)

- **Vector database:** As you take different embedding use cases to production,
it is common to store embeddings in a vector database.

[Vector database tutorialbolt](https://github.com/google-gemini/cookbook/blob/main/examples/chromadb/Vectordb_with_chroma.ipynb)

- **Classification:** You can train a model using embeddings to classify
documents into categories.

[Classification tutorialtoken](https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/tutorials/text_classifier_embeddings.ipynb)


## Embedding models

The Gemini API offers three models that generate text embeddings:

- [gemini-embedding-exp-03-07](https://ai.google.dev/gemini-api/docs/models#gemini-embedding)
- [text-embedding-004](https://ai.google.dev/gemini-api/docs/models/gemini#text-embedding)
- [embedding-001](https://ai.google.dev/gemini-api/docs/models/gemini#embedding)

## What's next

Check out the
[embeddings quickstart notebook](https://github.com/google-gemini/cookbook/blob/main/quickstarts/Embeddings.ipynb).

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-04-28 UTC.