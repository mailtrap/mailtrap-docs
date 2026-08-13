# Mailtrap Skills

Mailtrap offers official agent skills you can use to give your AI coding assistant accurate Mailtrap context for sending emails, receiving emails, testing with sandbox, using email templates, setting up a sending domain, and managing contacts.

For more information, read the official [GitHub repository](https://github.com/mailtrap/mailtrap-skills).

{% hint style="info" %}
Skills are not a substitute for [docs.mailtrap.io](http://docs.mailtrap.io) or the developer [API documentation](https://docs.mailtrap.io/developers).
{% endhint %}

### How to use Mailtrap Skills

To install, simply copy the [skills folders](https://github.com/mailtrap/mailtrap-skills) into the directory your agent reads. For example, for Cursor, that’s `.cursor/skills/`. Or, you can install via npx:

```
npx skills add mailtrap/mailtrap-skills
```

Mailtrap skills and their purpose:

| sending-emails            | Use when integrating, configuring, or troubleshooting Mailtrap (Email API or SMTP).                                                         |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| testing-with-sandbox      | Use when capturing outbound email in development or staging in a fake inbox.                                                                |
| using-email-templates     | Use when creating, managing, and sending Mailtrap-hosted email templates.                                                                   |
| setting-up-sending-domain | Use when adding or verifying a Mailtrap sending domain.                                                                                     |
| managing-contacts         | Use when using Mailtrap Contacts API or UI to add, update, bulk import, list, segment marketing contacts, custom fields, or custom events.  |

### Why use Mailtrap Skills

* **Ship email integrations faster** – AI coding assistants (Cursor, Claude Code) get correct Mailtrap endpoints, auth patterns, and stream choices without the developer leaving their editor
* **Fewer integration mistakes** – Skills encode the "common mistakes", catching errors before they happen
* **Lower time-to-first-send** – New users get a guided path from domain verification to first sent email
* **Always-current reference in context** – Skills point to live docs and OpenAPI specs, so the AI agent generates code against current APIs
