# API Keys

## Get started with API keys

To use Gemini, you need an API key. You can get this from Google AI Studio.

### Get an API key

1. Go to the [Google AI Studio](https://makersuite.google.com/app/home).
2. Click Get API key in the upper-right navigation.
3. Select Create API key in your project.

### Store your API key securely

Make sure to:
- Keep your API key secure and never share it
- Use environment variables or secure secret management
- Don't commit API keys to version control
- Rotate keys periodically
- Have a process to revoke compromised keys

### Using API keys

The API key needs to be included in API requests as a header:

```python
import google.generativeai as genai

genai.configure(api_key='YOUR_API_KEY')
```

### API key best practices

- Use different API keys for development and production
- Monitor API key usage and set appropriate quotas
- Implement rate limiting as needed
- Have an incident response plan for compromised keys
- Review access logs regularly

### Rate limits and quotas

API keys have associated rate limits and quotas. Monitor your usage to stay within limits:

- Request rate limits per minute/hour
- Daily/monthly quota limits
- Concurrent request limits
- Token limits per request

Contact Google Cloud support if you need increased quotas.

### Revoking API keys

If an API key is compromised:
1. Go to Google AI Studio
2. Navigate to API key management
3. Select the key and click Revoke
4. Create a new key and update your applications

Always have a plan to quickly revoke and rotate keys if needed.