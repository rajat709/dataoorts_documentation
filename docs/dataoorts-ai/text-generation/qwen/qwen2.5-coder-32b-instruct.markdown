---
layout: page
title: qwen/qwen2.5-coder-32b-instruct
permalink: /docs/qweb-coder/
parent: "Text Generation"
nav_order: 10
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

### Qwen2.5‑Coder is the newest code‑specialized entry in the Qwen model family (formerly known as CodeQwen), now available in six sizes—0.5B, 1.5B, 3B, 7B, 14B, and 32B parameters—to cater to developers with diverse requirements. Building on the foundation laid by CodeQwen‑1.5, Qwen2.5‑Coder introduces several key enhancements.


| Model Name                |qwen/qwen2.5-coder-32b-instruct          |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.55 Per Million Tokens                |
| Model Cost(Output)        | $0.57 Per Million Tokens                |
| Model Hosted (Region)     | US, Norway, India and Japan             |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 32,500 Tokens                           |
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
    "model": "qwen/qwen2.5-coder-32b-instruct",
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
        "response": "Deep Learning is a subset of machine learning that is inspired by the structure and function of the human brain, particularly the way neurons connect and learn from data. It involves the use of neural networks with many layers (hence \"deep\") to model and solve complex problems. Here are some key aspects of deep learning:\n\n1. **Neural Networks**: At the core of deep learning are artificial neural networks (ANNs), which are composed of layers of interconnected nodes or \"neurons.\" Each neuron receives input, processes it, and passes it on to the next layer.\n\n2. **Layers**: Deep learning models typically have multiple layers, including input layers, hidden layers, and output layers. The hidden layers are where the model learns to extract features from the input data.\n\n3. **Training**: Deep learning models are trained on large datasets using algorithms like backpropagation and gradient descent. During training, the model adjusts the weights of the connections between neurons to minimize the difference between its predictions and the actual outcomes.\n\n4. **Feature Learning**: One of the key advantages of deep learning is its ability to automatically learn features from raw data. This is particularly useful in domains like image and speech recognition, where manual feature extraction can be challenging.\n\n5. **Applications**: Deep learning has a wide range of applications, including image and video recognition, natural language processing, speech recognition, autonomous vehicles, and more.\n\n6. **Challenges**: Despite its successes, deep learning also faces challenges, such as the need for large amounts of data, high computational resources, and the difficulty of interpreting the decisions made by complex models (often referred to as the \"black box\" problem).\n\n7. **Frameworks**: Popular deep learning frameworks include TensorFlow, PyTorch, Keras, and Caffe, which provide tools and libraries to build, train, and deploy deep learning models efficiently.\n\nIn summary, deep learning is a powerful tool for solving complex problems by learning from data, and it has revolutionized many fields by enabling machines to perform tasks that were previously thought to be too complex for automation.",
        "tool_calls": [],
        "usage": {
            "completion_tokens": 416,
            "prompt_tokens": 24,
            "total_tokens": 440
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