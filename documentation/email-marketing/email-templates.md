---
title: Email Templates
description: Design, edit, and host HTML email templates and reference them via API
icon: palette
---

# Email Templates

Email Templates allow you to design, edit, and host HTML email templates.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.&#x20;

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine. You variable should match the \{{merge\_tag\}} in your contact Fields.

You can put `{{name}}` into your template and as your contact has a field named "name" with the value "John", the template will display "John". In our visual builder you'll a list of your contact fields.

## Creating a Template

{% stepper %}
{% step %}
Navigate to the **Templates** menu

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-menu-nav.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Click the **Create New Template** button

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-list-create-button.png" alt="" width="563"></div>
{% endstep %}

{% step %}
**Configure template details**

Click the drop-down menu to select one of your domains, enter the Template name, Subject, and Category, and click **Continue**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-details-form.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Choose your editor**

Choose the **Drag & Drop Editor** to build the template without coding, or select **HTML Editor** if you prefer to write/modify the code.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-design-selection.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Create your design**

Create/modify the design and click **Finish**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-drag-drop-editor.png" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The main Templates menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.
{% endhint %}

## Editing and Customizing Templates

### Template Details

Each template must have a name, subject, category, and assigned domain. The subject also supports variables.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-details-view.png" alt="" width="563"></div>

### Available Editors

{% tabs %}
{% tab title="Drag & Drop Editor" %}
The drag-and-drop editor allows you to design templates without any coding.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-drag-drop-interface.png" alt="" width="563"></div>
{% endtab %}

{% tab title="Code Editor" %}
Code Editor allows you to edit the HTML or Text content, depending on the emails you want to send.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-html-code-editor.png" alt="Code editor interface for HTML and text content" width="563"></div>

The editor supports Find and Replace options, and you can use **Cmd+F** or **Win+F** as a hotkey to reveal a quick search bar.

{% hint style="warning" %}
**Template Validation**

If your template has an error, Handlebars cannot render it. You'll see an error message in the Preview tab, and the RAW code with an error will be highlighted in the Editor.

You can't save a template with errors. Note that we don't validate HTML—only Handlebars syntax is validated.
{% endhint %}

<div data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-templates-error.png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

### Uploading Images

{% stepper %}
{% step %}
**Open the image upload menu**

Click **Upload image** in the upper right corner of the Code Editor.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-upload-image-button.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Upload a new image**

Hit the **Upload New** button in the following menu and choose an image from your local drive.

{% hint style="info" %}
**Image Requirements**

* Supported formats: JPG, PNG, and GIF
* Maximum file size: 2 MB
{% endhint %}

<div align="left"><img src="../.gitbook/assets/template-images-library.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Confirm the upload**

Once the image is uploaded, you will receive a confirmation notification. If the file format is unsupported or the image is too big, you will receive the corresponding error message.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-image-upload-success.png" alt="" width="563"></div>
{% endstep %}

{% step %}
**Copy the image URL**

Click the **Copy URL** button to copy the image URL to your clipboard, then click **Template** to return to the editing menu.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-copy-url-button.png" alt="" width="563"></div>
{% endstep %}

{% step %}
**Add image to template**

Proceed to add the image to the template body under the `<img>` tag. You can preview it in the template as soon as the asset is added.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-image-in-code.png" alt="" width="375"></div>
{% endstep %}
{% endstepper %}

### Test Data

Code Editor automatically parses your template and shows all the variables found. The Test Data tab helps you preview the object variables.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-test-data-variables.png" alt="" width="563"></div>

{% hint style="info" %}
By default, as a value, we put a variable name and add the "Test\_" prefix.
{% endhint %}

### Sending Test Emails

If you're using email templates in production, you can send a test email to the account owner's email address to run basic tests. Simply press the **Send Test** button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/template-send-test-button.png" alt="" width="563"></div>

{% hint style="warning" %}
**Test Email Requirements**

* Your domain must be verified to send a test
* Each test email is billed over your quota
{% endhint %}
