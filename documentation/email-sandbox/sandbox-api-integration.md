# Sandbox API integration

**In this article:**

* [How the API works](https://help.mailtrap.io/article/24-mailtrap-testing-api#how-API-works)
* [What you can do with the API](https://help.mailtrap.io/article/24-mailtrap-testing-api#What-you-can-do-with-the-Sandbox-API-LoE94)
* [How to get started](https://help.mailtrap.io/article/24-mailtrap-testing-api#start-API)

### **How the API works** <a href="#how-api-works" id="how-api-works"></a>

The testing API uses REST protocol and can return calls as JSON objects. And it's compatible with the majority of programming languages.&#x20;

Mailtrap supports the following HTTPs requests:

* &#x20;**POST** to create a resource
* &#x20;**PATCH**  to update a resource
* &#x20;**GET** to get a resource or list of resources
* &#x20;**DELETE** to delete a resource

#### What you can do with the Sandbox API <a href="#what-you-can-do-with-the-sandbox-api-loe94" id="what-you-can-do-with-the-sandbox-api-loe94"></a>

Via the API, you can run the following commands:&#x20;

* **Sandbox**: create a new sandbox, reset the sandbox credentials and its email address; receive messages, clean one or all messages in the sandbox, mark all messages as read; manage users.
* **Project**: Create a new project, update, and delete it; manage its users.&#x20;
* **Email forwarding**: manage forwarding messages to real email addresses (available starting from the Individual plan).&#x20;
* **Email content**: inspect the email body by getting raw HTML (you can also download it), text, and detailed info about the HTML part, including a list of possible errors; receive message attachments.
* **Bcc and message headers**: receive message headers (Bcc is also included in this section, notwithstanding that it is not a regular message header). Bcc is available starting from the Team plan.&#x20;
* **Deliverability**: get a SPAM report and domain blacklisting details.

This way, you can test and verify the following scenarios:&#x20;

* Email sending script works.
* Email recipients are correct + Bcc testing (on the advanced plans).
* HTML template doesn’t cause errors.
* Mail merge/dynamic content is replaced properly.
* Appropriate files are attached.
* Important links, such as reset password and account confirmation, work.
* Your message doesn’t trigger a spam filter and your domain is not blacklisted, etc.

### How to get started with Sandbox API <a href="#start-api" id="start-api"></a>

First, you need to get a token. You can find it under Settings, API Tokens.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6401d7f0188a9d242a7d6593/file-YC3nwspl1B.png)\
To learn more about managing your tokens, please [check this guide](https://help.mailtrap.io/article/103-api-tokens). Then, there are a couple ways to send authenticated HTTP requests:

* Send a HTTP header  `Api-Token: {api_token}` , where `{api_token}`  is your API token
* Send a HTTP header `Authorization: Bearer #{token}` , where `{api_token}`   is your API token (more info: Token Access Authentication)

Go to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api), check samples, and experiment in the console.
