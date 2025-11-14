{% hint style="info" %}
Bulk emails are typically marketing or promotional emails sent to a large number of recipients at once, for example, newsletters, product announcements, etc.
{% endhint %}

{% stepper %}
{% step %}
**Verify the sending domain you own**

To add a domain you own, go to the Sending Domains tab and click Add Domain. Type your domain name and confirm with the Add button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/bulk-add-domain-name.png" alt="Add Domain Name dialog with domain input field and Add button" width="563"></div>

Then, add the DNS records Mailtrap provides to your domain provider.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/bulk-dns-records-verification.png" alt="DNS records verification page showing DKIM, SPF, and DMARC records to add" width="563"></div>

Check our [Sending Domain Setup Guide](sending-domain-setup/) for detailed instructions on adding and verifying your domain.
{% endstep %}

{% step %}
**Integrate your application with Mailtrap**

To send emails via Mailtrap SMTP, follow the instructions [in this article](smtp-integration.md).

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/bulk-smtp-credentials.png" alt="Bulk Stream SMTP credentials with host, port, username, and password" width="563"></div>

To send emails via Mailtrap Email API, follow the steps [in this article](api-integration.md).

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/bulk-api-credentials.png" alt="Bulk Stream API credentials with host and API token" width="563"></div>
{% endstep %}
{% endstepper %}

<details>

<summary>Why is it critical to use different streams for Transactional and Bulk Email?</summary>

The main goal of using different streams is to keep your deliverability high.

</details>
