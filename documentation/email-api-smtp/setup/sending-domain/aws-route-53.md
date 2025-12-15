---
description: >-
  Verify your Mailtrap sending domain in AWS Route 53. Add DNS records for
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

# AWS Route 53

To add and verify a sending domain in Mailtrap, you need access to your domain's DNS records and your domain provider account.

<a href="../sending-domain.md" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to AWS Route 53.

{% hint style="info" %}
This guide assumes that your domain is either registered and managed with AWS Route 53 or registered elsewhere but points to AWS Route 53. It also assumes that you've already created and configured a Hosted Zone for your domain.
{% endhint %}

{% stepper %}
{% step %}
Go to the **AWS Management Console**, type **Route 53** in the search bar, and click on it.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-search.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Navigate to **Hosted Zone** settings for the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-hosted-zones.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Click the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-domain-records.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Click **Create record** button.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-create-record-button.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Return to Mailtrap. On the Domain Verification page, you'll see the DNS records you need to add to AWS Route 53. These are **Domain Verification**, **DKIM**, **DMARC**, and **Domain Tracking**. You'll need the values under **Type**, **Name**, and **Value**.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-mailtrap-dns-records.png" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in AWS Route 53. There are **four CNAME type records** (Domain Verification, DKIM (2), and Custom Tracking Domain) and **one TXT type records** (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../../../.gitbook/assets/mailtrap-dns-record-types.png" alt="Mailtrap Domain Verification page with Type column highlighted showing CNAME and TXT record types" width="563"><figcaption></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
Copy the **Name** and **Value** for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/mailtrap-dns-records-copy.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Paste the **Name** and **Value** into AWS Route 53. The namings of the records are the same in AWS Route 53 as in Mailtrap.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-add-record-form.png" alt="" width="563"></div>

Use the default value for TTL as indicated in Mailtrap. Click Add another record after adding each record in AWS Route 53.
{% endstep %}

{% step %}
Repeat the process of copying and pasting for each record until you've added all the Mailtrap DNS records to AWS Route 53. Click **Create Records**.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-all-records-added.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/aws-route53-recheck-dns.png" alt="" width="563"></div>
{% endstep %}

{% step %}
If you add all the required DNS records correctly, the **Status** of DNS records will change from Missing to **Verified**, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../../../.gitbook/assets/mailtrap-verified-dns-records.png" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, [consult AWS documentation](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-creating.html) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
