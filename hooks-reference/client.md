+++
title = "Client"
weight = 10

+++

The following hooks are provided for Client related events.

## AfterClientMerge

Executes after a client merge has completed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| toUserID | int | The id of the user being merged into. |
| fromUserID | int | The id of the user being merged from. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AfterClientMerge', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAdd

Executes as a client is being added to WHMCS.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| client_id | int | The id of the client that has been added |
| user_id | int | The user id the client belongs to |
| ~~userid~~ | ~~int~~ | ~~The id of the client that has been added~~ |
| firstname | string |  |
| lastname | string |  |
| companyname | string |  |
| email | string |  |
| address1 | string |  |
| address2 | string |  |
| city | string |  |
| state | string |  |
| postcode | string |  |
| country | string |  |
| phonenumber | string |  |
| tax_id | string |  |
| password | string |  |
| customFields | array |  |
| taxexempt | bool |  |
| latefeeoveride | bool |  |
| overideduenotices | bool |  |
| separateinvoices | bool |  |
| disableautocc | bool |  |
| emailoptout | bool |  |
| marketing_emails_opt_in | bool |  |
| overrideautoclose | bool |  |
| notes | string |  |
| groupid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAlert

Executes when Client Alerts are being defined

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | \WHMCS\User\Client | The client model |

#### Response

Return a new alert object for rendering.

#### Example Code

```
<?php

use WHMCS\User\Alert;

add_hook('ClientAlert', 1, function($client) {
    $firstName = $client->firstName;
    $lastName = $client->lastName;
    return new Alert(
        "This is a test notification for {$firstName} {$lastName}",
        'info' //see http://getbootstrap.com/components/#alerts
    );
});
```

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

## ClientClose

Executes after a client has been closed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientClose', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientDelete

DEPRECATED (since 8.0.0-beta.1): See PreDeleteClient hook as replacement.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientDetailsValidation

Executes before adding a client or updating a client through the Admin or Client area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| firstname | string | The client's firstname |
| lastname | string | The client's lastname |
| companyname | string | The client's company, if entered |
| email | string | The client's email |
| address1 | string | The client's address1 |
| address2 | string | The client's address2, if entered |
| city | string | The client's city |
| state | string | The client's state |
| postcode | string | The client's postcode/zipcode |
| country | string | The client's country (2 character code) |
| phonenumber | string | The client's phone number |
| tax_id | string | The client's tax ID |
| paymentmethod | string | If selected, the client's default payment method |
| customfield | string | An array of Key => Value pairs |
| securityqid | int | Only from Admin Area or when registering |
| securityqans | string | Only from Admin Area or when registering |

#### Response

Return accepts both a `string` or an `array`. Use a string for `single` error message or an `array` of strings for multiple error messages.

#### Example Code

```
<?php

add_hook('ClientDetailsValidation', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
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

## PreDeleteClient

Executes immediately before a client is deleted

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreDeleteClient', 1, function($vars) {
    // Perform hook code here...
});
```

