---
title: Cloudflare DNS Setup
description: >-
  Verify your Mailtrap sending domain in Cloudflare. Add DNS records for
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

To add and verify a sending domain in Mailtrap, you need access to your domain's DNS records and your domain provider account.

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Cloudflare.

{% hint style="info" %}
This guide assumes that your domain is either registered with Cloudflare and uses its nameservers or isn't registered with Cloudflare but uses its nameservers.
{% endhint %}

{% stepper %}
{% step %}
## Open the Cloudflare dashboard

Open the Cloudflare dashboard and click the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-domain-dashboard.png" alt="Cloudflare dashboard showing domain selection" width="563"></div>
{% endstep %}

{% step %}
## Access DNS settings

Click DNS in the left navigation panel. This will open DNS records.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-dns-menu.png" alt="Cloudflare DNS menu in left navigation panel" width="188"></div>
{% endstep %}

{% step %}
## Add a new DNS record

Click the Add Record button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-add-record-button.png" alt="Cloudflare Add Record button" width="563"></div>
{% endstep %}

{% step %}
## View Mailtrap DNS records

Return to Mailtrap. On the Verification page, you'll see the DNS records you need to add to Cloudflare. These are Domain Verification, DKIM, DMARC, and Domain Tracking. You'll need the values under Type, Name, and Value.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-mailtrap-dns-records.png" alt="Mailtrap verification page showing required DNS records" width="563"></div>

Pay attention to the Type next to each record in Mailtrap and choose a relevant one in Cloudflare. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and one TXT type record (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/cloudflare-mailtrap-record-types.png" alt="DNS record types and categories in Mailtrap" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/cloudflare-record-type-dropdown.png" alt="DNS record type dropdown in Cloudflare" width="375"><figcaption><p>DNS record types in Cloudflare </p></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
## Copy DNS record values from Mailtrap

Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-copy-dns-values.png" alt="Copying DNS record values from Mailtrap" width="563"></div>
{% endstep %}

{% step %}
## Paste values into Cloudflare

And paste them into Cloudflare. Remember that Cloudflare refers to the Value field as Target for CNAME records and Content for TXT records.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-paste-dns-values.png" alt="Pasting DNS values into Cloudflare record form" width="563"></div>
{% endstep %}

{% step %}
## Disable proxy if not needed

If you're not using proxy, make sure you disable it. By default, it will be enabled.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-disable-proxy.png" alt="Disabling Cloudflare proxy for DNS record"></div>
{% endstep %}

{% step %}
## Set TTL and save

Use the default value for TTL.

Click Save and repeat the process for all the remaining DNS records.
{% endstep %}

{% step %}
## Verify DNS records in Mailtrap

Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-recheck-dns-records.png" alt="Mailtrap Re-check DNS Records button" width="563"></div>
{% endstep %}

{% step %}
## Confirm verification status

If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/cloudflare-verified-dns-records.png" alt="Mailtrap showing all DNS records as verified with green status" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, [consult Cloudflare documentation](https://developers.cloudflare.com/dns/manage-dns-records/how-to/create-dns-records/) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io)
{% endhint %}
