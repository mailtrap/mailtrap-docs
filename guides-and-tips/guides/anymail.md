---
cover: ../.gitbook/assets/anymail-cover (1).png
coverY: 0
---

# Anymail

Integrate Mailtrap with Django apps using Anymail or SMTP to send and test emails.

<a href="https://github.com/anymail/django-anymail" class="button primary">Anymail on GitHub</a>

### Overview

Mailtrap can be integrated with Django apps for email sending and testing. You can connect it in two ways:

* **Anymail integration**: [Anymail](https://anymail.dev/en/stable/esps/mailtrap/) includes a Mailtrap email backend that sends through the Mailtrap Email API, so you keep sending with Django's `send_mail()` and `EmailMessage`.
* **SMTP integration**: Django's built-in SMTP backend with your Mailtrap SMTP credentials.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain)
* [Create and save an API token](https://docs.mailtrap.io/general/api-tokens)

### Email Live Sending for Django

#### Anymail integration

[Anymail](https://anymail.dev/en/stable/esps/mailtrap/) connects Django's email system to email service providers. Its Mailtrap backend plugs into Django's native mail functions and sends through the Mailtrap Email API. It supports:

* Transactional and bulk email sending
* Batch sending with per-recipient data
* Mailtrap email templates
* Categories and custom variables
* Email Sandbox
* Status tracking webhooks

{% hint style="info" %}
The Mailtrap backend is available in Anymail 14.0 and later. The current version, Anymail 15.2, requires Django 5.0 or later and Python 3.10 or later.
{% endhint %}

#### Installation

Install Anymail with the Mailtrap extra:

```bash
pip install "django-anymail[mailtrap]"
```

#### Configuration

Add `anymail` to `INSTALLED_APPS` and set the Mailtrap backend in `settings.py`. The sender addresses must use your verified sending domain:

```python
import os

INSTALLED_APPS = [
    # ...
    "anymail",
]

EMAIL_BACKEND = "anymail.backends.mailtrap.EmailBackend"

ANYMAIL = {
    "MAILTRAP_API_TOKEN": os.environ["MAILTRAP_API_TOKEN"],
}

DEFAULT_FROM_EMAIL = "hello@yourdomain.com"
SERVER_EMAIL = "server@yourdomain.com"
```

To send through the [Bulk Stream](https://docs.mailtrap.io/email-live-sending/setup/bulk-stream), add the Bulk Stream API URL:

```python
ANYMAIL = {
    "MAILTRAP_API_TOKEN": os.environ["MAILTRAP_API_TOKEN"],
    "MAILTRAP_API_URL": "https://bulk.api.mailtrap.io/api/",
}
```

{% hint style="info" %}
Django 6.1 deprecates `EMAIL_BACKEND` and the other `EMAIL_*` settings in favor of the new `MAILERS` setting. They still work. To move to `MAILERS`, see Django's [migration guide](https://docs.djangoproject.com/en/6.1/howto/mailers-migration/).
{% endhint %}

#### Minimal example

* To send a test email, open the Django shell:

```bash
python manage.py shell
```

* Then run:

```python
from django.core.mail import send_mail

send_mail(
    subject="Welcome to our app",
    message="Hi Jon, welcome aboard!",
    from_email="hello@yourdomain.com",
    recipient_list=["recipient@example.com"],
    html_message="<p>Hi Jon, welcome aboard!</p>",
)
```

The email appears in your [Email Logs](https://docs.mailtrap.io/email-live-sending/analytics/logs) as soon as it's sent.

#### Categories and custom variables

Add a [category](https://docs.mailtrap.io/email-live-sending/analytics/categories) and [custom variables](https://docs.mailtrap.io/email-live-sending/advanced/custom-variables) to filter and analyze your emails in Mailtrap. Anymail sends `tags` as the category and `metadata` as custom variables:

```python
from django.core.mail import EmailMessage

message = EmailMessage(
    subject="Welcome to our app",
    body="Hi Jon, welcome aboard!",
    from_email="hello@yourdomain.com",
    to=["recipient@example.com"],
)
message.tags = ["Welcome email"]
message.metadata = {"user_id": "45982", "batch_id": "PSJ-12"}
message.send()
```

Each email can have one category, so set only one tag. Custom variables are limited to 1,000 bytes per email.

#### Send with an email template

To send a [Mailtrap email template](https://docs.mailtrap.io/general/email-templates), set its UUID in `template_id` and its variables in `merge_global_data`. You'll find the UUID in the template's **Integration** tab:

```python
from django.core.mail import EmailMessage

message = EmailMessage(
    from_email="hello@yourdomain.com",
    to=["recipient@example.com"],
)
message.template_id = "YOUR_TEMPLATE_UUID"
message.merge_global_data = {"user_name": "Jon"}
message.send()
```

{% hint style="info" %}
Don't set a subject, body, or tag when you send a template. The template defines them, and the API returns an error if you add a tag.
{% endhint %}

#### Batch sending

To send personalized emails to many recipients in one API call, set `merge_data`. Anymail then sends a separate email to each address in `to`:

```python
from django.core.mail import EmailMessage

message = EmailMessage(
    from_email="hello@yourdomain.com",
    to=["alice@example.com", "Bob <bob@example.com>"],
)
message.template_id = "YOUR_TEMPLATE_UUID"
message.merge_data = {
    "alice@example.com": {"name": "Alice", "order_no": "12345"},
    "bob@example.com": {"name": "Bob", "order_no": "54321"},
}
message.merge_global_data = {"ship_date": "May 15"}
message.send()
```

Without `merge_data`, Mailtrap sends one email and every recipient sees the full `to` list. The batch API accepts up to 500 emails per call.

#### Status tracking webhooks

Anymail can receive Mailtrap [webhook](https://docs.mailtrap.io/general/webhooks) events and pass them to your app as Django signals. To set it up:

* Add Anymail's URLs to your `urls.py`:

```python
from django.urls import include, path

urlpatterns = [
    # ...
    path("anymail/", include("anymail.urls")),
]
```

* In Mailtrap, go to **Settings** → **Webhooks** and create a webhook with these values:
  * **Webhook URL**: `https://yoursite.example.com/anymail/mailtrap/tracking/`
  * **Payload format**: JSON (not JSON Lines)
  * **Area**: Email Sending, with the Transactional or Bulk Stream, your domain, and the events you need
* Copy the webhook's signing secret and add it to your settings:

```python
ANYMAIL = {
    # ...
    "MAILTRAP_TRACKING_SECRET": os.environ["MAILTRAP_TRACKING_SECRET"],
}
```

* Handle the events with a signal receiver:

```python
from anymail.signals import tracking
from django.dispatch import receiver

@receiver(tracking)
def handle_bounce(sender, event, esp_name, **kwargs):
    if event.event_type == "bounced":
        print(f"Message {event.message_id} to {event.recipient} bounced")
```

Anymail reports these events: delivered, opened, clicked, bounced, deferred, rejected, complained, and unsubscribed. Signature verification requires Anymail 15.2 or later.

For more options, see the [Anymail Mailtrap documentation](https://anymail.dev/en/stable/esps/mailtrap/).

#### SMTP integration

You can also send with Django's built-in SMTP backend. To get your credentials:

1. Go to the [Sending Setup](https://mailtrap.io/api-smtp/sending-setup) page under **Live Sending** and choose your domain.
2. Select the Transactional or Bulk Stream.
3. Toggle the switch to **SMTP** and copy the credentials.

Add the credentials to `settings.py`:

```python
import os

EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "live.smtp.mailtrap.io"
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "api"
EMAIL_HOST_PASSWORD = os.environ["MAILTRAP_API_TOKEN"]

DEFAULT_FROM_EMAIL = "hello@yourdomain.com"
```

For the Bulk Stream, use `EMAIL_HOST = "bulk.smtp.mailtrap.io"` with the Bulk Stream credentials. Mailtrap SMTP supports ports 587 (recommended), 2525, 25, and 465. For port 465, set `EMAIL_USE_SSL = True` instead of `EMAIL_USE_TLS`.

To add a category and custom variables to emails sent over SMTP, set the `X-MT-Category` and `X-MT-Custom-Variables` headers:

```python
import json

from django.core.mail import EmailMessage

message = EmailMessage(
    subject="Welcome to our app",
    body="Hi Jon, welcome aboard!",
    from_email="hello@yourdomain.com",
    to=["recipient@example.com"],
    headers={
        "X-MT-Category": "Welcome email",
        "X-MT-Custom-Variables": json.dumps({"user_id": "45982"}),
    },
)
message.send()
```

{% hint style="info" %}
SMTP integration doesn't need Anymail, so you can also use it on Django versions older than 5.0.
{% endhint %}

Read more in the [SMTP integration guide](https://docs.mailtrap.io/email-live-sending/setup/smtp-integration).

### Email Sandbox for Django

[Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox) catches every email your Django app sends, so you can inspect it without reaching real recipients. You don't need a verified domain to use it.

#### Anymail integration

If you use Anymail, add your sandbox ID to the `ANYMAIL` settings:

```python
ANYMAIL = {
    "MAILTRAP_API_TOKEN": os.environ["MAILTRAP_API_TOKEN"],
    "MAILTRAP_SANDBOX_ID": os.environ.get("MAILTRAP_SANDBOX_ID"),
}
```

You'll find the sandbox ID in your sandbox's URL. Anymail treats an empty value as not set, so the same settings send to real recipients when `MAILTRAP_SANDBOX_ID` is empty.

{% hint style="info" %}
Email Sandbox doesn't trigger webhook events.
{% endhint %}

#### SMTP integration

To use the SMTP backend, go to **Sandboxes**, open your sandbox, and copy the credentials from the **Integration** tab. You can also pick your language or framework under **Code Samples** and copy the ready-made configuration:

```python
EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "sandbox.smtp.mailtrap.io"
EMAIL_PORT = 2525
EMAIL_USE_TLS = True
EMAIL_HOST_USER = "YOUR_SANDBOX_USERNAME"
EMAIL_HOST_PASSWORD = "YOUR_SANDBOX_PASSWORD"
```

Each sandbox has its own username and password. Read more in the [Sandbox SMTP integration guide](https://docs.mailtrap.io/email-sandbox/setup/sandbox-smtp-integration).

#### Switch from Sandbox to live sending

When you're ready to send to real recipients, update your settings:

* **Anymail**: remove `MAILTRAP_SANDBOX_ID` or leave it empty.
* **SMTP**: replace the Sandbox credentials with your Email Live Sending SMTP credentials.

Set these values per environment, so your development and staging servers send to Sandbox and production sends to real recipients.

#### Troubleshooting

* **"You must set ANYMAIL = {'MAILTRAP\_API\_TOKEN': ...}" error**

Anymail can't find your API token. Anymail reads Django settings, not environment variables, so load the token into the `ANYMAIL` setting in `settings.py`.

* **"Sending from domain is not allowed" error**

The sender address doesn't use a verified sending domain. Django's default sender is `webmaster@localhost`, so make sure `DEFAULT_FROM_EMAIL`, `SERVER_EMAIL`, and any `from_email` you set use your verified domain. See [Domain not allowed](https://docs.mailtrap.io/email-live-sending/troubleshooting/sending-from-domain-not-allowed) for more fixes.

* **`AnymailUnsupportedFeature` error**

The message uses an option Mailtrap doesn't support, such as more than one tag, `send_at`, or `track_clicks`. Remove the option from the message.

* **"'category' is not allowed with 'template\_uuid'" error**

You set a tag on a template email. Remove `tags` from the message, because the template defines its own category.

* **Emails from tests don't reach Mailtrap**

Django's test runner replaces your email backend with an in-memory backend, so test emails aren't sent. Send from the Django shell or a running app instead.

* **Webhook events don't arrive**

Check that the webhook uses the JSON payload format, not JSON Lines, and that your endpoint returns HTTP 200. Emails sent to Email Sandbox don't trigger webhooks.

If you need help with your Django integration, contact our support team at **support@mailtrap.io**.
