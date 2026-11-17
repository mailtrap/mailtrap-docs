# Manage your organization without accessing sub-account data

Organization Access Only lets you delegate organization administration while keeping access to individual sub-accounts separate.

This is especially useful for central operations, finance teams, and agencies or companies managing multiple sub-accounts.

### How to grant Organization Access Only

1. Go to **Organization** → **User Management** → **Add Member**.
2. Leave **Organization & Sub-accounts** unchecked.
3. Select **Organization Access Only** and choose **Admin** or **Viewer**.
4. Send the invitation.

The recipient joins the organization directly and does not need a sub-account.

For an existing member, edit their permissions in organization-level User Management. To restrict access to the organization, remove Organization & Sub-accounts and any separate sub-account permissions.

If you select Organization & Sub-accounts, Organization Access Only is selected and locked automatically because the broader permission already includes organization access.

Note: This permission is available only in organization-level User Management, not in a sub-account’s user management form. How to choose the right access

| **Permission**                  | **Organization access**                                | **Sub-account access**                |
| ------------------------------- | ------------------------------------------------------ | ------------------------------------- |
| **Organization & Sub-accounts** | Broad organization access, based on the selected level | Access to every sub-account           |
| **Organization Access Only**    | Organization administration or read-only visibility    | No access granted by this permission  |
| **Billing**                     | Billing and usage only                                 | No access granted by this permission  |

Organization Access Only has two levels: **Admin** and **Viewer**. There is no Owner level.

Keep in mind that **separate permissions still apply**. If a person also has permission to access specific sub-accounts, they can open those sub-accounts. Organization Access Only does not extend that access to any others.

### What Organization Access Only users can do

Those users have access to the Organization panel only (unless they have been granted access to some specific accounts additionally).

<br>

| **Section of the Organization panel** | **Admin**                                                                        | **Viewer**                                              |
| ------------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Sub-accounts**                      | View the list and create sub-accounts                                            | View the list                                           |
| **Usage & limits**                    | View usage and edit sub-account limits                                           | View usage and limits                                   |
| **Organization details**              | View details and rename the organization                                         | View details                                            |
| **Billing and subscriptions**         | Manage plans, payment methods, and billing settings                              | View subscriptions, payment method, and payment history |
| **User management**                   | Manage Organization Access Only users and users whose only permission is Billing | Unavailable                                             |
| **API Tokens**                        | Manage organization-only tokens                                                  | Unavailable                                             |
| **Audit Log**                         | View organization events when included in the plan                               | Unavailable                                             |

Neither level grants access to the settings or content inside a sub-account. Creating a sub-account does not give the creator permission to open it.

#### Managing users

An Organization Access Only Admin can invite and manage other Organization Access Only users and users whose only permission is Billing.

They can see organization owners and users with sub-account access, but cannot change those users’ permissions. Furthermore, they cannot change their own access or grant Organization & Sub-accounts access or permissions inside a sub-account.

#### Managing API tokens

Admins can create, reset, and delete tokens with Organization Access Only permissions, at either Admin or Viewer level.

An Admin token can list, create or delete sub-accounts. A Viewer token can only list them. Neither can read or change data inside a sub-account. Billing permission cannot be assigned to API tokens.

### Other management limits

* Transferring a sub-account requires access to that sub-account and is unavailable through this role alone.
* An Organization Access Only Admin can request deletion of a sub-account without access to its contents.&#x20;
* An Organization Access Only Admin can turn off the Organization & Sub-accounts feature from organization settings only when exactly one sub-account remains.

\
<br>
