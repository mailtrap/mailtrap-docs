---
icon: exclamation
---

# Sandbox - FAQs

### [General questions](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#General-questions-J1uAK)

* [How to integrate Email Sandbox with my application?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#How-do-I-integrate-Mailtrap-Email-Testing-with-my-application-9z6Qo)
* [Do you need to view Sandbox emails only through its interface?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#Do-you-need-to-view-Sandbox-emails-only-through-its-interface-kxQt2)
* [How does Email Sandbox render emails?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#How-does-Email-Sandbox-render-emails-mQHuK)
* [Can Email Sandbox show what emails look like in various email clients?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#Can-Mailtrap-Email-Testing-show-what-emails-look-like-in-various-email-pRnot)
* [What does Sandbox do with the \<style> tag?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#What-does-Mailtrap-Email-Testing-do-with-style-tag-FLZEA)
* [What does Sandbox do with the \<script> tag?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#What-does-Mailtrap-Email-Testing-do-with-script-tag-UApXU)
* [Can I use Email Sandbox as a /dev/null SMTP server?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#Can-I-use-Mailtrap-Email-Testing-as-a-devnull-SMTP-server-Gja63)
* [What is the email size limit for Sandbox?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#What-is-the-email-size-limit-for-Mailtrap-Email-Testing-ZHBEJ)
* [What is the Testing rate limit for the sandbox?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#What-is-the-Testing-rate-limit-for-the-sandbox-it79F)
* [What is the monthly messages limit for Email Sandbox?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#What-is-the-monthly-messages-limit-for-Email-Testing-n0RAZ)
* [How much does Email Sandbox cost?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#Should-I-pay-to-use-Mailtrap-Email-Testing-lnhxO)

### [I have a technical problem](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#I-have-a-technical-problem-LOxwR)

* [My sandboxes disappeared](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#My-inboxes-disappeared-5Hn2c)
* [I have a problem integrating Sandbox with my app, what should I do?](https://help.mailtrap.io/article/115-mailtrap-testing-faqs#I-have-a-problem-integrating-Mailtrap-Email-Testing-with-my-app-what--M7lyL)

### General questions <a href="#general-questions-j1uak" id="general-questions-j1uak"></a>

#### How do I integrate Email Sandbox with my application? <a href="#how-do-i-integrate-mailtrap-email-testing-with-my-application-9z6qo" id="how-do-i-integrate-mailtrap-email-testing-with-my-application-9z6qo"></a>

The integration is very simple and takes just a couple of minutes:

1. [Sign up](https://mailtrap.io/register/signup/) by creating a free account.
2. Go to My sandbox in the [My Sandboxes](https://mailtrap.io/inboxes/) project.
3. Copy a code sample for your framework from the Integrations section or copy credentials provided in the SMTP Settings section.&#x20;
4. Embed them into your app code in development, QA, or staging environment.

Alternatively, you can send messages from your email client or another application to your Mailtrap sandbox using its email address. You will find it in the Email Address tab in your sandbox. It works the same as any other email address - just don't forget to enable it by clicking the **Enable** icon in the three-dots menu.

#### Do you need to view Sandbox emails only through its interface? <a href="#do-you-need-to-view-sandbox-emails-only-through-its-interface-kxqt2" id="do-you-need-to-view-sandbox-emails-only-through-its-interface-kxqt2"></a>

You should not necessarily stick to Mailtrap web interface. Instead, you can forward every single email to your or a teammate's mailbox.

You can even enable automatic forwarding, and Mailtrap will act as a proxy between your application and your email client. In this case, you can be sure you won't miss important messages from the QA environment, such as exception notifications.

Read the [Email Forwarding](https://mailtrap.helpscoutdocs.com/article/17-email-forwarding) article for more details.&#x20;

#### How does Email Sandbox render emails? <a href="#how-does-email-sandbox-render-emails-mqhuk" id="how-does-email-sandbox-render-emails-mqhuk"></a>

Sandbox renders emails in the same way browsers do, which means no additional stylesheet or CSS presets are applied by default.

#### Can Email Sandbox show what emails look like in various email clients? <a href="#can-mailtrap-email-testing-show-what-emails-look-like-in-various-email-prnot" id="can-mailtrap-email-testing-show-what-emails-look-like-in-various-email-prnot"></a>

Mailtrap is compatible with web email clients.

Mailtrap does not show exactly how an email will look like in any email client. It renders HTML as-is, without external CSS styles.

Also, Mailtrap provides HTML checks and demonstrates potential errors that different email clients may experience when rendering an HTML email. But note that you can get a preview of test emails for different devices - mobile, tablet, desktop.&#x20;

You can also [forward emails](https://mailtrap.helpscoutdocs.com/article/17-email-forwarding) to Outlook, Thunderbird, etc., and use these desktop clients to view them.

#### What does Sandbox do with the \<style> tag? <a href="#what-does-mailtrap-email-testing-do-with-style-tag-flzea" id="what-does-mailtrap-email-testing-do-with-style-tag-flzea"></a>

Sandbox doesn't rip the style tag out of the email templates.

#### What does Sandbox do with the \<script> tag? <a href="#what-does-mailtrap-email-testing-do-with-script-tag-uapxu" id="what-does-mailtrap-email-testing-do-with-script-tag-uapxu"></a>

For enhanced security, Sandbox removes all \<script> tags from HTML.

#### Can I use Email Sandbox as a /dev/null SMTP server? <a href="#can-i-use-mailtrap-email-testing-as-a-devnull-smtp-server-gja63" id="can-i-use-mailtrap-email-testing-as-a-devnull-smtp-server-gja63"></a>

The main goal of Sandbox is to help you test emails, and /dev/null is not part of it.

Should you need /dev/null SMTP server, please use the following built-in Python SMTP server:

```
$ python -m smtpd -nc DebuggingServer localhost:2525 > /dev/null. 
```

_Learn how exactly Sandbox can help you streamline email testing processes from our_ [_case study with The Software House_](https://mailtrap.io/blog/tsh-mailtrap-casestudy/)_._

#### What is the email size limit for Sandbox? <a href="#what-is-the-email-size-limit-for-mailtrap-email-testing-zhbej" id="what-is-the-email-size-limit-for-mailtrap-email-testing-zhbej"></a>

The maximum size of an email including attachments for Sandbox ranges from 5 MB to 25 MB. It depends on your [subscription plan](https://mailtrap.io/pricing/). If your message exceeds this limit, you will get the following error: '552 5.3.4 Error: message too big'.

#### What is the Testing rate limit for the sandbox? <a href="#what-is-the-testing-rate-limit-for-the-sandbox-it79f" id="what-is-the-testing-rate-limit-for-the-sandbox-it79f"></a>

It's the number of emails you can send to each of your sandboxes every 10 seconds. The rate limit depends on the subscription plan. For more details, check out the [Pricing page](https://mailtrap.io/pricing/).

#### What is the monthly messages limit for Email Sandbox? <a href="#what-is-the-monthly-messages-limit-for-email-testing-n0raz" id="what-is-the-monthly-messages-limit-for-email-testing-n0raz"></a>

It's the maximum number of emails you can test and get in all your sandboxes per month. The total emails per month limit depends on the subscription plan. For more details, check the [Pricing page](https://mailtrap.io/pricing/).

If you reach your monthly limit, you'll receive the SMTP protocol error: "535 5.7.0 Monthly messages limit reached". We also send out notifications for having used 80%, 90%, and 100% of the monthly limit.

To continue testing when you're over the limit, please upgrade your subscription plan. Alternatively, you can wait until the next billing period starts, when the limit is reset.

#### How much does Email Sandbox cost? <a href="#should-i-pay-to-use-mailtrap-email-testing-lnhxo" id="should-i-pay-to-use-mailtrap-email-testing-lnhxo"></a>

Email Sandbox provides a free subscription plan for new users who want to evaluate it.

For larger teams, we offer sets of features within several paid subscription plans, starting from $17/month.

To choose one that best fits your needs, check our pricing plans at [here](https://mailtrap.io/pricing/?tab=sandbox).

### I have a technical problem <a href="#i-have-a-technical-problem-loxwr" id="i-have-a-technical-problem-loxwr"></a>

Visit [the troubleshooting section](https://help.mailtrap.io/article/59-troubleshooting) for the answers to the most common problems or [contact our support](mailto:support@mailtrap.io).&#x20;

#### My sandboxes disappeared <a href="#my-sandboxes-disappeared-5hn2c" id="my-sandboxes-disappeared-5hn2c"></a>

Sandboxes that are shared with you are moved to the top right menu. Switch to the shared account by clicking on its name.

#### I have a problem integrating Sandbox with my app, what should I do? <a href="#i-have-a-problem-integrating-mailtrap-email-testing-with-my-app-what-m7lyl" id="i-have-a-problem-integrating-mailtrap-email-testing-with-my-app-what-m7lyl"></a>

Please send us an email at [support@mailtrap.io](mailto:support@mailtrap.io) describing the issue; we'll try to help you ASAP.
