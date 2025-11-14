---
description: >-
  Integrate Mailtrap email API. Get API credentials, choose transactional or
  bulk sending, use SDKs or code samples, and start sending.
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

# API integration

Use API credentials to integrate Mailtrap with your project.

1. Go to the Sending Domains tab and choose the domain you want to send emails from. Remember that you’ll be able to start sending emails once the domain is verified.
2. Open the Integration tab.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/m2ijl7AqsNHDotlvsRBBMHNWOz5YUiOfF7riOlkPC8XH6imNLqbE0jtWarhXIL4aew3JxPnHNkruXFwvF-tSfUX206CxGbJR1Ll33tlkK8QjyPrN5xRTq02Ybc4t4dlzeanHfwlcmJVzKixLawQO2Vk" alt="" width="563"></div>

3. Click the Integrate button under Transactional Stream or Bulk Stream.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/R8o93mWlwrNEEbGIkpzAwM8_TRTuCPIFJ9XdtKRGUzRLzKAKGFW3Mk2SFXnEwGpNm2IA-NHzouieBFRRMhSlJqLy51SXAB12jrsZGJNaF5IcHX-TYbmbeu6gsX_ixwGEiKP8-Z9VoAW9zK3iZE0TJug" alt="" width="375"></div>

* Transactional Stream is used to send automated, non-promotional application emails triggered by the specific user action.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a2450048915f570c6a8846/file-3nPXwIZaNk.png" alt="" width="563"></div>

* Bulk Stream is used to send a single marketing campaign to a large group of recipients in bulk.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a2451948915f570c6a8847/file-ZRDhVyUvU1.png" alt="" width="563"></div>

4. Toggle the switch to API.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a24577d39e504a2aed1cbf/file-Lj2WUAEACu.png" alt="" width="563"></div>

5. Build the authenticated HTTP request in your programming language or framework and configure it with Mailtrap Host and API Token.

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a245e96eb51e63b8f9dc97/file-qjoAogG22Y.png" alt="" width="563"><figcaption><p>Transactional Stream API credentials</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a246176eb51e63b8f9dc98/file-yWEym3bHnF.png" alt="" width="563"><figcaption><p>Bulk Stream API credentials</p></figcaption></figure></div>

*   Alternatively, choose the programming language or framework from the menu under Code Samples and copy the sample configuration already containing your credentials. In this menu, you’ll find official SDKs for [PHP](https://github.com/railsware/mailtrap-php), [Python](https://github.com/railsware/mailtrap-python), [Ruby](https://github.com/railsware/mailtrap-ruby), and [Node.js](https://github.com/railsware/mailtrap-nodejs).

    _Note: For now, only Ruby, PHP (Laravel + Symfony), and Node.js SDKs support Bulk Stream, but others are in development. Request and response examples are also available_ [_here_](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/67f1d70aeb62c-send-email-including-templates)_._

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a2468c6eb51e63b8f9dc9a/file-QfrIxlNCkH.png" alt="" width="563"><figcaption><p>Transactional Stream code samples</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a2469a6eb51e63b8f9dc9b/file-w5kQFpcn4l.png" alt="" width="563"><figcaption><p>Bulk Stream code samples</p></figcaption></figure></div>

6. Complete your script and run it. If you did everything correctly, you should find the sent email in the inbox of the email address you indicated in the script. The email will also appear in Email Logs in Mailtrap.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/sBKpOoDvt_7hTAEfmVu7f3TMeipJ3nK1ZoElNqPlwpf2aQD_OlMGyDAcP9LmzfonKkBEcAXbtyG8G_CvIE4QnJo5tq_mHNMW0l9Acd7sFyRn-J011XnKVAU5RS4EYI66GHnj_4nHdFRbUchVSU5hHy4" alt="" width="563"></div>

Remember that each domain has different API tokens that you can always access by clicking on the desired domain and going to the Integration tab.

You can also create additional API tokens by going to Settings → API Tokens and clicking Add Token.

<a href="email-sandbox/email-marketing/account-and-billing/user-management/troubleshooting/privacy-and-security/api-tokens.md" class="button primary" data-icon="magnifying-glass">Learn more about API Tokens</a>

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/eniGWd9R_Qg8BeachWjf1WpO1LKMEBiNrWDXFGxVJoJcvobyRbULGRuzE8nhKVjjO3kkar8vOFb2fkxUYnCYgP4CpYEZyNulgft_MXel97FrybiPWkZ2zVP65Am0vQqC59LQBX3MF7p8wTm-SPlz5AE" alt="" width="563"></div>

Mailtrap Email Sending API supports:

* attachments
* [email templates](email-sandbox/email-marketing/email-templates.md)
* [custom variables](custom-variables.md)
* [email categories](statistics/email-categories.md)

{% hint style="info" %}
_If you need any help with API integration, please, contact our support team at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._
{% endhint %}

