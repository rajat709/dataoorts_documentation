---
layout: page
title: meta/llama-3.1-70b-instruct
permalink: /docs/metallama-3.1-70b-instruct/
parent: "Text Generation"
nav_order: 6
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

### The Meta Llama 3.1 series comprises multilingual large language models that are both pretrained and instruction-tuned for generative tasks. The text-only instruction-tuned models in the Llama 3.1 collection are specifically optimized for multilingual dialogue applications and outperform numerous open-source and proprietary chat models on standard industry benchmarks.


| Model Name                |meta/llama-3.1-70b-instruct              |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.31 Per Million Tokens                |
| Model Cost(Output)        | $0.34 Per Million Tokens                |
| Model Hosted (Region)     | Norway and India                        |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 25,000 Tokens                           |
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
    "model": "meta/llama-3.1-70b-instruct",
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
        "response": "Deep learning is a subset of machine learning that involves the use of artificial neural networks to analyze and interpret data. Inspired by the structure and function of the human brain, deep learning algorithms are designed to learn and improve on their own by automatically adjusting the connections between nodes or \"neurons\" in the network.\n\nIn traditional machine learning, a model is trained on a dataset using a set of hand-engineered features, which are carefully designed and selected by a human expert. In contrast, deep learning algorithms can automatically learn the relevant features from the data itself, without the need for manual feature engineering.\n\nDeep learning models are typically composed of multiple layers of interconnected nodes or \"neurons\", which process and transform the input data in a hierarchical manner. Each layer learns to represent the input data in a more abstract and higher-level way, allowing the model to capture complex patterns and relationships in the data.\n\nSome key characteristics of deep learning include:\n\n1. **Distributed representations**: Deep learning models learn to represent the input data as a distributed pattern of activity across multiple nodes, rather than relying on a single node or feature.\n2. **Hierarchical representations**: Deep learning models learn to represent the input data in a hierarchical manner, with early layers learning low-level features and later layers learning higher-level features.\n3. **Automatic feature learning**: Deep learning models can automatically learn the relevant features from the data itself, without the need for manual feature engineering.\n4. **Large capacity**: Deep learning models can learn to represent very complex patterns and relationships in the data, making them suitable for tasks such as image and speech recognition, natural language processing, and more.\n\nSome common types of deep learning models include:\n\n1. **Convolutional Neural Networks (CNNs)**: Designed for image and video processing, CNNs use convolutional and pooling layers to extract features from data with grid-like topology.\n2. **Recurrent Neural Networks (RNNs)**: Designed for sequential data such as text, speech, or time series data, RNNs use recurrent connections to capture temporal relationships.\n3. **Autoencoders**: Designed for dimensionality reduction and generative modeling, autoencoders learn to compress and reconstruct the input data.\n4. **Generative Adversarial Networks (GANs)**: Designed for generative modeling, GANs learn to generate new data samples that are similar to the training data.\n\nDeep learning has many applications in areas such as:\n\n1. **Computer Vision**: Image classification, object detection, segmentation, and generation.\n2. **Natural Language Processing",
        "usage": {
            "completion_tokens": 512,
            "prompt_tokens": 27,
            "total_tokens": 539
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