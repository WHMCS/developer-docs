+++
title = "Client"
weight = 10

+++

The following hooks are provided for Client related events.

## ClientChangePassword

Executed when a change of password occurs for a client.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int | The ID of the Client being updated |
| password | string | The new password |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientEdit

Executes when a client is edited through the Client Area, Admin Area, or API.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| uuid | string |  |
| firstname | string |  |
| lastname | string |  |
| companyname | string |  |
| email | string |  |
| address1 | string |  |
| address2 | string |  |
| city | string |  |
| state | string |  |
| postcode | string |  |
| country | string | Two-letter ISO code. |
| phonenumber | string |  |
| currency | int | The id of the currency |
| notes | string |  |
| status | string |  |
| taxexempt | bool |  |
| latefeeoveride | bool | Used to prevent overdue invoices from including late fees. |
| overideduenotices | bool | Used to disable overdue email notices for clients. |
| separateinvoices | bool | Prevent items with the same due date and payment method from being grouped into a single invoice. |
| disableautocc | bool | Prevent invoices that are due via a merchant gateway from being automatically attempted for capture. |
| emailoptout | bool | Prevent emails sent via the Email Campaigns (formerly mass mail) or Email Marketer tools. |
| marketing_emails_opt_in | bool |  |
| overrideautoclose | bool |  |
| language | string |  |
| billingcid | int | The main contact for billing-related items. |
| groupid | int | The id of the client group |
| allow_sso | bool | Whether Single Sign-On is enabled for the client. |
| olddata | array | An array of the previous contact information |
| authmodule | string | The Two-Factor Authentication module enabled for the user. |
| authdata | string | The Two-Factor Authentication data for the user. |
| email_verified | bool | Whether the client has verified their email address. |
| isOptedInToMarketingEmails | bool |  |
| email_preferences[affiliate] | bool | Receives affiliate communications. |
| email_preferences[domain] | bool | Whether the client receives registration or transfer confirmations and renewal notices. |
| email_preferences[general] | bool | Whether the client receives account-related email. |
| email_preferences[invoices] | bool | Whether the client receives new invoices, reminders, and overdue notices. |
| email_preferences[product] | bool | Receives Welcome Emails, Suspension & Other Lifecycle Notifications. |
| email_preferences[support] | bool | Receives CC of all support ticket communications. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientEdit', 1, function($vars) {
    // Perform hook code here...
});
```

