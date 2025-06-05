## [Encyclopedia](https://developer.puter.com/encyclopedia/)

# Claude 3.7 Sonnet

Claude 3.7 Sonnet is a [large language model](https://en.wikipedia.org/wiki/Large_language_model) developed by [Anthropic](https://en.wikipedia.org/wiki/Anthropic), released on February 25, 2025. It is part of the Claude 3 family of models, known for introducing hybrid reasoning capabilities through a feature called "extended thinking mode." This feature allows the model to work through complex problems using step-by-step reasoning, a capability that distinguishes it from earlier models in the Claude lineup. Anthropic has positioned Claude 3.7 Sonnet as their most intelligent model to date, with particular strengths in coding, reasoning through complex problems, and handling agentic tasks.

## Features and capabilities

Claude 3.7 Sonnet builds on the foundation of its predecessor, Claude 3.5 Sonnet, with several key enhancements:

### Hybrid reasoning

Claude 3.7 Sonnet's defining feature is its hybrid reasoning capability, which combines quick responses with what Anthropic calls "extended thinking mode" within a single model architecture. This design differs from other approaches that use separate models for different types of reasoning. When activated, extended thinking mode allows Claude to work through complex problems using detailed, step-by-step reasoning before providing an answer. This process is similar to human deliberative thinking and is visible to users as the model shows its explicit reasoning process.

The model provides two modes:

- **Standard mode**: An improved version of Claude 3.5 Sonnet's capabilities for routine tasks
- **Extended thinking mode**: Allows deeper analysis of problems with explicit reasoning steps

Extended thinking mode is implemented through what Anthropic describes as "serial test-time compute." This means the model uses multiple sequential reasoning steps before producing a final output, adding computational resources as it processes the request. Performance generally improves logarithmically with the number of "thinking tokens" the model is allowed to use, particularly for tasks requiring complex reasoning like mathematics.

Anthropic has also experimented with "parallel test-time compute," where multiple independent thought processes are generated and the best one is selected, further improving performance on challenging tasks.

### Visible thought process

A distinctive aspect of Claude 3.7 Sonnet is its "visible thought process" feature, which displays the model's reasoning in raw form. This was implemented to provide several benefits:

1. **Trust**: Making the reasoning process observable helps users understand and verify the model's answers
2. **Alignment**: Revealing internal reasoning can help identify potentially concerning behaviors
3. **Interest**: The thought process itself can be instructive, as it mimics human problem-solving approaches

However, this transparency comes with tradeoffs. The revealed thinking is often more detached and less personalized than Claude's standard outputs, and Anthropic acknowledges that the model sometimes works through incorrect or incomplete thoughts along the way. There are also questions about whether the visible thought process truly represents what's happening in the model's "mind," a problem Anthropic refers to as "faithfulness."

For security reasons, in cases where Claude's thought process might include potentially harmful content (related to topics like child safety, cyber attacks, or dangerous weapons), Anthropic encrypts that portion of the thought process. Users will see the message "the rest of the thought process is not available for this response" instead.

### Context window and output capacity

Claude 3.7 Sonnet features a 128K token [context window](https://developer.puter.com/encyclopedia/context-window/), allowing it to process extensive documents, codebases, or conversations in a single session. Compared to its predecessor Claude 3.5 Sonnet, the model offers significantly expanded output length—up to 128K tokens (with up to 64K tokens generally available and up to 128K tokens available in beta). This extended capacity is particularly useful for generating detailed content, multiple examples, or comprehensive analyses.

### Code generation and understanding

Claude 3.7 Sonnet shows significant improvements in coding capabilities, with Anthropic claiming state-of-the-art performance on coding benchmarks. According to Anthropic, the model achieves 70.3% accuracy on the SWE-bench Verified benchmark in standard mode, outperforming competitors like OpenAI's o1 (48.9%) and DeepSeek-R1 (49.2%).

The model demonstrates enhanced abilities in:

- Understanding and working with large codebases
- Debugging complex programming issues
- Writing code across multiple programming languages
- Explaining technical concepts

These capabilities make it particularly suited for software development workflows and complex coding tasks that require reasoning through multiple steps.

### Computer use abilities

Claude 3.7 Sonnet includes enhanced computer use capabilities, allowing it to see a user's computer screen and take actions on their behalf through a feature called "action scaling." This improvement enables the model to issue virtual mouse clicks and keyboard presses to complete tasks on a user's computer. Compared to earlier models, Claude 3.7 Sonnet can allocate more computational resources and time to these tasks, resulting in better performance.

The model demonstrates improved performance on OSWorld, an evaluation measuring the capabilities of multimodal AI agents interacting with computer systems. Anthropic has implemented safety measures against "prompt injection" attacks, where malicious third parties might try to trick the model into performing unintended actions while using a computer.

## Performance and benchmarks

Claude 3.7 Sonnet has demonstrated improved performance across various benchmarks compared to earlier Claude models and competing AI systems:

### Mathematical reasoning

On mathematics tests like the American Invitational Mathematics Examination (AIME) 2024, Claude 3.7 Sonnet's performance improves logarithmically with additional thinking tokens. However, Anthropic acknowledges that mathematics is not the model's strongest domain. The company reports that Claude 3.7 Sonnet scores 23.3% on the AIME2024 in standard mode, with performance improving to 61-80% when extended thinking mode is activated.

### Scientific knowledge

Using parallel test-time compute scaling with a learned scoring model and a 64K token thinking budget, Claude 3.7 Sonnet achieved an 84.8% score on the GPQA evaluation, a challenging set of questions on biology, chemistry, and physics. The physics subscore reached 96.5%.

### Coding performance

Anthropic reports that Claude 3.7 Sonnet achieves state-of-the-art performance on coding benchmarks. On SWE-bench, which measures software development skills, the model scored 70.3% in standard mode, outperforming competitive models. The addition of a "think" tool, which provides space for structured thinking during complex tasks, further improved performance on SWE-bench by an average of 1.6%.

### Agentic capabilities

Claude 3.7 Sonnet shows enhanced performance in agentic tasks, where the model must interact with its environment over multiple turns. One notable demonstration of these capabilities was the model's ability to play the video game Pokémon Red, progressing significantly further than previous Claude models. While earlier versions struggled with basic navigation, Claude 3.7 Sonnet successfully defeated multiple game bosses and earned three gym badges.

### Tau-Bench

The model's performance was evaluated on [τ-bench (tau-bench)](https://arxiv.org/abs/2406.12045), a benchmark for testing tool use in realistic customer service scenarios. Using a "think" tool, which creates space for structured thinking during complex tasks, Claude 3.7 Sonnet achieved significant improvements:

- In the airline domain: 0.570 on the pass^1 metric (a 54% relative improvement over baseline)
- In the retail domain: 0.812 on the pass^1 metric (compared to 0.783 for baseline)

### Other evaluations

While specific details are limited, Anthropic claims Claude 3.7 Sonnet outperforms previous models across most benchmarks, with particular strengths in coding, complex reasoning, and agentic tasks.

When compared to other leading models like Google's Gemini 2.5 Pro and OpenAI's o3-mini on the [Humanity's Last Exam (HLE)](https://agi.safe.ai/) benchmark, Claude 3.7 Sonnet scored 8.9%, below both Gemini 2.5's 18.8% and o3-mini's 14%. HLE is considered a particularly challenging benchmark designed to test the limits of current AI systems.

## Safety measures

As part of Anthropic's [Responsible Scaling Policy](https://www.anthropic.com/responsible-scaling-policy), Claude 3.7 Sonnet undergoes extensive safety testing and implements various safeguards:

### AI Safety Level

Anthropic applies their AI Safety Level (ASL) framework to assess and mitigate potential risks from their models. Claude 3.7 Sonnet was determined to meet the ASL-2 standard, the same level applied to previous Claude models. This assessment followed extensive testing by Anthropic's Frontier Red Team and Alignment Stress Testing team.

Testing revealed that while Claude 3.7 Sonnet demonstrated increased sophistication and capabilities across all domains, it did not require stronger measures than the existing ASL-2 standard. Studies examining tasks related to Chemical, Biological, Radiological, and Nuclear (CBRN) weapons showed that model-assisted participants could progress further than non-assisted participants, but all attempts contained critical failures that prevented successful completion.

In response to these findings, Anthropic implemented targeted classifiers and monitoring systems to enhance their ASL-2 measures.

### Thought process security

To address potential risks from the visible thought process feature, Anthropic implemented encryption for thought content that might be potentially harmful. In these cases, the relevant portion of the thought process is not visible to users, though the model can still use this thinking to produce appropriate responses.

### Prompt injection resistance

Anthropic enhanced safety measures for Claude's computer use capability, particularly focusing on defending against "prompt injection" attacks. Through new training, system prompting, and a specialized classifier, the model can now prevent these attacks 88% of the time, up from 74% without these mitigations.

## Development and release

Claude 3.7 Sonnet was released on February 25, 2025, following the earlier release of Claude 3.5 Sonnet. The naming convention (3.7 rather than 4.0) suggests an incremental but significant update rather than a complete model redesign.

The model was released with both free and paid access tiers:

- Free access through Claude.ai with standard features
- Paid access through Claude Pro subscription ($20 per month), which includes the extended thinking mode feature

For developers, Claude 3.7 Sonnet is available through Anthropic's API with pricing set at $3 per million input tokens and $15 per million output tokens. This pricing structure is positioned at a premium compared to some competitive offerings.

The model is also accessible through cloud platforms including [Amazon Bedrock](https://aws.amazon.com/blogs/aws/anthropics-claude-3-7-sonnet-the-first-hybrid-reasoning-model-is-now-available-in-amazon-bedrock/).

## Applications and use cases

### Software development

Claude 3.7 Sonnet's enhanced coding capabilities make it particularly valuable for software development tasks. The model can analyze entire codebases, identify bugs, suggest optimizations, and generate new code. For software teams, this can accelerate development workflows, reduce debugging time, and help navigate complex system architectures.

A notable application is the Claude Code command-line tool, which allows developers to access Claude 3.7 Sonnet directly from their terminal. This integration enables developers to incorporate AI assistance into their workflow with minimal context switching.

### Customer service

Claude 3.7 Sonnet shows improved capabilities in customer service scenarios, particularly in handling complex policy guidelines and making consistent decisions. The model's ability to use tools effectively and process sequential information makes it suitable for customer support applications where adherence to specific policies is critical.

The addition of the "think" tool significantly enhances performance in these scenarios by providing space for structured reasoning when following detailed guidelines or processing complex customer requests.

### Complex problem solving

The extended thinking capability enables Claude 3.7 Sonnet to tackle complex problems requiring detailed analysis. This makes it useful for applications in fields such as:

- Financial analysis and modeling
- Scientific research and data interpretation
- Strategic planning and decision making
- Educational instruction and tutoring

### Agent-based applications

Claude 3.7 Sonnet's improved agentic capabilities enable applications where the model must interact with its environment over multiple turns. This includes browsing the web, navigating computer interfaces, and executing complex multi-step tasks on behalf of users.

## Reception and impact

### Industry reception

Claude 3.7 Sonnet has received significant attention within the AI industry, particularly for its hybrid reasoning capabilities and performance on coding tasks. Several independent evaluations have confirmed Anthropic's claims about the model's coding performance, with many developers and organizations reporting that Claude 3.7 Sonnet outperforms competing models for software development tasks.

Companies like [Cursor](https://cursor.sh/), an AI-powered code editor, have integrated Claude 3.7 Sonnet into their products, offering it as "Claude Sonnet 3.7 MAX" to their users. [Vercel](https://vercel.com/), a platform for front-end development, has also incorporated Claude into their tools for generating web user interfaces.

The model has been particularly well-received for its ability to understand large codebases and reason through complex system architectures, addressing a significant pain point for software teams working with extensive codebases.

### Economic impact

Anthropic has been tracking the economic impact of Claude through its [Anthropic Economic Index](https://www.anthropic.com/news/anthropic-economic-index-insights-from-claude-sonnet-3-7), analyzing anonymized conversations to understand how the model is being used across different occupations and tasks.

Following the launch of Claude 3.7 Sonnet, Anthropic observed:

1. Increased usage for coding, educational, scientific, and healthcare applications
2. Extended thinking mode being used predominantly for technical tasks, particularly those associated with computer science research, software development, multimedia animation, and game design
3. No significant change in the balance between augmentative and automative uses of the model, with augmentation still comprising approximately 57% of usage

The data suggests that Claude 3.7 Sonnet's enhanced capabilities are being applied across a range of professional contexts, with particular adoption in technical and creative fields.

### Limitations and criticisms

Despite its improvements, Claude 3.7 Sonnet has several notable limitations:

1. **Mathematical reasoning**: Anthropic acknowledges that mathematics remains a relative weakness for the model, with performance on challenging mathematical problems lagging behind some competitors.

2. **Feature limitations**: Unlike some competing models, Claude 3.7 Sonnet lacks built-in web browsing capabilities, image generation, and certain research features available in models from OpenAI, xAI (Grok), and Google.

3. **Content restrictions**: Claude 3.7 Sonnet maintains stricter content restrictions than some competitors, particularly in handling sensitive topics. This has been noted as both a strength from a safety perspective and a limitation for users seeking more flexibility.

4. **Pricing**: The API pricing for Claude 3.7 Sonnet is higher than some competitive offerings, which may limit adoption for certain use cases.

5. **Performance on certain benchmarks**: While excelling in coding and reasoning tasks, Claude 3.7 Sonnet scored lower than some competitors on benchmarks like Humanity's Last Exam (HLE).


## Comparison to other models

### vs. OpenAI models

Compared to OpenAI's models like o1 and o3-mini, Claude 3.7 Sonnet shows particular strengths in coding tasks and agentic capabilities. However, OpenAI's models typically offer additional features like DALL-E image generation and web browsing capabilities that Claude lacks.

On coding benchmarks like SWE-bench, Claude 3.7 Sonnet reportedly outperforms OpenAI's models, though direct comparisons can be difficult due to differences in evaluation methodologies.

### vs. Google Gemini

Google's Gemini 2.5 Pro outperforms Claude 3.7 Sonnet on certain benchmarks, particularly the Humanity's Last Exam (HLE), where Gemini 2.5 scored 18.8% compared to Claude's 8.9%. Gemini also offers integrated search and multimodal capabilities not present in Claude.

However, Claude 3.7 Sonnet is often cited for stronger performance in coding tasks and detailed reasoning in professional contexts.

### vs. xAI Grok

Compared to xAI's Grok 3, Claude 3.7 Sonnet generally offers stronger performance on coding and reasoning tasks but maintains stricter content restrictions. Grok is noted for having fewer restrictions on generating creative content involving sensitive topics, while Claude takes a more conservative approach to content moderation.

In creative writing tasks, evaluations suggest Claude 3.7 Sonnet may have an edge over Grok 3 in narrative structure and language quality, though both models have strengths in different aspects of creative generation.

### vs. Previous Claude models

Claude 3.7 Sonnet demonstrates significant improvements over its predecessor, Claude 3.5 Sonnet, particularly in:

- Coding capabilities and complex reasoning
- Output capacity (up to 15x longer outputs)
- Agentic performance and tool use
- Handling of multi-step tasks requiring sequential decision making

The addition of extended thinking mode represents a major architectural advancement over previous Claude models.

## Technical details

Claude 3.7 Sonnet's full technical architecture has not been publicly disclosed by Anthropic, but several key technical aspects have been revealed:

### Model architecture

Claude 3.7 Sonnet uses what Anthropic describes as a "hybrid reasoning" architecture that integrates both quick responses and extended thinking within a single model. This differs from approaches that use separate models for different types of reasoning.

### Thinking budget

When using extended thinking mode through the API, developers can control the "thinking budget" by allocating more tokens for complex problems or limiting tokens for faster responses. This allows for optimization based on the specific use case requirements.

### "Think" tool

Anthropic has implemented a "think" tool that creates dedicated space for structured thinking during complex tasks. This tool has demonstrated significant improvements in performance on benchmarks like tau-bench and SWE-bench.

The tool is defined using a standard specification format:

```json hljs
{
  "name": "think",
  "description": "Use the tool to think about something. It will not obtain new information or change the database, but just append the thought to the log. Use it when complex reasoning or some cache memory is needed.",
  "input_schema": {
    "type": "object",
    "properties": {
      "thought": {
        "type": "string",
        "description": "A thought to think about."
      }
    },
    "required": ["thought"]
  }
}

```

This approach improves Claude's ability to follow policies, make consistent decisions, and handle multi-step problems with minimal implementation overhead.

## The future of Claude

Anthropic has indicated several directions for future development of the Claude model family:

### Safety enhancements

While Claude 3.7 Sonnet was assessed at AI Safety Level 2 (ASL-2), Anthropic is preparing for future models that might require ASL-3 safeguards. The company is developing Constitutional Classifiers and other technologies to implement these more stringent requirements.

### Context window expansion

Reports suggest Anthropic may be preparing a significant expansion of Claude's context window from the current 200K tokens to 500K tokens. Evidence for this has appeared in feature flags, suggesting the rollout may be imminent. This expanded context window would allow users to input and process substantially larger datasets or codebases in a single session.

### Continued reasoning improvements

Anthropic's research into both serial and parallel test-time compute scaling suggests the company will continue to enhance Claude's reasoning capabilities in future releases. Their experiments with parallel sampling and learned scoring models have already demonstrated significant performance improvements on challenging evaluations.

## See also

- [Vibe Coding](https://developer.puter.com/encyclopedia/vibe-coding)

## References

01. [Claude 3.7 Sonnet: the first AI model that understands your entire codebase](https://medium.com/@DaveThackeray/claude-3-7-sonnet-the-first-ai-model-that-understands-your-entire-codebase-560915c6a703)
02. [Anthropic may soon launch Claude 3.7 Sonnet with 500k token context window](https://www.testingcatalog.com/anthropic-may-soon-launch-claude-3-7-sonnet-with-500k-token-context-window/)
03. [Anthropic's stealth enterprise coup: How Claude 3.7 is becoming the coding agent of choice](https://venturebeat.com/ai/anthropics-stealth-enterprise-coup-how-claude-3-7-is-becoming-the-coding-agent-of-choice/)
04. [Anthropic's Claude AI is playing Pokémon on Twitch — slowly](https://techcrunch.com/2025/02/25/anthropics-claude-ai-is-playing-pokemon-on-twitch-slowly/)
05. [Claude 3.7 Sonnet: the first hybrid reasoning model is now available in Amazon Bedrock](https://aws.amazon.com/blogs/aws/anthropics-claude-3-7-sonnet-the-first-hybrid-reasoning-model-is-now-available-in-amazon-bedrock/)
06. [I tested Anthropic's Claude 3.7 Sonnet. Its 'extended thinking' mode outdoes ChatGPT and Grok, but it can overthink](https://www.businessinsider.com/anthropic-claude-3-7-sonnet-test-thinking-grok-chatgpt-comparison-2025-2)
07. [Claude 3.7 Sonnet Takes Back the AI Crown—Here's How it Stands Against the Rest](https://decrypt.co/307951/claude-3-7-sonnet-takes-back-the-ai-crown)
08. [The "think" tool: Enabling Claude to stop and think in complex tool use situations](https://www.anthropic.com/engineering/claude-think-tool)
09. [Visible extended thinking](https://www.anthropic.com/news/visible-extended-thinking)
10. [Anthropic Economic Index: Insights from Claude Sonnet 3.7](https://www.anthropic.com/news/anthropic-economic-index-insights-from-claude-sonnet-3-7)
11. [Everyone can now try Gemini 2.5 Pro - for free](https://www.zdnet.com/article/everyone-can-now-try-gemini-2-5-pro-for-free/)

## Ready to Build Your First App?

Start creating powerful web applications with Puter.js today!

[Get Started Now](https://docs.puter.com/getting-started/)

[Read the Docs](https://docs.puter.com/)• [Try the Playground](https://docs.puter.com/playground/)