---
title: Troubleshooting - Email Sandbox
description: Common issues and solutions for Mailtrap Email Sandbox
icon: exclamation
---

# Troubleshooting - Email Sandbox

**In this article**

* [Connection errors](#connection-errors)
* [Expected response code 250 but got code "530", with the message "530 5.7.1 Authentication required"](#id-530)
* [Messages are not delivered to my sandbox](#not-in-sandbox)
* [Mail not delivered to the recipient](#recipient)
* [Why is my sandbox email address disabled?](#address-disabled)
* [Tech info/ headers unavailable](#headers)
* [I can't add more team members](#team-members)
* [Automatic Forwarding doesn't work](#forwarding)
* [I see suspicious emails in my sandbox](#suspicious-emails)

## Connection errors <a href="#connection-errors" id="connection-errors"></a>

If you can't connect to the Sandbox SMTP server and receive errors _Connection cannot be established_ or _Connection timed out_, follow the steps described below. 

First, test your connection using the Telnet utility:  `telnet sandbox.smtp.mailtrap.io 2525` .

If Telnet shows that a connection can't be established with our server, follow the next steps:

1. Try using another SMTP port: 2525, 465, or 25. In most cases, the issue is related to the firewall blocking the SMTP port.
2. If none of these ports work, try connecting with a different machine, location, or ISP, or use a VPN. This will help identify the route affected by the issue.
3. Check if the SMTP connection is not closed on idle timeout on the server side. If you’ve opened an SMTP connection and haven't closed it afterward, the SMTP server will close the session after the idle timeout time.

To make sure our SMTP server is up and running, go to the [Status page](http://status.mailtrap.info/). Here, you can check the SMTP server availability from different locations.

If the issue persists, please let us know at [support@mailtrap.io](mailto:support@mailtrap.io).

## Expected response code 250 but got code "530", with the "530 5.7.1 Authentication required" message <a href="#id-530" id="id-530"></a>

When you receive the _5.7.1 Authentication required_ error, it means that either:

* The SMTP authentication is disabled in your configuration, or
* The authentication failed.

In either case, an email was not sent.

Please enable SMTP authentication in your settings and configure your app to enable SMTP authentication. If it is already enabled, revise your credentials and authentication settings, and try sending an email again.

## Messages are not delivered to my sandbox <a href="#not-in-sandbox" id="not-in-sandbox"></a>

1\. Check your [SMTP integration](how-to-integrate-email-sandbox-with-your-application.md)

* Go to your sandbox Integration tab;
* Compare hostname, username, and password with those in your app (if you reset SMTP/POP3, all existing integrations are affected)

2\. Make sure that the number and frequency of the messages sent correspond to the terms of your [billing plan](https://mailtrap.io/pricing/).

If everything is correct, view your SMTP logs and check whether you received any errors. To view SMTP logs, enable debugging in your email code. [Here is an example of how to do this PHPMailer](https://mailtrap.io/blog/phpmailer/).

If you still can’t figure out why your emails aren’t getting delivered to your sandbox, please save an undelivered message in **.eml** format and send it to us at support@mailtrap.io. Just don't forget to remove any sensitive information!

## Why is my sandbox email address disabled? <a href="#address-disabled" id="address-disabled"></a>

Email per sandbox is a premium feature available in the [Basic, Team, Enterprise, or Business plans.](https://mailtrap.io/pricing/).

<figure><img src="../.gitbook/assets/troubleshoot-sandbox-email-address-disabled.png" alt="Sandbox Email Address tab showing disabled status with upgrade message"><figcaption><p>Email address disabled - upgrade required</p></figcaption></figure>

Once you upgrade your plan, make sure you activate the address. Go to the Email Address tab in your sandbox, click the three-dot menu to the right, and select Enable.

<figure><img src="../.gitbook/assets/troubleshoot-sandbox-enable-email-address.png" alt="Email Address menu with Enable option highlighted"><figcaption><p>Enable email address option</p></figcaption></figure>

Of course, you can freely test emails without this feature.

With any plan (including the free tier), you can integrate SMTP credentials into your app and receive every email this way.

You’ll find the integration samples for over 20 frameworks and libraries on the Integration page of your sandbox. You can also use the API without any restrictions.

## Tech info/headers unavailable <a href="#headers" id="headers"></a>

The Tech Info tab will show the following headers if they’re present in an email:

* Message\_id
* X\_mailer
* Sender
* From
* To
* Cc
* Reply\_to
* Return\_path

If any of these headers haven’t been specified (for example, an email doesn’t have a reply\_to header specified), it won’t be displayed.

If you are on the Business plan or higher ([view plans](https://mailtrap.io/pricing/)), you will also see the BCC header in this tab (if specified for the message). On lower plans, no bcc field will appear even if it was included with a message.

## I can't add more team members <a href="#team-members" id="team-members"></a>

If that happens, you may have reached the user limit of your plan.

## Automatic Forwarding doesn't work <a href="#forwarding" id="forwarding"></a>

If your test emails aren’t forwarded, there’s very probably an error in the auto-forwarding configuration.

When auto-forwarding to the predefined addresses/domains, sandbox verifies the ‘to’ and ‘cc’ headers of a message (bcc is ignored). An email is forwarded if:

* TO or CC of your email matches the value in the Emails list or
* The domain in the TO or CC of your email matches the value in the Domains list.

Remember that a forwarding rule needs to be verified (its status must be ‘Active’) before it can be considered. To do that, you’ll need to confirm the email address or the domain's ownership.

If a particular email is not forwarded, check its headers via the Tech Info tab to see whether you have the correct TO or CC address set.

## I see suspicious emails in my sandbox <a href="#suspicious-emails" id="suspicious-emails"></a>

If you see emails in your sandbox that you didn’t send from your app,  someone may have accessed your SMTP credentials.

Don't panic, though. It's very easy to reset your credentials. Log in to your dashboard, open your sandbox, and go to the Integration tab. There, click the Reset Credentials button, and your details will be reset right away. Make sure you update them in your app, as old credentials will no longer be valid.

<figure><img src="../.gitbook/assets/troubleshoot-sandbox-reset-credentials.png" alt="Integration tab with Reset Credentials button highlighted"><figcaption><p>Reset Credentials button in Integration tab</p></figcaption></figure>

Unfortunately, we don’t store information about the server or IP address that sent the message in question. As such, we won’t be able to help you track down the sender.
