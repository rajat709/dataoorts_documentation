---
layout: page
title: black-forest-labs/flux-1-schnell
permalink: /docs/black-forest-labsflux-1-schnell/
parent: "Image Generation"
nav_order: 1
published: Jun 28, 2025
updated: Jun 28, 2025
---

# {{page.title}}

<div style="font-size:0.78em;color: #797878; margin-bottom:1.5em;">
     <span>Updated on {{page.updated}}</span>
    <span style="margin-left:2em;">Published on {{page.published}}</span>
</div>

<hr style="border:none;height:3px;background-color:#e0e0e0;margin:0;">
<hr style="border:none;height:3px;background-color:#bebebe;margin-top:0.2em;margin-bottom:1.5em;">


### FLUX.1 [schnell] is a rectified flow transformer with 12 billion parameters, designed to generate images from text descriptions.
<br>


| Model Name                |    black-forest-labs/flux-1-schnell|
|---------------------------|------------------------------------|
| Model Type                |    Image Generation                |
| Model Cost                | $0.0012 Per Image                  |
| Model Hosted (Region)     | US, Norway, India, and Germany     |
| Model Available (Region)  | Global                             |
| Model Base Architecture   | Diffusion                          |
| Model Endpoint Access URL | https://cloud.dataoorts.com/api/v1 |

<br>

{: .important }
> Get Your API Credential From: [https://cloud.dataoorts.com/ai](https://cloud.dataoorts.com/ai)

```python
import requests
import json
import base64

## Define the endpoint URL
url = 'https://cloud.dataoorts.com/api/v1'

## Define the headers including the API Authorization token
headers = {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer $Dataoorts_Serverless_API_KEY'
}

## Define the Model Name and Data Payload with Optional Additional Hyper-Parameters
payload = {
    "model": "black-forest-labs/flux-1-schnell",
    "data": {
        ## Prompt Required: A text description of the image you want to generate (min 2, max 2048)
        "prompt": "A tiny astronaut hatching from an egg on the moon",
        ## Steps Default 4: The number of diffusion steps; higher values can improve quality but take longer (min 1, max 8)
        #"steps": 8,
        ## Optional: Random seed for reproducibility of the image generation
        #"seed": '12345'
    }
}

# Fire the request
response = requests.post(url, headers=headers, json=payload, timeout=30)
try:
    response.raise_for_status()
except requests.exceptions.HTTPError as e:
    print("Request failed:", e)
    print("Response body:", response.text)
    raise

# Decide how to unpack the result
content_type = response.headers.get("Content-Type", "")

if content_type.startswith("application/json"):
    # JSON envelope → extract and decode Base64
    js = response.json()
    b64 = js.get("result", {}).get("image_base64")
    if not b64:
        raise ValueError("No image_base64 field in JSON response!")
    try:
        image_bytes = base64.b64decode(b64)
    except Exception as e:
        raise ValueError(f"Failed to decode Base64 image data: {e}")
else:
    # Raw bytes
    image_bytes = response.content

# Write out the PNG
with open('output.png', 'wb') as f:
    f.write(image_bytes)

print("Image saved as output.png")
```
<br>

{: .new }
> The provided example for API access is written in Python, but you can use any programming language of your choice to adapt and transform the code as needed. Below, the example output image is shared for reference.

![output.png](image-gen.webp)