# Sandbox Glossary

**Sandbox API** - Compatible with most programming languages, uses the REST protocol, and returns calls in JSON format. Here's the [link](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) to the API documentation. With API, you can take actions related to an sandbox, a project, email forwarding, email content, message headers, and more. 

**CORS Domains** - CORS is Cross-Origin Resource Sharing. It’s a mechanism that allows restricted resources to be requested from another domain outside the domain from which the first resource was served. You can specify a list of domains that will have access to API.  

**Sandbox** - A virtual sandbox with its own credentials to organize your emails. Typically, users have sandboxes for different environments, i.e. staging, development, and testing.

**POP3** - Stands for Post Office Protocol 3. It’s among the most widely used protocols for receiving various emails.

**Project** - Sandboxes can be grouped into different projects to separate testing environments, companies, and projects you work on. Note that the number of projects is limited based on your plan.

**STARTTLS** - It’s an email protocol command that relays security information between an email server and an email client. The command shows an email client that Gmail, for example, wants to upgrade to a secure connection with TLS or SSL. STARTTLS is also commonly used with IMAP.

### Miscellaneous Terms

**Email Headers** - All the original values of the email headers displayed as a table.

**HTML Source** - The HTML source code of an email that you send.

**MTA** - Message (or Mail) Transfer Agent. It’s the software that relays emails between senders’ and recipients’ computers via SMTP. To find out more about MTA, check out our related [blog post](https://mailtrap.io/blog/mail-transfer-agent/).

**MTA Settings** - When setting up a sandbox, you get the SMTP settings to copy-paste into your MTA. That way, your MTA will use Mailtrap servers.

**RAW** - It’s your processed email consisting of a series of required and optional text headers followed by a message body. These details may be important for diagnosing email delivery issues.

**Text** - The plain text version of an email. If your email has only an HTML version, the Text tab won’t be available. This is true the other way around, too.
