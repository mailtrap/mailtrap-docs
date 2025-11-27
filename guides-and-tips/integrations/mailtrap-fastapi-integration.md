---
title: <i class="fa-python">:python:</i> Mailtrap FastAPI Integration
description: >-
  Learn how to integrate Mailtrap with FastAPI to send emails using the Email
  API.
---

# FastAPI Integration

This guide shows you how to integrate Mailtrap with FastAPI and send emails using the Email API.

Before we start, you'll need to:

* [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
* [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens)

## Send emails using FastAPI and Mailtrap

To integrate Mailtrap and send emails via FastAPI, simply copy/paste the following script into your configuration:

{% code title="fastapi-example.py" %}
```python
import mailtrap as mt
from typing import Dict
from fastapi import FastAPI

app = FastAPI()

@app.post("/")
def send_mail() -> Dict:
    mail = mt.Mail(
        sender=mt.Address(email="YOUR-EMAIL-HERE", name="Mailtrap Test"),
        to=[mt.Address(email="RECIPIENT-EMAIL-HERE")],
        subject="Hello World",
        html="<strong>it works!</strong>",
    )

    client = mt.MailtrapClient(token="YOUR-MAILTRAP-API-KEY-HERE")
    response = client.send(mail)

    return response
```
{% endcode %}

Once you copy the script, make sure to insert your Mailtrap API token in the `token=` field and enter your and your recipient's emails in the `sender=` and `to=` fields.

{% hint style="info" %}
To learn more about API integration, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}
