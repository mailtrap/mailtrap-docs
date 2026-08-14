# Mailtrap CLI app

Mailtrap CLI is a command-line tool for accessing Mailtrap features that allow you to send emails, inspect sandbox inboxes, monitor deliverability stats, and administer domains, templates, contacts, and more, all from your terminal.

Link to official [GitHub documentation](https://github.com/mailtrap/mailtrap-cli).

### How it works

#### Installation

To install Mailtrap CLI app, choose one of the following installation methods:

* Homebrew (macOS / Linux):

```
brew install mailtrap/cli/mailtrap
```

* Download binary

Download the latest release from [GitHub Releases](https://github.com/mailtrap/mailtrap-cli/releases) and add it to your `PATH`.

* Go install:

```
go install github.com/mailtrap/mailtrap-cli@latest
```

#### Authentication

To validate your token, detect your account ID, and save both to **\~/.mailtrap.yaml** run the following command:

```
mailtrap configure --api-token YOUR_TOKEN
```

Or, you can also use environment variables:

```
export MAILTRAP_API_TOKEN=your-token
```

#### Using the CLI

Then use any of the \~87 commands across 20 resource groups. A few examples:

```
# Send a transactional email
mailtrap send transactional \
  --from "app@yourdomain.com" \
  --to "user@example.com" \
  --subject "Order confirmed" \
  --html "<h1>Thanks for your order</h1>"

# Check spam score on a sandbox message
mailtrap messages spam-score --sandbox-id 12345 --id 67890

# Pull sending stats by mailbox provider
mailtrap stats by-esp --start-date "2025-01-01" --end-date "2025-04-07" --domain-ids 111



# Bulk import contacts from JSON
mailtrap contacts import --file contacts.json
```

Every command supports `--output` json for scripting and CI/CD integration. Shell completion is available for Bash, Zsh, Fish, and PowerShell.

### Use case examples

#### Test before you send

Here's how you can verify your email renders correctly in sandbox before sending to real users.

{% stepper %}
{% step %}
### Create a project for your sandbox

To create a project for your sandbox and get a project ID, use the following command:

```
mailtrap projects create --name "My App Testing"
```
{% endstep %}

{% step %}
### Create a sandbox inside your project

Next, use the following command to create a sandbox and get a sandbox ID:

```
mailtrap sandboxes create --name "Staging Inbox" --project-id [YOUR-PROJECT-ID]
```

{% hint style="warning" %}
Replace \[YOUR-PROJECT-ID] with your actual project ID.
{% endhint %}
{% endstep %}

{% step %}
### Send a test email to sandbox

Then, simply send the email, just like so:

```
mailtrap sandbox-send single \
  --sandbox-id [YOUR-SANDBOX-ID] \
  --from "noreply@myapp.com" \
  --to "dev@myapp.com" \
  --subject "Welcome to MyApp" \
  --html '<html><body style="font-family:Arial,sans-serif;max-width:600px;margin:0 auto;padding:20px"><h1 style="color:#1a1a2e">Welcome to MyApp!</h1><p>Hi there,</p><p>Your account is ready. Click the button below to confirm your email address.</p><a href="https://myapp.com/confirm" style="display:inline-block;background:#4f46e5;color:#fff;padding:12px 24px;border-radius:6px;text-decoration:none;font-weight:bold">Confirm my email</a><p style="color:#666;font-size:12px;margin-top:32px">If you did not sign up, you can ignore this email.</p></body></html>'
```

{% hint style="warning" %}
Replace \[YOUR-SANDBOX-ID] with your actual sandbox ID.
{% endhint %}
{% endstep %}

{% step %}
### Inspect the email

To list the sandboxes, use:

```
mailtrap messages list --sandbox-id [YOUR-SANDBOX-ID]
```

Then, to get a spam score, use the following command:

```
mailtrap messages spam-score --sandbox-id [YOUR-SANDBOX-ID] --id [MESSAGE-ID]
```

Or, to inspect the HTML:

```
mailtrap messages html-analysis --sandbox-id [YOUR-SANDBOX-ID] --id 789
```

{% hint style="info" %}
Replace \[MESSAGE-ID] with the actual message ID that you get after sending an email to your sandbox.
{% endhint %}
{% endstep %}
{% endstepper %}

#### Email marketing – build and send a campaign

You can also send an email marketing campaign from the Mailtrap CLI app, covering everything from managing contacts to creating email templates. Here's how:

{% stepper %}
{% step %}
### Create a contact list

```
mailtrap contact-lists create --name "Product Launch Waitlist"
```
{% endstep %}

{% step %}
### Add a custom field

```
mailtrap contact-fields create \
  --name "Job Title" \
  --data-type text \
  --merge-tag 'Job Title'
```
{% endstep %}

{% step %}
### Add contacts to the list

```
mailtrap contacts create \
  --email "john@acme.com" \
  --first-name "John" \
  --last-name "Doe" \
  --list-ids "101"
```
{% endstep %}

{% step %}
### Create an email template

```
mailtrap templates create \
  --name "Product Launch" \
  --subject 'We are live!' \
  --body-html '<h1>Hello {{first_name}}, we just launched!</h1>' \
  --category "product-launch"
```
{% endstep %}

{% step %}
### Launch the email campaign

```
mailtrap send bulk \
  --from "team@myapp.com" \
  --to "john@acme.com" \
  --subject 'We are live!' \
  --html '<h1>Hello John, we just launched!</h1>' \
  --category "product-launch"
```
{% endstep %}
{% endstepper %}

#### Analytics – monitor email performance

Once you start sending emails, use the Mailtrap CLI app to track delivery, opens, clicks across categories and providers, and more.

{% stepper %}
{% step %}
### Overall stats

```
mailtrap stats get \
  --start-date "2026-05-01" \
  --end-date "2026-05-14"
```
{% endstep %}

{% step %}
### Break down by email category

```
mailtrap stats by-category \
  --start-date "2026-05-01" \
  --end-date "2026-05-14"
```
{% endstep %}

{% step %}
### See which email providers deliver best

```
mailtrap stats by-esp \
  --start-date "2026-05-01" \
  --end-date "2026-05-14"
```
{% endstep %}

{% step %}
### Drill into recent individual emails

```
mailtrap email-logs list
```
{% endstep %}

{% step %}
### List your suppressed recipients

```
mailtrap suppressions list
```
{% endstep %}
{% endstepper %}
