---
icon: exclamation
---

# Troubleshooting - Email Sending

* [MS Office 365 threat management](https://help.mailtrap.io/article/116-troubleshooting-email-sending#MS-Office-365-threat-management-6Kmcf)
* [Sending from domain is not allowed](https://help.mailtrap.io/article/116-troubleshooting-email-sending#Sending-from-domain-is-not-allowed-qI7MR)
* [I'm getting an "Unauthorised" error (401 code)](https://help.mailtrap.io/article/116-troubleshooting-email-sending#Im-getting-an-Unauthorised-error-401-code-93CbF)
* [SSL\_ERROR\_NO\_CYPHER\_OVERLAP or Error 1001](https://help.mailtrap.io/article/116-troubleshooting-email-sending#SSLERRORNOCYPHEROVERLAP-or-Error-1001-vxBG0)
* ["From: Header does not match the sender's domain" error](https://help.mailtrap.io/article/116-troubleshooting-email-sending#How-to-fix-the-From-Header-does-not-match-the-senders-domain-error-zCFKH)

### MS Office 365 threat management <a href="#ms-office-365-threat-management-6kmcf" id="ms-office-365-threat-management-6kmcf"></a>

Sometimes transactional messages from Mailtrap (such as email confirmations, invitations to join an sandbox, invoices, etc.) can be sent to Threat Management >> Quarantine by MS Office 365.

If you have faced this issue, follow these steps to resolve it:

1. Go to [https://protection.office.com/#/quarantine](https://protection.office.com/#/quarantine).
2. Select the emails sent from Mailtrap.
3. Click the Release messages button.
4. Check the "Add sender to your organization’s allow list" checkbox.

When signing up for Mailtrap, you have the option to use Office 365 account authorization "oAuth" for smooth integration. In this case, email confirmation won't be required.

### Sending from domain is not allowed <a href="#sending-from-domain-is-not-allowed-qi7mr" id="sending-from-domain-is-not-allowed-qi7mr"></a>

`Error: Mail command failed: 550 5.7.1 Sending from domain is not allowed`

In case you get this error, you tried to send an email using SMTP.

The possible reasons are:

* You’re sending an email with FROM: {anything}@mydomain.com, but in Mailtrap, you’ve verified anotherdomain.com. The verified domain and FROM: domain in your emails should match.
* You added some DNS records for your domain, and now it's not verified or you haven’t passed the Compliance Check. Go to [Sending Domains](https://mailtrap.io/sending/domains) and check the status of the domain you're trying to send emails with. If you don't see the Verified badge next to your domain, click on the domain and check if all DNS records are found by Mailtrap (all should be green). If the records are verified, scroll down to see the Compliance Check status and check if you need to take any additional steps.

### I'm getting an "Unauthorised" error (401 code) <a href="#im-getting-an-unauthorised-error-401-code-93cbf" id="im-getting-an-unauthorised-error-401-code-93cbf"></a>

There are several reasons why you might be getting the "Unauthorised" error.

* Make sure you're sending from the domain that you've set up and verified. Using any other domain will result in the given error.
* If you've configured a custom token for your domain - [make sure it has proper permissions](https://mailtrap.io/api-tokens) to send emails.
* Make sure you're using the correct SMTP/API credentials provided in the Integration tab of your domain.

![](https://lh7-us.googleusercontent.com/2jsTyFIASQcq4huw61kK-00vgyH6DP9UDEm6KxlEahnOw6YqWLGCc7QuUgOKEAXnIm3OKXMVBukaauGkVqMInTc_5WQ-gRCSEroxzl24cMvH0WtFuqKPEdBHHuYgM4m-DO3mGzVCueAsQbSUbnpO0RA)

*   Use the cURL code example to see if you can replicate the error. Here's the path to the exemplary code:

    Sending Domains > Integration > Integrate (under Transactional or Bulk Stream) > Code Samples > cURL.

![](https://lh7-us.googleusercontent.com/QTCHKrMQh6DNibhV9x8MW65mO8ppVPqEgpQBAiL6AluflFuxiAmKr2tFWjsgZL5FALSaB_SayOlm5Vnnd6zk_5XhbkXa-Vx7-AX1kgZ1MZDW0nZlmMaLx_aA3t3hHcNsNJHgXZNqIHf3PPF3dEabzv0)

### SSL\_ERROR\_NO\_CYPHER\_OVERLAP or Error 1001 <a href="#sslerrornocypheroverlap-or-error-1001-vxbg0" id="sslerrornocypheroverlap-or-error-1001-vxbg0"></a>

When using a custom domain for click tracking, you may encounter `SSL_ERROR_NO_CYPHER_OVERLAP` or `Error 1001` error.

![](https://lh7-us.googleusercontent.com/lsA4u4fL3vAB-L8CG5rM2dHM8PNiM4C1itn68k6hokws0eKpJtETh0PScslHpZRShh6kP6ei8HaLfpwDXF55ZmEJBKwGt4K4b51rp0BLFhSHu4rJ1Wz7NPjFtdAZ7ZK3JyOMlCa0mlUmIECyN2A8mZQ)

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

![](https://lh7-us.googleusercontent.com/qej3Tsb4grsj_yLxdF6oVNRoQKBC8CoY0LPO3Cte7XKw9CrbId4_jJuaumeppBYUcy2DdEVbui0ssWpE1AEGQMAzR8FrxpnJDzz1LkJvdVAyecfGe5SWv9wXImOukbKjs1jCVBlv1gtPObQ_wKWUK4U)

| Type   | Value                                                                                                  | Description                                                                                                |
| ------ | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| Name   | blank or `@` , depending on your provider                                                              | <p><br></p>                                                                                                |
| TTL    | 1 hour or any other appropriate TTL                                                                    | It controls how long the record is valid.                                                                  |
| Flag   | 0                                                                                                      | \`0\` means that no flags have been set. Please read the documentation if you need more specific behavior. |
| Tag    | issue                                                                                                  | It allows the CA to issue certificates for this domain and its subdomains (e.g., mt-link subdomain).       |
| Domain | <ul><li><code>pki.goog; cansignhttpexchanges=yes</code></li><li><code>letsencrypt.org</code></li></ul> | Google Trust Services needs an additional parameter, `cansignhttpexchanges=yes` .                          |

#### Additional Information

It can take several hours for the changes to your CAA records to propagate after creating them. Eventually, you should be able to resolve the error and ensure your mt-link subdomain functions correctly:

![](https://lh7-us.googleusercontent.com/kaTRz3r3l4-FFzX_zpIhf9yvjVj-MOqH07yoV8XBu7mlBE9nCq4QakXB0QUwG-hMf7aY4_K-KDkDkxZ0tXNPkd5mXXIW83SoTGk70m5fmgVzzx6mo32J4CGPPivzxMtFPv1rVpDTKM5e_KeDwePcqHY)

### How to fix the "From: Header does not match the sender's domain" error? <a href="#how-to-fix-the-from-header-does-not-match-the-senders-domain-error-zcfkh" id="how-to-fix-the-from-header-does-not-match-the-senders-domain-error-zcfkh"></a>

To send email with Mailtrap you `From:` should match your domain. In example, your verified domain in Mailtrap is acme.com, so your `From:` could be {anything}@acme.com. If you send from your subdomain, you From: domain should match your subdomain.

Laravel

First, check if your domain has been added to your account. If not, please add and verify the domain.

Next, check if your _`mail message`_ has a `From:` header and that the `From:` header also contains an address on your domain.

Most likely, the `MAIL_FROM_NAME` is the only variable used for the `envelope from` address, and it's not the same as the header. Please make sure it’s the same as the header.
