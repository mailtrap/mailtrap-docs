---
title: Troubleshooting - Email Sending
description: Common issues and solutions for Mailtrap Email Sending
icon: exclamation
---

# Troubleshooting - Email Sending

* [MS Office 365 threat management](#ms-office-365-threat-management-6kmcf)
* [Sending from domain is not allowed](#sending-from-domain-is-not-allowed-qi7mr)
* [I'm getting an "Unauthorised" error (401 code)](#im-getting-an-unauthorised-error-401-code-93cbf)
* [SSL\_ERROR\_NO\_CYPHER\_OVERLAP or Error 1001](#sslerrornocypheroverlap-or-error-1001-vxbg0)
* ["From: Header does not match the sender's domain" error](#how-to-fix-the-from-header-does-not-match-the-senders-domain-error-zcfkh)

## MS Office 365 threat management <a href="#ms-office-365-threat-management-6kmcf" id="ms-office-365-threat-management-6kmcf"></a>

Sometimes transactional messages from Mailtrap (such as email confirmations, invitations to join an sandbox, invoices, etc.) can be sent to Threat Management >> Quarantine by MS Office 365.

If you have faced this issue, follow these steps to resolve it:

1. Go to [https://protection.office.com/#/quarantine](https://protection.office.com/#/quarantine).
2. Select the emails sent from Mailtrap.
3. Click the Release messages button.
4. Check the "Add sender to your organization’s allow list" checkbox.

When signing up for Mailtrap, you have the option to use Office 365 account authorization "oAuth" for smooth integration. In this case, email confirmation won't be required.

## Sending from domain is not allowed <a href="#sending-from-domain-is-not-allowed-qi7mr" id="sending-from-domain-is-not-allowed-qi7mr"></a>

`Error: Mail command failed: 550 5.7.1 Sending from domain is not allowed`

In case you get this error, you tried to send an email using SMTP.

The possible reasons are:

* You’re sending an email with FROM: {anything}@mydomain.com, but in Mailtrap, you’ve verified anotherdomain.com. The verified domain and FROM: domain in your emails should match.
* You added some DNS records for your domain, and now it's not verified or you haven’t passed the Compliance Check. Go to [Sending Domains](https://mailtrap.io/sending/domains) and check the status of the domain you're trying to send emails with. If you don't see the Verified badge next to your domain, click on the domain and check if all DNS records are found by Mailtrap (all should be green). If the records are verified, scroll down to see the Compliance Check status and check if you need to take any additional steps.

## I'm getting an "Unauthorised" error (401 code) <a href="#im-getting-an-unauthorised-error-401-code-93cbf" id="im-getting-an-unauthorised-error-401-code-93cbf"></a>

There are several reasons why you might be getting the "Unauthorised" error.

* Make sure you're sending from the domain that you've set up and verified. Using any other domain will result in the given error.
* If you've configured a custom token for your domain - [make sure it has proper permissions](https://mailtrap.io/api-tokens) to send emails.
* Make sure you're using the correct SMTP/API credentials provided in the Integration tab of your domain.

<figure><img src="../.gitbook/assets/troubleshoot-sending-credentials-both-streams.png" alt="Integration tab showing SMTP and API credentials for both Transactional Stream and Bulk Stream in Mailtrap"><figcaption><p>SMTP and API credentials in Integration tab</p></figcaption></figure>

*   Use the cURL code example to see if you can replicate the error. Here's the path to the exemplary code:

    Sending Domains > Integration > Integrate (under Transactional or Bulk Stream) > Code Samples > cURL.

<figure><img src="../.gitbook/assets/troubleshoot-sending-code-samples.png" alt="Code Samples section in Mailtrap showing cURL integration example"><figcaption><p>Code Samples section with cURL example</p></figcaption></figure>

## SSL\_ERROR\_NO\_CYPHER\_OVERLAP or Error 1001 <a href="#sslerrornocypheroverlap-or-error-1001-vxbg0" id="sslerrornocypheroverlap-or-error-1001-vxbg0"></a>

When using a custom domain for click tracking, you may encounter `SSL_ERROR_NO_CYPHER_OVERLAP` or `Error 1001` error.

<figure><img src="../.gitbook/assets/troubleshoot-sending-ssl-error.png" alt="Browser showing SSL_ERROR_NO_CYPHER_OVERLAP or Error 1001 when accessing custom tracking domain"><figcaption><p>SSL error when accessing custom domain for click tracking</p></figcaption></figure>

#### Custom Domain for Click Tracking

Mailtrap allows you to use your own domain for click tracking. To achieve this, you need to add an mt-link CNAME record during the domain setup process. Mailtrap also facilitates issuing a security certificate for the mt-link subdomain to ensure a secure connection. Certificates from Let's Encrypt and Google Trust Services are used.

#### The Cause of the Error

Some domains have a list of trusted Certificate Authorities (CAs) specified in CAA records. If this list doesn't include Google Trust Services and Let's Encrypt, Mailtrap won't be able to request certificates from them. Consequently, click tracking won’t work because the browser won't be able to establish a secure connection.

#### Checking Your CAA Records:

You can check the CAA records for your domain using the following command:

```
dig CAA example.com
```

The output might look similar to this:

```
;; ANSWER SECTION:
example.com.   13990    IN    CAA    0 issue "globalsign.com"
example.com.   13990    IN    CAA    0 issuewild "globalsign.com"
```

#### Resolving the Error

If you want to keep your existing CAA records, you need to modify them to include Google Trust Services and Let's Encrypt:

```
# Google Trust Services
0 issue "pki.goog; cansignhttpexchanges=yes"

# Let's Encrypt
0 issue "letsencrypt.org"
```

<figure><img src="../.gitbook/assets/troubleshoot-sending-caa-records-form.png" alt="DNS provider interface showing CAA record configuration form with Type, Name, TTL, Flag, Tag, and Domain fields"><figcaption><p>CAA record configuration form</p></figcaption></figure>

| Type   | Value                                                                                                  | Description                                                                                                |
| ------ | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Name   | blank or `@` , depending on your provider                                                              | <p><br></p>                                                                                                |
| TTL    | 1 hour or any other appropriate TTL                                                                    | It controls how long the record is valid.                                                                  |
| Flag   | 0                                                                                                      | \`0\` means that no flags have been set. Please read the documentation if you need more specific behavior. |
| Tag    | issue                                                                                                  | It allows the CA to issue certificates for this domain and its subdomains (e.g., mt-link subdomain).       |
| Domain | <ul><li><code>pki.goog; cansignhttpexchanges=yes</code></li><li><code>letsencrypt.org</code></li></ul> | Google Trust Services needs an additional parameter, `cansignhttpexchanges=yes` .                          |

#### Additional Information

It can take several hours for the changes to your CAA records to propagate after creating them. Eventually, you should be able to resolve the error and ensure your mt-link subdomain functions correctly:

<figure><img src="../.gitbook/assets/troubleshoot-sending-ssl-resolved.png" alt="Browser showing successful secure connection to mt-link.mailtrap.io verified by Google Trust Services LLC"><figcaption><p>Successful SSL connection after CAA records configuration</p></figcaption></figure>

## How to fix the "From: Header does not match the sender's domain" error? <a href="#how-to-fix-the-from-header-does-not-match-the-senders-domain-error-zcfkh" id="how-to-fix-the-from-header-does-not-match-the-senders-domain-error-zcfkh"></a>

To send email with Mailtrap you `From:` should match your domain. In example, your verified domain in Mailtrap is acme.com, so your `From:` could be {anything}@acme.com. If you send from your subdomain, you From: domain should match your subdomain.

Laravel

First, check if your domain has been added to your account. If not, please add and verify the domain.

Next, check if your _`mail message`_ has a `From:` header and that the `From:` header also contains an address on your domain.

Most likely, the `MAIL_FROM_NAME` is the only variable used for the `envelope from` address, and it's not the same as the header. Please make sure it’s the same as the header.
