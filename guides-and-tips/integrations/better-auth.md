---
description: >-
  Learn how to send Better Auth verification and password reset emails using
  Mailtrap's Email API.
---

# Better Auth

## Overview

This guide explains how to integrate Mailtrap with [Better Auth](https://www.better-auth.com) to deliver the emails your authentication flows depend on, such as email verification links and password reset tokens.

Better Auth does not send email itself. It calls a function you provide, so you decide which provider delivers the message. This guide implements that function with the Mailtrap Email API.

Better Auth sends email from several places. Core email and password authentication uses two callbacks, and some plugins add their own:

| Surface             | Callback                                  |
| ------------------- | ----------------------------------------- |
| Email verification  | `emailVerification.sendVerificationEmail` |
| Password reset      | `emailAndPassword.sendResetPassword`      |
| Magic Link plugin   | `magicLink({ sendMagicLink })`            |
| Email OTP plugin    | `emailOTP({ sendVerificationOTP })`       |
| Organization plugin | `organization({ sendInvitationEmail })`   |

All of them are plain async functions, so a single `sendEmail` helper can serve every one.

### Prerequisites

Before you start, make sure you have:

* [Verified your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain)
* [Created and saved an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-tokens)
* An existing Better Auth project

### Installation

Install the Mailtrap Node.js SDK:

{% code title="npm" %}
```bash
npm install mailtrap
```
{% endcode %}

## Send emails using Better Auth and Mailtrap

First, create a reusable `sendEmail` function backed by the Mailtrap Email API:

{% code title="email.ts" %}
```typescript
import { MailtrapClient } from "mailtrap";

const mailtrap = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY!,
});

// Any value your users control (names, organizations, custom messages) has to be
// escaped before it goes into an `html` body. Otherwise someone can name their
// organization `</a><a href="https://attacker.example">Verify now</a>` and your
// email delivers their link instead of yours.
const HTML_ESCAPES: Record<string, string> = {
  "&": "&amp;",
  "<": "&lt;",
  ">": "&gt;",
  '"': "&quot;",
  "'": "&#39;",
};

export const escapeHtml = (value: string) =>
  value.replace(/[&<>"']/g, (char) => HTML_ESCAPES[char]);

export async function sendEmail(options: {
  to: string;
  subject: string;
  text: string;
  html?: string;
  category?: string;
}) {
  try {
    await mailtrap.send({
      from: { name: "Your App", email: "no-reply@yourdomain.com" },
      to: [{ email: options.to }],
      subject: options.subject,
      text: options.text,
      html: options.html,
      category: options.category,
    });
  } catch (error) {
    console.error(`Failed to send "${options.subject}" to ${options.to}`, error);
  }
}
```
{% endcode %}

Then pass it to Better Auth to handle email verification and password resets:

{% code title="auth.ts" %}
```typescript
import { betterAuth } from "better-auth";
import { sendEmail } from "./email";

export const auth = betterAuth({
  emailVerification: {
    sendOnSignUp: true,
    sendVerificationEmail: async ({ user, url }) => {
      void sendEmail({
        to: user.email,
        subject: "Verify your email address",
        text: `Verify your email address: ${url}`,
        html: `<p>Click <a href="${url}">here</a> to verify your email address.</p>`,
        category: "Email verification",
      });
    },
  },
  emailAndPassword: {
    enabled: true,
    sendResetPassword: async ({ user, url }) => {
      void sendEmail({
        to: user.email,
        subject: "Reset your password",
        text: `Reset your password: ${url}`,
        html: `<p>Click <a href="${url}">here</a> to reset your password.</p>`,
        category: "Password reset",
      });
    },
  },
});
```
{% endcode %}

### Plugin emails

If you use the Magic Link, Email OTP, or Organization plugins, reuse the same `sendEmail` helper for their callbacks. Add the `plugins` array to the same `betterAuth` call shown above, keeping only the plugins your app actually uses:

{% code title="auth.ts" %}
```typescript
import { magicLink, emailOTP, organization } from "better-auth/plugins";
import { escapeHtml, sendEmail } from "./email";

export const auth = betterAuth({
  // ...emailVerification and emailAndPassword from above
  plugins: [
    magicLink({
      sendMagicLink: async ({ email, url }) => {
        void sendEmail({
          to: email,
          subject: "Sign in to Your App",
          text: `Sign in to Your App: ${url}`,
          html: `<p>Click <a href="${url}">here</a> to sign in.</p>`,
          category: "Magic link",
        });
      },
    }),
    emailOTP({
      async sendVerificationOTP({ email, otp, type }) {
        void sendEmail({
          to: email,
          subject: "Your verification code",
          text: `Your code is ${otp}`,
          category: `OTP ${type}`,
        });
      },
    }),
    organization({
      async sendInvitationEmail(data) {
        const link = `https://yourdomain.com/accept-invitation/${data.id}`;
        const org = data.organization.name;
        void sendEmail({
          to: data.email,
          subject: `${data.inviter.user.name} invited you to ${org}`,
          text: `Join ${org}: ${link}`,
          html: `<p>Click <a href="${link}">here</a> to join ${escapeHtml(org)}.</p>`,
          category: "Organization invitation",
        });
      },
    }),
  ],
});
```
{% endcode %}

### Configuration

Once you copy the scripts, update the following:

* Set `MAILTRAP_API_KEY` in your environment to your Mailtrap API token
* Replace `no-reply@yourdomain.com` with an address on your verified sending domain
* Replace `Your App` with the sender name you want recipients to see
* Replace `https://yourdomain.com` in the invitation link with your app's base URL

