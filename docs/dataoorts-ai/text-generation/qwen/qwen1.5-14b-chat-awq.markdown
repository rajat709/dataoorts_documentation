---
layout: page
title: qwen/qwen1.5-14b-chat-awq 
permalink: /docs/qwenqwen15-14b-chat-awq/
parent: "Text Generation"
nav_order: 10
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

### Qwen1.5 is an enhanced iteration of Qwen, the large language model series created by Alibaba Cloud. AWQ is a highly efficient, precise, and ultra-fast low-bit weight quantization technique, currently supporting 4-bit quantization.

| Model Name                |qwen/qwen1.5-14b-chat-awq                |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.11 Per Million Tokens                |
| Model Cost(Output)        | $0.12 Per Million Tokens                |
| Model Hosted (Region)     | Finland                                 |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 8,000 Tokens                            |
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
    "model": "qwen/qwen1.5-14b-chat-awq",
    "data": {
        "messages": [
            {"role": "system", "content": "You are an expert deep learning engineer"},
            {"role": "user", "content": "What is Deep Learning"}
        ],
        # Additional hyper-parameters for fine-tuning the output (optional):
        "temperature": 0.1,
        "top_p": 0.9,
        "top_k": 40,
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
        "response": "Deep Learning is a subset of machine learning, a branch of artificial intelligence, that involves the use of artificial neural networks to solve complex problems. It is inspired by the structure and function of the human brain, where multiple layers of interconnected nodes (artificial neurons) process and learn from data.\n\nIn deep learning, these networks consist of multiple hidden layers, allowing them to learn hierarchical representations of the input data. Each layer extracts increasingly abstract features, enabling the model to learn and generalize from large, high-dimensional datasets. The process involves forward propagation, where input data is fed through the network, and backpropagation, where the model adjusts its weights to minimize the error between predicted and actual outputs.\n\nDeep learning has been particularly successful in various applications, such as image recognition, speech recognition, natural language processing, recommendation systems, and autonomous vehicles, due to its ability to automatically learn and extract relevant features without manual feature engineering. Some popular deep learning architectures include Convolutional Neural Networks (CNNs) for image analysis, Recurrent Neural Networks (RNNs) for sequential data, and Transformers for natural language processing.",
        "usage": {
            "completion_tokens": 223,
            "prompt_tokens": 24,
            "total_tokens": 247
        }
    },
    "success": true
}
```

### You can include additional hyperparameters as optional settings to achieve more fine-grained output:

| max_tokens             | The maximum number of tokens to generate in the response |
|------------------------|----------------------------------------------------------|
| temperature            | Default 0.6 minimum 0 and maximum 5                      |
| top_p                  | minimum 0 and maximum 2                                  |
| top_k                  | minimum 1 and maximum 50                                 |
| seed                   |  minimum 1 and maximum 9999999999                        |
| repetition_penalty     | minimum 0 and maximum 2                                  |
| frequency_penalty      | minimum 0 and maximum 2                                  |
| presence_penalty       |minimum 0 and maximum 2                                   |