---
title: Audience Management
description: Manage contacts, lists, and segments for targeted email marketing
---

# Audience Management

Build and maintain a healthy email list with Mailtrap's audience management tools. Organize contacts, create segments, and ensure compliance with email regulations.

## Core Features

### [Contacts](../contacts.md)
Manage your subscriber database. Import, export, and organize contacts with custom fields and tags.

## Contact Management

### Adding Contacts
- **Manual Entry**: Add individual contacts
- **CSV Import**: Bulk import from spreadsheets
- **API Integration**: Sync from your application
- **Signup Forms**: Embed forms on your website
- **Third-party Import**: Connect CRM and other tools

### Contact Information
- Email address (required)
- First and last name
- Custom fields
- Tags and labels
- Subscription status
- Engagement history

### Data Management
- Merge duplicate contacts
- Clean invalid emails
- Update contact information
- Export contact data
- Delete inactive contacts

## List Organization

### List Types
- **Master List**: All contacts
- **Active Subscribers**: Engaged contacts
- **Segments**: Filtered subsets
- **Suppression Lists**: Unsubscribed/bounced
- **Test Lists**: For campaign testing

### Segmentation Strategies
- Demographics (age, location, gender)
- Behavior (opens, clicks, purchases)
- Preferences (interests, frequency)
- Engagement level (active, inactive)
- Customer lifecycle stage

## Segmentation

### Basic Segments
```
Segment: "Engaged Users"
Conditions:
- Opened email in last 30 days
- Clicked link in last 60 days
- Not unsubscribed
```

### Advanced Segments
```
Segment: "High-Value Customers"
Conditions:
- Purchase value > $100
- Purchase frequency > 3/year
- Email engagement > 50%
- Account age > 6 months
```

### Dynamic Segments
- Auto-update based on criteria
- Real-time membership changes
- Behavior-triggered updates
- Time-based conditions
- Custom field changes

## Compliance & Privacy

### GDPR Compliance
- Double opt-in process
- Consent tracking
- Data portability
- Right to deletion
- Privacy policy integration

### CAN-SPAM Compliance
- Clear unsubscribe option
- Accurate sender information
- Relevant subject lines
- Physical mailing address
- Honor opt-out requests

### Best Practices
- Regular list cleaning
- Re-engagement campaigns
- Preference centers
- Sunset policies
- Data security

## Growth Strategies

### List Building
- **Quality over Quantity**: Focus on engaged subscribers
- **Clear Value Proposition**: Explain benefits of subscribing
- **Multiple Touchpoints**: Website, social, events
- **Incentives**: Lead magnets, discounts
- **Referral Programs**: Encourage sharing

### Engagement Tactics
- Welcome series for new subscribers
- Personalized content based on interests
- Regular but not overwhelming frequency
- Interactive content and surveys
- Exclusive subscriber benefits

### Retention Methods
- Monitor engagement metrics
- Re-engagement campaigns
- Preference management
- Quality content delivery
- Responsive customer service

## Analytics & Reporting

### List Health Metrics
- **Growth Rate**: New subscribers over time
- **Churn Rate**: Unsubscribes and bounces
- **Engagement Rate**: Active vs. inactive
- **List Quality**: Deliverability metrics
- **Segment Performance**: Engagement by segment

### Contact Analytics
- Individual engagement scores
- Lifetime value calculations
- Interaction history
- Preference tracking
- Predictive analytics

## Import/Export

### Import Options
```csv
email,first_name,last_name,tags
john@example.com,John,Doe,"customer,vip"
jane@example.com,Jane,Smith,"prospect,newsletter"
```

### Export Formats
- CSV for spreadsheets
- JSON for APIs
- XML for integrations
- PDF for reports
- Custom formats via API

## Integration Capabilities

### CRM Integration
- Salesforce sync
- HubSpot connection
- Pipedrive integration
- Custom CRM APIs
- Bi-directional sync

### E-commerce Platforms
- Shopify customer sync
- WooCommerce integration
- Magento connections
- BigCommerce sync
- Custom platform APIs