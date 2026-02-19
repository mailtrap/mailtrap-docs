---
title: Email Templates
description: >-
  Create and send Mailtrap email templates with drag-and-drop builder or HTML
  editor, add Handlebars variables, and integrate via API or SMTP.
---

# Email Templates

### Overview

Email Templates allow you to design, edit, and host HTML email templates, and reference them via API.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (11).png" alt="" width="563"><figcaption></figcaption></figure></div>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine.

You can put \{{user\_name\}} into your template and pass "John" as the "user\_name" value via API.

For a complete guide on using Handlebars with email templates, see [Handlebars Guide](handlebars.md).

### Creating a template

{% stepper %}
{% step %}
Navigate to the **Templates** menu.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (13).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Click the **Create New Template** button.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (14).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Click the drop-down menu to select one of your domains, enter the **Template name**, **Subject**, and **Category**, and click **Continue**.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (16).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Choose the **Drag & Drop Editor** to build the template without coding, or select **HTML Editor** if you prefer to write/modify the code.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (17).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Create/modify the design and click **Finish**.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (18).png" alt="" width="563"><figcaption></figcaption></figure></div>

The main **Templates** menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (19).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### Managing templates

#### List of templates and user permissions

Clicking on Templates in the side menu lists all the templates you can access. Access to templates is managed on a domain level. You need to have Admin access to a domain to manipulate the templates. In case you don't have Edit rights, you can't change the template. Each account can have up to 200 email templates.

{% hint style="warning" %}
You can delete a template. However, this action is irreversible, so be sure to change the sending/testing code after deletion. When the template is deleted, the UUID is also deleted, and Mailtrap won't be able to render it.
{% endhint %}

### Next steps

* [Editing and Customizing Templates](editing-and-customizing.md) - Learn how to customize templates with the Drag & Drop or Code Editor
* [Handlebars Guide](handlebars.md) - Complete guide to using Handlebars syntax in templates
* [Integration](integration.md) - Integrate templates with Email API/SMTP
* [Debugging](debugging.md) - Test templates with Email Sandbox
