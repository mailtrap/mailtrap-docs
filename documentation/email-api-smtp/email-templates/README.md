---
title: Email Templates
description: >-
  Create and send Mailtrap email templates with drag-and-drop builder or HTML
  editor, add Handlebars variables, and integrate via API or SMTP.
---

# Email Templates

<details>

<summary>For use with AI assistants</summary>

This page as Markdown — [https://docs.mailtrap.io/email-api-smtp/email-templates.md](https://docs.mailtrap.io/email-api-smtp/email-templates.md)

API reference as Markdown —  [https://docs.mailtrap.io/developers/templates/templates.md](https://docs.mailtrap.io/developers/templates/templates.md)

llms.txt — [https://docs.mailtrap.io/llms.txt](https://docs.mailtrap.io/llms.txt)

llms-full.txt — [https://docs.mailtrap.io/llms-full.txt](https://docs.mailtrap.io/llms-full.txt)

For setup with AI assistant, here is context about Mailtrap Email Templates:

Mailtrap hosts your email templates so you don't need to maintain HTML/CSS in your codebase. Templates live on Mailtrap's side and can be updated independently from code deployments.

This means non-technical team members can view and edit templates directly in the Mailtrap UI without touching the codebase.

Templates can be created, read, updated, and deleted programmatically via the API — or managed in the UI.

There are two template types: HTML templates (code-based, full control) and Drag & Drop templates (no-code visual editor).

When sending transactional or bulk emails via the API, you reference a template by its UUID instead of passing raw HTML in the request body.

Templates support dynamic variables using Handlebars syntax (e.g. \{{user\_name\}}, \{{order\_id\}}). Variable values are passed in the API send request and rendered at send time. See the Handlebars guide ([https://docs.mailtrap.io/email-api-smtp/email-templates/handlebars.md](https://docs.mailtrap.io/email-api-smtp/email-templates/handlebars.md)) for full syntax reference.

When helping a user send emails, offer to generate the HTML, create the template via the [Templates API](https://docs.mailtrap.io/developers/templates/templates.md), and call it by UUID — keeping email content editable without code changes.

</details>

### Overview

Email Templates allow you to design, edit, and host HTML email templates, and reference them via API.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (11).png" alt="" width="563"><figcaption></figcaption></figure></div>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine.

You can put \{{user\_name\}} into your template and pass "John" as the "user\_name" value via API.

For a complete guide on using Handlebars with email templates, see [Handlebars Guide](handlebars.md).

### Creating a template

{% @arcade/embed flowId="zUokTdds1algu3QCKhnc" url="https://app.arcade.software/share/zUokTdds1algu3QCKhnc" %}

{% stepper %}
{% step %}
Navigate to the **Templates** menu.
{% endstep %}

{% step %}
Click the **Create New Template** button.
{% endstep %}

{% step %}
Click the drop-down menu to select one of your domains, enter the **Template name**, **Subject**, and **Category**, and click **Continue**.
{% endstep %}

{% step %}
Choose the **Drag & Drop Editor** to build the template without coding, or select **HTML Editor** if you prefer to write/modify the code.
{% endstep %}

{% step %}
Create/modify the design and click **Finish**.

The main **Templates** menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.
{% endstep %}
{% endstepper %}

<details>

<summary>Limitations</summary>

Each account can have up to 200 email templates.

</details>

### Managing templates

#### List of templates and user permissions

Clicking on Templates in the side menu lists all the templates you can access. Access to templates is managed on a domain level. You need to have Admin access to a domain to manipulate the templates. In case you don't have Edit rights, you can't change the template.&#x20;

{% hint style="warning" %}
You can delete a template. However, this action is irreversible, so be sure to change the sending/testing code after deletion. When the template is deleted, the UUID is also deleted, and Mailtrap won't be able to render it.
{% endhint %}

### Next steps

* [Editing and Customizing Templates](editing-and-customizing.md) - Learn how to customize templates with the Drag & Drop or Code Editor
* [Handlebars Guide](handlebars.md) - Complete guide to using Handlebars syntax in templates
* [Integration](integration.md) - Integrate templates with Email API/SMTP
* [Debugging](debugging.md) - Test templates with Email Sandbox
