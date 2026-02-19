---
title: SMTP integration
description: >-
  Integrate Mailtrap SMTP. Get SMTP credentials, choose transactional or bulk
  sending, use code samples, and start sending.
icon: envelope-open
---

# SMTP Integration

Learn how to integrate your application via SMTP.

{% stepper %}
{% step %}
Go to the **Sending Domains** tab and choose the domain you want to send emails from. Remember that you'll be able to start sending emails once the [domain is verified](sending-domain-setup/).
{% endstep %}

{% step %}
Navigate to the **Integrations** tab for your selected domain.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/smtp-integration-tab-navigation.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Click the Integrate button under **Transactional Stream** or **Bulk Stream**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/smtp-integration-stream-selection.png" alt="" width="375"></div>

**Transactional Stream** is used to send automated, non-promotional application emails that are triggered by the user's specific action.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/smtp-integration-credentials-transactional.png" alt="" width="563"></div>

**Bulk Stream** is used to send a single marketing campaign to a large group of recipients in bulk.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/smtp-integration-credentials-bulk.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Toggle the switch to SMTP and copy credentials, such as **Host**, **Port**, **Username**, and **Password** and paste them into your project, app, email-sending service, or any platform that supports SMTP.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/smtp-integration-credentials-transactional.png" alt="Transactional Stream SMTP credentials showing highlighted credentials section with Host, Port, Username, Password, Auth, and STARTTLS fields" width="563"><figcaption><p>Transactional Stream SMTP credentials</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/smtp-integration-credentials-bulk.png" alt="Bulk Stream SMTP credentials showing highlighted credentials section with Host, Port, Username, Password, Auth, and STARTTLS fields" width="563"><figcaption><p>Bulk Stream SMTP credentials</p></figcaption></figure></div>

Alternatively, choose the programming language or framework from the menu under **Code Samples** and copy the sample configuration containing your credentials.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/smtp-integration-code-samples-transactional.png" alt="Transactional Stream integration showing highlighted Code samples section with cURL example and programming language options" width="563"><figcaption><p>Transactional Stream code samples</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/smtp-integration-code-samples-bulk.png" alt="Bulk Stream integration showing highlighted Code samples section with cURL example and programming language options" width="563"><figcaption><p>Bulk Stream code samples</p></figcaption></figure></div>
{% endstep %}

{% step %}
Complete your email-sending script and run it. If you did everything correctly, you should find the sent email in the inbox of the email address you indicated in the script. The email will also appear in Email Logs in Mailtrap.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (8).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

Remember that each domain has different SMTP credentials that you can always access by clicking on the desired domain and going to the **Integrations** tab.

You can also create additional API tokens (or SMTP passwords) by going to **Settings** → **API Tokens** and clicking **Add Token**.

<a href="setup/api-tokens.md" class="button primary" data-icon="magnifying-glass">Learn more about API Tokens</a>

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/smtp-tokens-add-token.png" alt="" width="563"></div>

{% hint style="info" %}
If you need any help with SMTP integration, please, contact our support team at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
