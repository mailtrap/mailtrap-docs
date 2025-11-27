---
title: Managing Contacts
description: Search, filter, edit, and perform bulk operations on your contact database
icon: users-gear
---

# Managing Contacts

Efficiently manage your contact database with powerful search, filtering, and bulk operation capabilities. Keep your lists clean and up-to-date with comprehensive management tools.

## Viewing Contacts

Navigate to **Contacts** → **All contacts** to access your complete contact database.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-details-view.png" alt="Contact details page showing subscription status and associated fields" width="563"></div>

## Searching and Filtering

### Quick Search

Use the search bar to quickly find contacts by:

* Email address
* Name (if custom field exists)
* Any custom field value

### Advanced Filtering

Build complex filters using multiple criteria:

{% stepper %}
{% step %}
**Select Filter Type**

Choose from:

* Subscription Status
* Email
* Lists
* Custom Fields
{% endstep %}

{% step %}
**Set Conditions**

Define your filter logic:

* **Is** / **Is not**
* **Contains** / **Does not contain**
* **Greater than** / **Less than** (for numbers)
* **Before** / **After** (for dates)
{% endstep %}

{% step %}
**Apply Filter**

Click **Search** to view filtered results.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-filter-search.png" alt="Contact filtering interface with subscription status filter" width="563"></div>
{% endstep %}
{% endstepper %}

### Common Filter Examples

{% tabs %}
{% tab title="Active Subscribers" %}
```
Subscription Status → Is → Subscribed
```

Find all contacts who can receive campaigns.
{% endtab %}

{% tab title="Recent Signups" %}
```
Signup Date → After → [Last 30 days]
AND Subscription Status → Is → Subscribed
```

Identify new subscribers for welcome campaigns.
{% endtab %}

{% tab title="VIP Customers" %}
```
Customer Tier → Is → VIP
OR Total Purchases → Greater than → 1000
```

Target high-value customers.
{% endtab %}

{% tab title="Inactive Users" %}
```
Last Activity → Before → [90 days ago]
AND Subscription Status → Is → Subscribed
```

Re-engage dormant subscribers.
{% endtab %}
{% endtabs %}

## Individual Contact Actions

Click on any contact to view their details and perform individual actions:

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-actions-menu.png" alt="Contact actions menu with delete, unsubscribe, and edit options" width="563"></div>

### Available Actions

{% tabs %}
{% tab title="Edit Details" %}
**Update contact information**

* Modify custom field values
* Update email address
* Change list assignments
* Add notes or tags

{% hint style="info" %}
Changes are saved automatically and reflected immediately in campaigns.
{% endhint %}
{% endtab %}

{% tab title="Manage Lists" %}
**Add or remove from lists**

* Add to multiple lists
* Remove from specific lists
* View all assigned lists
* Check list membership history
{% endtab %}

{% tab title="Unsubscribe" %}
**Remove from all marketing**

* Marks contact as unsubscribed
* Removes from all active campaigns
* Preserves contact data
* Cannot be reversed manually

{% hint style="warning" %}
Unsubscribed contacts must re-subscribe themselves to receive emails again.
{% endhint %}
{% endtab %}

{% tab title="Delete" %}
**Permanently remove contact**

* Deletes all contact data
* Removes from all lists
* Cannot be undone
* Frees up contact quota

{% hint style="danger" %}
Deletion is permanent. Export contact data before deleting if needed.
{% endhint %}
{% endtab %}
{% endtabs %}

## Bulk Operations

Perform actions on multiple contacts simultaneously for efficient management.

### Selecting Contacts

{% hint style="info" %}
**Selection Methods**

* Click checkboxes for individual contacts
* Use "Select All" for current page
* Apply filters first to target specific groups
{% endhint %}

### Bulk Actions Available

#### Add to Lists

{% stepper %}
{% step %}
**Select Contacts**

Check the contacts you want to add to lists.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-bulk-add-to-lists.png" alt="Bulk action to add selected contacts to lists" width="563"></div>
{% endstep %}

{% step %}
**Choose Lists**

Select one or more destination lists.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-select-lists.png" alt="List selection dialog for adding contacts" width="563"></div>
{% endstep %}

