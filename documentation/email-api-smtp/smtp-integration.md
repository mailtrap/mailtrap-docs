---
description: >-
  Integrate Mailtrap SMTP. Get SMTP credentials, choose transactional or bulk
  sending, use code samples, and start sending.
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

# SMTP integration

Learn how to integrate your application via SMTP.

1. Go to the Sending Domains tab and choose the domain you want to send emails from. Remember that you’ll be able to start sending emails once the [domain is verified](sending-domain-setup/).
2. Open the Integrations tab.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/gYGy9BXrQMZp-EigE0LA7cTrDr63jn0_9lwrZXXOD8B19171U2IXU-TEMlH_F7jH33E2r_e55qukYRTQAaPnSthYEW-d_HDII_CHiaJF1aeBZJH40LpIqolcfJB5EsaZnCJuASM8dfVyY01dthJHDv4" alt="" width="563"></div>

3. Click the Integrate button under Transactional Stream or Bulk Stream.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/scIgiBuvYnuwQXtW5byVP4QLGQyjfMu-1MgdJhTLDHoQStph_ONouURbf-djFkngLJMDqL1ZTd6bvyMbDbOx4IyoJ8D8bAuiZ85E0sU-bnrF09qimzsFjb8nNt4Sv4nDzdGy9w9uqC56fB4erDpQor8" alt="" width="375"></div>

* Transactional Stream is used to send automated, non-promotional application emails that are triggered by the user’s specific action.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a240c06eb51e63b8f9dc95/file-gEDHceUiAf.png" alt="" width="563"></div>

* Bulk Stream is used to send a single marketing campaign to a large group of recipients in bulk.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a240cc9638c36b868f1b66/file-m4ll9av3Ug.png" alt="" width="563"></div>

4. Toggle the switch to SMTP and copy credentials, such as Host, Port, Username, and Password and paste them into your project, app, email-sending service, or any platform that supports SMTP.

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a24162d39e504a2aed1cbd/file-0a2G0GSPDs.png" alt="" width="563"><figcaption><p>Transactional Stream SMTP credentials</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a241a26eb51e63b8f9dc96/file-CGe0ccmAlM.png" alt="" width="563"><figcaption><p>Bulk Stream SMTP credentials</p></figcaption></figure></div>

* Alternatively, choose the programming language or framework from the menu under Code Samples and copy the sample configuration containing your credentials.

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a242458919a15d1b1d1f84/file-loZgd6vu5c.png" alt="" width="563"><figcaption><p>Transactional Stream code samples</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a2427848915f570c6a8845/file-YvlB4mk58M.png" alt="" width="563"><figcaption><p>Bulk Stream code samples</p></figcaption></figure></div>

5. Complete your email-sending script and run it. If you did everything correctly, you should find the sent email in the inbox of the email address you indicated in the script. The email will also appear in Email Logs in Mailtrap.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/z1Ez69cZmidYH3J06QTnGdd6a0okqkvleAUVLwiI4xCq1qwvXvodvPjFEpag07m4I70l6bQWBcV8jNHVLLwd5zDU5nK4TivQ-0Ngvx0TgXgyn34UESPG5ur8nnxvL4urfAxxtiX5hiXsHBFRFa7cFdA" alt="" width="563"></div>

Remember that each domain has different SMTP credentials that you can always access by clicking on the desired domain and going to the Integrations tab.

You can also create additional API tokens (or SMTP passwords) by going to Settings → API Tokens and clicking Add Token.

<a href="email-sandbox/email-marketing/account-and-billing/user-management/troubleshooting/privacy-and-security/api-tokens.md" class="button primary" data-icon="magnifying-glass">Learn more about API Tokens</a>

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/VkkmQj64_MMwu99HRd5Hi5jMh3fihYc1zhSyDwouB2azhBhOGjFlfVaM6zZRitcL-ftSLyAdG_dOfCkrTQ_4dQOng0pf8LwKveAgYAV7oKZLU8MPWeSKPHe3ZQPPT643QbUVUQMPtNBC4ncYUdvSc-E" alt="" width="563"></div>

{% hint style="info" %}
_If you need any help with SMTP integration, please, contact our support team at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._
{% endhint %}
