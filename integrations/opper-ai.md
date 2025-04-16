---
description: Setting Up An LLM Access Platform With $10 Credits Per Month
---

# Opper AI

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Go to [https://opper.ai/](https://opper.ai/) and sign up for a free account.

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Click on "Settings" in the bottom of the left sidebar. Click "API Keys" in the main section. Click "Create API Key" in the top right corner.&#x20;

Store the API key in your Polytope vault by running the following command in your system project directory.

```
pt secret set opper-api-key YOUR_OPPER_API_KEY
```

## Using Opper AI

We use [Opper AI](https://opper.ai) for LLM response generation and knowledge base integration. The response generation follows a pattern:

```python
def bake_response(messages):
    response, _ = opper.call(
        name="generate_response",
        instructions="Generate a helpful, friendly but brief response to the user's message in the conversation.",
        input={"messages": messages},
        output_type=str,
    )
    return response
```

Learn more about the [Opper SDK on GitHub](https://github.com/opper-ai/opper-python) and in the [official documentation](https://docs.opper.ai/).
