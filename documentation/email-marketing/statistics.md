# Statistics

**In this article:**

* [Navigating around the statistics dashboard ](https://help.mailtrap.io/article/88-statistics#navigating)
* [Thresholds](https://help.mailtrap.io/article/88-statistics#thresholds)
* [Terminology](https://help.mailtrap.io/article/88-statistics#Terminology-tkssh)
  * [Delivered](https://help.mailtrap.io/article/88-statistics#delivered)
  * [Unique open rate](https://help.mailtrap.io/article/88-statistics#unique%20open)
  * [Click rate](https://help.mailtrap.io/article/88-statistics#click%20rate)
  * [Bounce rate](https://help.mailtrap.io/article/88-statistics#bounce%20rate)
  * [Spam complaints](https://help.mailtrap.io/article/88-statistics#spam%20complaints)

Mailtrap provides analytics for all the emails you send.

![](<../../../.gitbook/assets/unknown (4).png>)

On the statistics dashboards, you can see the following metrics:

* Delivered emails
* Unique open rate
* Click rate
* Bounce rate
* Spam complaints

### Navigating around the statistics dashboards

In that **Stats** tab, you'll find a domain selector at the top of the page. Here, you can choose to show stats for a particular domain.

![](https://lh7-us.googleusercontent.com/tUFcCa-3_iKL57k4X9LqxJZngVtIrove4PaKxW9GASFnyrKbZr4Yre1bWUCmJuzPh0-LDDyElfO1rcDh7I6jgvXudSQ7K-TtcdFz018v48MHz4nOVe9XnD2VUqGsZOBEh0TGzDCa1NNcTSLfHF34I8I)

By default, the stats are shown for the last week + today.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6401ef95188a9d242a7d65a8/file-QGQA9mEWm0.png)

### Thresholds <a href="#thresholds-s8z17" id="thresholds-s8z17"></a>

The thresholds are based on our extensive cross-industry research and, at this point, can’t be edited. The current values are:

* For bounce rate:
  * 2-5% is a warning level (yellow)
  * \>5% is a critical level (red)
* For spam rate:
  * 0.08%-0.1% is a warning level (yellow)
  * \>0.1% is a critical level (red)

### Terminology <a href="#terminology-tkssh" id="terminology-tkssh"></a>

#### Delivered <a href="#delivered" id="delivered"></a>

Delivered refers to the percentage of emails that were accepted by the recipient’s mailbox providers compared to all emails sent. Email is counted as delivered when a Delivery event is recorded in its Event History in [Email Logs](https://help.mailtrap.io/article/71-email-logs).

**Note:** "**Delivered**" status doesn’t mean that a message went straight into the recipient’s Primary folder. It may have still gone into Promotions and Updates, or it might have been automatically put into a Spam folder.

Mailtrap will reject an email if a recipient is on a suppression list for a given domain. Read more about suppressions [here](https://help.mailtrap.io/article/95-suppressions-list).

On top of that, an email can be rejected on the recipient’s end for various reasons:

* A message is considered spam, phishing, or other foul play.
* A security policy on the recipient’s end dictates that a message should be declined.
* A server timeout occurs (in such case, Mailtrap will retry the delivery 10 times until it eventually gives up).
* Email authentications (SPF, DKIM, DMARC) fail.

#### Unique open rate <a href="#unique-open" id="unique-open"></a>

Unique open rate refers to the percentage of emails that were opened at least once compared to all emails sent.

Open tracking needs to be enabled for a domain in question in the Sending Domains tab. Only then will email opens be recorded.

![](https://lh7-us.googleusercontent.com/G4wfcj9NzqHOkJlA0KU9_3_VZVJWeFwOzedTikmrCC68pw54-8u9mZpaUmfflnzAQkmeRpDNEZwkmWjoG3gSwRl0npyX5vUBXHJ4pDB_2ZOs10kddFd1u216wPkvXWV4jqW2KiPaW2kQooceBKDPOck)

#### Click rate <a href="#click-rate" id="click-rate"></a>

Click rate refers to the percentage of emails that received at least one link click compared to all delivered emails.

When any of the links in an email are clicked, a **click** event is recorded. The same happens for any further clicks, even if a recipient keeps clicking on the same or different links.

You can see the details of each click (timestamp, Recipient's IP, URL) in the **Events History** in the **Email Logs**.

![](https://lh7-us.googleusercontent.com/iNboqLTvD7XwYaJevUwkpfh3zr68WfEFh7TbwyTuFJmxgoLLLvKyO2UafZ53fzdXOc0N1c11tFGDrif1y6_P7dHZ6QvMa1ej8bU2n05EOnO2ABppo7JbJidiYKyE-jD-NJ3E0IjBU2lU8EgnagI9mAM)

However, the metrics such as **clicked** and **click rate** used in the statistics are calculated differently.

**Clicked** metric indicates how many emails received at least one click on.

The **click rate** is basically clicked/delivered \* 100%.

#### Bounce rate <a href="#bounce-rate" id="bounce-rate"></a>

Bounce rate refers to the percentage of emails dispatched from Mailtrap that were rejected on the recipient’s end compared to all emails sent.

Emails may bounce for different reasons, most commonly:

* Invalid email address.
* Rejection by the recipient’s mailbox because email is deemed spam, phishing, etc.
* The security policy of a mailbox provider that rejects emails from all or some domains.
* Permanent connection issue.

The term bounce used in Mailtrap is also known as a hard bounce. This is different from a soft bounce - another event present in Mailtrap that refers to a temporary delivery problem.

If an email soft bounces, Mailtrap will try to deliver it 10 more times. If there’s no positive outcome, an email will (hard) bounce and get counted towards the bounce rate.

#### Spam complaints <a href="#spam-complaints" id="spam-complaints"></a>

Spam complaints refer to the percentage of emails that are reported as spam by recipients, as compared to all emails that were delivered.
