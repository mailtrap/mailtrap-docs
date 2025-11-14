---
icon: exclamation
---

# Get Started - Bulk Stream

{% hint style="info" %}
Bulk emails are typically marketing or promotional emails sent to a large number of recipients at once, for example, newsletters, product announcements, etc.
{% endhint %}

{% stepper %}
{% step %}
#### Verify the sending domain you own

To add a domain you own, go to the Sending Domains tab and click Add Domain. Type your domain name and confirm with the Add button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfBVdp9d0wjUPpthAPzPeNnlkJHK6Bm03SJoZM5-XEChiwHHJ7XeiQ8E9dtfkxJR52zWdJ7wZy9QqDkGDk_WqJP0IKjUP2btux41nM7YrRjd_b_pqJviWCIVA5i8tDu1WKkphXlWVRFF7YVKDtIFgDVAv47?key=weXL3hiMUUu1WTp53wm5ng" alt="" width="563"></div>

Then, add the DNS records Mailtrap provides to your domain provider.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcH3jMljRY-eAPjqIOHx7wPFWthcAoIIfIjX70AOTn9vwfpiJE6it1D0U5zAoIcG6FxW8M_Wdcm9C9YWEHH6dJaWDUyQ7qM1YOH-AML_zIwZSveZgUVPXIHnHZY9w24x_GI9TN8-XcBJg9QwCltgNhW3kTE?key=weXL3hiMUUu1WTp53wm5ng" alt="" width="563"></div>

Check our [Sending Domain Setup Guide](sending-domain-setup/) for detailed instructions on adding and verifying your domain.
{% endstep %}

{% step %}
#### Integrate your application with Mailtrap

To send emails via Mailtrap SMTP, follow the instructions [in this article](smtp-integration.md).

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdOxRylYXh4PfS1sahw5IeGcczK6kTTX94GBVLIa8wPB6TIw63oRYss4yw12fPj4URlidKX_5WDDKBzBgw95d2uZqnTzGgB9MsI_m_mO9NOow-FrxXiLlzUyPlNIzrHm4YwTAr6B4hWV3K1AORNo588BrQz?key=weXL3hiMUUu1WTp53wm5ng" alt="" width="563"></div>

To send emails via Mailtrap Email API, follow the steps [in this article](api-integration.md).

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdCCOREBVQbvNpdAyJTlvkH3cJj0GzeMRmMSqbAW5aBPxBS3C8YcinENrGBqdpg6I1ca0ja7hZOu4O4jx8KS-p2jLWL-pWqXPwC3wPsRJYOZcAw3fh8GxoqAeWYS6mZmZpAwZASJ7lAmQrrX9C50iEKCy3i?key=weXL3hiMUUu1WTp53wm5ng" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

<details>

<summary>Why is it critical to use different streams for Transactional and Bulk Email?</summary>

The main goal of using different streams is to keep your deliverability high.

</details>
