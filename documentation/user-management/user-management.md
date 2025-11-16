---
title: User Management
description: >-
  Manage user roles and permissions in your Mailtrap account. Learn about
  account owners, admins, viewers, domain permissions, template access, and
  billing roles.
---

# 👥 User Management

This is the centralized place to manage users in your account.

<div align="left"><img src="../.gitbook/assets/user-management-interface.png" alt="Mailtrap User Management interface showing list of users with their roles and permissions" width="563"></div>

<div align="left"><img src="../.gitbook/assets/user-management-roles-table.png" alt="User roles permission table showing different access levels for account entities" width="563"></div>

* Account Owner is a person who has registered an account or to whom [it has been transferred](my-profile.md). Account Owner can rename an account, delete it, transfer ownership, manage all projects and sandboxes, and add/edit/invite team members. Nobody can alter the permissions of an Account Owner.
* Account Admin has the same permissions as an Account Owner, with the exception of deleting an account and transferring its ownership. Account Owner and other Account Admins can alter the permission of Account Admins.
* Account Viewer has access to all the entities in the account (projects, sandboxes, billing) but can't add, edit, or remove anything. For example, the Account Viewer can view all projects but can't add new ones or edit existing ones.
* Domain Admin can rename and delete a domain, manage domain settings (e.g., reset the credentials, enable/disable open or click tracking, or modify unsubscribe footer settings), and add/remove domain team members.
* Domain Viewer can view domain settings, reports, statistics, and email logs (except for email content) for the domain but can't add, edit, or remove anything.
* Templates Admin can create, edit, delete, and duplicate the templates
* Templates Viewer can only preview templates, check their type, category, update date.
* View Email Content permission is available for all sending domains. It enables Account Owners, Account Admins, and Domain Admins to grant Viewers access to view email bodies in Email Logs. They can provide View Email Content permission for one domain and limit it for another. By default, Account Owners, Account Admins, and Domain Admins have the right to view email bodies, while Viewers don't.
  * If the user doesn't have the permission to view email content, they will see the following message in Email Logs:

<div align="left"><img src="../.gitbook/assets/user-no-email-content-permission.png" alt="Email Logs page showing no permission message for viewing email content" width="563"></div>

* Email Campaign Admin can create, edit, delete, and send email campaigns, as well as view reports.
* Email Campaign Viewer can only view email campaigns and campaign reports.
* Project Admin can rename and delete a project, fully manage all its sandboxes (add new or delete existing ones), and add or remove project team members. They cannot add new projects in the account.
* Project Viewer can see all the sandboxes in the project but can't edit anything (e.g., [sandbox email address](../email-sandbox/email-address-per-sandbox.md) or [forwarding settings](../email-sandbox/automatic-email-forwarding.md)). They also can't add or remove teammates, projects, or sandboxes.
* Sandbox Admin can rename and delete a sandbox, manage sandbox settings (e.g., reset the credentials or add forwarding rules), and add/remove sandbox team members. However, they can't add new sandbox or projects.
* Sandbox Viewer can see all the sandbox messages but can't edit anything (e.g., [sandbox email addresss](../email-sandbox/email-address-per-sandbox.md) or [forwarding domains](../email-sandbox/automatic-email-forwarding.md)). They also can't add or remove sandbox teammates, sandboxes, or projects.
* Billing Admin permission allows users to manage the Billing settings, add or remove credit cards, upgrade and downgrade the account, and cancel the subscription.
* Billing Viewer can only see the credit card on file and details of the current subscription. They can also opt out of receiving invoices to their email address.

When you remove a user on the User Management page, they immediately lose access to your account, but stay in the system as Mailtrap users.

If you remove a person from a Sandbox or a Project, they remain in your account but lose access to a sandbox or a project in question.

A person can stay in your account without any permissions at all. This can happen if you remove them from all projects/sandboxes but not from the list on the User Management page. If you no longer work with a teammate, the best way to remove them is to use the User Management page. Otherwise, users with zero access who are still present on your account will be counted towards your [account limits](https://mailtrap.io/billing/dashboard).

To check your own permissions, find your user on the list and click "edit permissions" in the three dots menu. You'll see which entities are available to you. You cannot change your own permissions.
