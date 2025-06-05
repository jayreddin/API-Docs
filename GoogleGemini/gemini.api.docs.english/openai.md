[Skip to main content](https://ai.google.dev/gemini-api/docs/openai#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/openai)
- [Deutsch](https://ai.google.dev/gemini-api/docs/openai?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/openai?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/openai?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/openai?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/openai?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/openai?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/openai?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/openai?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/openai?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/openai?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/openai?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/openai?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/openai?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/openai?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/openai?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/openai?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/openai?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/openai?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/openai?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/openai?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/openai?hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Fopenai&prompt=select_account)

- On this page
- [Thinking](https://ai.google.dev/gemini-api/docs/openai#thinking)
- [Streaming](https://ai.google.dev/gemini-api/docs/openai#streaming)
- [Function calling](https://ai.google.dev/gemini-api/docs/openai#function-calling)
- [Image understanding](https://ai.google.dev/gemini-api/docs/openai#image-understanding)
- [Generate an image](https://ai.google.dev/gemini-api/docs/openai#generate-image)
- [Audio understanding](https://ai.google.dev/gemini-api/docs/openai#audio-understanding)
- [Structured output](https://ai.google.dev/gemini-api/docs/openai#structured-output)
- [Embeddings](https://ai.google.dev/gemini-api/docs/openai#embeddings)
- [List models](https://ai.google.dev/gemini-api/docs/openai#list-models)
- [Retrieve a model](https://ai.google.dev/gemini-api/docs/openai#retrieve-model)
- [Current limitations](https://ai.google.dev/gemini-api/docs/openai#current-limitations)

Gemini models are accessible using the OpenAI libraries (Python and TypeScript /
Javascript) along with the REST API, by updating three lines of code
and using your [Gemini API key](https://aistudio.google.com/apikey). If you
aren't already using the OpenAI libraries, we recommend that you call the
[Gemini API directly](https://ai.google.dev/gemini-api/docs/quickstart).

[Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More

```
from openai import OpenAI

client = OpenAI(
    api_key="GEMINI_API_KEY",
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

response = client.chat.completions.create(
    model="gemini-2.0-flash",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {
            "role": "user",
            "content": "Explain to me how AI works"
        }
    ]
)

print(response.choices[0].message)

```
```
import OpenAI from "openai";

const openai = new OpenAI({
    apiKey: "GEMINI_API_KEY",
    baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/"
});

const response = await openai.chat.completions.create({
    model: "gemini-2.0-flash",
    messages: [
        { role: "system", content: "You are a helpful assistant." },
        {
            role: "user",
            content: "Explain to me how AI works",
        },
    ],
});

console.log(response.choices[0].message);

```
```
curl "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions" \
-H "Content-Type: application/json" \
-H "Authorization: Bearer GEMINI_API_KEY" \
-d '{
    "model": "gemini-2.0-flash",
    "messages": [
        {"role": "user", "content": "Explain to me how AI works"}
    ]
    }'

```
What changed? Just three lines!

- **`api_key="GEMINI_API_KEY"`**: Replace " `GEMINI_API_KEY`" with your actual Gemini
API key, which you can get in [Google AI Studio](https://aistudio.google.com/).

- **`base_url="https://generativelanguage.googleapis.com/v1beta/openai/"`:** This
tells the OpenAI library to send requests to the Gemini API endpoint instead of
the default URL.

- **`model="gemini-2.0-flash"`**: Choose a compatible Gemini model
153 | ## Thinking
154 | 
155 | Gemini 2.5 models are trained to think through complex problems, leading to
156 | significantly improved reasoning. The Gemini API comes with a ["thinking budget"\
157 | parameter](https://ai.google.dev/gemini-api/docs/thinking) which gives fine grain control over how
158 | much the model will think.
159 | 
160 | Unlike the Gemini API, the OpenAI API offers three levels of thinking control:
161 | "low", "medium", and "high", which behind the scenes we map to 1K, 8K, and 24K
162 | thinking token budgets.
163 | 
164 | If you want to disable thinking, you can set the reasoning effort to "none".
165 | 
166 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
167 | 
168 | ```
169 | from openai import OpenAI
170 | 
171 | client = OpenAI(
172 |     api_key="GEMINI_API_KEY",
173 |     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
174 | )
175 | 
176 | response = client.chat.completions.create(
177 |     model="gemini-2.5-flash-preview-04-17",
178 |     reasoning_effort="low",
179 |     messages=[
180 |         {"role": "system", "content": "You are a helpful assistant."},
181 |         {
182 |             "role": "user",
183 |             "content": "Explain to me how AI works"
184 |         }
185 |     ]
186 | )
187 | 
188 | print(response.choices[0].message)
189 | 
190 | ```
191 | 
192 | ```
193 | import OpenAI from "openai";
194 | 
195 | const openai = new OpenAI({
196 |     apiKey: "GEMINI_API_KEY",
197 |     baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/"
198 | });
199 | 
200 | const response = await openai.chat.completions.create({
201 |     model: "gemini-2.5-flash-preview-04-17",
202 |     reasoning_effort: "low",
203 |     messages: [
204 |         { role: "system", content: "You are a helpful assistant." },
205 |         {
206 |             role: "user",
207 |             content: "Explain to me how AI works",
208 |         },
209 |     ],
210 | });
211 | 
212 | console.log(response.choices[0].message);
213 | 
214 | ```
215 | 
216 | ```
217 | curl "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions" \
218 | -H "Content-Type: application/json" \
219 | -H "Authorization: Bearer GEMINI_API_KEY" \
220 | -d '{
221 |     "model": "gemini-2.5-flash-preview-04-17",
222 |     "reasoning_effort": "low",
223 |     "messages": [
224 |         {"role": "user", "content": "Explain to me how AI works"}
225 |       ]
226 |     }'
227 | 
228 | ```
229 | 
230 | ## Streaming
231 | 
232 | The Gemini API supports [streaming responses](https://ai.google.dev/gemini-api/docs/text-generation?lang=python#generate-a-text-stream).
233 | 
234 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
235 | 
236 | ```
237 | from openai import OpenAI
238 | 
239 | client = OpenAI(
240 |     api_key="GEMINI_API_KEY",
241 |     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
242 | )
243 | 
244 | response = client.chat.completions.create(
245 |   model="gemini-2.0-flash",
246 |   messages=[
247 |     {"role": "system", "content": "You are a helpful assistant."},
248 |     {"role": "user", "content": "Hello!"}
249 |   ],
250 |   stream=True
251 | )
252 | 
253 | for chunk in response:
254 |     print(chunk.choices[0].delta)
255 | 
256 | ```
257 | 
258 | ```
259 | import OpenAI from "openai";
260 | 
261 | const openai = new OpenAI({
262 |     apiKey: "GEMINI_API_KEY",
263 |     baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/"
264 | });
265 | 
266 | async function main() {
267 |   const completion = await openai.chat.completions.create({
268 |     model: "gemini-2.0-flash",
269 |     messages: [
270 |       {"role": "system", "content": "You are a helpful assistant."},
271 |       {"role": "user", "content": "Hello!"}
272 |     ],
273 |     stream: true,
274 |   });
275 | 
276 |   for await (const chunk of completion) {
277 |     console.log(chunk.choices[0].delta.content);
278 |   }
279 | }
280 | 
281 | main();
282 | 
283 | ```
284 | 
285 | ```
286 | curl "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions" \
287 | -H "Content-Type: application/json" \
288 | -H "Authorization: Bearer GEMINI_API_KEY" \
289 | -d '{
290 |     "model": "gemini-2.0-flash",
291 |     "messages": [
292 |         {"role": "user", "content": "Explain to me how AI works"}
293 |     ],
294 |     "stream": true
295 |   }'
296 | 
297 | ```
298 | 
299 | ## Function calling
300 | 
301 | Function calling makes it easier for you to get structured data outputs from
302 | generative models and is [supported in the Gemini API](https://ai.google.dev/gemini-api/docs/function-calling/tutorial).
303 | 
304 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
305 | 
306 | ```
307 | from openai import OpenAI
308 | 
309 | client = OpenAI(
310 |     api_key="GEMINI_API_KEY",
311 |     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
312 | )
313 | 
314 | tools = [
315 |   {
316 |     "type": "function",
317 |     "function": {
318 |       "name": "get_weather",
319 |       "description": "Get the weather in a given location",
320 |       "parameters": {
321 |         "type": "object",
322 |         "properties": {
323 |           "location": {
324 |             "type": "string",
325 |             "description": "The city and state, e.g. Chicago, IL",
326 |           },
327 |           "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]},
328 |         },
329 |         "required": ["location"],
330 |       },
331 |     }
332 |   }
333 | ]
334 | 
335 | messages = [{"role": "user", "content": "What's the weather like in Chicago today?"}]
336 | response = client.chat.completions.create(
337 |   model="gemini-2.0-flash",
338 |   messages=messages,
339 |   tools=tools,
340 |   tool_choice="auto"
341 | )
342 | 
343 | print(response)
344 | 
345 | ```
346 | 
347 | ```
348 | import OpenAI from "openai";
349 | 
350 | const openai = new OpenAI({
351 |     apiKey: "GEMINI_API_KEY",
352 |     baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/"
353 | });
354 | 
355 | async function main() {
356 |   const messages = [{"role": "user", "content": "What's the weather like in Chicago today?"}];
357 |   const tools = [
358 |       {
359 |         "type": "function",
360 |         "function": {
361 |           "name": "get_weather",
362 |           "description": "Get the weather in a given location",
363 |           "parameters": {
364 |             "type": "object",
365 |             "properties": {
366 |               "location": {
367 |                 "type": "string",
368 |                 "description": "The city and state, e.g. Chicago, IL",
369 |               },
370 |               "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]},
371 |             },
372 |             "required": ["location"],
373 |           },
374 |         }
375 |       }
376 |   ];
377 | 
378 |   const response = await openai.chat.completions.create({
379 |     model: "gemini-2.0-flash",
380 |     messages: messages,
381 |     tools: tools,
382 |     tool_choice: "auto",
383 |   });
384 | 
385 |   console.log(response);
386 | }
387 | 
388 | main();
389 | 
390 | ```
391 | 
392 | ```
393 | curl "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions" \
394 | -H "Content-Type: application/json" \
395 | -H "Authorization: Bearer GEMINI_API_KEY" \
396 | -d '{
397 |   "model": "gemini-2.0-flash",
398 |   "messages": [
399 |     {
400 |       "role": "user",
401 |       "content": "What''s the weather like in Chicago today?"
402 |     }
403 |   ],
404 |   "tools": [
405 |     {
406 |       "type": "function",
407 |       "function": {
408 |         "name": "get_weather",
409 |         "description": "Get the current weather in a given location",
410 |         "parameters": {
411 |           "type": "object",
412 |           "properties": {
413 |             "location": {
414 |               "type": "string",
415 |               "description": "The city and state, e.g. Chicago, IL"
416 |             },
417 |             "unit": {
418 |               "type": "string",
419 |               "enum": ["celsius", "fahrenheit"]
420 |             }
421 |           },
422 |           "required": ["location"]
423 |         }
424 |       }
425 |     }
426 |   ],
427 |   "tool_choice": "auto"
428 | }'
429 | 
430 | ```
431 | 
432 | ## Image understanding
433 | 
434 | Gemini models are natively multimodal and provide best in class performance on
435 | [many common vision tasks](https://ai.google.dev/gemini-api/docs/vision).
436 | 
437 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
438 | 
439 | ```
440 | import base64
441 | from openai import OpenAI
442 | 
443 | client = OpenAI(
444 |     api_key="GEMINI_API_KEY",
445 |     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
446 | )
447 | 
448 | # Function to encode the image
449 | def encode_image(image_path):
450 |   with open(image_path, "rb") as image_file:
451 |     return base64.b64encode(image_file.read()).decode('utf-8')
452 | 
453 | # Getting the base64 string
454 | base64_image = encode_image("Path/to/agi/image.jpeg")
455 | 
456 | response = client.chat.completions.create(
457 |   model="gemini-2.0-flash",
458 |   messages=[
459 |     {
460 |       "role": "user",
461 |       "content": [
462 |         {
463 |           "type": "text",
464 |           "text": "What is in this image?",
465 |         },
466 |         {
467 |           "type": "image_url",
468 |           "image_url": {
469 |             "url":  f"data:image/jpeg;base64,{base64_image}"
470 |           },
471 |         },
472 |       ],
473 |     }
474 |   ],
475 | )
476 | 
477 | print(response.choices[0])
478 | 
479 | ```
480 | 
481 | ```
482 | import OpenAI from "openai";
483 | import fs from 'fs/promises';
484 | 
485 | const openai = new OpenAI({
486 |   apiKey: "GEMINI_API_KEY",
487 |   baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/"
488 | });
489 | 
490 | async function encodeImage(imagePath) {
491 |   try {
492 |     const imageBuffer = await fs.readFile(imagePath);
493 |     return imageBuffer.toString('base64');
494 |   } catch (error) {
495 |     console.error("Error encoding image:", error);
496 |     return null;
497 |   }
498 | }
499 | 
500 | async function main() {
501 |   const imagePath = "Path/to/agi/image.jpeg";
502 |   const base64Image = await encodeImage(imagePath);
503 | 
504 |   const messages = [
505 |     {
506 |       "role": "user",
507 |       "content": [
508 |         {
509 |           "type": "text",
510 |           "text": "What is in this image?",
511 |         },
512 |         {
513 |           "type": "image_url",
514 |           "image_url": {
515 |             "url": `data:image/jpeg;base64,${base64Image}`
516 |           },
517 |         },
518 |       ],
519 |     }
520 |   ];
521 | 
522 |   try {
523 |     const response = await openai.chat.completions.create({
524 |       model: "gemini-2.0-flash",
525 |       messages: messages,
526 |     });
527 | 
528 |     console.log(response.choices[0]);
529 |   } catch (error) {
530 |     console.error("Error calling Gemini API:", error);
531 |   }
532 | }
533 | 
534 | main();
535 | 
536 | ```
537 | 
538 | ```
539 | bash -c '
540 |   base64_image=$(base64 -i "Path/to/agi/image.jpeg");
541 |   curl "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions" \
542 |     -H "Content-Type: application/json" \
543 |     -H "Authorization: Bearer GEMINI_API_KEY" \
544 |     -d "{
545 |       \"model\": \"gemini-2.0-flash\",
546 |       \"messages\": [
547 |         {
548 |           \"role\": \"user\",
549 |           \"content\": [
550 |             { \"type\": \"text\", \"text\": \"What is in this image?\" },
551 |             {
552 |               \"type\": \"image_url\",
553 |               \"image_url\": { \"url\": \"data:image/jpeg;base64,${base64_image}\" }
554 |             }
555 |           ]
556 |         }
557 |       ]
558 |     }"
559 | '
560 | 
561 | ```
562 | 
563 | ## Generate an image
564 | 
565 | Generate an image:
566 | 
567 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
568 | 
569 | ```
570 | import base64
571 | from openai import OpenAI
572 | from PIL import Image
573 | from io import BytesIO
574 | 
575 | client = OpenAI(
576 |     api_key="GEMINI_API_KEY",
577 |     base_url="https://generativelanguage.googleapis.com/v1beta/openai/",
578 | )
579 | 
580 | response = client.images.generate(
581 |     model="imagen-3.0-generate-002",
582 |     prompt="a portrait of a sheepadoodle wearing a cape",
583 |     response_format='b64_json',
584 |     n=1,
585 | )
586 | 
587 | for image_data in response.data:
588 |   image = Image.open(BytesIO(base64.b64decode(image_data.b64_json)))
589 |   image.show()
590 | 
591 | ```
592 | 
593 | ```
594 | import OpenAI from "openai";
595 | 
596 | const openai = new OpenAI({
597 |   apiKey: "GEMINI_API_KEY",
598 |   baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/",
599 | });
600 | 
601 | async function main() {
602 |   const image = await openai.images.generate(
603 |     {
604 |       model: "imagen-3.0-generate-002",
605 |       prompt: "a portrait of a sheepadoodle wearing a cape",
606 |       response_format: "b64_json",
607 |       n: 1,
608 |     }
609 |   );
610 | 
611 |   console.log(image.data);
612 | }
613 | 
614 | main();
615 | 
616 | ```
617 | 
618 | ```
619 | curl "https://generativelanguage.googleapis.com/v1beta/openai/images/generations" \
620 |   -H "Content-Type: application/json" \
621 |   -H "Authorization: Bearer GEMINI_API_KEY" \
622 |   -d '{
623 |         "model": "imagen-3.0-generate-002",
624 |         "prompt": "a portrait of a sheepadoodle wearing a cape",
625 |         "response_format": "b64_json",
626 |         "n": 1,
627 |       }'
628 | 
629 | ```
630 | 
631 | ## Audio understanding
632 | 
633 | Analyze audio input:
634 | 
635 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
636 |
637 | ```
638 | import base64
639 | from openai import OpenAI
640 | 
641 | client = OpenAI(
642 |     api_key="GEMINI_API_KEY",
643 |     base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
644 | )
645 | 
646 | with open("/path/to/your/audio/file.wav", "rb") as audio_file:
647 |   base64_audio = base64.b64encode(audio_file.read()).decode('utf-8')
648 | 
649 | response = client.chat.completions.create(
650 |     model="gemini-2.0-flash",
651 |     messages=[
652 |     {
653 |       "role": "user",
654 |       "content": [
655 |         {
656 |           "type": "text",
657 |           "text": "Transcribe this audio",
658 |         },
659 |         {
660 |               "type": "input_audio",
661 |               "input_audio": {
662 |                 "data": base64_audio,
663 |                 "format": "wav"
664 |           }
665 |         }
666 |       ],
667 |     }
668 |   ],
669 | )
670 | 
671 | print(response.choices[0].message.content)
672 | 
673 | ```
674 | 
675 | ```
676 | import fs from "fs";
677 | import OpenAI from "openai";
678 | 
679 | const client = new OpenAI({
680 |   apiKey: "GEMINI_API_KEY",
681 |   baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/",
682 | });
683 | 
684 | const audioFile = fs.readFileSync("/path/to/your/audio/file.wav");
685 | const base64Audio = Buffer.from(audioFile).toString("base64");
686 | 
687 | async function main() {
688 |   const response = await client.chat.completions.create({
689 |     model: "gemini-2.0-flash",
690 |     messages: [
691 |       {
692 |         role: "user",
693 |         content: [
694 |           {
695 |             type: "text",
696 |             text: "Transcribe this audio",
697 |           },
698 |           {
699 |             type: "input_audio",
700 |             input_audio: {
701 |               data: base64Audio,
702 |               format: "wav",
703 |             },
704 |           },
705 |         ],
706 |       },
707 |     ],
708 |   });
709 | 
710 |   console.log(response.choices[0].message.content);
711 | }
712 | 
713 | main();
714 | 
715 | ```
716 | 
717 | ```
718 | bash -c '
719 |   base64_audio=$(base64 -i "/path/to/your/audio/file.wav");
720 |   curl "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions" \
721 |     -H "Content-Type: application/json" \
722 |     -H "Authorization: Bearer GEMINI_API_KEY" \
723 |     -d "{
724 |       \"model\": \"gemini-2.0-flash\",
725 |       \"messages\": [
726 |         {
727 |           \"role\": \"user\",
728 |           \"content\": [
729 |             { \"type\": \"text\", \"text\": \"Transcribe this audio file.\" },
730 |             {
731 |               \"type\": \"input_audio\",
732 |               \"input_audio\": {
733 |                 \"data\": \"${base64_audio}\",
734 |                 \"format\": \"wav\"
735 |               }
736 |             }
737 |           ]
738 |         }
739 |       ]
740 |     }"
741 | '
742 | 
743 | ```
744 | 
745 | ## Structured output
746 | 
747 | Gemini models can output JSON objects in any [structure you define](https://ai.google.dev/gemini-api/docs/structured-output).
748 | 
749 | [Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)More
750 |
```
from pydantic import BaseModel
from openai import OpenAI

client = OpenAI(
    api_key="GEMINI_API_KEY",
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

class CalendarEvent(BaseModel):
    name: str
    date: str
    participants: list[str]

completion = client.beta.chat.completions.parse(
    model="gemini-2.0-flash",
    messages=[
        {"role": "system", "content": "Extract the event information."},
        {"role": "user", "content": "John and Susan are going to an AI conference on Friday."},
    ],
    response_format=CalendarEvent,
)

print(completion.choices[0].message.parsed)
```

```
import OpenAI from "openai";
import { zodResponseFormat } from "openai/helpers/zod";
import { z } from "zod";

const openai = new OpenAI({
    apiKey: "GEMINI_API_KEY",
    baseURL: "https://generativelanguage.googleapis.com/v1beta/openai"
});

const CalendarEvent = z.object({
  name: z.string(),
  date: z.string(),
  participants: z.array(z.string()),
});

const completion = await openai.beta.chat.completions.parse({
  model: "gemini-2.0-flash",
  messages: [
    { role: "system", content: "Extract the event information." },
    { role: "user", content: "John and Susan are going to an AI conference on Friday" },
  ],
  response_format: zodResponseFormat(CalendarEvent, "event"),
});

const event = completion.choices[0].message.parsed;
console.log(event);
```

## Embeddings

Text embeddings measure the relatedness of text strings and can be generated
using the [Gemini API](https://ai.google.dev/gemini-api/docs/embeddings).

[Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
```
from openai import OpenAI

client = OpenAI(
    api_key="GEMINI_API_KEY",
    base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

response = client.embeddings.create(
    input="Your text string goes here",
    model="text-embedding-004"
)

print(response.data[0].embedding)
```

```
import OpenAI from "openai";

const openai = new OpenAI({
    apiKey: "GEMINI_API_KEY",
    baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/"
});

async function main() {
  const embedding = await openai.embeddings.create({
    model: "text-embedding-004",
    input: "Your text string goes here",
  });

  console.log(embedding);
}

main();
```

```
curl "https://generativelanguage.googleapis.com/v1beta/openai/embeddings" \
-H "Content-Type: application/json" \
-H "Authorization: Bearer GEMINI_API_KEY" \
-d '{
    "input": "Your text string goes here",
    "model": "text-embedding-004"
  }'
```

## List models

Get a list of available Gemini models:

[Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More

```
from openai import OpenAI

client = OpenAI(
  api_key="GEMINI_API_KEY",
  base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

models = client.models.list()
for model in models:
  print(model.id)
```

```
import OpenAI from "openai";

const openai = new OpenAI({
  apiKey: "GEMINI_API_KEY",
  baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/",
});

async function main() {
  const list = await openai.models.list();

  for await (const model of list) {
    console.log(model);
  }
}
main();
```

```
curl https://generativelanguage.googleapis.com/v1beta/openai/models \
-H "Authorization: Bearer GEMINI_API_KEY"
```

## Retrieve a model

Retrieve a Gemini model:

[Python](https://ai.google.dev/gemini-api/docs/openai#python)[JavaScript](https://ai.google.dev/gemini-api/docs/openai#javascript)[REST](https://ai.google.dev/gemini-api/docs/openai#rest)More
```
from openai import OpenAI

client = OpenAI(
  api_key="GEMINI_API_KEY",
  base_url="https://generativelanguage.googleapis.com/v1beta/openai/"
)

model = client.models.retrieve("gemini-2.0-flash")
print(model.id)
```

```
import OpenAI from "openai";

const openai = new OpenAI({
  apiKey: "GEMINI_API_KEY",
  baseURL: "https://generativelanguage.googleapis.com/v1beta/openai/",
});

async function main() {
  const model = await openai.models.retrieve("gemini-2.0-flash");
  console.log(model.id);
}

main();
```

```
curl https://generativelanguage.googleapis.com/v1beta/openai/models/gemini-2.0-flash \
-H "Authorization: Bearer GEMINI_API_KEY"
```

## Current limitations

Support for the OpenAI libraries is still in beta while we extend feature support.

If you have questions about supported parameters, upcoming features, or run into
any issues getting started with Gemini, join our [Developer Forum](https://discuss.ai.google.dev/c/gemini-api/4).

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-04-26 UTC.