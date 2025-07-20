---
layout: page
title: meta/llama-3.3-70b-instruct-fp8-fast
permalink: /docs/metallama-3.3-70b-instruct-fp8-fast
parent: "Text Generation"
nav_order: 5
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

### Llama 3.3 70B has been quantized to FP8 precision, enhancing its optimization for improved speed.

| Model Name                |meta/llama-3.3-70b-instruct-fp8-fast     |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.31 Per Million Tokens                |
| Model Cost(Output)        | $0.34 Per Million Tokens                |
| Model Hosted (Region)     | US, Norway and India                    |
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
    "model": "meta/llama-3.3-70b-instruct-fp8-fast",
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
        "response": "Deep learning! It's a subset of machine learning that has revolutionized the field of artificial intelligence (AI) in recent years. Deep learning is a type of machine learning that involves the use of artificial neural networks to analyze and interpret data.\n\n**What makes deep learning \"deep\"?**\n\nThe term \"deep\" refers to the fact that these neural networks have multiple layers, typically more than two, which allows them to learn complex patterns and representations of data. Each layer in the network processes and transforms the input data in a hierarchical manner, enabling the network to learn abstract features and relationships.\n\n**Key characteristics of deep learning:**\n\n1. **Artificial neural networks**: Deep learning models are based on artificial neural networks, which are composed of interconnected nodes (neurons) that process and transmit information.\n2. **Multiple layers**: Deep learning models have multiple layers, including input layers, hidden layers, and output layers. Each layer processes the input data in a specific way, allowing the network to learn complex patterns.\n3. **Hierarchical representations**: Deep learning models learn hierarchical representations of data, where early layers learn simple features and later layers learn more complex features.\n4. **Large amounts of data**: Deep learning models require large amounts of data to train, as they need to learn from many examples to develop robust patterns and relationships.\n5. **Computational power**: Deep learning models require significant computational power to train, often using specialized hardware such as graphics processing units (GPUs) or tensor processing units (TPUs).\n\n**Types of deep learning models:**\n\n1. **Convolutional Neural Networks (CNNs)**: Used for image and video processing, object detection, and image classification.\n2. **Recurrent Neural Networks (RNNs)**: Used for sequential data such as speech, text, and time series data.\n3. **Autoencoders**: Used for dimensionality reduction, anomaly detection, and generative modeling.\n4. **Generative Adversarial Networks (GANs)**: Used for generative modeling, data augmentation, and style transfer.\n\n**Applications of deep learning:**\n\n1. **Computer vision**: Image classification, object detection, segmentation, and generation.\n2. **Natural Language Processing (NLP)**: Text classification, sentiment analysis, language translation, and text generation.\n3. **Speech recognition**: Speech-to-text, voice recognition, and speech synthesis.\n4. **Robotics**: Control, navigation, and manipulation.\n5. **Healthcare**: Medical imaging, disease diagnosis, and personalized medicine.\n\n**Challenges",
        "usage": {
            "completion_tokens": 512,
            "prompt_tokens": 28,
            "total_tokens": 540
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