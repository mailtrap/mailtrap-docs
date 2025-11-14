---
title: Email Templates
description: Design, edit, and host HTML email templates and reference them via API
---

# Email Templates

#### Overview

Email Templates allow you to design, edit, and host HTML email templates, and reference them via API.

<div align="left"><img src="../.gitbook/assets/template-html-code-editor (1).png" alt="Email Templates overview showing template management interface" width="563"></div>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine.

You can put \{{user\_name\}} into your template and pass “John” as the “user\_name” value via API. For more, check our article on [using Handlebars syntax with Mailtrap](https://mailtrap.io/blog/using-handlebars-with-mailtrap-email-templates-quick-guide-with-examples/).

#### Creating a template

1. Navigate to the Templates menu.

<div align="left"><img src="../.gitbook/assets/template-menu-nav (1).png" alt="Templates menu in the left navigation" width="563"></div>

2. Click the Create New Template button.

<div align="left"><img src="../.gitbook/assets/template-list-create-button (1).png" alt="Create New Template button" width="563"></div>

3. Click the drop-down menu to select one of your domains, enter the Template name, Subject, and Category, and click Continue.

<div align="left"><img src="../.gitbook/assets/template-details-form (1).png" alt="Form to create new template with domain, name, subject, and category fields" width="563"></div>

4. Choose the Drag & Drop Editor to build the template without coding, or select HTML Editor if you prefer to write/modify the code.

<div align="left"><img src="../.gitbook/assets/template-design-selection (1).png" alt="Editor selection showing Drag and Drop and HTML editor options" width="563"></div>

5. Create/modify the design and click Finish.

<div align="left"><img src="../.gitbook/assets/template-drag-drop-editor (1).png" alt="Template editor with Finish button" width="563"></div>

* The main Templates menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.

<div align="left"><img src="../.gitbook/assets/template-list-view (1).png" alt="List of all saved email templates" width="563"></div>

#### Editing and customizing templates

**Details**

Each template must have a name, subject, category, and assigned domain. The subject also supports variables.

<div align="left"><img src="../.gitbook/assets/template-details-view (1).png" alt="Template details page showing name, subject, category, and domain fields" width="563"></div>

**Drag & Drop Editor**

The drag-and-drop editor allows you to design templates without any coding.

<div align="left"><img src="../.gitbook/assets/template-drag-drop-interface (1).png" alt="Drag and drop template editor interface" width="563"></div>

**Code Editor**

Code Editor allows you to edit the HTML or Text content, depending on the emails you want to send.

<div align="left"><img src="../.gitbook/assets/template-html-code-editor (1).png" alt="Code editor interface for HTML and text content" width="563"></div>

The editor supports Find and Replace options, and you can use Cmd+F or Win+F as a hotkey to reveal a quick search bar.

If your template has an error, Handlebars cannot render it. You'll see an error message in the Preview tab, and the RAW code with an error will be highlighted in the Editor.

<div align="left"><img src="../.gitbook/assets/marketing-templates-error (1).png" alt="Template error message showing highlighted error in code editor" width="563"></div>

You can't save a template with errors, either. Remember that we don't validate HTML.

**Uploading an image**

1\. Click Upload image in the upper right corner of the Code Editor.

<div align="left"><img src="../.gitbook/assets/template-upload-image-button (1).png" alt="Upload image button in code editor" width="375"></div>

2\. Hit the Upload New button in the following menu and choose an image from your local drive (Supported formats are JPG, PNG, and GIF, and the maximum file size is 2 MB).

<div align="left"><img src="../.gitbook/assets/template-images-library (1).png" alt="Upload New button to select image from local drive" width="375"></div>

3\. Once the image is uploaded, you will receive a confirmation notification. If the file format is unsupported or the image is too big, you will receive the corresponding error message.

<div align="left"><img src="../.gitbook/assets/template-image-upload-success (1).png" alt="Success notification after image upload" width="375"></div>

4\. Click the Copy URL button to copy the image URL to your clipboard, then click Template to return to the editing menu.

<div align="left"><img src="../.gitbook/assets/template-copy-url-button (1).png" alt="Copy URL button to copy image URL to clipboard" width="375"></div>

5\. Proceed to add the image to the template body under the `<img>` tag. You can preview it in the template as soon as the asset is added.

<div align="left"><img src="../.gitbook/assets/template-image-in-code (1).png" alt="Template preview showing added image" width="563"></div>

**Test Data**

Code Editor automatically parses your template and shows all the variables found. The Test Data tab helps you preview the object variables.

<div align="left"><img src="../.gitbook/assets/template-test-data-variables (1).png" alt="Test Data tab showing template variables" width="563"></div>

By default, as a value, we put a variable name and add the “Test\_” prefix.

**Send test**

If you're using email templates in production, you can send a test email to the account owner's email address to run basic tests. Simply press the Send Test button.

<div align="left"><img src="../.gitbook/assets/template-send-test-button (1).png" alt="Send Test button to send test email" width="375"></div>

Important Notes:

* Your domain should be verified to send a test.
* Each test email is billed over your quota.

#### Template integration - Email API/SMTP

1. Navigate to Templates in the menu on the left.

<div align="left"><img src="../.gitbook/assets/template-menu-nav (1).png" alt="Templates menu in left navigation" width="563"></div>

2. Click the template you want to call using the API.

<div align="left"><img src="../.gitbook/assets/template-list-view (1).png" alt="Select template from list for API integration" width="563"></div>

3. Open the Integration tab.

<div align="left"><img src="../.gitbook/assets/template-integration-tab (1).png" alt="Integration tab in template details" width="563"></div>

4. With Email API/SMTP toggled on, click Integrate under Transactional Stream or Bulk Stream.

<div align="left"><img src="../.gitbook/assets/template-stream-options (1).png" alt="Email API/SMTP toggle with Integrate buttons for streams" width="563"></div>

5. Copy the necessary credentials such as Host, API Token, and Template UUID.

<div align="left"><img src="../.gitbook/assets/marketing-templates-transactional (1).png" alt="Transactional Stream API credentials" width="563"></div>

<div align="left"><img src="../.gitbook/assets/marketing-templates-bulk (1).png" alt="Bulk Stream API credentials" width="563"></div>

6. Alternatively, under Code Samples, choose the desired language and copy the sample configuration already containing the necessary credentials. Mailtrap’s official SDKs ([Node.js](https://github.com/railsware/mailtrap-nodejs), [Python](https://github.com/railsware/mailtrap-python), [PHP](https://github.com/railsware/mailtrap-php), and [Ruby](https://github.com/railsware/mailtrap-ruby)) also support the templates feature.
7. Paste the code into your project and customize it if needed. Then, run the code to send an email to the email address you indicated in your script.

For more details, [open the API docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api) and go to Email Sending API → Emails → Send email (including template) for transactional stream and Bulk Sending API → Emails → Send email (including template) for bulk stream. Under Body, click the dropdown menu, and choose `EmailFromTemplate` .

#### Template debugging

1. Navigate to Templates in the menu on the left.

<div align="left"><img src="../.gitbook/assets/template-menu-nav (1).png" alt="Templates menu in left navigation" width="563"></div>

2. Click the template you want to call using the API.

<div align="left"><img src="../.gitbook/assets/template-list-view (1).png" alt="Select template from list for testing" width="563"></div>

3. Open the Integration tab.

<div align="left"><img src="../.gitbook/assets/template-integration-tab (1).png" alt="Integration tab for template testing" width="563"></div>

4. Toggle the switch to Email Testing.

<div align="left"><img src="../.gitbook/assets/template-email-testing-toggle (1).png" alt="Toggle switch to Email Testing mode" width="563"></div>

5. And click Integrate.

<div align="left"><img src="../.gitbook/assets/template-testing-inbox-integrate (1).png" alt="Integrate button for Email Testing" width="375"></div>

6. Select the desired sandbox from the dropdown menu to reveal its credentials. Copy the Host, API Token, Template UUID, and Sandbox ID.
   1. Alternatively, you can also use one of the pre-made Code Samples.

<div align="left"><img src="../.gitbook/assets/template-sandbox-credentials (1).png" alt="Sandbox credentials for template testing" width="563"></div>

7. Paste the code into your project and customize it if needed. Then, run the code to send an email to the selected Email Testing sandbox.
8. Finally, check the sandbox you specified in the script.

<div align="left"><img src="../.gitbook/assets/template-test-email-received (1).png" alt="Email Testing sandbox showing received template test" width="563"></div>

* The Tech Info tab contains the link to the template you tested and lists all the variables used in the template.

<div align="left"><img src="../.gitbook/assets/template-tech-info-variables (1).png" alt="Tech Info tab showing template link and variables" width="563"></div>

For more details, [open the API docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api) and go to [Sandbox API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) → Test Emails → Send email (including templates). Under Body, click the dropdown menu, and choose `EmailFromTemplate` .

#### List of templates and user permissions

Clicking on Templates in the side menu lists all the templates you can access.

<div align="left"><img src="../.gitbook/assets/template-final-list (1).png" alt="Complete list of all accessible templates" width="563"></div>

Access to templates is managed on a domain level. You need to have Admin access to a domain to manipulate the templates. In case you don’t have Edit rights, you can’t change the template.

Reminder: You can delete a template. However, this action is irreversible, so be sure to change the sending/testing code after deletion. When the template is deleted, the UUID is also deleted, and Mailtrap won’t be able to render it.

Each account can have up to 200 email templates. If you need more - please contact Support.

\\
