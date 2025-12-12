---
description: >-
  Learn how to integrate Mailtrap with Java applications using SDK, SMTP, or
  RESTful API for email sending.
icon: java
---

# Java Integration

<a href="https://github.com/mailtrap/mailtrap-java" class="button primary">Mailtrap Java SDK on GitHub</a>

## Java Integration

### Overview

Mailtrap can be integrated with Java apps and projects for email sending with SDK, SMTP, and RESTful API.

### Email API/SMTP for Java

#### SDK integration

The [Mailtrap Java SDK](https://github.com/mailtrap/mailtrap-java) is a robust, enterprise-ready library for sending transactional and bulk emails from Java applications. The SDK supports:

* Transactional email sending
* Batch email sending
* Template management
* Contact management
* Sandbox testing
* Account management
* Thread-safe operations

### Installation

Add the SDK to your project using your preferred build tool:

{% tabs %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```xml
<dependency>
    <groupId>com.mailtrap</groupId>
    <artifactId>mailtrap-java</artifactId>
    <version>1.0.0</version>
</dependency>
```
{% endcode %}
{% endtab %}

{% tab title="Gradle (Groovy)" %}
{% code title="build.gradle" %}
```groovy
implementation 'com.mailtrap:mailtrap-java:1.0.0'
```
{% endcode %}
{% endtab %}

{% tab title="Gradle (Kotlin DSL)" %}
{% code title="build.gradle.kts" %}
```kotlin
implementation("com.mailtrap:mailtrap-java:1.0.0")
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Minimal Example

Here's a minimal example to send your first email:

{% code title="SendEmail.java" %}
```java
import com.mailtrap.MailtrapClient;
import com.mailtrap.model.Mail;
import com.mailtrap.model.Address;

public class SendEmail {
    public static void main(String[] args) {
        MailtrapClient client = new MailtrapClient("your-api-token");

        Mail mail = Mail.builder()
            .from(new Address("hello@example.com", "Mailtrap Test"))
            .to(new Address("recipient@example.com"))
            .subject("Hello from Mailtrap!")
            .text("Welcome to Mailtrap Email Sending!")
            .html("<p>Welcome to <strong>Mailtrap</strong> Email Sending!</p>")
            .build();

        try {
            var response = client.send(mail);
            System.out.println("Email sent successfully: " + response);
        } catch (Exception e) {
            System.err.println("Error sending email: " + e.getMessage());
        }
    }
}
```
{% endcode %}

{% hint style="info" %}
Get your API token from your Mailtrap account under **Settings → API Tokens**.
{% endhint %}

#### SMTP integration

To integrate SMTP with your Java app, navigate to the Integrations tab and copy-paste the credentials or ready-made code snippet into your configuration.

{% hint style="info" %}
SMTP integration is compatible with any Java framework or library that sends emails via SMTP.
{% endhint %}

<div data-with-frame="true"><img src="../.gitbook/assets/mailtrap-java-smtp-integration.png" alt=""></div>

For more information, read the [SMTP Integration article](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/smtp-integration).

#### RESTful API integration

To integrate Mailtrap using RESTful API, use the configuration available among Code samples under the API section.

API integration can be used with any Java framework or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

<div data-with-frame="true"><img src="../.gitbook/assets/mailtrap-java-api-integration.png" alt=""></div>

Read more about API integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration).
