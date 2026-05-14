---
title: Template Debugging
description: Learn how to test and debug your email templates using Mailtrap Email Sandbox.
icon: bug
---

# Debugging with Sandbox

### Overview

Before sending your email templates to production, it's important to test them in a safe environment. Mailtrap Email Sandbox allows you to test your templates, preview how they render, and verify that all variables are working correctly.

### Debugging steps

{% @arcade/embed flowId="9uF1XI537kgKMP1RyZxw" url="https://app.arcade.software/share/9uF1XI537kgKMP1RyZxw" %}

{% stepper %}
{% step %}
Navigate to Templates in the menu on the left.
{% endstep %}

{% step %}
Click the template you want to call using the API.
{% endstep %}

{% step %}
Open the Integration tab.
{% endstep %}

{% step %}
Toggle the switch to Email Testing.
{% endstep %}

{% step %}
And click Integrate.
{% endstep %}

{% step %}
Select the desired sandbox from the dropdown menu to reveal its credentials. Copy the Host, API Token, Template UUID, and Sandbox ID.

Alternatively, you can also use one of the pre-made Code Samples.
{% endstep %}

{% step %}
Paste the code into your project and customize it if needed. Then, run the code to send an email to the selected Email Testing sandbox.
{% endstep %}

{% step %}
Finally, check the sandbox you specified in the script.

The Tech Info tab contains the link to the template you tested and lists all the variables used in the template.

For more details, [open the API docs](https://docs.mailtrap.io/developers) and go to [Sandbox API](https://docs.mailtrap.io/developers/email-sandbox/send-test-emails) → Test Emails → Send email (including templates). Under Body, click the dropdown menu, and choose `EmailFromTemplate`.
{% endstep %}
{% endstepper %}
