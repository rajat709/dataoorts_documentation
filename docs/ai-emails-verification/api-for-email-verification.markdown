---
layout: page
title: "API For Email Verification" 
permalink: /docs/api-email-verification/
nav_order: 6
parent: "AI-Powered CRM"
published: May 21, 2025
updated: May 22, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">


{: .important-title }
> Asynchronous Architecture
>
> Our API features an async architecture, allowing you to handle multiple requests seamlessly and execute parallel operations efficiently.
>

{: .highlight }
> Multiple failed and unauthorized attempts will result in a permanent IP block.

## 👉 Get your Unify API KEY [Here](https://cloud.dataoorts.com/unify_api)

![Dataoorts Unify API - AI Mails Verification](api_for_email_verification.jpg)

{: .important }
> Our REST API enables AI-powered email verification and is compatible with any framework. For demonstration purposes, we have used Python as an example.


## 1. For Single Email Verification

{: .important-title }
> API Endpoint URL:
>
> https://cloud.dataoorts.com/ai_mails_api/v1
>

```python
# Health Check
import requests

URL = "https://cloud.dataoorts.com/ai_mails_api/v1"
resp = requests.get(URL)
print(resp.status_code, resp.json())
PythonCopy
200 {'status': 'All Services Operational'}
```

### ➡️ Both Email Verification and Data Prediction

```python
import requests, json

# Set Everything
URL = "https://cloud.dataoorts.com/ai_mails_api/v1"
API_KEY = <Your_Unify_API_Key>

response = requests.post(
    URL,
    headers={
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json"
    },
    json={
        "email": "rajatvishwakarma3656@dataoorts.com",
        "info": "true"
    }
)

print(response.status_code)
print(json.dumps(response.json(), indent=2))
```
```json
200
{
  "info": {
    "domain": "dataoorts.com",
    "email": "rajatvishwakarma3656@dataoorts.com",
    "email_avatar": null,
    "is_disposable": false,
    "is_free": false,
    "isv_domain": true,
    "isv_format": true,
    "isv_mx": null,
    "isv_noblock": true,
    "isv_nocatchall": true,
    "isv_nogeneric": true,
    "mx_record": "route1.mx.cloudflare.net",
    "provider": null,
    "result_cause": "no_connect",
    "test_result": "unknown",
    "test_score": 40
  },
  "user_info": {
    "accuracy": 0.75,
    "name": "Rajat Vishwakarma",
    "username": "rajatvishwakarma3656"
  }
}
```

### ➡️ Only Email Verification

```python
import requests, json

# Set Everything
URL = "https://cloud.dataoorts.com/ai_mails_api/v1"
API_KEY = <Your_Unify_API_Key>

response = requests.post(
    URL,
    headers={
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json"
    },
    json={
        "email": "quantum.rjvishwa@gmail.com",
        "info": "false"
    }
)

print(response.status_code)
print(json.dumps(response.json(), indent=2))
```
```json
200
{
  "info": {
    "domain": "gmail.com",
    "email": "quantum.rjvishwa@gmail.com",
    "email_avatar": null,
    "is_disposable": false,
    "is_free": true,
    "isv_domain": true,
    "isv_format": true,
    "isv_mx": true,
    "isv_noblock": true,
    "isv_nocatchall": true,
    "isv_nogeneric": true,
    "mx_record": "gmail-smtp-in.l.google.com",
    "provider": "gmail",
    "result_cause": "accepted_email",
    "test_result": "deliverable",
    "test_score": 100
  }
}
```

### ➡️ Only Email Data Prediction

{: important-title }
> API Endpoint URL:
>
> [https://cloud.dataoorts.com/ai_mails_api/data/v1](https://cloud.dataoorts.com/ai_mails_api/data/v1)
>

```python
import requests

# Replace with your valid API key
URL = "https://cloud.dataoorts.com/ai_mails_api/data/v1"
HEADERS = {"Authorization": "Bearer <Your_Unify_API_Key>"}
PAYLOAD = {"email": "rajat696viswwakarrma@gmail.com"}

response = requests.post(URL, json=PAYLOAD, headers=HEADERS)
print("Response JSON:", response.json())
```
```json
Response JSON: {'user_info': {'accuracy': 0.81, 'name': 'Rajat Vishwakarma', 'username': 'rajat696viswwakarrma'}}
```


{: .important }
> Feedback on our API<br>
> If you encounter any issues with the API, have feature requests, or want to share your thoughts, feel free to contact us at [help@dataoorts.com](help@dataoorts.com).
