---
layout: page
title: bytedance/stable-diffusion-xl-lightning
permalink: /docs/bytedancestable-diffusion-xl-lightning/
parent: "Image Generation"
nav_order: 3
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


### SDXL-Lightning is an exceptionally fast text-to-image generation model, capable of producing high-quality 1024px images in just a few steps.


| Model Name                | bytedance/stable-diffusion-xl-lightning |
|---------------------------|-----------------------------------------|
| Model Type                |    Image Generation                     |
| Model Cost                | $0.0011 Per Image                        |
| Model Hosted (Region)     | US and India                            |
| Model Available (Region)  | Global                                  |
| Model Base Architecture   | Diffusion                               |
| Model Endpoint Access URL | https://cloud.dataoorts.com/api/v1      |


{: .important }
> Get Your API Credential From: [https://cloud.dataoorts.com/ai](https://cloud.dataoorts.com/ai)


```python
import requests
import json

## Define the endpoint URL
url = 'https://cloud.dataoorts.com/api/v1'

## Define the headers including the API Authorization token
headers = {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer $Dataoorts_Serverless_API_KEY'
}

## Define the Model Name and Data Payload with Optional Additional Hyper-Parameters
payload = {
    "model": "bytedance/stable-diffusion-xl-lightning",
    "data": {
        ## Required: A text description of the image you want to generate (min 2)
        "prompt": "futuristic spacecraft",
        ## Optional: Text describing elements to avoid in the generated image
        #"negative_prompt": "blurry, low quality, deformed",
        ## Optional: Height of the generated image in pixels (min 256, max 2048)
        #"height": 512,
        ## Optional*: Width of the generated image in pixels (min 256, max 2048)
        #"width": 512,
        ## Optional: Number of diffusion steps; default is 20 (max 20)
        #"num_steps": 20,
        ## Optional: Guidance scale; higher values make the image more aligned with the prompt (default 7.5)
        #"guidance": 7.5,
        ## Optional: Random seed for reproducibility of the image generation
        #"seed": 12345
    }
}

## Make the POST request and save the output to a file
response = requests.post(url, headers=headers, data=json.dumps(payload))
## Save the response content as an image file
with open('output.png', 'wb') as f:
    f.write(response.content)
print("Image saved as output.png")
```

{: .new }
> The provided example for API access is written in Python, but you can use any programming language of your choice to adapt and transform the code as needed. Below, the example output image is shared for reference.

![output.png](bytedance-stable-diffusion-xl-base-1.0.jpg)
