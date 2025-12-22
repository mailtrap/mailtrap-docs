---
title: Sending Glossary
description: >-
  Definitions of key terms and phrases used in Mailtrap Email API/SMTP,
  including DNS records, email events, SMTP settings, and deliverability
  concepts.
icon: book-open
---

# Sending Glossary

This glossary explains key terms and phrases used in Mailtrap Email API/SMTP.

## A

**API sending** — Send emails using Mailtrap's API endpoints. Our API is compatible with SendGrid, Mandrill, and Mailgun APIs.

**AWS CLI** — An abbreviation for Amazon Web Services Command Line Interface. It's a tool to control and manage AWS resources. Mailtrap provides DNS records in JSON format for AWS Route53 to create records using AWS CLI.

**AWS Route53** — A DNS service from Amazon. If you use it, you can copy-paste the DNS records in JSON format and add them to AWS Route53.

## B

**Bounce** — One of the possible events, also known as "hard bounce". Most commonly, a bounce occurs when the recipient's email address is incorrect or the server declines a message. It indicates a permanent failure of delivery. You won't be able to send any further emails to this address from this domain.

**Bounce rate** — The percentage of bounced emails. A bounce event may happen due to an invalid address, your email not passing certain mailbox provider criteria, or a connection issue. Note that it's the recipients who bounce the emails, not Mailtrap. To secure great deliverability in the long run, you want to keep the bounce rate low.

## C

**Category** — A method used to categorize different types of emails sent from your Mailtrap account. You specify a category when creating an email as one of its parameters. For each unique category specified this way, you'll be able to see separate email analytics. Example categories can include password reset, invoice, welcome email, etc.

**Click** — An event that occurs when a link in your email is clicked. Click tracking must be enabled prior to sending an email for any clicks to be recorded.

{% hint style="info" %}
When an email with click tracking enabled is forwarded, all further clicks will also be included in the click count.
{% endhint %}

**Click rate** — The percentage of opened emails that got one or more clicks on their links. All clicks are recorded and can be seen under Events History in the Email Logs menu. But only the first click is calculated towards the Click Rate within a selected period.

**Client sending IP** — IP address of a device that was used to send an email.

**cURL** — A command-line tool to transfer data using various protocols and an option to quickly make API calls. With Mailtrap, you get a sample cURL code with an API to send an email to yourself.

## D

**DNS records** — A DNS record is an instruction stored at a DNS server. It describes how to handle requests from that domain. Certain records you add give Mailtrap a guarantee that you own the domain and have the right to send from it. Other records let mailbox providers know that you're an authenticated server and boost your email deliverability.

### DNS record types

| Record type                     | Description                                                                                                                                                                                                                                                            |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CNAME domain authentication** | DNS record used for verification purposes. Mailtrap uses it to verify that you're the owner of a domain and can send through it.                                                                                                                                       |
| **SPF**                         | A very common TXT-type authentication method. It specifies which IP addresses (mail servers) are authorized to send emails on your behalf.                                                                                                                             |
| **DKIM**                        | A CNAME type authentication method, an encrypted digital signature that comes with each email. Mailtrap uses private keys to sign the body and the header of your emails before sending them to the mailbox providers.                                                 |
| **DMARC**                       | A TXT type email authentication protocol used to ensure an authenticated email domain aligns with the domain found in the `from:` address. It's an additional security layer that tells mailbox providers what to do with your emails should they fail authentication. |

**Domain** (or **Sending Domain**) — The domain used in the `from:` field of an email. You must be the owner of a domain and have it verified to be able to send emails from Mailtrap. No public domains can be used with Mailtrap Sending (e.g. Gmail, Hotmail).

## E

**Email Logs** — The list of all the emails sent from your account. Contains all the vital details of each message, including the recipient's details, timestamps, HTML/CSS of a message, opens/clicks stats, as well as additional tools, such as email preview or spam check.

**Event** — A particular action that occurred to your email. The available events are: Sending, Delivery, Reject, Open, Click, Bounce, Spam, Unsubscribe, Soft Bounce, Suspension. In the Email Logs, you can view all the events associated with a particular message in chronological order.

## M

**Mailbox provider** — An email service used by the end recipient to receive emails. Examples include Gmail, Outlook, Cisco email protection, or Mimecast email protection.

**Mailtrap sending IP** — IP address of Mailtrap, used to send a message to the final recipient.

## O

**Open** — An event that occurs when an email is opened. Mailtrap inserts an invisible pixel into an email. When a message is opened and a pixel is "displayed", an 'open' event is recorded.

{% hint style="info" %}
Some mailbox providers, browsers, and plugins block the tracking of opens. Users or their providers can also block images from being displayed. In each of these cases, no "open" event will be recorded even if an email is opened.
{% endhint %}

## R

**Recipient IP** — IP address of a device or an email server where an email was opened. If a message is opened on devices using different IP addresses, multiple recipient IPs will be recorded. If a message is not opened at all, no recipient IP will be displayed.

## S

**SMTP** — Short for Simple Mail Transfer Protocol, SMTP is a protocol that facilitates email transmissions.

### SMTP Settings

| Setting      | Description                                                                                                                                                                                       |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Host**     | Name of Mailtrap's outgoing email sending server.                                                                                                                                                 |
| **Port**     | Communication endpoints responsible for moving email data between servers via SMTP. Mailtrap supports 587, 2525, and 25 ports. We recommend using 587 because it's the standard secure SMTP port. |
| **Username** | When configuring Mailtrap Sending with SMTP, the username is 'api'.                                                                                                                               |
| **Password** | Mailtrap uses API tokens as SMTP passwords. By default, a token is generated when you add a domain.                                                                                               |
| **Auth**     | Authentication mechanism that Mailtrap supports. We use two common mechanisms: LOGIN, PLAIN.                                                                                                      |
| **TLS**      | Short for Transport Layer Security, TLS is a protocol that encrypts and delivers mail securely.                                                                                                   |

**Spam** — One of the possible email events. This happens when a recipient chooses to report a message as spam. No further messages will be delivered to such recipients. Recurring spam complaints are known to very negatively influence email deliverability.

**Spam complaints** — The percentage of delivered emails that got labeled as spam by recipients. It also includes the emails that got automatically labeled as spam by mailbox providers.

**Status** — Indicates the most recent state of your message. The available statuses are: Delivered, Not Delivered, Enqueued, and Opted Out. An email can have only one status at a time.

**Suppression list** — A list of email addresses that Mailtrap won't send any further emails to. Email addresses land on a suppression list when a message bounces, a recipient unsubscribes, or they report an email as spam.

{% hint style="info" %}
Suppression lists are individual for each of your sending domains. If an address lands on such a list for domain X, it won't prevent you from sending emails to them from other verified domains.
{% endhint %}

## T

**Transactional email** — The type of email triggered by a user's action (e.g. registration, password reset, etc.) or a certain event in the system (monthly invoice, notification about a limit reached, etc.). Transactional emails are usually triggered separately for each recipient, as opposed to marketing or sales emails that are traditionally sent in batches.

## U

**Unique open rate** — The percentage of opened emails out of all delivered emails within a specified period. Recipients may block tracking on their end, so the actual open rate could be higher than what you see in Mailtrap.

**Unsubscribe** — One of the possible events. It occurs when a recipient of your email clicks on the "unsubscribe" link in your message. No further emails will be sent to this recipient from a given domain.
