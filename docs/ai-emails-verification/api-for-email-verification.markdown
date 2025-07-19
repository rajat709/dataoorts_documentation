---
layout: page
title: "API For Email Verification" 
permalink: /docs/api-email-verification/
nav_order: 6
parent: "AI Powered Email Verification"
---

> Asynchronous Architecture <br>
Our API features an async architecture, allowing you to handle multiple requests seamlessly and execute parallel operations efficiently.

> Multiple failed and unauthorized attempts will result in a permanent IP block.

## 👉 Get your Unify API KEY [Here](https://cloud.dataoorts.com/unify_api)

![Dataoorts Unify API - AI Mails Verification](api_for_email_verification.jpg)

> Our REST API enables AI-powered email verification and is compatible with any framework. For demonstration purposes, we have used Python as an example.

## 1. For Single Email Verification

> API Endpoint URL:
<br>https://cloud.dataoorts.com/ai_mails_api/v1

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

> API Endpoint URL:
<br>https://cloud.dataoorts.com/ai_mails_api/data/v1


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

## 2. For Bulk Email Verification
> API Endpoint URL:
<br>https://cloud.dataoorts.com/ai_mails_api/bulk/v1


```python
# Health Check - Endpoint
import requests, json

URL = "https://cloud.dataoorts.com/ai_mails_api/bulk/v1"

resp = requests.get(URL)
print(resp.status_code)
print(json.dumps(resp.json(), indent=2))
```
```json
200
{
  "status": "All Services Operational"
}
```

### ➡️ Submit and Queue the Batch Request
> Current Limits for Bulk Email Verification:
* The maximum limit for a single batch of email verification is 50,000 emails or fewer.
* If you need to verify more than 50,000 emails, you can process them in multiple batches, with each batch containing no more than 50,000 emails.
* You may submit up to three batches per day under this default limit.
<br><br>→ Need a Higher Limit?
        This limit can be increased on a case-by-case basis. If you require a higher quota, please contact our team at help@dataoorts.com to request an increase.
<br><br>→ Single Email Verification:
    There are no limits for single email verification—verify as many emails as you need, asynchronously!

```python
import json, requests

# Replace with your valid API key
URL = "https://cloud.dataoorts.com/ai_mails_api/bulk/v1"
API_KEY = <Your_Unify_API_Key>

# Example batch of emails
emails = [
    "alice@example.com",
    "bob@example.net",
    "carol@example.org"
]

response = requests.post(
    URL,
    headers={
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json"
    },
    json={"emails": emails}
)

# Ensure that you save the response unique batch ID, as it is volatile.
print(response.status_code)
print(json.dumps(response.json(), indent=2))
```
```json
200
{
  "id": "0KVBG3TK6QXFJKIYY6Z4ECA7AXZ"
}
```
### ➡️ Retrieve the Batch Response Using its Unique ID

> API Endpoint URL:
<br> https://cloud.dataoorts.com/ai_mails_api/bulk_results/v1

> Multiple failed and unauthorized attempts to retrieve the batch response will result in a permanent IP block.

```python
import json, requests

# Replace with your valid API key
URL = "https://cloud.dataoorts.com/ai_mails_api/bulk_results/v1"
API_KEY = <Your_Unify_API_Key>

# Use the valid batch ID obtained from the batch submission response.
payload = {"id": "0KVBG3TK6QXFJKIYY6Z4ECA7AXZ"}

response = requests.post(
    URL,
    headers={
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json"
    },
    json=payload
)

print(response.status_code)
print(json.dumps(response.json(), indent=2))
```
```json
200
[
  {
    "domain": "example.org",
    "email": "carol@example.org",
    "email_avatar": null,
    "is_disposable": false,
    "is_free": false,
    "isv_domain": true,
    "isv_format": true,
    "isv_mx": null,
    "isv_noblock": true,
    "isv_nocatchall": true,
    "isv_nogeneric": true,
    "mx_record": "",
    "provider": null,
    "result_cause": "no_connect",
    "test_result": "unknown",
    "test_score": 40,
    "username": "carol"
  },
  {
    "domain": "example.net",
    "email": "bob@example.net",
    "email_avatar": null,
    "is_disposable": false,
    "is_free": false,
    "isv_domain": true,
    "isv_format": true,
    "isv_mx": null,
    "isv_noblock": true,
    "isv_nocatchall": true,
    "isv_nogeneric": true,
    "mx_record": "",
    "provider": null,
    "result_cause": "no_connect",
    "test_result": "unknown",
    "test_score": 40,
    "username": "bob"
  },
  {
    "domain": "example.com",
    "email": "alice@example.com",
    "email_avatar": null,
    "is_disposable": true,
    "is_free": false,
    "isv_domain": true,
    "isv_format": true,
    "isv_mx": null,
    "isv_noblock": true,
    "isv_nocatchall": true,
    "isv_nogeneric": true,
    "mx_record": "",
    "provider": null,
    "result_cause": "no_connect",
    "test_result": "unknown",
    "test_score": 10,
    "username": "alice"
  }
]
```

> Feedback on our API<br>
If you encounter any issues with the API, have feature requests, or want to share your thoughts, feel free to contact us at [help@dataoorts.com](help@dataoorts.com).
