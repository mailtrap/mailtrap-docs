---
title: Campaign attachments
description: Attach files to an email marketing campaign and learn the limits that apply
---

# Overview

Attach files, such as a catalog, a price list or an event invitation, to a campaign. Every recipient gets the same files as real email attachments.

{% hint style="info" %}
Attachments make each email larger. Large emails are slower to deliver and can land in spam more often. For large files, put a link to the file in the email instead.
{% endhint %}

## Limits

* Up to 5 files per campaign
* Up to 5 MB for all files together
* Allowed file types: PDF, PNG, JPG, GIF, WebP, TXT, CSV, ICS, DOCX, XLSX, PPTX

Mailtrap checks the content of each file, not only its name. A file whose content does not match its extension is rejected. If the content is an allowed type but the extension is wrong, Mailtrap corrects the extension.

## Add files to a campaign

{% stepper %}
{% step %}
#### Open the Design step

Create a campaign, or open a draft campaign, and go to the **Design** step.
{% endstep %}

{% step %}
#### Attach the files

Above the editor, click **Attach Files** and select one or more files. Each file shows its upload progress, and the line next to the button shows how much space is left.

While files upload, **Continue** and **Send Test** are not available.
{% endstep %}

{% step %}
#### Remove a file

To remove a file, click the **×** on it.
{% endstep %}
{% endstepper %}

You can add or remove files only while the campaign is a draft. To change the files of a scheduled campaign, click **Cancel Scheduling** first. After the campaign starts sending, its files cannot change.

## Test the files

* **Send Test** → **Email address** sends the test email with the files.
* **Send Test** → **Device Previews** sends to a sandbox without the files.

## What to know

* Links inside the files are not tracked.
* A campaign with files can take longer to start, because Mailtrap reviews it before sending.
* The campaign page shows the files in the **Design** section, and you can download them there.
* When you duplicate a campaign, the copy gets the same files.
* Attachments are available for campaigns only. Email templates, automations and the API do not support them.
