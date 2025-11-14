# User Management

This is the centralized place to manage users in your account.

![](https://lh7-us.googleusercontent.com/AYwmGp_wI-meS21R7McUWacTFGWZl4FxNQ6d_lVMC8A4HUv0muHP7lP6APORax_05oOUz4ghEc2AiW5vL0w4690gAIh2IuZAlutZs8DD5jJMFRed23RFmxyfQPQYAjRPd8su5s4ZjFxr0WkdBK1t6MI)

![](https://lh7-us.googleusercontent.com/NqJ0bSqQ2qFDb2tLAWbX4HL0UGP2IH2Q6iEbWmou-oLAeRJZ4q_yllg4PnqOFvUDdjVkve_8E6eZJU4CXipZ6-QGdFi8TVbD78lv3TreNEp9kBj1ymfT0bQ97bGw8vu1PDtM9iQq64Ev3UwgNQNearU)

* Account Owner is a person who has registered an account or to whom [it has been transferred](https://help.mailtrap.io/article/61-account-management). Account Owner can rename an account, delete it, transfer ownership, manage all projects and sandboxes, and add/edit/invite team members. Nobody can alter the permissions of an Account Owner.
* Account Admin has the same permissions as an Account Owner, with the exception of deleting an account and transferring its ownership. Account Owner and other Account Admins can alter the permission of Account Admins.
* Account Viewer has access to all the entities in the account (projects, sandboxes, billing) but can’t add, edit, or remove anything. For example, the Account Viewer can view all projects but can’t add new ones or edit existing ones.
* Domain Admin can rename and delete a domain, manage domain settings (e.g., reset the credentials, enable/disable open or click tracking, or modify unsubscribe footer settings), and add/remove domain team members.
* Domain Viewer can view domain settings, reports, statistics, and email logs (except for email content) for the domain but can’t add, edit, or remove anything.
* Templates Admin can create, edit, delete, and duplicate the templates
* Templates Viewer can only preview templates, check their type, category, update date.
* View Email Content permission is available for all sending domains. It enables Account Owners, Account Admins, and Domain Admins to grant Viewers access to view email bodies in Email Logs. They can provide View Email Content permission for one domain and limit it for another. By default, Account Owners, Account Admins, and Domain Admins have the right to view email bodies, while Viewers don’t.
  * If the user doesn’t have the permission to view email content, they will see the following message in Email Logs:

![](https://lh7-us.googleusercontent.com/mq9k-IfGOonaXmyssnCMcS8B5XSXzA5QbsskdmreCuylaSTQscuxPV5wkMPL_1IPCy1bexLdgALKvJ314OlSb4KUV-iMf3NJTmbWhszJ7D9l_ia_1fvWDCIGjsAROvtfQVr15syCxIGsVCs5JTCJ6XA)

* Email Campaign Admin can create, edit, delete, and send email campaigns, as well as view reports.
* Email Campaign Viewer can only view email campaigns and campaign reports.
* Project Admin can rename and delete a project, fully manage all its sandboxes (add new or delete existing ones), and add or remove project team members. They cannot add new projects in the account.
* Project Viewer can see all the sandboxes in the project but can’t edit anything (e.g., [sandbox email address](https://help.mailtrap.io/article/18-email-per-inbox) or [forwarding settings](https://help.mailtrap.io/article/41-auto-forward)). They also can’t add or remove teammates, projects, or sandboxes.
* Sandbox Admin can rename and delete a sandbox, manage sandbox settings (e.g., reset the credentials or add forwarding rules), and add/remove sandbox team members. However, they can’t add new sandbox or projects.
* Sandbox Viewer can see all the sandbox messages but can’t edit anything (e.g., [sandbox email addresss](https://help.mailtrap.io/article/18-email-per-inbox) or [forwarding domains](https://help.mailtrap.io/article/41-auto-forward)). They also can’t add or remove sandbox teammates, sandboxes, or projects.
* Billing Admin permission allows users to manage the Billing settings, add or remove credit cards, upgrade and downgrade the account, and cancel the subscription.
* Billing Viewer can only see the credit card on file and details of the current subscription. They can also opt out of receiving invoices to their email address.

When you remove a user on the User Management page, they immediately lose access to your account, but stay in the system as Mailtrap users.

If you remove a person from a Sandbox or a Project, they remain in your account but lose access to a sandbox or a project in question.

A person can stay in your account without any permissions at all. This can happen if you remove them from all projects/sandboxes but not from the list on the User Management page. If you no longer work with a teammate, the best way to remove them is to use the User Management page. Otherwise, users with zero access who are still present on your account will be counted towards your [account limits](https://mailtrap.io/billing/dashboard).

To check your own permissions, find your user on the list and click “edit permissions” in the three dots menu. You’ll see which entities are available to you. You cannot change your own permissions.

\
