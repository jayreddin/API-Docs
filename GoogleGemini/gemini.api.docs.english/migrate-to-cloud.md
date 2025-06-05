[Skip to main content](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/migrate-to-cloud)
- [Deutsch](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/migrate-to-cloud?hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fmigrate-to-cloud&prompt=select_account)

- On this page
- [Migrate from Gemini on Google AI to Vertex AI](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#migrate-gemini)
- [Delete unused API Keys](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#delete-unused-keys)
- [Next steps](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#next-steps)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# Build with Gemini on Google Cloud

- On this page
- [Migrate from Gemini on Google AI to Vertex AI](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#migrate-gemini)
- [Delete unused API Keys](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#delete-unused-keys)
- [Next steps](https://ai.google.dev/gemini-api/docs/migrate-to-cloud#next-steps)

If you are new to Gemini, using the [quickstarts](https://ai.google.dev/gemini-api/docs/quickstart?lang=python)
is the fastest way to get started.

However, as your generative AI solutions mature, you may need a platform for building and
deploying generative AI applications and solutions end to end. Google Cloud provides a
comprehensive ecosystem of tools to enable developers to harness the power of generative AI,
from the initial stages of app development to app deployment, app hosting, and managing complex
data at scale.

Google Cloud's Vertex AI platform offers a suite of MLOps tools that streamline usage, deployment,
and monitoring of AI models for efficiency and reliability. Additionally, integrations with
databases, DevOps tools, logging, monitoring, and IAM provide a holistic approach to managing the
entire generative AI lifecycle.

The following table summarizes the main differences between Google AI and Vertex AI to help you
decide which option is right for your use case:

| **Features** | **Google AI Gemini API** | **Vertex AI Gemini API** |
| --- | --- | --- |
| Gemini models | Gemini 2.0 Flash, Gemini 2.0 Flash-Lite | Gemini 2.0 Flash, Gemini 2.0 Flash-Lite |
| Sign up | Google account | Google Cloud account (with terms agreement and billing) |
| Authentication | API key | Google Cloud service account |
| User interface playground | Google AI Studio | Vertex AI Studio |
| API & SDK | Server and mobile/web client SDKs<br>- Server: Python, Node.js, Go, Dart, ABAP<br>- Mobile/Web client: Android (Kotlin/Java), Swift, Web, Flutter | Server and mobile/web client SDKs<br>- Server: Python, Node.js, Go, Java, ABAP<br>- Mobile/Web client (via<br>   [Vertex AI for Firebase](https://firebase.google.com/docs/vertex-ai)):<br>   Android (Kotlin/Java), Swift, Web, Flutter |
| No-cost usage of API & SDK | Yes,<br> [where applicable](https://ai.google.dev/gemini-api/docs/billing#is-Gemini-free-in-EEA-UK-CH) | $300 Google Cloud credit for new users |
| Quota (requests per minute) | Varies based on model and pricing plan<br> (see [detailed information](https://ai.google.dev/pricing)) | Varies based on model and region<br> (see [detailed information](https://cloud.google.com/vertex-ai/generative-ai/docs/quotas)) |
| Enterprise support | No | Customer encryption key<br> Virtual private cloud<br> Data residency<br> Access transparency<br> Scalable infrastructure for application hosting<br> Databases and data storage |
| MLOps | No | Full MLOps on Vertex AI (examples: model evaluation, Model Monitoring, Model Registry) |

To learn which products, frameworks, and tools are the best match for building
your generative AI application on Google Cloud, see
[Build a generative AI application on Google Cloud](https://cloud.google.com/docs/ai-ml/generative-ai).

## Migrate from Gemini on Google AI to Vertex AI

If your application uses Google AI Gemini APIs, you'll need to migrate to
Google Cloud's Vertex AI Gemini APIs.

When you migrate:

- You can use your existing Google Cloud project
(the same one you used to generate your API key) or you can
[create a new Google Cloud project](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

- Supported regions may differ between Google AI Studio and Vertex AI. See the
list of [supported regions for generative AI on Google Cloud](https://cloud.google.com/vertex-ai/generative-ai/docs/learn/locations-genai).

- Any models you created in Google AI Studio need to be retrained in Vertex AI.


The [Google Gen AI SDK](https://ai.google.dev/gemini-api/docs/sdks) provides a unified interface to
Gemini 2.0 through both the Gemini Developer API and Vertex AI. With a few
exceptions, code that runs on one platform will run on both.

Note that if you want to call the Gemini API directly from a production mobile
or web app, then
[migrate to use the Vertex AI in Firebase client SDKs](https://firebase.google.com/docs/vertex-ai/migrate-to-vertex-ai)
(available for Swift, Android, Web, and Flutter apps). These client SDKs offer
critical security options and other features for production mobile and web
apps.

## Delete unused API Keys

If you no longer need to use your Google AI Gemini API key, follow security best
practices and delete it.

To delete an API key:

1. Open the
[Google Cloud API Credentials](https://console.cloud.google.com/apis/credentials)
page.

2. Find the API key you want to delete and click the **Actions** icon.

3. Select **Delete API key**.

4. In the **Delete credential** modal, select **Delete**.

Deleting an API key takes a few minutes to propagate. After
propagation completes, any traffic using the deleted API key is rejected.


## Next steps

- See the
[Generative AI on Vertex AI overview](https://cloud.google.com/vertex-ai/generative-ai/docs/multimodal/overview)
to learn more about generative AI solutions on Vertex AI.
- Dive deeper into the [Vertex AI Gemini API](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/gemini).

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-04-07 UTC.