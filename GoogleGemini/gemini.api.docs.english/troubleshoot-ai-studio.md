[Skip to main content](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio)
- [Deutsch](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio?hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Ftroubleshoot-ai-studio&prompt=select_account)

- On this page
- [Understand 403 Access Restricted errors](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#understand-403-errors)
- [Resolve No Content responses on Google AI Studio](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#resolve-no-content)
- [Check token usage and limits](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#check-token-usage)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# Troubleshoot Google AI Studio

- On this page
- [Understand 403 Access Restricted errors](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#understand-403-errors)
- [Resolve No Content responses on Google AI Studio](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#resolve-no-content)
- [Check token usage and limits](https://ai.google.dev/gemini-api/docs/troubleshoot-ai-studio#check-token-usage)

This page provides suggestions for troubleshooting Google AI Studio if you
encounter issues.

## Understand 403 Access Restricted errors

If you see a 403 Access Restricted error, you are using Google AI Studio in a
way that does not follow the [Terms of Service](https://ai.google.dev/terms). One common reason is
you are not located in a [supported region](https://ai.google.dev/available_regions).

## Resolve No Content responses on Google AI Studio

A warning **No Content** message appears on
Google AI Studio if the content is blocked for any reason. To see more details,
hold the pointer over **No Content** and click
warning **Safety**.

If the response was blocked due to [safety settings](https://ai.google.dev/docs/safety_setting) and
you considered the [safety risks](https://ai.google.dev/docs/safety_guidance) for your use case, you
can modify the
[safety settings](https://ai.google.dev/docs/safety_setting#safety_settings_in_makersuite)
to influence the returned response.

If the response was blocked but not due to the safety settings, the query or
response may violate the [Terms of Service](https://ai.google.dev/terms) or be otherwise unsupported.

## Check token usage and limits

When you have a prompt open, the **Text Preview** button at the bottom of the
screen shows the current tokens used for the content of your prompt and the
maximum token count for the model being used.

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-02-25 UTC.