# Mailtrap CLI app

Mailtrap CLI is a command-line tool for accessing Mailtrap features that allow you to send emails, inspect sandbox inboxes, monitor deliverability stats, and administer domains, templates, contacts, and more, all from your terminal.

Link to official [GitHub documentation](https://github.com/mailtrap/mailtrap-cli).

### How it works

#### Installation&#x20;

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
