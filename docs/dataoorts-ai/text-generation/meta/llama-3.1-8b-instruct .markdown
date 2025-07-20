---
layout: page
title: meta/llama-3.1-8b-instruct
permalink: /docs/metallama-3.1-8b-instruct/
parent: "Text Generation"
nav_order: 7
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

### The Meta Llama 3.1 8B series consists of multilingual large language models that are both pretrained and instruction-tuned for generative tasks. These text-only instruction-tuned models are specifically designed for multilingual dialogue scenarios and surpass many open-source and proprietary chat models in common industry benchmarks.


| Model Name                |meta/llama-3.1-8b-instruct               |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.07 Per Million Tokens                |
| Model Cost(Output)        | $0.08 Per Million Tokens                |
| Model Hosted (Region)     | US and India                            |
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
    "model": "meta/llama-3.1-8b-instruct",
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
        "response": "Deep learning is a subset of machine learning that involves the use of artificial neural networks (ANNs) to analyze and interpret data. It is a type of machine learning that is inspired by the structure and function of the human brain, with multiple layers of interconnected nodes or \"neurons\" that process and transmit information.\n\nDeep learning algorithms are designed to learn and improve their performance on a specific task by automatically adjusting the connections between these nodes, or \"weights,\" based on the data they are trained on. This process is called backpropagation, and it allows the network to learn complex patterns and relationships in the data.\n\nDeep learning has several key characteristics that distinguish it from other types of machine learning:\n\n1. **Multiple layers**: Deep learning models typically consist of multiple layers of interconnected nodes, with each layer processing the output of the previous layer.\n2. **Non-linearity**: Deep learning models use non-linear activation functions, such as the sigmoid or ReLU (Rectified Linear Unit) function, to introduce non-linearity into the model.\n3. **Large number of parameters**: Deep learning models have a large number of parameters, which are adjusted during training to optimize the model's performance.\n4. **Automatic feature learning**: Deep learning models can automatically learn relevant features from the data, rather than relying on hand-engineered features.\n\nSome common applications of deep learning include:\n\n1. **Computer vision**: Image and video analysis, object detection, image segmentation, and image generation.\n2. **Natural language processing**: Text classification, language translation, sentiment analysis, and text generation.\n3. **Speech recognition**: Speech-to-text systems, voice assistants, and speech recognition for voice-controlled interfaces.\n4. **Robotics**: Control of robots, autonomous vehicles, and other machines that require complex decision-making and control.\n\nSome popular deep learning architectures include:\n\n1. **Convolutional Neural Networks (CNNs)**: Used for image and video analysis.\n2. **Recurrent Neural Networks (RNNs)**: Used for sequential data, such as speech and text.\n3. **Long Short-Term Memory (LSTM) networks**: A type of RNN that is particularly well-suited for sequential data.\n4. **Generative Adversarial Networks (GANs)**: Used for generating new data that resembles existing data.\n\nDeep learning has many benefits, including:\n\n1. **Improved accuracy**: Deep learning models can achieve state-of-the-art performance on many tasks.\n2. **Automatic feature learning**: Deep learning models can automatically learn relevant features from the data.\n",
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