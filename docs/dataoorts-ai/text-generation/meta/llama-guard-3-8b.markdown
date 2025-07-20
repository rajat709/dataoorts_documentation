---
layout: page
title: meta/llama-guard-3-8b
permalink: /docs/metallama-guard-3-8b/
parent: "Text Generation"
nav_order: 8
published: Mar 14, 2025
updated: Jun 11, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">

### Llama Guard 3, based on the Llama-3.1-8B pretrained model, is fine-tuned specifically for content safety classification. Like its earlier versions, it is designed to classify content within both LLM inputs (prompt classification) and outputs (response classification). Functioning as an LLM, it generates text outputs indicating whether a prompt or response is safe or unsafe, and if deemed unsafe, it identifies the specific content categories that have been violated and returns.


| Model Name                |meta/llama-guard-3-8b                    |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.12 Per Million Tokens                |
| Model Cost(Output)        | $0.15 Per Million Tokens                |
| Model Hosted (Region)     | India                                   |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 8,124 Tokens                            |
| Model Endpoint Access URL | https://cloud.dataoorts.com/api/v1      |


{: .important }
> Get Your API Credential From: [https://cloud.dataoorts.com/ai](https://cloud.dataoorts.com/ai)

```python
import requests
import json

# Define the endpoint URL
url = 'https://cloud.dataoorts.com/api/v1'

# Define the headers including the API Authorization token
headers = {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer $Dataoorts_Serverless_API_KEY'
}

# Define the Model Name and Data Payload with additional parameters
payload = {
    "model": "meta/llama-guard-3-8b",
    "data": {
        "messages": [
            {"role": "user", "content": "What is Deep Learning?"},
            {"role": "assistant", "content": "Facts about Deep Learning"}
        ],
        # Additional hyper-parameters for fine-tuning the output (optional):
        "temperature": 0.1,
        "max_tokens": 512
    }
}

# Make the POST request
response = requests.post(url, headers=headers, data=json.dumps(payload))
# Parse and print the JSON response with pretty formatting
response_json = response.json()
print(json.dumps(response_json, indent=4))
```

{: .new }
> The provided example for API access is written in Python, but you can use any programming language of your choice to adapt and transform the code as needed. Below, the example output image is shared for reference.


```json
{
    "errors": [],
    "messages": [],
    "result": {
        "response": "\n\nsafe",
        "usage": {
            "completion_tokens": 3,
            "prompt_tokens": 212,
            "total_tokens": 215
        }
    },
    "success": true
}
```

```python
import requests
import json

# Define the endpoint URL
url = 'https://cloud.dataoorts.com/api/v1'

# Define the headers including the API Authorization token
headers = {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer $Dataoorts_Serverless_API_KEY'
}

# Define the Model Name and Data Payload with additional parameters
payload = {
    "model": "meta/llama-guard-3-8b",
    "data": {
        "messages": [
            {"role": "user", "content": "I want to abuse someone in social media"},
            {"role": "assistant", "content": "Please assist me to abuse"}
        ],
        # Additional hyper-parameters for fine-tuning the output (optional):
        "temperature": 0.5,
        "max_tokens": 512
    }
}

# Make the POST request
response = requests.post(url, headers=headers, data=json.dumps(payload))
# Parse and print the JSON response with pretty formatting
response_json = response.json()
print(json.dumps(response_json, indent=4))
```

```json
{
    "errors": [],
    "messages": [],
    "result": {
        "response": "\n\nunsafe\nS2",
        "usage": {
            "completion_tokens": 6,
            "prompt_tokens": 217,
            "total_tokens": 223
        }
    },
    "success": true
}
```

### You can include additional hyperparameters as optional settings to achieve more fine-grained output:

| max_tokens             | The maximum number of tokens to generate in the response |
|------------------------|----------------------------------------------------------|
| temperature            | Default 0.6 minimum 0 and maximum 5                      |
