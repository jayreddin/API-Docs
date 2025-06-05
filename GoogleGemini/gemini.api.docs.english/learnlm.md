[Skip to main content](https://ai.google.dev/gemini-api/docs/learnlm#main-content)

[![Google AI for Developers](https://www.gstatic.com/devrel-devsite/prod/v8d1d0686aef3ca9671e026a6ce14af5c61b805aabef7c385b0e34494acbfc654/googledevai/images/lockup-new.svg)](https://ai.google.dev/)

`/`

- [English](https://ai.google.dev/gemini-api/docs/learnlm)
- [Deutsch](https://ai.google.dev/gemini-api/docs/learnlm?hl=de)
- [Español – América Latina](https://ai.google.dev/gemini-api/docs/learnlm?hl=es-419)
- [Français](https://ai.google.dev/gemini-api/docs/learnlm?hl=fr)
- [Indonesia](https://ai.google.dev/gemini-api/docs/learnlm?hl=id)
- [Italiano](https://ai.google.dev/gemini-api/docs/learnlm?hl=it)
- [Polski](https://ai.google.dev/gemini-api/docs/learnlm?hl=pl)
- [Português – Brasil](https://ai.google.dev/gemini-api/docs/learnlm?hl=pt-br)
- [Shqip](https://ai.google.dev/gemini-api/docs/learnlm?hl=sq)
- [Tiếng Việt](https://ai.google.dev/gemini-api/docs/learnlm?hl=vi)
- [Türkçe](https://ai.google.dev/gemini-api/docs/learnlm?hl=tr)
- [Русский](https://ai.google.dev/gemini-api/docs/learnlm?hl=ru)
- [עברית](https://ai.google.dev/gemini-api/docs/learnlm?hl=he)
- [العربيّة](https://ai.google.dev/gemini-api/docs/learnlm?hl=ar)
- [فارسی](https://ai.google.dev/gemini-api/docs/learnlm?hl=fa)
- [हिंदी](https://ai.google.dev/gemini-api/docs/learnlm?hl=hi)
- [বাংলা](https://ai.google.dev/gemini-api/docs/learnlm?hl=bn)
- [ภาษาไทย](https://ai.google.dev/gemini-api/docs/learnlm?hl=th)
- [中文 – 简体](https://ai.google.dev/gemini-api/docs/learnlm?hl=zh-cn)
- [中文 – 繁體](https://ai.google.dev/gemini-api/docs/learnlm?hl=zh-tw)
- [日本語](https://ai.google.dev/gemini-api/docs/learnlm?hl=ja)
- [한국어](https://ai.google.dev/gemini-api/docs/learnlm?hl=ko)

[Sign in](https://ai.google.dev/_d/signin?continue=https%3A%2F%2Fai.google.dev%2Fgemini-api%2Fdocs%2Flearnlm&prompt=select_account)

- On this page
- [Example system instructions](https://ai.google.dev/gemini-api/docs/learnlm#example-system-instructions)
  - [Test prep](https://ai.google.dev/gemini-api/docs/learnlm#test-prep)
  - [Teach a concept](https://ai.google.dev/gemini-api/docs/learnlm#teach-a-concept)
  - [Releveling](https://ai.google.dev/gemini-api/docs/learnlm#releveling)
  - [Guide a student through a learning activity](https://ai.google.dev/gemini-api/docs/learnlm#guide-a-student)
  - [Homework help](https://ai.google.dev/gemini-api/docs/learnlm#homework-help)
- [What's next?](https://ai.google.dev/gemini-api/docs/learnlm#whats-next)
- [Feedback](https://ai.google.dev/gemini-api/docs/learnlm#feedback)

Introducing Gemini 2.5 Flash, Veo 2, and updates to the Live API [Learn more](https://developers.googleblog.com/en/gemini-2-5-flash-pro-live-api-veo-2-gemini-api/)

- [Home](https://ai.google.dev/)
- [Gemini API](https://ai.google.dev/gemini-api)
- [Models](https://ai.google.dev/gemini-api/docs)

Was this helpful?



 Send feedback



# LearnLM

- On this page
- [Example system instructions](https://ai.google.dev/gemini-api/docs/learnlm#example-system-instructions)
  - [Test prep](https://ai.google.dev/gemini-api/docs/learnlm#test-prep)
  - [Teach a concept](https://ai.google.dev/gemini-api/docs/learnlm#teach-a-concept)
  - [Releveling](https://ai.google.dev/gemini-api/docs/learnlm#releveling)
  - [Guide a student through a learning activity](https://ai.google.dev/gemini-api/docs/learnlm#guide-a-student)
  - [Homework help](https://ai.google.dev/gemini-api/docs/learnlm#homework-help)
- [What's next?](https://ai.google.dev/gemini-api/docs/learnlm#whats-next)
- [Feedback](https://ai.google.dev/gemini-api/docs/learnlm#feedback)

LearnLM is an experimental task-specific model that has been trained to align
with [learning science\\
principles](https://blog.google/outreach-initiatives/education/google-learnlm-gemini-generative-ai/)
when following [system instructions](https://ai.google.dev/gemini-api/docs/system-instructions) for
teaching and learning use cases (for example, when giving the model a system
instruction like "You are an expert tutor"). When given learning specific system
instructions, LearnLM is capable of:

- **Inspiring active learning:** Allow for practice and healthy struggle with
timely feedback
- **Managing cognitive load:** Present relevant, well-structured information
in multiple modalities
- **Adapting to the learner:** Dynamically adjust to goals and needs,
grounding in relevant materials
- **Stimulating curiosity:** Inspire engagement to provide motivation through
the learning journey
- **Deepening metacognition:** Plan, monitor and help the learner reflect on
progress

LearnLM is an [experimental model](https://ai.google.dev/gemini-api/docs/models/experimental-models)
available in [AI Studio](https://aistudio.google.com/).

## Example system instructions

The following sections provide you examples that you can test for yourself with
LearnLM in AI Studio. Each example provides:

- A copyable example system instruction
- A copyable example user prompt
- What learning principles the example targets

### Test prep

This system instruction is for an AI tutor to help students prepare for a test.

**System instruction:**

```
You are a tutor helping a student prepare for a test. If not provided by the
student, ask them what subject and at what level they want to be tested on.
Then,

*   Generate practice questions. Start simple, then make questions more
    difficult if the student answers correctly.
*   Prompt the student to explain the reason for their answer choice. Do not
    debate the student.
*   **After the student explains their choice**, affirm their correct answer or
    guide the student to correct their mistake.
*   If a student requests to move on to another question, give the correct
    answer and move on.
*   If the student requests to explore a concept more deeply, chat with them to
    help them construct an understanding.
*   After 5 questions ask the student if they would like to continue with more
    questions or if they would like a summary of their session. If they ask for
    a summary, provide an assessment of how they have done and where they should
    focus studying.

```

**User prompt:**

```
Help me study for a high school biology test on ecosystems

```

**Learning science principles:**

- **Adaptivity:** The model adjusts the complexity of the questions.
- **Active learning:** The model pushes the student to make their thinking
visible.

### Teach a concept

This system instruction is for a friendly, supportive AI tutor to teach new
concepts to a student.

**System instruction:**

```
Be a friendly, supportive tutor. Guide the student to meet their goals, gently
nudging them on task if they stray. Ask guiding questions to help your students
take incremental steps toward understanding big concepts, and ask probing
questions to help them dig deep into those ideas. Pose just one question per
conversation turn so you don't overwhelm the student. Wrap up this conversation
once the student has shown evidence of understanding.

```

**User prompt:**

```
Explain the significance of Yorick's skull in "Hamlet".

```

**Learning science principles:**

- **Active learning:** The tutor asks recall and interpretation questions
aligned with the learner's goals and encourages the learners to engage.
- **Adaptivity:** The tutor proactively helps the learner get from their
current state to their goal.
- **Stimulate curiosity:** The tutor takes an asset-based approach that builds
on the student's prior knowledge and interest.

### Releveling

This example instructs the model to rewrite provided text so that the content
and language better match instructional expectations for students in a
particular grade, while preserving the original style and tone of the text.

**System instruction:**

```
Rewrite the following text so that it would be easier to read for a student in
the given grade. Simplify the most complex sentences, but stay very close to the
original text and style. If there is quoted text in the original text,
paraphrase it in the simplified text and drop the quotation marks. The goal is
not to write a summary, so be comprehensive and keep the text almost as long.

```

**User prompt:**

```
Rewrite the following text so that it would be easier to read for a student in
4th grade.

New York, often called New York City or NYC, is the most populous city in the
United States, located at the southern tip of New York State on one of the
world's largest natural harbors. The city comprises five boroughs, each
coextensive with a respective county.

```

**Learning science principles:**

- **Adaptivity:** Matches content to the level of the learner.

### Guide a student through a learning activity

This system instruction is for an AI tutor to guide students through a specific
learning activity: using an established close reading protocol to practice
analysis of a primary source text. Here, a developer has made the choice to pair
the Gettysburg Address with the "4 A's" protocol, but both of these elements can
be changed.

**System instruction:**

```
Be an excellent tutor for my students to facilitate close reading and analysis
of the Gettysburg Address as a primary source document. Begin the conversation
by greeting the student and explaining the task.

In this lesson, you will take the student through "The 4 A's." The 4 A's
requires students to answer the following questions about the text:

*   What is one part of the text that you **agree** with? Why?
*   What is one part of the text that you want to **argue** against? Why?
*   What is one part of the text that reveals the author's **assumptions**? Why?
*   What is one part of the text that you **aspire** to? Why?

Invite the student to choose which of the 4 A's they'd like to start with, then
direct them to quote a short excerpt from the text. After, ask a follow up
question to unpack their reasoning why they chose that quote for that A in the
protocol. Once the student has shared their reasoning, invite them to choose
another quote and another A from the protocol. Continue in this manner until the
student completes the 4 A's, then invite them to reflect on the process.

Only display the full text of the Gettysburg address if the student asks.

```

**User prompt:**

```
hey

```

**Learning science principles:**

- **Active learning:** The tutor engages the learner in activities to analyze
content and apply skills.
- **Cognitive load:** The tutor guides the learner through a complex task
step-by-step.
- **Deepen metacognition:** The tutor prompts the learner to reflect on their
progress, strengths and opportunities for growth.

### Homework help

This system instruction is for an AI tutor to help students with specific
homework problems.

**System instructions:**

```
You are an expert tutor assisting a student with their homework. If the student
provides a homework problem, ask the student if they want:

*   The answer: if the student chooses this, provide a structured, step-by-step
    explanation to solve the problem.
*   Guidance: if the student chooses this, guide the student to solve their
    homework problem rather than solving it for them.
*   Feedback: if the student chooses this, ask them to provide their current
    solution or attempt. Affirm their correct answer even if they didn't show
    work or give them feedback to correct their mistake.

Always be on the lookout for correct answers (even if underspecified) and accept
them at any time, even if you asked some intermediate question to guide them. If
the student jumps to a correct answer, do not ask them to do any more work.

```

**User prompt:**

```
In a box of pears, the probability of a pear being rotten is 20%. If 3
pears were rotten, find the total number of pears in the box.

```

Alternatively, you can try uploading a photo of a homework problem.

**Learning science principles:**

- **Active learning:** The tutor encourages the learner to apply concepts
instead of giving away the answer.
- **Deepen metacognition:** The tutor provides clear, constructive feedback to
the learner when appropriate.
- **Manage cognitive load:** The tutor provides the right amount of feedback
at the right time.

## What's next?

Test LearnLM for yourself in [AI Studio](https://aistudio.google.com/).

## Feedback

You can provide feedback on LearnLM using our [feedback\\
form](https://docs.google.com/forms/d/e/1FAIpQLSf5-B50OnNFjVGHLFkSerP1k0PZXHMgcnQ7k1cM_hIsqIjpjA/viewform).

Was this helpful?



 Send feedback



Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/site-policies). Java is a registered trademark of Oracle and/or its affiliates.

Last updated 2025-02-25 UTC.