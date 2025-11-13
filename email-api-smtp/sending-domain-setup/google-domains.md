---
description: >-
  Verify your Mailtrap sending domain in Google Domains. Add DNS records for
  SPF/DKIM/DMARC verification, pass compliance, and start sending emails.
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

# Google Domains

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Google Domain.

{% hint style="info" %}
_Note: On September 7, 2023, Squarespace acquired all domain registrations and related customer accounts from Google Domains. This means that Google Domains is now in the process of migrating account and domain data to Squarespace. Until the migration is completed, you can still manage your domains in Google Domains. After the migration, you’ll need to manage your domain in Squarespace._&#x20;

_This guide assumes that your domain is either registered with Google Domains and uses its nameservers or isn’t registered with Google Domains but uses its nameservers._
{% endhint %}

1. Go to Google Domains and select the domain you’ve added to Mailtrap.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/wpUU0w4AuXiJMZuO8ogQfUNnTcspWigcvS-SAoFCdT_54QPTyoFlyRCIh70px8u_7W2zLQSid2z4FXtGJ2r05XtbY7iqqPgJccYp7H6tiUtJvml0zLazIrufrwEbE0FXOJMGEKaW0VUSlZkQ-Wc6_Sg" alt="" width="563"></div>

2. In the left navigation panel, click DNS.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/9tsVwKlxFMbAMKmJuOl1O2FeSqYc-wl_3dYu-9o_84RofWvLw222qI_v6RbG8F8O4hLghGdFYhLM3puJW4LcHot_s6Y4SWJ-Vc2VIvgxSjGS_-IP6B6e-KLHDo-M38DKpDmR7Hil-Yg3rIjjRgIx9Cc" alt="" width="188"></div>

3. Under Custom records in the Resource records section, choose Manage custom records. In case you don’t have any resource records, click Custom records directly.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/6mMISQpP5VxiTEL1j2pnsIZpecP6g4cQ4iqbI4IIK15Ubc-4CiwRKX9Kzj2zQqC-w-yLzIG0yWLi7dDyladDkw0O1jiHrczaubx-zGj8Dg1Og_fYe6DeiA5Qf9loJssL9sifakRDnXKOvV_h4LhFxiY" alt="" width="563"></div>

4. Scroll down at the bottom of the records and click Create new record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/iXT_RjAL8EWzmbJ3ARQuOHe5wrf027GgEAn3-R2xcXKvuySvzHq2-uB5E1nqJFJPhzDTN-l0Mxr7COP4Edgq8Lje2vAoWYVW599heBLXruNZAz0cC2e_3Kb-QrOWWbWXhhyYdTk52qmNI-J5oedrx2Q" alt="" width="563"></div>

5. Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to Google Domains. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value. &#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/GB27qZTh1LMpcKid1hCcSy35YgqzQXCerSGXQjpWeblFe7bJBuBps9jE_B3w6H7yUnuj_hzC-cQ72MdJRdlQewSiBGswLBvOz3m3iqwsCzEqgC07cI5I4e8dHRvFkLWFnDCqeD_pJtp49h_L7n2DnW4" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in Google Domains. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/vXe7Y_QVrg8N7vbJKAhbjE7we6mizYpMKchtSJ2phAlr-g_Xp7Z6FdBltNZpm-6kcJwaRuxswWeRivZZRv1K0J8bqIb2EPgHC-ZvYzmEiOV_plPYuAcO1zM3porAhZIdmgClKAlNGKPS7LLE8xf9N-0" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

{% hint style="info" %}
You should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records.
{% endhint %}

6. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/Tbvy0_47Z6A6duGquxhyy2v9UqKMugerXaelNaEhPeDehMshBzYxynRoK_ljgV2675GBjuLaYGD71DVDM05FrNzUV_5GvkGEA9ueCRxXWAV-W8AZW0_O8nSt99y_lb8XKxU96jG3TPVSm-Jeo6fKlDQ" alt="" width="563"></div>

7. And paste them into Google Domains. Remember that Google Domains refers to the Name field as the Host name and the Value field as either the Domain name (for CNAME-type records) or Text (for TXT-type records).&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/XRhRBvu1k5-NlStCKFZNyHjODBOK9Xwevg5LEmXvAgiACkSmaldI7qHaNy8bY86QwbzUopfEXrsmPcL4e0fQ2jkVesYZNOxqXxnlzrdfhf6b6hnuRlsXkVavAZhrpAMot3CzN9lP4rO1OY7J1Mnzq4I" alt="" width="563"></div>

8. Use the default value for TTL.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/pIUKsPsfXYGtXAwOBjlfDgpZ4dgtX3ixQfy-5AqMcsZaFbZ8XCeFtNKFFiTa-yJDJRPOhMJ6YRDznizYs1YUNqtSUGkw4z2pKK1eUUHUKpLcc-vYyFPXNlMwMd2fG18XHuVqfnTMxbFznEja2NGuT-M" alt="" width="563"></div>

9. Repeat the process of copying, pasting, and clicking Create new record for each record until you’ve added all the Mailtrap DNS records to Google Domains. Click Save.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/5HwIaXT1fnLBaqXROu8wgmJemj-BQNDel3FH5hoczQaoBfMPNF4fEt5m6r3aEpnxVRprbCI60qFD6uLy055js306IV-zgmz2xlwdL8gUX8R9e4z8Y70KvpsuoW8nhpX8eGT2I-mh26GopKs1o1hjldE" alt="" width="563"></div>

10. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/xisvSIu3HljviXIgxC_VO3eheofPJOiKdufeS5JT4aYke297VBj4JMsEWWSixgTF9khCEZOzCy3VQxGTLuNF2f6yi-r6SaIKs9NPfTztsBz8PaG6o5hboQ_9O7wB39LNyxEKsbhuny7Bth4INBq-beE" alt="" width="563"></div>

11. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/sxg0Aom8xVnSWeSXSX9NobXVPgp7SRy1pXqJej36Aap0J4wcun7G7DgX9VD16e-ztfc5kGFU_yGNCNlD9YDZE3wOUfrMriCwvECnuGPzWyjgt6yNvstKpa1rv2SjufsHWKCmJk5JixEBmI1-QW3ZQJg" alt="" width="563"></div>

{% hint style="info" %}
_If you have additional questions,_ [_consult Google Domains documentation_](https://support.google.com/domains/answer/3290350?hl=en) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._&#x20;
{% endhint %}
