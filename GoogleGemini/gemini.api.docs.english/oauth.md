# Authentication with OAuth quickstart

The easiest way to authenticate to the Gemini API is to configure an API key, as described in the Gemini API quickstart. If you need stricter access controls, you can use OAuth instead. This guide will help you set up authentication with OAuth.

This guide uses a simplified authentication approach that is appropriate for a testing environment. For a production environment, learn about [authentication and authorization](https://developers.google.com/workspace/guides/auth-overview) before [choosing the access credentials](https://developers.google.com/workspace/guides/create-credentials#choose_the_access_credential_that_is_right_for_you) that are appropriate for your app.

## Prerequisites

To run this quickstart, you need:

- [A Google Cloud project](https://developers.google.com/workspace/guides/create-project)
- [A local installation of the gcloud CLI](https://cloud.google.com/sdk/docs/install)

## Set up your cloud project

### 1. Enable the API

Before using Google APIs, you need to turn them on in a Google Cloud project. In the Google Cloud console, enable the Google Generative Language API.

[Enable the API](https://console.cloud.google.com/flows/enableapi?apiid=generativelanguage.googleapis.com)

### 2. Configure the OAuth consent screen

1. In the Google Cloud console, go to **Menu** > **Google Auth platform** > **Overview**.
2. Complete the project configuration form and set the user type to **External** in the **Audience** section.
3. Complete the rest of the form, accept the User Data Policy terms, and click **Create**.
4. For now, you can skip adding scopes and click **Save and Continue**.
5. Add test users:
   - Navigate to the [Audience page](https://console.developers.google.com/auth/audience)
   - Under **Test users**, click **Add users**
   - Enter your email address and any other authorized test users, then click **Save**

### 3. Authorize credentials for a desktop application

1. In the Google Cloud console, go to **Menu** > **Google Auth platform** > **Clients**.
2. Click **Create Client**.
3. Click **Application type** > **Desktop app**.
4. Name your credential (only shown in console).
5. Click **Create**.
6. Click **OK** when shown your new Client ID and Client secret.
7. Download the JSON file, rename it to `client_secret.json` and move it to your working directory.

## Set up application default credentials

Convert the `client_secret.json` file into usable credentials:

```bash
gcloud auth application-default login \
    --client-id-file=client_secret.json \
    --scopes='https://www.googleapis.com/auth/cloud-platform,https://www.googleapis.com/auth/generative-language.retriever'
```

For systems without a browser:
```bash
gcloud auth application-default login \
    --no-browser \
    --client-id-file=client_secret.json \
    --scopes='https://www.googleapis.com/auth/cloud-platform,https://www.googleapis.com/auth/generative-language.retriever'
```

### Test with Curl

```bash
access_token=$(gcloud auth application-default print-access-token)
project_id=<MY PROJECT ID>
curl -X GET https://generativelanguage.googleapis.com/v1/models \
    -H 'Content-Type: application/json' \
    -H "Authorization: Bearer ${access_token}" \
    -H "x-goog-user-project: ${project_id}" | grep '"name"'
```

### Test with Python

```bash
pip install google-generativeai
```

```python
import google.generativeai as genai

print('Available base models:', [m.name for m in genai.list_models()])
```

## Manage credentials yourself [Python]

For cases without `gcloud`, you can manage credentials within your app:

### 1. Install libraries

```bash
pip install --upgrade -q google-api-python-client google-auth-httplib2 google-auth-oauthlib
pip install google-generativeai
```

### 2. Create credential manager (load_creds.py)

```python
import os.path
from google.auth.transport.requests import Request
from google.oauth2.credentials import Credentials
from google_auth_oauthlib.flow import InstalledAppFlow

SCOPES = ['https://www.googleapis.com/auth/generative-language.retriever']

def load_creds():
    """Converts `client_secret.json` to a credential object.
    
    This function caches the generated tokens to minimize the use of the
    consent screen.
    """
    creds = None
    if os.path.exists('token.json'):
        creds = Credentials.from_authorized_user_file('token.json', SCOPES)
    if not creds or not creds.valid:
        if creds and creds.expired and creds.refresh_token:
            creds.refresh(Request())
        else:
            flow = InstalledAppFlow.from_client_secrets_file(
                'client_secret.json', SCOPES)
            creds = flow.run_local_server(port=0)
        with open('token.json', 'w') as token:
            token.write(creds.to_json())
    return creds
```

### 3. Create your script (script.py)

```python
import pprint
import google.generativeai as genai
from load_creds import load_creds

creds = load_creds()
genai.configure(credentials=creds)

print()
print('Available base models:', [m.name for m in genai.list_models()])
```

### 4. Run your program

```bash
python script.py
```

The first time you run the script, it will open a browser window for authorization. Select the account you set as a "Test Account". Authorization information is stored in the file system for future use.