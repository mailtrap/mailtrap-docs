---
title: Editing and Customizing Templates
description: >-
  Learn how to edit and customize email templates using Details, Drag & Drop
  Editor, Code Editor, and test your templates.
icon: pen
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

# Editing and Customizing

### Details

Each template must have a name, subject, category, and assigned domain. The subject also supports variables.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-details-view.png" alt="Template Details page showing domain, name, subject, and category fields in a bordered section" width="563"><figcaption><p>Template details section</p></figcaption></figure></div>

### Drag & Drop Editor

The drag-and-drop editor allows you to design templates without any coding.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-drag-drop-interface.png" alt="Drag and Drop Editor interface showing template preview in center with blocks and content options on right sidebar" width="563"><figcaption><p>Drag and Drop Editor</p></figcaption></figure></div>

### Code Editor

Code Editor allows you to edit the HTML or Text content, depending on the emails you want to send.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (20).png" alt="" width="563"><figcaption></figcaption></figure></div>

The editor supports Find and Replace options, and you can use Cmd+F or Win+F as a hotkey to reveal a quick search bar.

If your template has an error, Handlebars cannot render it. You'll see an error message in the Preview tab, and the RAW code with an error will be highlighted in the Editor.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (21).png" alt="" width="563"><figcaption></figcaption></figure></div>

You can't save a template with errors, either. Remember that we don't validate HTML.

### **Uploading an image**

{% stepper %}
{% step %}
Click Upload image in the upper right corner of the Code Editor.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-upload-image-button.png" alt="Code Editor with Upload image button highlighted in upper right corner" width="375"><figcaption><p>Upload image button in Code Editor</p></figcaption></figure></div>
{% endstep %}

{% step %}
Hit the Upload New button in the following menu and choose an image from your local drive (Supported formats are JPG, PNG, and GIF, and the maximum file size is 2 MB).

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-images-library.png" alt="Images library page showing Upload New button highlighted in top right" width="563"><figcaption><p>Images library with Upload New button</p></figcaption></figure></div>
{% endstep %}

{% step %}
Once the image is uploaded, you will receive a confirmation notification. If the file format is unsupported or the image is too big, you will receive the corresponding error message.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-image-upload-success.png" alt="Success notification showing Image successfully uploaded message in green banner" width="563"><figcaption><p>Image upload success notification</p></figcaption></figure></div>
{% endstep %}

{% step %}
Click the Copy URL button to copy the image URL to your clipboard, then click Template to return to the editing menu.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-copy-url-button.png" alt="Images library showing uploaded images with Copy URL button highlighted" width="563"><figcaption><p>Copy URL button for uploaded images</p></figcaption></figure></div>
{% endstep %}

{% step %}
Proceed to add the image to the template body under the `<img>` tag. You can preview it in the template as soon as the asset is added.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-image-in-code.png" alt="HTML code showing image URL inserted in img src attribute with highlighted code" width="375"><figcaption><p>Image URL added to template HTML</p></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### **Test Data**

Code Editor automatically parses your template and shows all the variables found. The Test Data tab helps you preview the object variables.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-test-data-variables.png" alt="Test Data tab showing template variables with test values and preview" width="563"><figcaption><p>Test Data tab with template variables</p></figcaption></figure></div>

By default, as a value, we put a variable name and add the "Test\_" prefix.

### Send test

If you're using email templates in production, you can send a test email to the account owner's email address to run basic tests. Simply press the Send Test button.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-send-test-button.png" alt="Template editor showing Send Test button highlighted in top right" width="563"><figcaption><p>Send Test button</p></figcaption></figure></div>

Important Notes:

* Your domain should be verified to send a test.
* Each test email is billed over your quota.

### Next steps

* [Handlebars Guide](handlebars-guide.md) - Learn how to use Handlebars syntax to add dynamic content
* [Integration](integration.md) - Integrate templates with Email API/SMTP
* [Debugging](debugging.md) - Test templates with Email Sandbox
