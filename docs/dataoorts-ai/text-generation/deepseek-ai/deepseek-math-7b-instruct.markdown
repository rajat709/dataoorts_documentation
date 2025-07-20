---
layout: page
title: deepseek-ai/deepseek-math-7b-instruct
permalink: /docs/deepseek-aideepseek-math-7b-instruct/
parent: "Text Generation"
nav_order: 2
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


### DeepSeekMath-Instruct 7B is a fine-tuned mathematical model based on DeepSeekMath-Base 7B. It originates from DeepSeek-Coder-v1.5 7B and undergoes additional pre-training on 500B tokens, incorporating math-related data from Common Crawl, as well as natural language and code data.


| Model Name                |deepseek-ai/deepseek-math-7b-instruct    |
|---------------------------|-----------------------------------------|
| Model Type                |    Text  Generation                     |
| Model Cost(Input)         | $0.10 Per Million Tokens                |
| Model Cost(Output)        | $0.11 Per Million Tokens                |
| Model Hosted (Region)     | US and India                            |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Transformer                             |
| Context Window            | 4,096 Tokens                            |
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
    "model": "deepseek-ai/deepseek-math-7b-instruct",
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
        "response": "branch of artificial intelligence. It is a set of algorithms that allows computers to learn from data without being explicitly programmed. Deep learning algorithms are inspired by the way the brain learns from experience and are used to solve complex problems such as image recognition, speech recognition, and natural language processing. Deep learning is a powerful tool that can help us understand and solve problems in various fields, including medicine, finance, and robotics. As a deep learning engineer, you are responsible for designing and implementing deep learning algorithms to solve specific problems. You may work on projects that involve building models to recognize objects in images, translating text from one language to another, or predicting the behavior of complex systems. To become a deep learning engineer, you need to have a strong background in mathematics, computer science, and statistics. You should be familiar with algorithms, data structures, and programming languages such as Python and TensorFlow. You should also have a good understanding of machine learning concepts, such as supervised and unsupervised learning, and be able to apply these concepts to solve real-world problems. As a deep learning engineer, you will be working with large amounts of data and will need to be able to analyze and interpret results effectively. You will also need to be able to communicate your findings and explain the results of your work to non-technical stakeholders. Deep learning is a rapidly growing field, and there are many opportunities for career advancement and innovation. If you are passionate about solving complex problems and want to make a difference in the world, consider becoming a deep learning engineer.",
        "usage": {
            "completion_tokens": 321,
            "prompt_tokens": 12,
            "total_tokens": 333
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