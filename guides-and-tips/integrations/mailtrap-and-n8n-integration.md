---
title: <i class="fa-diagram-project">:diagram-project:</i> N8N Integration
description: >-
  Seamlessly integrate Mailtrap into your N8N workflows to automate email
  sending and contact management tasks without coding.
---

# N8N Integration

<a href="https://n8n.io/integrations/mailtrap/" class="button primary">View on N8N Marketplace</a>

## Overview

Mailtrap can be integrated into N8N workflows to automate email sending and contact management. This guide shows you how to install the Mailtrap node, obtain API credentials, and configure N8N to work with Mailtrap.

In this article, you'll learn how to:

* Install Mailtrap node and set up N8N
* Obtain Mailtrap API credentials
* Integrate N8N with Mailtrap

### N8N Cloud

If you are a user of n8n Cloud, you can have access to Mailtrap integration out of the box.

Just search for "Mailtrap" in the nodes.

### Local N8N setup

To install Mailtrap node, you can simply type in `n8n-nodes-mailtrap` under 'Enter npm package name' in Community Nodes, just like so:

![N8N community nodes settings page with install dialog showing n8n-nodes-mailtrap package name and checkbox confirmation](../.gitbook/assets/mailtrap-and-n8n-integration-1.png)

Or, you can run use npm to install the node manually:

```
npm install n8n-nodes-mailtrap
```

Next, simply [create a free N8N account](https://app.n8n.cloud/register):

![N8N owner account setup form with fields for email, first name, last name, and password](../.gitbook/assets/mailtrap-and-n8n-integration-2.png)

### Obtain Mailtrap API credentials

Whether you want to only create contacts or send/test emails via Mailtrap and N8N, you'll first need a Mailtrap API token and Mailtrap Account ID. To obtain one, follow these steps:

{% stepper %}
{% step %}
#### Navigate to API Tokens

Go to **Settings** on the left side-bar menu, navigate to **API Tokens**, and click on **Add Token**.

![Mailtrap API Tokens page displaying list of existing tokens with their names, creators, access levels, and token values](../.gitbook/assets/mailtrap-and-n8n-integration-3.png)
{% endstep %}

{% step %}
#### Create a new API token

Enter the desired name, click on **Add Token**, tick the desired permission checkboxes, and hit **Save**.

![Mailtrap Add API Token dialog with permissions table showing different access levels for account features and domain-specific actions](../.gitbook/assets/mailtrap-and-n8n-integration-4.png)
{% endstep %}

{% step %}
#### Copy and save the token

Copy the token and save it in a secure place.

![Mailtrap Edit API Token page with copy button and reset button for managing the API token](../.gitbook/assets/mailtrap-and-n8n-integration-5.png)
{% endstep %}

{% step %}
#### Obtain the Account ID

To obtain the **Account ID**, go to **Settings** → **Account Settings** → **Account Details**.

![Mailtrap Account Settings page showing account details tab with account name, owner email, and account ID information](../.gitbook/assets/mailtrap-and-n8n-integration-6.png)
{% endstep %}
{% endstepper %}

### Integrate N8N with Mailtrap

{% stepper %}
{% step %}
#### Select Mailtrap

When you open your N8N dashboard, click on the left card 'Start from scratch'.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-7.png" alt="N8N workflows overview page with cards to create new workflows from scratch or use AI agent example" width="563"></div>

Then, click on the 'Add first step…'.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-8.png" alt="N8N workflow canvas with add node button highlighted in the center of empty workflow" width="563"></div>

On the right-side menu, type 'Mailtrap' in the search bar, click on it, and select which actions you want to automate (e.g., sending an email, creating/updating contacts, etc.).

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-9.png" alt="N8N node selection panel showing Mailtrap triggers and available contact-related actions in list format" width="563"></div>

Here's an example workflow I created for the purposes of this demo:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-10.png" alt="N8N workflow showing trigger connected to five sequential Mailtrap contact management nodes including get lists, create, update, and delete operations" width="563"></div>
{% endstep %}

{% step %}
#### Enter your Mailtrap credentials

In the parameters window, click on 'Select Credential' and '+ Create new credential' to add the credentials we obtained in the previous chapter.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-11.png" alt="Mailtrap node parameters showing Create Contact operation with dropdown for credential selection and fields for account ID and email" width="563"></div>

In the credentials setting, simply add the API Token and Mailtrap Host.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-12.png" alt="Mailtrap API Token credential dialog with fields for API token and mailing host configuration showing send.api.mailtrap.io" width="563"></div>

**Important**: Keep in mind that I've added my Sending credentials (send.api.mailtrap.io).

Then, back in the Parameters window, add the account ID.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-13.png" alt="Mailtrap node parameters panel configured for Get Contact Lists operation with account ID value entered in the field" width="563"></div>
{% endstep %}

{% step %}
#### Test the integration

Lastly, simply click on 'Test step' to test the integration:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-and-n8n-integration-14.png" alt="N8N workflow execution results showing three contact records with IDs and names successfully retrieved from Mailtrap" width="563"></div>

Now, every time a new user logs in and updates their name, they will get a confirmation email via Mailtrap and their information will be logged in my Mailtrap Contacts page. There, I can group them into lists, segment them accordingly, and use Fields to personalize my email campaigns further.
{% endstep %}
{% endstepper %}

## Next Steps

Once your N8N and Mailtrap integration is complete, you can leverage the full power of workflow automation to send targeted emails, manage contacts, and track engagement across your applications.
