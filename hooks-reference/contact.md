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
| subaccount | bool |  |
| password | string |  |
| permissions | string | A comma separated list of allowed permissions for a sub-account |
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

## ContactChangePassword

Executed when a change of password occurs for a contact.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| contactid | int |  |
| password | string | The new password |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ContactChangePassword', 1, function($vars) {
    // Perform hook code here...
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
| subaccount | bool |  |
| permissions | string | A comma separated list of permissions if the contact is a sub-account |
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

