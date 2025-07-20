---
layout: page
title: meta/llama-4-scout-17b-16e-instruct
permalink: /docs/meta-4/
parent: "Text Generation"
nav_order: 4
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

### Meta’s Llama 4 Scout is a native multimodal model featuring a 17-billion‑parameter "active" layer, supported by 16 experts, and built on a mixture‑of‑experts architecture. It delivers state‑of‑the‑art performance in both text and image understanding, thanks to its efficient design and expert routing.

| Model Name                |meta/llama-4-scout-17b-16e-instruct      |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.32 Per Million Tokens                |
| Model Cost(Output)        | $0.34 Per Million Tokens                |
| Model Hosted (Region)     | US, Norway, India and Japan             |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 130,000 Tokens                          |
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
    "model": "meta/llama-4-scout-17b-16e-instruct",
    "data": {
        "messages": [
            {"role": "system", "content": "You are an expert deep learning engineer"},
            {"role": "user", "content": "What is Deep Learning"}
        ],
        # Additional hyper-parameters for fine-tuning the output (optional):
        "temperature": 0.1,
        "top_p": 0.9,
        "top_k": 40,
        "max_tokens": 1024
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
        "response": "Deep learning! It's a fascinating field that has revolutionized the way we approach artificial intelligence, machine learning, and data analysis. So, let's dive in!\n\n**What is Deep Learning?**\n\nDeep learning is a subset of machine learning, which is a type of artificial intelligence (AI) that enables computers to learn from data without being explicitly programmed. Deep learning is inspired by the structure and function of the human brain, specifically the neural networks that process and transmit information.\n\nIn traditional machine learning, algorithms are designed to learn from data using a single layer of features, which are often hand-engineered by experts. In contrast, deep learning algorithms use multiple layers of artificial neural networks to learn complex patterns and representations from data. These neural networks are composed of multiple layers of interconnected nodes or \"neurons,\" which process and transform inputs into meaningful representations.\n\n**Key Characteristics of Deep Learning:**\n\n1. **Multiple Layers**: Deep learning algorithms use multiple layers of neural networks to learn hierarchical representations of data. Each layer learns to recognize specific features or patterns, which are then combined to form more abstract representations.\n2. **Neural Networks**: Deep learning algorithms are based on artificial neural networks, which are composed of nodes or \"neurons\" that process and transmit information.\n3. **Distributed Representations**: Deep learning algorithms learn distributed representations of data, where each feature or pattern is represented as a combination of multiple nodes or neurons.\n4. **Automatic Feature Learning**: Deep learning algorithms can automatically learn relevant features from data, eliminating the need for manual feature engineering.\n\n**Types of Deep Learning:**\n\n1. **Convolutional Neural Networks (CNNs)**: CNNs are commonly used for image and video processing tasks, such as image classification, object detection, and segmentation.\n2. **Recurrent Neural Networks (RNNs)**: RNNs are used for sequential data, such as speech, text, or time series data, and are commonly used for tasks like language modeling, speech recognition, and machine translation.\n3. **Autoencoders**: Autoencoders are used for unsupervised learning tasks, such as dimensionality reduction, anomaly detection, and generative modeling.\n4. **Generative Adversarial Networks (GANs)**: GANs are used for generative modeling tasks, such as generating new images, videos, or music.\n\n**Applications of Deep Learning:**\n\n1. **Computer Vision**: Deep learning is widely used in computer vision applications, such as image classification, object detection, segmentation, and generation.\n2. **Natural Language Processing (NLP)**: Deep learning is used in NLP applications, such as language modeling, text classification, sentiment analysis, and machine translation.\n3. **Speech Recognition**: Deep learning is used in speech recognition systems, such as Siri, Alexa, and Google Assistant.\n4. **Robotics**: Deep learning is used in robotics to enable robots to learn from experience and adapt to new situations.\n\n**Real-World Examples:**\n\n1. **Self-Driving Cars**: Deep learning is used in self-driving cars to detect and respond to objects, such as pedestrians, cars, and road signs.\n2. **Virtual Assistants**: Deep learning is used in virtual assistants, such as Siri, Alexa, and Google Assistant, to understand voice commands and respond accordingly.\n3. **Medical Diagnosis**: Deep learning is used in medical diagnosis to analyze medical images, such as X-rays and MRIs, and detect diseases like cancer.\n4. **Recommendation Systems**: Deep learning is used in recommendation systems, such as those used by Netflix and Amazon, to suggest personalized products or content.\n\nIn summary, deep learning is a powerful subset of machine learning that uses multiple layers of neural networks to learn complex patterns and representations from data. Its applications are diverse and widespread, and it has the potential to revolutionize many industries and aspects of our lives.",
        "tool_calls": [],
        "usage": {
            "completion_tokens": 759,
            "prompt_tokens": 30,
            "total_tokens": 789
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