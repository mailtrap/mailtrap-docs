---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Email Sandbox

Learn how to inspect and debug emails with sandbox functionality.

1. Catch testing emails from staging.
2. Preview and analyze content for spam.
3. Validate HTML/CSS before sending emails. 

#### Good to know

* Your emails won’t reach your users as you use our Sandbox SMTP.
* You don’t need to verify a domain to use sandbox.

### Email Sandbox Overview

#### Step 1. Navigate to Email Sandbox

Go to [your first Sandbox](https://mailtrap.io/inboxes) by clicking Sandboxes, then My Sandbox. 

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b16cd14a14f74312312f04/file-qMNm0UX5sm.png)

**Tip:** By default, we created an sandbox for you and called it "My Sandbox". The Edit button on the far right allows you to rename either a project or an sandbox.

Once inside “My Sandbox”, copy the credentials from the "Integration" tab to your clipboard.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b16d7c0d5a6676085238a4/file-p8axQ7xFyA.png)

Or, use one of the pre-made code snippets for major programming languages and frameworks:

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b16df44a14f74312312f0a/file-T3tSYwnf3r.png)

#### Step 2. Send your first test email

After sending the first test email, you can immediately find it in your Mailtrap sandbox.

![](https://lh4.googleusercontent.com/82eOJxc8ODR0P40eLN1jjjX-3Hq9BSj_m5mxO7z2CzOHtXEt9g9a1cqGMyYuswfqz0RqMfAyUd6zSh3rJDEbok_gsFfmPelYC2M8sE5901PEf1XvaKPXmY4fnu5UgZNurXLmn5B2GEPhAFLTumuYOWM)

Click on the email, and proceed to inspect and debug it by selecting the HTML Check tab.

![](https://lh5.googleusercontent.com/VceBlKbSXtoCG_XasLPWJdiUr_whrPrmti1TyFh7-mkcLK3sCzo49dy_b-tUTh3OVGu8YLNBp4DQWeNh9GANkCaQ2eevFMfuN-iFPoFCUFKBwYUIi4X5Ad0xFYWPKjwAmWRfALzoM8wrkgcPq7ddQco)

Lastly, you can automate the QA flow with [API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) if you need it.

#### Bonus: Invite your colleagues

Mailtrap is a collaborative tool. Starting from the [Team Plan](https://mailtrap.io/billing/plans/testing), you can create different sandboxes and projects and share them with your colleagues.

That allows you to organize all testing-related workflows among different people - from user management with different permissions to SSO.

### What else you can do with Email Testing

* [Enable email per sandbox feature](https://help.mailtrap.io/article/18-email-per-inbox)
* [HTML or RAW format preview](https://help.mailtrap.io/article/20-test-email-template)
* [HTML Check](https://help.mailtrap.io/article/60-html-check)
* [Automatic Forwarding](https://help.mailtrap.io/article/41-auto-forward) and [Manual Forwarding](https://help.mailtrap.io/article/17-manual-forward) to view emails in real sandboxes
* [Test Bcc and email headers](https://help.mailtrap.io/article/42-email-headers-and-bcc)
