---
title: Email Templates
description: >-
  Create and send Mailtrap email templates with drag-and-drop builder or HTML
  editor, add Handlebars variables, and integrate via API or SMTP.
---

# Templates

<details>

<summary>For use with AI assistants</summary>

This page as Markdown — [https://docs.mailtrap.io/email-api-smtp/email-templates.md](https://docs.mailtrap.io/email-api-smtp/email-templates.md)

API reference as Markdown — [https://docs.mailtrap.io/developers/templates/templates.md](https://docs.mailtrap.io/developers/templates/templates.md)

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

Email Templates allow you to design, edit, and host HTML email templates.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/SCR-20260929-sdkq.png" alt="" width="563"><figcaption></figcaption></figure></div>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine. Your variable should match the `{{merge_tag}}` in your contact Fields.

You can put `{{name}}` into your template and, as your contact has a field named "name" with the value "John", the template will display "John". In our visual builder, you'll see a list of your contact fields.

## Creating a template

{% @arcade/embed url="https://app.arcade.software/share/c9gFQdhM24VPlzXW2TSl" flowId="c9gFQdhM24VPlzXW2TSl" %}

{% stepper %}
{% step %}
Navigate to the **Templates** menu.
{% endstep %}

{% step %}
Click the **Create New Template** button.
{% endstep %}

{% step %}
Click the drop-down menu to select one of your domains, enter the Template name, Subject, and Category, and click **Continue**.
{% endstep %}

{% step %}
Choose the **Drag & Drop Editor** to build the template without coding, or select **HTML Editor** if you prefer to write/modify the code.
{% endstep %}

{% step %}
Create/modify the design and click **Finish**.

{% hint style="info" %}
The main Templates menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.
{% endhint %}
{% endstep %}
{% endstepper %}

<details>

<summary>Limitations</summary>

Each account can have up to 200 email templates.

</details>

## Editing and customizing templates

### Template details

Each template must have a name, subject, category, and an assigned domain. The subject also supports variables.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/SCR-20260929-sdys.png" alt="" width="563"></div>

### Available editors

{% tabs %}
{% tab title="Drag & Drop Editor" %}
The drag-and-drop editor allows you to design templates without any coding. Drag blocks such as images, buttons, videos and countdown timers from the **Content** tab. The **Audit** tab lists images without alt text or an image URL, and buttons without a link.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/SCR-20260929-senk.png" alt="" width="563"></div>
{% endtab %}

{% tab title="Code Editor" %}
The Code Editor allows you to edit the HTML or text content, depending on the emails you want to send.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/SCR-20260929-sdkq.png" alt="" width="563"></div>

The editor supports Find and Replace options, and you can use **Cmd+F** or **Win+F** as a hotkey to reveal a quick search bar.

{% hint style="warning" %}
**Template Validation**

If your template has an error, Handlebars cannot render it. You'll see an error message in the Preview tab, and the RAW code with an error will be highlighted in the Editor.

You can't save a template with errors. Note that we don't validate HTML — only Handlebars syntax is validated.
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/SCR-20260929-sffa-2.png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

### Uploading images

{% @arcade/embed url="https://app.arcade.software/share/v0uTC2zslHSZKJNameNr" flowId="v0uTC2zslHSZKJNameNr" %}

{% stepper %}
{% step %}
Click **Upload image** in the upper right corner of the Code Editor.
{% endstep %}

{% step %}
Hit the **Upload New** button in the following menu and choose an image from your local drive.

{% hint style="info" %}
**Image Requirements**

* Supported formats: JPG, PNG, and GIF
* Maximum file size: 2 MB
{% endhint %}
{% endstep %}

{% step %}
Once the image is uploaded, you will receive a confirmation notification. If the file format is unsupported or the image is too big, you will receive the corresponding error message.
{% endstep %}

{% step %}
Click the **Copy URL** button to copy the image URL to your clipboard, then click **Template** to return to the editing menu.
{% endstep %}

{% step %}
Proceed to add the image to the template body under the `<img>` tag. You can preview it in the template as soon as the asset is added.
{% endstep %}
{% endstepper %}

### Test Data

Code Editor automatically parses your template and shows all the variables found. The Test Data tab helps you preview the object variables.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/SCR-20260929-sfyv-2.png" alt="" width="563"></div>

{% hint style="info" %}
By default, as a value, we put a variable name and add the "Test\_" prefix.
{% endhint %}

### Sending test emails

If you're using email templates in production, you can send a test email to the account owner's email address to run basic tests. Simply press the **Send Test** button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/SCR-20260929-sfyv.png" alt=""></div>

{% hint style="warning" %}
**Test email requirements**

* Your domain must be verified to send a test.
* Each test email is billed over your quota.
{% endhint %}
