---
title: User Management
description: >-
  Manage users, teams, and organizational structure in Mailtrap. Control
  permissions, access, and collaboration.
---

# 👤 User Management

Efficiently manage your team's access to Mailtrap. Control permissions, organize users into teams, and maintain security across your organization.

## User Management Features

### [Organization & Sub-Accounts](organization-and-sub-accounts.md)

Structure your Mailtrap account with organizations and sub-accounts for better resource management and billing separation.

### [User Management](user-management.md)

Add, remove, and manage team members. Control access levels and permissions for different users.

### [User Profile](user-profile.md)

Manage individual user profiles, preferences, and settings within your organization.

### [My Profile](my-profile.md)

Personal profile management including account settings, notifications, and security options.

## Team Structure

### Organization Hierarchy

```
Organization
├── Admin Users
├── Teams
│   ├── Development Team
│   ├── QA Team
│   └── Marketing Team
└── Sub-Accounts
    ├── Project A
    ├── Project B
    └── Client Accounts
```

### User Roles

#### Organization Owner

* Full administrative control
* Billing management
* User management
* All feature access
* Cannot be removed

#### Admin

* User management
* Project creation
* Settings management
* Feature configuration
* No billing access

#### Member

* Access assigned projects
* Use assigned features
* View permissions
* Limited settings
* No admin functions

#### Viewer

* Read-only access
* View emails and logs
* Generate reports
* No modifications
* No sending capabilities

## Permission Management

### Feature Permissions

* **Email API/SMTP**: Send emails, view logs, manage domains
* **Email Sandbox**: Create sandboxes, view emails, forward
* **Email Marketing**: Create campaigns, manage contacts
* **Analytics**: View reports, export data
* **Settings**: Modify configuration

### Project-Level Access

Assign users to specific projects:

* Full access to project resources
* Isolated from other projects
* Custom role per project
* Transferable ownership
* Audit trail maintenance

## Team Collaboration

### Shared Resources

* Team sandboxes
* Shared templates
* Common suppressions list
* Unified analytics
* Collaborative workflows

### Communication Features

* Team notifications
* Activity logs
* Comments on emails
* Shared notes
* Status updates

## Security & Compliance

### Access Control

* Two-factor authentication
* SSO integration
* IP whitelisting
* Session management
* API key management

### Audit & Compliance

* Activity logging
* Access history
* Change tracking
* Compliance reports
* Data governance

## User Onboarding

### Adding New Users

1. Navigate to Team Settings
2. Click "Invite User"
3. Enter email address
4. Select role and permissions
5. Send invitation

### Onboarding Process

* Welcome email sent
* Account activation
* Initial permissions set
* Team assignment
* Training resources provided

## Best Practices

### Team Organization

* Create logical team groups
* Use descriptive team names
* Document team purposes
* Regular permission reviews
* Clear escalation paths

### Security Guidelines

* Enforce 2FA for all users
* Regular password updates
* Minimal necessary permissions
* Regular access audits
* Remove inactive users

### Collaboration Tips

* Establish naming conventions
* Document workflows
* Share best practices
* Regular team sync
* Clear communication channels

## Common Tasks

### Invite Team Member

```javascript
POST /api/team/invite
{
  "email": "newuser@company.com",
  "role": "member",
  "teams": ["development", "qa"],
  "projects": ["project-a"]
}
```

### Update User Role

```javascript
PATCH /api/users/{userId}
{
  "role": "admin",
  "permissions": {
    "email_api": "full",
    "sandbox": "full",
    "marketing": "read"
  }
}
```

### Remove User Access

```javascript
DELETE /api/users/{userId}
{
  "transfer_ownership_to": "admin@company.com",
  "preserve_data": true
}
```

## Troubleshooting

### Common Issues

* **Cannot invite user**: Check plan limits
* **Permission denied**: Verify role settings
* **Cannot access project**: Check team assignment
* **Missing features**: Confirm plan includes feature
* **Login issues**: Reset password or check 2FA

### Getting Help

* Review user management docs
* Contact account admin
* Check permission settings
* Submit support ticket
* Review audit logs
