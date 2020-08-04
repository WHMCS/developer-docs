+++
title = "Contact"
weight = 10

+++

The following hooks are provided for Contact related events.

## ContactAdd

Executes as a contact is being added to WHMCS.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| contactid | int |  |
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
| generalemails | bool |  |
| productemails | bool |  |
| domainemails | bool |  |
| invoiceemails | bool |  |
| supportemails | bool |  |
| affiliateemails | bool |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactAdd', 1, function($vars) {
    // Perform hook code here...
});
```

## ContactDelete

Executes on Contact Delete after the contact has been removed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| contactid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactDelete', 1, function($vars) {
    // Perform hook code here...
});
```

## ContactDetailsValidation

Executes on validation of contact details.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | array | The POSTed variables |

#### Response

Return accepts both a `string` or an `array`. Use a string for `single` error message or an `array` of strings for multiple error messages.

#### Example Code

```
<?php

add_hook('ContactDetailsValidation', 1, function($vars) {
    return [
        'Error message feedback error 1',
        'Error message feedback error 2',
    ];
});
```

## ContactEdit

Runs when a contact is edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| contactid | int |  |
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
| domainemails | bool |  |
| generalemails | bool |  |
| invoiceemails | bool |  |
| productemails | bool |  |
| supportemails | bool |  |
| affiliateemails | bool |  |
| olddata | array | An array of the previous contact information |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactEdit', 1, function($vars) {
    // Perform hook code here...
});
```

