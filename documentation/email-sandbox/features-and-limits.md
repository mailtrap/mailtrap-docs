# Features and limits

**All Mailtrap features and possible limits explained in this article.**

* [Total test emails per month](https://help.mailtrap.io/article/44-features-and-limits#Total-test-emails-per-month-QrVnc)
* [Rate limits per 10 sec](https://help.mailtrap.io/article/44-features-and-limits#Rate-limits-per-10-sec-EfCLs)
* [Sandboxes](https://help.mailtrap.io/article/44-features-and-limits#Sandboxes-jiHIm)
* [Projects](https://help.mailtrap.io/article/44-features-and-limits#Projects-Z1y30)
* [Team members](https://help.mailtrap.io/article/44-features-and-limits#Team-members-NgCZY)
* [Maximum emails per sandbox](https://help.mailtrap.io/article/44-features-and-limits#Max-emails-per-sandbox-5lhZT)
* [Sandbox API](https://help.mailtrap.io/article/44-features-and-limits#Sandbox-API-bMknH)
* [Email address per sandbox](https://help.mailtrap.io/article/44-features-and-limits#Email-address-per-sandbox-YIPMO)
* [Email size, MB](https://help.mailtrap.io/article/44-features-and-limits#Email-size-MB-0EN6r)
* [Total forwarded emails per month](https://help.mailtrap.io/article/44-features-and-limits#Total-forwarded-emails-per-month-unNco)

#### **Total test emails per month** <a href="#total-test-emails-per-month-qrvnc" id="total-test-emails-per-month-qrvnc"></a>

The maximum number of emails you can test with Sandbox per month, depends on your [billing plan](https://mailtrap.io/pricing/?tab=email-sandbox).

#### **Rate limits per 10 sec** <a href="#rate-limits-per-10-sec-efcls" id="rate-limits-per-10-sec-efcls"></a>

The number of emails you can send to each of your Sandboxes every 10 seconds. The exact number depends on your billing plan.

Once the rate limit per 10 seconds is reached, the messages are not getting sent and are rejected with the error  "550 5.7.0 Requested action not taken: too many emails per second".

#### **Sandboxes** <a href="#sandboxes-jihim" id="sandboxes-jihim"></a>

Sandboxes are separate folders where your test messages from different environments (Dev, QA, staging) are captured. Every Sandbox is created inside a Project - a folder which can be shared with other users, according to the Team Members options (available in the Team plan and more advanced billing plans)

#### **Projects** <a href="#projects-z1y30" id="projects-z1y30"></a>

The groups that help you arrange your Sandboxes and distinguish different tasks you are working on simultaneously. You can share your projects with other team members (available in the Team and more advanced billing plans).

#### **Team members** <a href="#team-members-ngczy" id="team-members-ngczy"></a>

Mailtrap users who you can interact with by inviting them to your account and sharing projects or the billing section. This feature is available from the Basic Testing plan and more advanced billing plans. [Click here](https://help.mailtrap.io/article/65-user-management) to learn more about the User Management feature.

#### **Max emails per sandbox** <a href="#max-emails-per-sandbox-5lhzt" id="max-emails-per-sandbox-5lhzt"></a>

The total number of emails you can store in each of your sandboxes at once. The exact number depends on your billing plan.When the limit is reached, Mailtrap uses the FIFO model for automatic sandbox cleanup (oldest messages first).

#### **Sandbox API** <a href="#sandbox-api-bmknh" id="sandbox-api-bmknh"></a>

Sandbox API allows developers to run integration or load tests, as well as receive messages or email lists via API . To learn how to use the Email Sandbox API, refer to the [Email Sandbox API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-sandbox-api).

#### **Email address per sandbox** <a href="#email-address-per-sandbox-yipmo" id="email-address-per-sandbox-yipmo"></a>

The dedicated email address for each of your Sandboxes that you can use to send messages from other email accounts or right from your application during the testing process. It is available in the Basic Testing plan and more advanced billing plans.

#### **Email size, MB** <a href="#email-size-mb-0en6r" id="email-size-mb-0en6r"></a>

The maximum allowed size of each email message, including attachments, in megabytes, is between 5MB and 25MB, depending on your plan.

#### **Total forwarded emails per month** <a href="#total-forwarded-emails-per-month-unnco" id="total-forwarded-emails-per-month-unnco"></a>

The maximum number of emails you can forward from your account to real inboxes for testing and preview purposes. The maximum number of forwarding rules is 300. Email forwarding is available in the Basic Testing plan and more advanced billing plans.
