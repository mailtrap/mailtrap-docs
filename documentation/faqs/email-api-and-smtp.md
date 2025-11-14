---
icon: exclamation
---

# Email API and SMTP

### [General questions](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#general)

* [What is Mailtrap?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#What-is-Mailtrap-0K-n3)
* [How do I integrate Mailtrap with my application?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#How-do-I-integrate-Mailtrap-Email-Sending-with-my-application-CyPE3)
* [Can I send emails without my domain?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Can-I-send-emails-without-my-domain-c_JW4)
* [Can I send emails on behalf of other domains?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Can-I-send-emails-on-behalf-of-other-domains-QCliI)
* [Should I use my domain name with www. ?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Should-I-use-my-domain-name-with-www-zqJjn)
* [Can I receive emails with Mailtrap?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Can-I-receive-emails-with-Mailtrap-XErzc)
* [When I add a domain to Mailtrap Sending, does that include subdomains?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#When-I-add-a-domain-to-Mailtrap-Sending-does-that-include-subdomains--T0DdZ)
* [How Mailtrap billing works?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#How-does-Mailtrap-count-emails-RLi6K)
* [What is the email size limit?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#What-is-the-email-size-limit-for-Mailtrap-Email-Sending-P2Z2u)
* [What is the monthly message limit?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#What-is-the-monthly-messages-limit-for-Email-Sending-2XT51)
* [Is it possible to export Email logs?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Is-it-possible-to-export-Email-logs-x_PpT)
* [Does Mailtrap comply with the GDPR?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Does-Mailtrap-comply-with-GDPR-g1HXA)
* [Do you have a bug bounty program?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Do-you-have-a-bug-bounty-program-Tfa4N)
* [Can I send emails to end-users with Mailtrap?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Can-I-send-emails-to-end-users-with-Mailtrap-rmZ1N)
* [Can I force an encrypted connection?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Can-I-force-an-encrypted-connection--SnB2)
* [I would like to whitelist live.smtp.mailtrap.io on my firewall. What is Mailtrap's IP range?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#I-would-like-to-whitelist-livesmtpmailtrapio-on-my-firewall-What-i-SdmWo)

### [I have a technical problem](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#troubleshoot)

* [I have a problem integrating Mailtrap with my app; what should I do?](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#I-have-a-problem-integrating-Mailtrap-Email-Sending-with-my-app-what--W-sgZ)
* [I'm getting an "Unauthorised" error (401 code)](https://help.mailtrap.io/article/40-mailtrap-sending-faqs#Im-getting-an-Unauthorised-error-401-code-kGUC3)

### General questions <a href="#general" id="general"></a>

#### What is Mailtrap? <a href="#what-is-mailtrap-0k-n3" id="what-is-mailtrap-0k-n3"></a>

Mailtrap is an email delivery service to send transactional and promo emails. Popular among developer and product teams for it's Email API and SMTP solutions.

#### How do I integrate Mailtrap Email Sending with my application? <a href="#how-do-i-integrate-mailtrap-email-sending-with-my-application-cype3" id="how-do-i-integrate-mailtrap-email-sending-with-my-application-cype3"></a>

1. [Sign up](https://mailtrap.io/register/signup/) by creating a free account.
2. Go to Email Sending and select [Sending Domains](https://mailtrap.io/sending/domains).
3. After you've added and verified all the DNS records, wait for the Compliance Check to be completed.&#x20;
4. Proceed to integrate Mailtrap with your application via SMTP or API.

If you have any questions, contact us at [support@mailtrap.io](mailto:support@mailtrap.io).

#### Can I send emails without my domain? <a href="#can-i-send-emails-without-my-domain-c_jw4" id="can-i-send-emails-without-my-domain-c_jw4"></a>

No, you can't.

To send emails, Mailtrap requires you to add a sending domain, authenticated and verified using the DNS records Mailtrap provides.

#### Can I send emails on behalf of other domains? <a href="#can-i-send-emails-on-behalf-of-other-domains-qclii" id="can-i-send-emails-on-behalf-of-other-domains-qclii"></a>

No, you can’t.

If you verified mydomain.com, you can send emails only on behalf of your domain.

#### Should I use my domain name with www. ? <a href="#should-i-use-my-domain-name-with-www-zqjjn" id="should-i-use-my-domain-name-with-www-zqjjn"></a>

No, you should use your domain without it.

Please check our [Knowledge Base article](https://help.mailtrap.io/article/69-sending-domain-setup) on setting up a domain.

#### Can I receive emails with Mailtrap? <a href="#can-i-receive-emails-with-mailtrap-xerzc" id="can-i-receive-emails-with-mailtrap-xerzc"></a>

Right now, Mailtrap doesn't provide MX records to catch inbound emails, so they'll bounce.

Another option is to use a real email address in the "reply-to" field if a recipient replies to your email.

#### When I add a domain to Mailtrap, does that include subdomains? <a href="#when-i-add-a-domain-to-mailtrap-sending-does-that-include-subdomains-t0ddz" id="when-i-add-a-domain-to-mailtrap-sending-does-that-include-subdomains-t0ddz"></a>

No, you need to add and verify each subdomain/domain separately.

#### How Mailtrap billing works? <a href="#how-does-mailtrap-count-emails-rli6k" id="how-does-mailtrap-count-emails-rli6k"></a>

We bill each email. For example, if an email has 3 recipients - we bill 3 of them. If it has + 3 in CC, we bill 6 together. The same goes for recipients in BCC.&#x20;

#### What is the email size limit? <a href="#what-is-the-email-size-limit-for-mailtrap-email-sending-p2z2u" id="what-is-the-email-size-limit-for-mailtrap-email-sending-p2z2u"></a>

The maximum size of an email with attachments for Mailtrap is 10 MB. Upon request, we can extend the limit in some cases to 30 MB

#### What is the monthly message limit for email sending? <a href="#what-is-the-monthly-messages-limit-for-email-sending-2xt51" id="what-is-the-monthly-messages-limit-for-email-sending-2xt51"></a>

It's the maximum number of emails you can send with Mailtrap per month. The total number of emails per month depends on the subscription plan. For more details, check the [Pricing page](https://mailtrap.io/pricing/?tab=api).

If you reach your monthly limit, you'll receive the SMTP protocol error: "535 5.7.0 Monthly messages limit reached". We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue sending when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

#### Is it possible to export Email logs? <a href="#is-it-possible-to-export-email-logs-x_ppt" id="is-it-possible-to-export-email-logs-x_ppt"></a>

Right now, it’s not possible, but there's a workaround.

You can set up [Webhooks](https://help.mailtrap.io/article/102-webhooks) to automatically collect logs. And you can use a tool like Zapier, for example, to create a spreadsheet from your webhooks.

#### Does Mailtrap comply with the GDPR? <a href="#does-mailtrap-comply-with-gdpr-g1hxa" id="does-mailtrap-comply-with-gdpr-g1hxa"></a>

The General Data Protection Regulation (GDPR) came into effect on May 25, 2018. We have implemented appropriate technical and security processes to ensure Mailtrap's full compliance with this regulation. For more details, refer to our [Privacy Policy](https://mailtrap.io/privacy/), [Navigational Information](https://mailtrap.io/navigational-info/), and [Data Protection Agreement](https://mailtrap.io/dpa/).

#### Do you have a bug bounty program? <a href="#do-you-have-a-bug-bounty-program-tfa4n" id="do-you-have-a-bug-bounty-program-tfa4n"></a>

We do not. In case you have found a vulnerability on our website that you are eager to report to us, you are welcome to do so at support@mailtrap.io. All issue reporters will be mentioned on our [changelog page](https://mailtrap.io/changelog/).

#### How much does Mailtrap cost?

Mailtrap plans starts from 15$ for 10,000 emails/month. We offer plans for business from $85/month for 100,000 emails, and, for enterprises, there are plans from $750/month for 1,500,000 emails.&#x20;

To choose one that best fits your needs, check out our [pricing plans](https://mailtrap.io/pricing/?tab=api).

#### Can I send emails to end-users with Mailtrap? <a href="#can-i-send-emails-to-end-users-with-mailtrap-rmz1n" id="can-i-send-emails-to-end-users-with-mailtrap-rmz1n"></a>

Yes, you can. Mailtrap is an email delivery service to send transactional and promo emails. Popular among developer and product teams for it's Email API and SMTP solutions.

#### Can I force an encrypted connection? <a href="#can-i-force-an-encrypted-connection-snb2" id="can-i-force-an-encrypted-connection-snb2"></a>

Yes, you can enforce encrypted connections. Mailtrap SMTP server uses STARTTLS, which works for all SMTP ports. We support only TLS connections because of the POODLE vulnerability (SSLv2 and SSLv3 are disabled).

#### I would like to whitelist live.smtp.mailtrap.io on my firewall. What is Mailtrap's IP range? <a href="#i-would-like-to-whitelist-livesmtpmailtrapio-on-my-firewall-what-i-sdmwo" id="i-would-like-to-whitelist-livesmtpmailtrapio-on-my-firewall-what-i-sdmwo"></a>

We use AWS with auto-balancing, so our IP ranges are the following: [https://ip-ranges.amazonaws.com/ip-ranges.json](https://ip-ranges.amazonaws.com/ip-ranges.json)

### I have a technical problem <a href="#troubleshoot" id="troubleshoot"></a>

Visit [the troubleshooting section](https://help.mailtrap.io/article/59-troubleshooting) for the answers to the most common problems, or [contact our support](mailto:support@mailtrap.io).&#x20;

#### I have a problem integrating Mailtrap Email Sending with my app; what should I do? <a href="#i-have-a-problem-integrating-mailtrap-email-sending-with-my-app-what-w-sgz" id="i-have-a-problem-integrating-mailtrap-email-sending-with-my-app-what-w-sgz"></a>

Please email us at [support@mailtrap.io](mailto:support@mailtrap.io) describing the issue; we'll try to help you ASAP.

#### I'm getting an "Unauthorised" error (401 code) <a href="#im-getting-an-unauthorised-error-401-code-kguc3" id="im-getting-an-unauthorised-error-401-code-kguc3"></a>

There are several reasons why you might be getting the "Unauthorised" error. Here's what to check:

* Make sure you're sending from the domain that you've set up and verified. Using any other domain will result in the given error.
* If you've configured a custom token for your domain - [make sure it has proper permissions](https://mailtrap.io/api-tokens) to send emails.
* Make sure you're using the correct SMTP/API credentials provided in the Integration tab of your domain.

<figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a24162d39e504a2aed1cbd/file-0a2G0GSPDs.png" alt=""><figcaption><p>Transactional stream SMTP credentials</p></figcaption></figure>

<figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a241a26eb51e63b8f9dc96/file-CGe0ccmAlM.png" alt=""><figcaption><p>Bulk stream SMTP credentials</p></figcaption></figure>

*   Use the cURL code example to see if you can replicate the error. Here's the path to the exemplary code:

    Sending Domains > Integration > Integrate (under Transactional or Bulk Stream) > Code Samples > cURL.

<figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a242458919a15d1b1d1f84/file-loZgd6vu5c.png" alt=""><figcaption><p>Transactional stream cURL</p></figcaption></figure>

<figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66a2427848915f570c6a8845/file-YvlB4mk58M.png" alt=""><figcaption><p>Bulk stream cURL</p></figcaption></figure>
