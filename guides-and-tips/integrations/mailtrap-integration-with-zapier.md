---
title: Zapier Integration
description: Automate email sending by connecting Mailtrap to over 7,000 applications using Zapier without writing any code.
---

# Overview

<i class="fa-bolt">:bolt:</i>

Using the Mailtrap integration with Zapier, you can automate email sending by connecting Mailtrap to over 7,000 other applications without any coding. This guide shows you how to set up the integration, create automations, and manage your connections.

## Connecting Mailtrap to Zapier

{% stepper %}
{% step %}
## Log in to Zapier

Log in to your [Zapier account](https://zapier.com/sign-up) or create a new account.
{% endstep %}

{% step %}
## Navigate to Apps

Navigate to **Apps** in the left-hand side menu.

![Zapier dashboard with Apps menu item highlighted in left sidebar navigation](../.gitbook/assets/mailtrap-integration-with-zapier-1.png)
{% endstep %}

{% step %}
## Add connection

Click **Add connection**.

![Zapier Apps page with Add connection button highlighted in top right corner](../.gitbook/assets/mailtrap-integration-with-zapier-2.png)
{% endstep %}

{% step %}
## Search for Mailtrap

Type _Mailtrap_ in the **App name** search bar.

![Zapier add connection dialog showing Mailtrap search result with app icon](../.gitbook/assets/mailtrap-integration-with-zapier-3.png)
{% endstep %}

{% step %}
## Enter API key

Enter your Mailtrap API key to allow Zapier to access your account. Note: This should be the token for the domain you've added and verified in Mailtrap. You'll find it in the **Settings** → **API Tokens** menu.

![Zapier authorization dialog requesting Mailtrap API key with input field and continue button](../.gitbook/assets/mailtrap-integration-with-zapier-4.png)
{% endstep %}
{% endstepper %}

## Creating an automation

To set up trigger-based email sending via Mailtrap in Zapier, you need to create a Zap.

A Zap is a workflow connecting multiple apps that consists of a trigger (an event that starts a Zap) and one or more actions (events the Zap performs).

### Using Copilot

{% stepper %}
{% step %}
## Describe your workflow

Describe the workflow you want to create to Copilot.

![Zapier Copilot interface with example prompt showing how to send an email from Google Forms to Mailtrap](../.gitbook/assets/mailtrap-integration-with-zapier-5.png)
{% endstep %}

{% step %}
## Add steps from Copilot

Add some or all the steps created by Copilot to the Zap or continue to prompt the chatbot to add or replace steps.

![Zapier workflow builder showing copilot suggestion with trigger and action step configuration panels](../.gitbook/assets/mailtrap-integration-with-zapier-6.png)
{% endstep %}

{% step %}
## Configure email fields

Configure the required fields for sending an email. The from email should contain the same sending domain you added and verified in Mailtrap.

![Mailtrap Send Email action configuration form with fields for from name, from email, to name, to email, and subject](../.gitbook/assets/mailtrap-integration-with-zapier-7.png)
{% endstep %}

{% step %}
## Send test email

Send a test email to Mailtrap (optional).

![Zapier test step panel showing email data preview with skip and test step options](../.gitbook/assets/mailtrap-integration-with-zapier-8.png)
{% endstep %}

{% step %}
## Publish the Zap

Publish the Zap.
{% endstep %}
{% endstepper %}

### Manually

{% stepper %}
{% step %}
## Select trigger event

Select an event (trigger) to start your Zap.

![Zapier trigger selection interface showing step box to select the event that starts the Zap](../.gitbook/assets/mailtrap-integration-with-zapier-9.png)

Zapier's app directory contains 7,000+ apps with triggers and actions available for each.

![Zapier app selection panel displaying popular apps like Google Forms, Gmail, Google Calendar, and built-in tools](../.gitbook/assets/mailtrap-integration-with-zapier-10.png)
{% endstep %}

{% step %}
## Select Mailtrap action

Select **Mailtrap** as the action for your Zap to run.

![Zapier app search dialog showing Mailtrap in search results with app icon](../.gitbook/assets/mailtrap-integration-with-zapier-11.png)
{% endstep %}

{% step %}
## Select Send Email event

Select **Send Email** as the action event.

![Mailtrap action setup panel showing Send Email selected as the action event with beta badge](../.gitbook/assets/mailtrap-integration-with-zapier-12.png)
{% endstep %}

{% step %}
## Configure email fields

Configure the required fields for sending an email.

![Mailtrap Send Email action configuration form with fields for from name, from email, to name, to email, and subject](../.gitbook/assets/mailtrap-integration-with-zapier-7.png)
{% endstep %}

{% step %}
## Send test email

Send a test email to Mailtrap (optional).

![Zapier test step panel showing email data preview with skip and test step options](../.gitbook/assets/mailtrap-integration-with-zapier-8.png)
{% endstep %}

{% step %}
## Publish the Zap

Publish the Zap.
{% endstep %}
{% endstepper %}

## Removing Mailtrap credentials from Zapier

{% stepper %}
{% step %}
## Navigate to Apps

Navigate to **Apps** in the left-hand side menu.

![Zapier dashboard with Apps menu item highlighted in left sidebar navigation](../.gitbook/assets/mailtrap-integration-with-zapier-1.png)
{% endstep %}

{% step %}
## Open Mailtrap connection

Click on your Mailtrap connection.

![Zapier Apps page showing Mailtrap with one connection and one associated Zap](../.gitbook/assets/mailtrap-integration-with-zapier-16.png)
{% endstep %}

{% step %}
## Delete connection

Click the three-dot menu and then **Delete** in the dropdown menu. Using the same menu, you can edit the connection name, reconnect, test the connection, and view Zaps created using the connection.

![Zapier Mailtrap connection page showing dropdown menu with edit, reconnect, test, view Zaps, and delete options](../.gitbook/assets/mailtrap-integration-with-zapier-17.png)
{% endstep %}
{% endstepper %}

# Next Steps

After setting up your Mailtrap and Zapier integration, you can create unlimited Zaps to automate your email workflows and connect your favorite apps seamlessly.