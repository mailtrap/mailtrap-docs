---
title: <i class="fa-database">:database:</i> Supabase and Mailtrap Integration
description: Comprehensive guide to integrate Mailtrap with Supabase for email sending and contact management with flexible email options.
---

# Overview

Mailtrap can now be integrated with Supabase, giving you flexible options for email sending and contact automation. This integration allows you to exceed the default sending limits and sync your user base to send personalized email campaigns.

## Integration Options

Mailtrap offers two main integration approaches with Supabase:

### Mailtrap SMTP + Supabase

Use Mailtrap's SMTP settings to send emails directly through your Supabase project. This approach is ideal for applications that use SMTP-based email delivery.

**Key Features:**
- Configure SMTP credentials in Supabase Authentication settings
- Send emails through Supabase's built-in email system
- Adjust email rate limits beyond Supabase defaults

See the [Mailtrap SMTP and Supabase integration guide](https://help.mailtrap.io/article/165-mailtrap-smtp-and-supabase) for detailed setup instructions.

### Mailtrap Contacts Management + Supabase

Sync your Supabase user database with Mailtrap's Contacts feature to manage recipient lists and send campaigns.

**Key Features:**
- Manage and segment contacts from your Supabase database
- Send personalized email campaigns to contact lists
- Automate email sequences based on user actions
- Track opens, clicks, and other engagement metrics

See the [Mailtrap Contacts and Supabase integration guide](https://help.mailtrap.io/article/167-mailtrap-contacts-and-supabase) for detailed setup instructions.

## Which Integration Should You Choose?

**Choose SMTP + Supabase if you:**
- Need to send transactional emails from your application
- Prefer using Supabase's built-in email features
- Want automatic email notifications (password resets, confirmations, etc.)
- Don't need advanced contact management capabilities

**Choose Contacts Management + Supabase if you:**
- Want to build email marketing campaigns
- Need to segment and manage large recipient lists
- Require analytics on email engagement
- Plan to automate email sequences
- Want to sync users from Supabase to Mailtrap's contact system

## Getting Started

Both integration guides above contain step-by-step instructions, screenshots, and code examples. Choose the option that best fits your use case and follow the corresponding guide.
