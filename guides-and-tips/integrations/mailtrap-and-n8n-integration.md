---
title: <i class="fa-diagram-project">:diagram-project:</i> N8N Integration
description: >-
  Seamlessly integrate Mailtrap into your N8N workflows to automate email
  sending and contact management tasks without coding.
---

# N8N Integration

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
### Navigate to API Tokens

Go to **Settings** on the left side-bar menu, navigate to **API Tokens**, and click on **Add Token**.

![Mailtrap API Tokens page displaying list of existing tokens with their names, creators, access levels, and token values](../.gitbook/assets/mailtrap-and-n8n-integration-3.png)
{% endstep %}

{% step %}
### Create a new API token

Enter the desired name, click on **Add Token**, tick the desired permission checkboxes, and hit **Save**.

![Mailtrap Add API Token dialog with permissions table showing different access levels for account features and domain-specific actions](../.gitbook/assets/mailtrap-and-n8n-integration-4.png)
{% endstep %}

{% step %}
### Copy and save the token

Copy the token and save it in a secure place.

![Mailtrap Edit API Token page with copy button and reset button for managing the API token](../.gitbook/assets/mailtrap-and-n8n-integration-5.png)
{% endstep %}

{% step %}
### Obtain the Account ID

To obtain the **Account ID**, go to **Settings** → **Account Settings** → **Account Details**.

![Mailtrap Account Settings page showing account details tab with account name, owner email, and account ID information](../.gitbook/assets/mailtrap-and-n8n-integration-6.png)
{% endstep %}
{% endstepper %}

### Integrate N8N with Mailtrap

#### Step 1. Select Mailtrap

* When you open your N8N dashboard, click on the left card 'Start from scratch'.

![N8N workflows overview page with cards to create new workflows from scratch or use AI agent example](../.gitbook/assets/mailtrap-and-n8n-integration-7.png)

* Then, click on the 'Add first step…'.

![N8N workflow canvas with add node button highlighted in the center of empty workflow](../.gitbook/assets/mailtrap-and-n8n-integration-8.png)

* On the right-side menu, type 'Mailtrap' in the search bar, click on it, and select which actions you want to automate (e.g., sending an email, creating/updating contacts, etc.).

![N8N node selection panel showing Mailtrap triggers and available contact-related actions in list format](../.gitbook/assets/mailtrap-and-n8n-integration-9.png)

Here's an example workflow I created for the purposes of this demo:

![N8N workflow showing trigger connected to five sequential Mailtrap contact management nodes including get lists, create, update, and delete operations](../.gitbook/assets/mailtrap-and-n8n-integration-10.png)

#### Step 2. Enter your Mailtrap credentials

* In the parameters window, click on 'Select Credential' and '+ Create new credential' to add the credentials we obtained in the previous chapter.

![Mailtrap node parameters showing Create Contact operation with dropdown for credential selection and fields for account ID and email](../.gitbook/assets/mailtrap-and-n8n-integration-11.png)

* In the credentials setting, simply add the API Token and Mailtrap Host.

![Mailtrap API Token credential dialog with fields for API token and mailing host configuration showing send.api.mailtrap.io](../.gitbook/assets/mailtrap-and-n8n-integration-12.png)

**Important**: Keep in mind that I've added my Sending credentials (send.api.mailtrap.io).

* Then, back in the Parameters window, add the account ID.

![Mailtrap node parameters panel configured for Get Contact Lists operation with account ID value entered in the field](../.gitbook/assets/mailtrap-and-n8n-integration-13.png)

#### Step 3. Test the integration

* Lastly, simply click on 'Test step' to test the integration:

![N8N workflow execution results showing three contact records with IDs and names successfully retrieved from Mailtrap](../.gitbook/assets/mailtrap-and-n8n-integration-14.png)

Now, every time a new user logs in and updates their name, they will get a confirmation email via Mailtrap and their information will be logged in my Mailtrap Contacts page. There, I can group them into lists, segment them accordingly, and use Fields to personalize my email campaigns further.

## Next Steps

Once your N8N and Mailtrap integration is complete, you can leverage the full power of workflow automation to send targeted emails, manage contacts, and track engagement across your applications.
