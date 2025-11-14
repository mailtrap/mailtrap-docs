---
title: Auto BCC
description: Automatically add BCC recipients to all emails sent from your domain with custom headers support
---

## How to set up Auto BCC

{% stepper %}
{% step %}
Go to Sending Domains and choose the domain you want to set up Auto BCC for.

<figure><img src="../.gitbook/assets/auto-bcc-sending-domains-list.png" alt="Sending Domains page showing list of verified domains with domains highlighted"><figcaption><p>Select domain from Sending Domains list</p></figcaption></figure>
{% endstep %}

{% step %}
Navigate to the Auto BCC tab.

<figure><img src="../.gitbook/assets/auto-bcc-tab.png" alt="Domain page showing Auto BCC tab highlighted by red arrow"><figcaption><p>Open Auto BCC tab</p></figcaption></figure>
{% endstep %}

{% step %}
Enter an email address that will be included as BCC in all the emails you send from this domain and click Add Email.

<figure><img src="../.gitbook/assets/auto-bcc-add-email.png" alt="Auto BCC page with email input field and Add Email button highlighted by red arrow"><figcaption><p>Add BCC email address</p></figcaption></figure>
{% endstep %}

{% step %}
Optionally, specify a custom X-header that will be included in emails to BCC recipients. Enter the Name and Value, and click Add Header.

<figure><img src="../.gitbook/assets/auto-bcc-add-header.png" alt="Custom Headers section with Name and Value fields and Add Header button highlighted by red arrow"><figcaption><p>Add custom X-header</p></figcaption></figure>
{% endstep %}

{% step %}
To delete the email address or a custom header, click the trash bin icon and confirm the action by clicking Delete.

<figure><img src="../.gitbook/assets/auto-bcc-delete-confirmation.png" alt="Auto BCC page showing email with trash icon and delete confirmation dialog with Delete button highlighted"><figcaption><p>Delete email or header confirmation</p></figcaption></figure>
{% endstep %}
{% endstepper %}

## Important notes

* You can add multiple BCC email addresses, and all of them will receive email copies;
* You can’t use Auto BCC with a demo domain;
* Using this feature will increase your usage. Each email copy sent will count against your quota or overage calculation.
