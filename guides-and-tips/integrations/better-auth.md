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

| Surface | Callback |
| --- | --- |
| Email verification | `emailVerification.sendVerificationEmail` |
| Password reset | `emailAndPassword.sendResetPassword` |
| Magic Link plugin | `magicLink({ sendMagicLink })` |
| Email OTP plugin | `emailOTP({ sendVerificationOTP })` |
| Organization plugin | `organization({ sendInvitationEmail })` |

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

export async function sendEmail(options: {
  to: string;
  subject: string;
  text: string;
  html?: string;
  category?: string;
}) {
  await mailtrap.send({
    from: { name: "Your App", email: "no-reply@yourdomain.com" },
    to: [{ email: options.to }],
    subject: options.subject,
    text: options.text,
    html: options.html,
    category: options.category,
  });
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

If you use the Magic Link, Email OTP, or Organization plugins, reuse the same `sendEmail` helper for their callbacks. Add only the plugins your app actually uses:

{% code title="auth.ts" %}
```typescript
import { magicLink, emailOTP, organization } from "better-auth/plugins";

export const auth = betterAuth({
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
          html: `<p>Click <a href="${link}">here</a> to join ${org}.</p>`,
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

The `category` field is optional. Setting it per email type lets you filter authentication emails in [Email Logs](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/analytics/logs) and see the category on delivery [webhooks](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/webhooks), so you can tell reset emails from verification emails at a glance.

The examples send both `html` and `text`. The HTML version gives recipients a clickable link, and the plain text version is a fallback for clients that do not render HTML. For richer, designed emails, keep the markup out of your application code and use [Email Templates](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/email-templates) instead, passing `template_uuid` and `template_variables` in place of `subject`, `text`, and `html`.

{% hint style="info" %}
Better Auth recommends not awaiting the email call inside these handlers, which is why the examples use `void`. Awaiting it makes the response time depend on whether the address exists, which can leak that information. On serverless platforms, use `waitUntil` or the equivalent so the request is not torn down before the email is sent.
{% endhint %}

### Learn more

For additional details about the Email API, refer to the [Mailtrap Email Sending API Integration guide](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration) and the [Mailtrap Node.js SDK](https://github.com/mailtrap/mailtrap-nodejs).
