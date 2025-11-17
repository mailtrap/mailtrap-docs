---
title: Google Domains DNS Setup
description: >-
  Verify your Mailtrap sending domain in Google Domains. Add DNS records for
  DKIM/DMARC verification, pass compliance, and start sending emails.
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

# Google Domains

To add and verify a sending domain in Mailtrap, you need access to your domain's DNS records and your domain provider account.

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Google Domain.

{% hint style="info" %}
Note: On September 7, 2023, Squarespace acquired all domain registrations and related customer accounts from Google Domains. This means that Google Domains is now in the process of migrating account and domain data to Squarespace. Until the migration is completed, you can still manage your domains in Google Domains. After the migration, you'll need to manage your domain in Squarespace.

This guide assumes that your domain is either registered with Google Domains and uses its nameservers or isn't registered with Google Domains but uses its nameservers.
{% endhint %}

{% stepper %}
{% step %}
#### Select your domain

Go to Google Domains and select the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-select-domain.png" alt="Google Domains dashboard with domain selection" width="563"></div>
{% endstep %}

{% step %}
#### Access DNS settings

In the left navigation panel, click DNS.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-click-dns.png" alt="Google Domains left navigation showing DNS menu item" width="188"></div>
{% endstep %}

{% step %}
#### Manage custom records

Under Custom records in the Resource records section, choose Manage custom records. In case you don't have any resource records, click Custom records directly.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-manage-custom-records.png" alt="Google Domains Manage custom records button in Resource records section" width="563"></div>
{% endstep %}

{% step %}
#### Create new record

Scroll down at the bottom of the records and click Create new record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-create-new-record.png" alt="Google Domains Create new record button" width="563"></div>
{% endstep %}

{% step %}
#### View Mailtrap DNS records

Return to Mailtrap. On the Domain Verification page, you'll see the DNS records you need to add to Google Domains. These are Domain Verification, DKIM, DMARC, and Domain Tracking. You'll need the values under Type, Name, and Value.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-mailtrap-dns-records.png" alt="Mailtrap domain verification page showing required DNS records" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in Google Domains. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and one TXT type record (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/google-domains-dns-types.png" alt="DNS record types and categories in Mailtrap" width="563"><figcaption><p>DNS Types and Categories in Mailtrap</p></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
#### Copy DNS record values from Mailtrap

Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-copy-name-value.png" alt="Copying DNS record values from Mailtrap" width="563"></div>
{% endstep %}

{% step %}
#### Paste values into Google Domains

And paste them into Google Domains. Remember that Google Domains refers to the Name field as the Host name and the Value field as either the Domain name (for CNAME-type records) or Text (for TXT-type records).

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-paste-values.png" alt="Google Domains record form showing Host name and Domain name fields" width="563"></div>
{% endstep %}

{% step %}
#### Set TTL

Use the default value for TTL.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-ttl-default.png" alt="Google Domains TTL field with default value" width="563"></div>
{% endstep %}

{% step %}
#### Add all DNS records

Repeat the process of copying, pasting, and clicking Create new record for each record until you've added all the Mailtrap DNS records to Google Domains. Click Save.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-save-records.png" alt="Google Domains Save button after adding all records" width="563"></div>
{% endstep %}

{% step %}
#### Verify DNS records in Mailtrap

Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-recheck-dns.png" alt="Mailtrap Re-check DNS Records button" width="563"></div>
{% endstep %}

{% step %}
#### Confirm verification status

If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-domains-verified-status.png" alt="Mailtrap showing all DNS records verified with green status indicators" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, [consult Google Domains documentation](https://support.google.com/domains/answer/3290350?hl=en) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