{% step %}
**Confirm Action**

Click **Add To Lists** to complete the operation.
{% endstep %}
{% endstepper %}

#### Remove from Lists

{% stepper %}
{% step %}
**Select Contacts**

Mark contacts to remove from lists.

Click **More Actions** → **Remove from lists**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-bulk-remove.png" alt="Bulk action menu showing Remove from lists option" width="563"></div>
{% endstep %}

{% step %}
**Choose Lists**

Select which lists to remove contacts from.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-remove-from-lists.png" alt="List selection dialog for removing contacts" width="563"></div>
{% endstep %}

{% step %}
**Confirm Removal**

Click **Remove** to process the action.
{% endstep %}
{% endstepper %}

#### Bulk Unsubscribe

{% stepper %}
{% step %}
**Select Contacts**

Choose contacts to unsubscribe.

Click **More Actions** → **Unsubscribe**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-bulk-unsubscribe.png" alt="Bulk action menu showing Unsubscribe option" width="563"></div>
{% endstep %}

{% step %}
**Confirm Action**

Type 'unsubscribe' to confirm.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-unsubscribe-confirm.png" alt="Confirmation dialog to unsubscribe contacts" width="563"></div>
{% endstep %}

{% step %}
**Process Unsubscribe**

Click **Unsubscribe** to complete.

{% hint style="warning" %}
This action cannot be undone. Contacts must re-subscribe themselves.
{% endhint %}
{% endstep %}
{% endstepper %}

#### Export Contacts

{% stepper %}
{% step %}
**Select for Export**

Choose contacts to export.

Click **More Actions** → **Export**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-export.png" alt="Bulk action menu showing Export option" width="563"></div>
{% endstep %}

{% step %}
**Confirm Export**

Click **Confirm Export**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-export-confirm.png" alt="Confirmation dialog to export contacts" width="563"></div>
{% endstep %}

{% step %}
**Download File**

Check your email for the download link.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-export-email.png" alt="Email notification with download link for exported contacts" width="563"></div>

{% hint style="info" %}
Export includes all contact fields and list memberships.
{% endhint %}
{% endstep %}
{% endstepper %}

#### Bulk Delete

{% stepper %}
{% step %}
**Select for Deletion**

Choose contacts to delete.

Click **More Actions** → **Delete**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-bulk-delete.png" alt="Bulk action menu showing Delete option" width="563"></div>
{% endstep %}

{% step %}
**Confirm Deletion**

Type 'delete' to confirm.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/marketing-contacts-delete-confirm.png" alt="Confirmation dialog to delete contacts with warning" width="563"></div>
{% endstep %}

{% step %}
**Process Deletion**

Click **Delete** to permanently remove contacts.

{% hint style="danger" %}
This action cannot be undone. All contact data will be permanently deleted.
{% endhint %}
{% endstep %}
{% endstepper %}

## Contact Status Management

### Understanding Subscription Status

{% tabs %}
{% tab title="Subscribed" %}
**Active and engaged**

* Can receive marketing emails
* Counted in campaign recipients
* Full access to all features
* Default status for new imports
{% endtab %}

{% tab title="Unsubscribed" %}
**Opted out**

* Cannot receive marketing emails
* Excluded from all campaigns
* Status preserved for compliance
* Can only be changed by contact
{% endtab %}

{% tab title="Pending" %}
**Awaiting confirmation**

* Double opt-in required
* Confirmation email sent
* Cannot receive campaigns yet
* Expires after set period
{% endtab %}

{% tab title="Bounced" %}
**Invalid or unreachable**

* Email address is invalid
* Automatically marked by system
* Excluded from future sends
* Requires manual review
{% endtab %}
{% endtabs %}

## Best Practices

{% hint style="success" %}
**Contact Management Tips**

1. **Regular Cleaning**: Remove bounced and inactive contacts monthly
2. **List Hygiene**: Audit lists quarterly for relevance
3. **Segmentation**: Use filters to create targeted segments
4. **Export Backups**: Regular exports for data safety
5. **Consent Tracking**: Document how consent was obtained
{% endhint %}
