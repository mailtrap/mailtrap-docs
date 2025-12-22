---
title: How to integrate Email Sandbox with your application
description: >-
  Learn how to integrate sandbox with your application using SMTP credentials or
  code samples
icon: gears
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Sandbox SMTP Integration

## Copy SMTP credentials

{% stepper %}
{% step %}
Go to **Email Testing** → **Sandboxes**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/sandbox-integration-navigate-to-sandboxes.png" alt="Navigation menu showing Email Testing section with Sandboxes option" width="563"></div>
{% endstep %}

{% step %}
Open the sandbox (named **My Sandbox**) created by default.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/sandbox-integration-open-my-sandbox.png" alt="Sandboxes list displaying My Sandbox and other project sandboxes" width="563"></div>
{% endstep %}

{% step %}
Under the **Integration** tab, select **SMTP** and copy the credentials such as Host, Port, Username, and Password.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/sandbox-integration-smtp-credentials.png" alt="Integration tab showing SMTP credentials including Host, Port, Username, and Password" width="563"></div>
{% endstep %}

{% step %}
Paste them into your email-sending script, service, or MTA (any service that supports SMTP integration), and run it. The email will arrive in your sandbox in a few seconds.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/sandbox-integration-email-received.png" alt="Sandbox inbox displaying received test email message" width="563"></div>
{% endstep %}
{% endstepper %}

## Select your integration

Instead of copy-pasting the SMTP credentials, you can use the code samples already containing your credentials.

{% stepper %}
{% step %}
In the **Integration** tab of your sandbox, scroll down to **Code Samples** and select the programming language or framework you're working with.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/sandbox-integration-code-samples.png" alt="Code Samples section showing various programming language options for integration" width="563"></div>
{% endstep %}

{% step %}
Copy the configuration and paste it into your email-sending script. Then, run it. The email will arrive in the sandbox in a few seconds.
{% endstep %}
{% endstepper %}

{% hint style="success" %}
_Learn how exactly Mailtrap can help you streamline email testing processes from our_ [_case study with The Software House_](https://mailtrap.io/case-studies/the-software-house/)_._
{% endhint %}
