---
layout: page
title: google/gemma-3-12b-it
permalink: /docs/googlegemma-3-12b-it/
parent: "Text Generation"
nav_order: 3
published: Jun 11, 2025
updated: Jun 11, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">


### The Gemma 3 series excels across a wide range of text-generation and image-comprehension tasks—such as question‑answering, summarization, and logical reasoning. These multimodal models accept both text and image inputs and produce text outputs. They offer an expansive 128 K‑token context window, support over 140 languages, and come in a broader variety of model sizes than earlier versions.


| Model Name                |google/gemma-3-12b-it                    |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.11  Per Million Tokens               |
| Model Cost(Output)        | $0.12 Per Million Tokens                |
| Model Hosted (Region)     | US, Norway and India                    |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 80,000 Tokens                           |
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
    "model": "google/gemma-3-12b-it",
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
        "response": "Okay, let's break down Deep Learning. As a deep learning engineer, I spend my days building, training, and deploying these models, so I'll give you a comprehensive explanation, covering the core concepts, history, why it's become so dominant, and some of the current landscape.  I'll structure this to be understandable, but also with enough technical depth to be useful.\n\n**1. The Big Picture: What is Deep Learning?**\n\nAt its heart, Deep Learning is a subfield of Machine Learning, which itself is a subfield of Artificial Intelligence.  Here's the hierarchy:\n\n*   **Artificial Intelligence (AI):** The broad concept of creating machines that can perform tasks that typically require human intelligence.\n*   **Machine Learning (ML):** A technique where machines learn from data *without* being explicitly programmed. Instead of writing rules, you feed the machine data, and it figures out the rules itself.\n*   **Deep Learning (DL):** A specific type of Machine Learning that uses artificial neural networks with *multiple layers* (hence \"deep\") to analyze data and extract complex patterns.\n\n**The Key: Neural Networks**\n\nDeep Learning's power comes from its use of Artificial Neural Networks (ANNs).  Let's unpack that:\n\n*   **Inspired by the Brain:** ANNs are loosely inspired by the structure and function of the human brain. They consist of interconnected nodes (neurons) organized in layers.\n*   **Layers:**\n    *   **Input Layer:** Receives the raw data.\n    *   **Hidden Layers:**  These are the \"deep\" part.  Multiple hidden layers perform complex feature extraction and transformation.  The more layers, the more complex the patterns the network can learn.\n    *   **Output Layer:** Produces the final prediction or classification.\n*   **Connections (Weights):**  Neurons in adjacent layers are connected. Each connection has a \"weight\" associated with it.  These weights determine the strength of the connection.  *Learning* in a neural network is primarily about adjusting these weights.\n*   **Activation Functions:** Each neuron applies an activation function to its input. This introduces non-linearity, which is *crucial* for deep learning to model complex relationships in data. Common activation functions include ReLU, Sigmoid, and Tanh.\n\n**2. Why \"Deep\"? The Power of Hierarchical Feature Extraction**\n\nThe \"deep\" in Deep Learning",
        "tool_calls": [],
        "usage": {
            "completion_tokens": 512,
            "prompt_tokens": 21,
            "total_tokens": 533
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