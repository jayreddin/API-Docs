# Understand and count tokens

Gemini and other generative AI models process input and output at a granularity called a _token_.

## About tokens

Tokens can be single characters like `z` or whole words like `cat`. Long words are broken up into several tokens. The set of all tokens used by the model is called the vocabulary, and the process of splitting text into tokens is called _tokenization_.

For Gemini models, a token is equivalent to about 4 characters. 100 tokens is equal to about 60-80 English words.

When billing is enabled, the cost of a call to the Gemini API is determined in part by the number of input and output tokens, so knowing how to count tokens can be helpful.

## Context windows

The models available through the Gemini API have context windows that are measured in tokens. The context window defines how much input you can provide and how much output the model can generate. You can determine the size of the context window by calling the getModels endpoint or by looking in the models documentation.

In the following example, you can see that the `gemini-1.5-flash` model has an input limit of about 1,000,000 tokens and an output limit of about 8,000 tokens, which means a context window is 1,000,000 tokens.

```python
from google import genai

client = genai.Client()
model_info = client.models.get(model="gemini-2.0-flash")
print(f"{model_info.input_token_limit=}")
print(f"{model_info.output_token_limit=}")
# ( e.g., input_token_limit=30720, output_token_limit=2048 )
```

## Count tokens

All input to and output from the Gemini API is tokenized, including text, image files, and other non-text modalities.

You can count tokens in the following ways:

- **Call `count_tokens` with the input of the request.** This returns the total number of tokens in _the input only_. You can make this call before sending the input to the model to check the size of your requests.

- **Use the `usage_metadata` attribute on the `response` object after calling `generate_content`.** This returns the total number of tokens in _both the input and the output_: `total_token_count`. It also returns the token counts of the input and output separately: `prompt_token_count` (input tokens) and `candidates_token_count` (output tokens).

### Count text tokens

If you call `count_tokens` with a text-only input, it returns the token count of the text in _the input only_ (`total_tokens`). You can make this call before calling `generate_content` to check the size of your requests.

Another option is calling `generate_content` and then using the `usage_metadata` attribute on the `response` object to get the following:
- The separate token counts of the input (`prompt_token_count`) and the output (`candidates_token_count`)
- The total number of tokens in _both the input and the output_ (`total_token_count`)

```python
from google import genai

client = genai.Client()
prompt = "The quick brown fox jumps over the lazy dog."

# Count tokens using the new client method.
total_tokens = client.models.count_tokens(
    model="gemini-2.0-flash", contents=prompt
)
print("total_tokens: ", total_tokens)
# ( e.g., total_tokens: 10 )

response = client.models.generate_content(
    model="gemini-2.0-flash", contents=prompt
)

# The usage_metadata provides detailed token counts.
print(response.usage_metadata)
# ( e.g., prompt_token_count: 11, candidates_token_count: 73, total_token_count: 84 )
```

### Count multi-turn (chat) tokens

If you call `count_tokens` with the chat history, it returns the total token count of the text from each role in the chat (`total_tokens`).

Another option is calling `send_message` and then using the `usage_metadata` attribute on the `response` object to get the following:
- The separate token counts of the input (`prompt_token_count`) and the output (`candidates_token_count`)
- The total number of tokens in _both the input and the output_ (`total_token_count`)

To understand how big your next conversational turn will be, you need to append it to the history when you call `count_tokens`.

### Count multimodal tokens

All input to the Gemini API is tokenized, including text, image files, and other non-text modalities. Note the following high-level key points about tokenization of multimodal input during processing by the Gemini API:

- With Gemini 2.0, image inputs with both dimensions <=384 pixels are counted as 258 tokens. Images larger in one or both dimensions are cropped and scaled as needed into tiles of 768x768 pixels, each counted as 258 tokens. Prior to Gemini 2.0, images used a fixed 258 tokens.

- Video and audio files are converted to tokens at the following fixed rates: video at 263 tokens per second and audio at 32 tokens per second.

### System instructions and tools

System instructions and tools also count towards the total token count for the input.

If you use system instructions, the `total_tokens` count increases to reflect the addition of `system_instruction`.

If you use function calling, the `total_tokens` count increases to reflect the addition of `tools`.