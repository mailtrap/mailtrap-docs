---
description: >-
  Manage Mailtrap suppression lists. View, add, remove, or import suppressed
  emails from hard bounces, unsubscribes, and spam complaints via CSV or
  manually.
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

# Suppressions list

When hard bounce, unsubscribe, and spam complaints events occur, Mailtrap adds the email address to a suppression list. The suppression list contains all the addresses you cannot send emails to.

You’ll find all the addresses on suppression lists in the **Suppressions** menu to the left.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6639f90f1bee2d183948cae6/file-GgoQp5felm.png" alt="" width="563"></div>

The menu contains the data for all your domains. If an email address was suppressed for more than one domain, it appears multiple times on the list.

You can export the whole Suppressions list.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/b5sLWLtrMsOZ_b0_s8CH5e5M2LU2cjo4je9yiQuxB3mJHfbjh9R65FEhsr-vkNhSbGY_J6_mycBiRTUdYLv_pFVs8TwgvjSLHnEF3iLNppyikLdk6ewaNGxoPNAWhrvP9FOtQ8AZnv3CbS3tOUdcai0" alt="" width="563"></div>

#### How to remove an email from a suppression list?

If you believe an email landed on a suppression list by accident, you can remove it by clicking the **Reactivate** button to the right.

<div align="left" data-with-frame="true"><img src="https://lh6.googleusercontent.com/QptnHTV8qqEVEb8to38Pi1OWh52Zdbd-1hvmmMljJznaWyz_o2Y0f6uD8ERFT24QlzDI5n7hrazKMFTVaRFt7YdvYj7p9cIL-3PeIr0j2SfRAiqa3x2f4SCckjOryxY3Q3rwGYTm" alt="" width="563"></div>

However, we advise you not to misuse the feature.

If someone decided to report your message as spam or leave your email list, you really don’t want to be emailing them again (unless they explicitly told you they had done it by mistake). Any further attempts will probably result in the same outcome, immediately hurting your email deliverability.

### Suppression list filters

You can filter the suppression list for:

* Specific email address
* Sending domain
* Type of suppression
* Reason for suppression

<div align="left" data-with-frame="true"><img src="https://lh5.googleusercontent.com/QhjY1RIG4ESh_xcMczrEbBxsdwCvmS4xnJuFoI4mTmnN1eK5gCSoeNv6jtPCOLJ9aS8L49_NQeFJtb__R2VpPBE_X5zCqi99OQm2tAD0NjX1r6ZLBFJFnVhA1OYtDL6Pmiueq2-7" alt="" height="129" width="624"></div>

### How to add recipients to the suppression list

Mailtrap allows you to add recipients manually or upload CSV.

#### Manual method

Select Insert manually. Then, under Add to stream, choose Bulk, Transactional, or Any. Under Add to domain, choose all or one of your domains.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6687d43add0f8c60bb3fdf99/file-xxPxhrcnCd.png" alt="" width="375"></div>

After you select the domain and stream, type or copy-paste the email addresses you want to suppress into the designated box. Then, click the Add To Suppressions button to complete the action.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6687d80ee1989867dcefed22/file-h4O05MuJXB.png" alt="" width="375"></div>

You can add only one email address per line and up to 1000 emails per selected domain.

Note that there’s also the **Add New/Import** button at the top right of the screen in the Suppressions main dashboard. It allows you to access the Add recipients to suppression list menu quickly.

<div align="left" data-with-frame="true"><img src="https://lh4.googleusercontent.com/9WqZGQbgOyzz6-bBUvMwLTM_77jF-CiTwb0z3oDH2wnS8RC0wyhOsNk7XTxjqmpVnKCRg5NkUAN5ADwK5kE41S5j8xftdw12FsCaPx1SMPTQuO_sUneRVIjwubiOFtflN1Yk7uER" alt="" height="92" width="624"></div>

#### Upload CSV

Before you upload CSV to Mailtrap, you first need to export the document from your current sending provider. See how to do it with SendGrid, Postmark, and Mailgun.

**Exporting Suppressions**

**Sendgrid**

Navigate to Suppression Management - this is where you’ll find the list of all your Unsubscribe Groups. You’ll see the default groups and the ones you created.

To export the CSV file, you’ll need to click the Settings button (the gear icon) next to each group, then choose **Export**.

**Mailgun**

Mailgun keeps three suppression lists (complaints, bounces, and unsubscribes) for each of your sending domains. There’s no global, account-level suppression list, so you’d need to export separate lists for each domain you transfer to Mailtrap.

To get the list in CSV format, make sure you choose the correct domain and use the Mailgun dashboard to export the lists.

**Postmark**

There’s an Export button in the Postmark dashboard. This allows you to export up to 500 records in a JSON file. For more records, you’d need to use Postmark’s Messages API.

Many online services offer services for converting JSON to CSV. [Postmark’s help page](https://postmarkapp.com/support/article/881-can-i-export-a-list-of-all-bounces) provides more information.

**Importing to Mailtrap**

Select **Upload CSV** and then choose the stream and the domain.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6687da1ee1989867dcefed23/file-a3NJbH4tcH.png" alt="" width="375"></div>

Click **Browse file** to select the CSV file from your computer or drag and drop it into the **Select file** box.

To complete the action, click **Add To Suppressions** and you’re done. If you wish, you can also download our CSV template by clicking on the corresponding option.