The `category` field is optional. Setting it per email type lets you filter authentication emails in [Email Logs](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/analytics/logs) and see the category on delivery [webhooks](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/advanced/webhooks), so you can tell reset emails from verification emails at a glance.

The link-based examples send both `html` and `text`. The HTML version gives recipients a clickable link, and the plain text version is a fallback for clients that do not render HTML. The one-time code is plain text only, since there is nothing to link to.

Escape every user-controlled value you interpolate into an `html` body. The invitation example runs the organization name through `escapeHtml` because whoever created the organization chose that name: left raw, a name containing `</a><a href="...">` closes your link and opens theirs, so the email arrives from your verified domain carrying an attacker's URL. That makes it a convincing phishing message, and invitations are the worst case because Better Auth sends them to people who are not users yet and have no way to judge what is normal for your app.

Watch for this anywhere the value is not authored by you, including display names, team and organization names, and any custom note attached to an invitation. Escaping is only needed for `html`; `text` and `subject` are not parsed as markup, which is why the examples leave them as they are.

For richer, designed emails, keep the markup out of your application code and use [Email Templates](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/email-templates) instead. Templates need a different payload, so add a separate helper rather than reusing `sendEmail`:

{% code title="email.ts" %}
```typescript
export async function sendTemplateEmail(options: {
  to: string;
  templateUuid: string;
  variables?: Record<string, string>;
}) {
  try {
    await mailtrap.send({
      from: { name: "Your App", email: "no-reply@yourdomain.com" },
      to: [{ email: options.to }],
      template_uuid: options.templateUuid,
      template_variables: options.variables,
    });
  } catch (error) {
    console.error(`Failed to send template to ${options.to}`, error);
  }
}
```
{% endcode %}

Mailtrap renders the template, so the variables are passed as data and do not need HTML escaping.

{% hint style="info" %}
Better Auth recommends not awaiting the email call inside these handlers, which is why the examples use `void`. Awaiting it makes the response time depend on whether the address exists, which can leak that information. On serverless platforms, use `waitUntil` or the equivalent so the request is not torn down before the email is sent.

Because nothing awaits the result, `sendEmail` has to handle its own failures. That is what the `try/catch` is for: without it, a rejected send becomes an unhandled promise rejection, which terminates the Node.js process by default. Replace `console.error` with your own logger or error reporting.
{% endhint %}

### Learn more

For additional details about the Email API, refer to the [Mailtrap Email Sending API Integration guide](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration) and the [Mailtrap Node.js SDK](https://github.com/mailtrap/mailtrap-nodejs).
