---
layout: page
title: qwen/qwq-32b 
permalink: /docs/qwenqwen-32b/
parent: "Text Generation"
nav_order: 9
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

### QwQ is the dedicated reasoning model within Alibaba’s Qwen family. Unlike standard instruction-tuned models, QwQ is built to think and reason, delivering superior performance on challenging tasks. In particular, QwQ‑32B, the mid‑sized variant with approximately 32 billion parameters, achieves competitive results against leading reasoning models like DeepSeek‑R1 and o1‑mini.

| Model Name                |qwen/qwq-32b                             |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.54 Per Million Tokens                |
| Model Cost(Output)        | $0.57 Per Million Tokens                |
| Model Hosted (Region)     | US, France, India and South Korea       |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 24,000 Tokens                           |
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
    "model": "qwen/qwq-32b",
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
        "response": "Okay, so I need to explain what deep learning is. Hmm, I remember it's a part of machine learning, but I'm not entirely sure how it differs. Let me think. Machine learning involves algorithms that learn from data, right? And deep learning is a subset of that. Oh, right, it's inspired by the structure of the human brain, called artificial neural networks.\n\nWait, what's a neural network? I think it's a series of layers that process information. So, in deep learning, these networks have multiple layers, hence the term \"deep.\" Each layer learns different features from the data. For example, in image recognition, the first layer might detect edges, the next one shapes, and so on until it can recognize objects.\n\nBut how does it learn? I think it's through a process called backpropagation. The network makes predictions, compares them to the actual answers, and adjusts its weights to minimize errors. This happens over many iterations, allowing the model to improve.\n\nDeep learning can handle large amounts of data and find complex patterns that might be hard for humans to detect. It's used in various applications like speech recognition, natural language processing, and autonomous vehicles.\n\nWait, what about the differences between deep learning and traditional machine learning? Traditional methods often rely on feature engineering, where humans manually select the important features. Deep learning, on the other hand, can automatically learn these features from the data, which is a big advantage, especially with unstructured data like images or text.\n\nAlso, deep learning models typically require more data and computational resources to train effectively. They use techniques like convolutional neural networks for images and recurrent neural networks for sequences, which are specialized for their tasks.\n\nI should mention some common deep learning frameworks like TensorFlow, PyTorch, and Keras. These tools make it easier to build and train models without getting too deep into the math.\n\nIn summary, deep learning is a powerful approach within machine learning that uses neural networks with many layers to learn representations of data, enabling it to perform complex tasks with high accuracy when given sufficient data and computational resources.\n</think>\n\nDeep learning is a subset of machine learning that utilizes artificial neural networks with multiple layers to learn and make decisions. Inspired by the human brain, these networks process information through layers, each extracting different features. For instance, in image recognition, initial layers detect edges, while subsequent layers identify shapes and objects.\n\nThe learning process involves backpropagation, where the network adjusts its weights to minimize prediction errors over iterations. Unlike traditional machine learning,",
        "usage": {
            "completion_tokens": 512,
            "prompt_tokens": 19,
            "total_tokens": 531
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