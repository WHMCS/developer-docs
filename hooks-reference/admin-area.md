+++
title = "Admin Area"
weight = 10

+++

The following hooks are provided for Admin Area related events.

## AdminAreaClientSummaryActionLinks

Allows returning of links for display on the client summary page in the Action Links section.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int | The id of the user being displayed |

#### Response

An array of links to be displayed.

#### Example Code

```
<?php

add_hook('AdminAreaClientSummaryActionLinks', 1, function($vars) {
    $return = [];

    if ($vars['userid'] == 1) {
        $return[] = '<a href="https://www.whmcs.com/">WHMCS</a>';
        $return[] = '<a href="https://www.enom.com/">eNom</a>';
    }

    return $return;
});
```

## AdminAreaClientSummaryPage

Allows returning of output for display on the client summary page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int | The id of the user being displayed |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php

add_hook('AdminAreaClientSummaryPage', 1, function($vars) {
    return 'This message will be output on the Client Summary page. I can add HTML here';
});
```

## AdminAreaPage

Runs on every admin area page load. All template variables defined at the time the hook is invoked are made available to this hook point. This can vary by page. The list below is not an exhaustive list.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| charset | string | System charset setting eg. UTF-8 |
| template | string | The admin template being used |
| pagetemplate | string | The template for the current page (if applicable) |
| adminid | int | The currently logged in admin user ID |
| admin_username | string | The username of the current admin user |
| admin_notes | string | The private notes for the current admin user |
| admin_perms | array | The permissions of the current admin user |
| addon_modules | array | A list of add-on modules the current admin user has access to |
| filename | string | The name of the file being called |
| pagetitle | string | The title of the current page |
| helplink | string | The documentation url for the current page |
| sidebar | string | The sidebar output |
| minsidebar | bool | Returns true if the sidebar is minimised |
| jquerycode | string | jQuery code for the current page |
| jscode | string | Javascript code for the current page |
| datepickerformat | string | The format defined for dates in the admin area |
| adminsonline | string | A list of currently online admin users |

#### Response

Accepts a return of key/value pairs to be made available to the template layer as additional template variables.

#### Example Code

```
<?php
add_hook('AdminAreaPage', 1, function($vars) {
    $extraVariables = [];
    if ($vars['filename'] == 'index.php') {
        $extraVariables['newVariable1'] = 'thisValue';
        $extraVariables['newVariable2'] = 'thatValue';
    }
    return $extraVariables;
});
```

## AdminAreaViewQuotePage

Executes as the quote is being viewed.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| quoteid | int |  |

#### Response

Return the HTML to display on the View Quote page.

#### Example Code

```
<?php

add_hook('AdminAreaViewQuotePage', 1, function($vars) {
    return 'This will be displayed on the Admin Area View Quote Page. I can add HTML here';
});
```

## AdminClientDomainsTabFields

Executes when a domain is being viewed in the Admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | the id of the domain being loaded |

#### Response

An array of key -> value parameters to output additional fields as required.

#### Example Code

```
<?php

add_hook('AdminClientDomainsTabFields', 1, function($vars) {
    return [
        'Additional Field 1' => '<input type="text" name="additionalFieldOne" class="form-control input-150" />',
        'Additional Field 2' => '<input type="text" name="additionalFieldTwo" class="form-control input-150" />',
    ];
});
```

## AdminClientDomainsTabFieldsSave

Executes when the Domains tab in the Admin area is being saved. Receives all the $_REQUEST parameters as variables.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php

//Obtain the values defined in the AdminClientProfileTabFields hook point and save them as required
add_hook('AdminClientDomainsTabFieldsSave', 1, function($vars) {
    $domainId = $vars['id'];
    $additionalFieldOne = $_REQUEST['additionalFieldOne'];
    $additionalFieldTwo = $_REQUEST['additionalFieldTwo'];

    //Save the data here
});
```

## AdminClientFileUpload

Executes as a client file is being uploaded from the Client Summary.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| title | string |  |
| filename | string | The filename as stored on the server |
| origfilename | string | The original filename |
| adminonly | bool |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientFileUpload', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientProfileTabFields

Executes when a client profile is being viewed in the Admin area.

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
| country | string |  |
| phonenumber | string |  |
| password | string | The encrypted password for the user |
| currency | int | The id of the currency |
| notes | string |  |
| status | string |  |
| taxexempt | bool |  |
| latefeeoveride | bool |  |
| overideduenotices | bool |  |
| separateinvoices | bool |  |
| disableautocc | bool |  |
| emailoptout | bool |  |
| marketing_emails_opt_in | bool |  |
| overrideautoclose | bool |  |
| language | string |  |
| billingcid | int |  |
| groupid | int | The id of the client group |
| allow_sso | bool | Is Single Sign on enabled for the client? |
| olddata | array | An array of the previous contact information |
| authmodule | string | The 2Factor Auth Module enabled for the user |
| authdata | string | The 2Factor Auth Data for the user |
| email_verified | bool |  |

#### Response

An array of key -> value parameters to output additional fields as required.

#### Example Code

```
<?php

add_hook('AdminClientProfileTabFields', 1, function($vars) {
    return [
        'Additional Field 1' => '<input type="text" name="additionalFieldOne" class="form-control input-150" />',
        'Additional Field 2' => '<input type="text" name="additionalFieldTwo" class="form-control input-150" />',
    ];
});
```

## AdminClientProfileTabFieldsSave

Executes when the Profile in the Admin area is being saved. Receives all the $_REQUEST parameters as variables.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php

//Obtain the values defined in the AdminClientProfileTabFields hook point and save them as required
add_hook('AdminClientProfileTabFieldsSave', 1, function($vars) {
    $userId = $vars['userid'];
    $additionalFieldOne = $_REQUEST['additionalFieldOne'];
    $additionalFieldTwo = $_REQUEST['additionalFieldTwo'];

    //Save the data here
});
```

## AdminClientServicesTabFields

Executes when a service is being viewed in the Admin area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| id | int | the id of the service being loaded |

#### Response

An array of key -> value parameters to output additional fields as required.

#### Example Code

```
<?php
add_hook('AdminClientServicesTabFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminClientServicesTabFieldsSave

Executes when the Services tab in the Admin area is being saved. Receives all the $_REQUEST parameters as variables.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminClientServicesTabFieldsSave', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminHomepage

Allows returning of output for display on the admin homepage

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('AdminHomepage', 1, function($vars) {
    return 'This message will appear on the Admin Homepage';
});
```

## AdminLogin

Executes post successful authentication of an admin user

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| adminid | int |  |
| username | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminLogin', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminLogout

Executes on Admin log out

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| adminid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminLogout', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminPredefinedAddons

Executes as the Create New Addon page is loaded.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

array of values used for the creation of predefined addon panels. See example for array structure.

#### Example Code

```
<?php

/**
 * Setting the 'icontype' value to 'fa' allows for the use of Font Awesome icons.
 */
add_hook('AdminPredefinedAddons', 1, function () {
    return [
        [
            'module' => 'yourmodule',
            'icontype' => 'fa',
            'iconvalue' => 'fad fa-cube',
            'labeltype' => 'success',
            'labelvalue' => 'Sample Label',
            'paneltitle' => 'Sample Title',
            'paneldescription' => 'Description to be displayed in the Predefined Addon panel.',
            'addonname' => 'On addon creation, this value will be used as the addon name.',
            'addondescription' => 'On addon creation, this value will be used as the addon description.',
            'welcomeemail' => 'Hosting Account Welcome Email',
            'featureaddon' => 'Name of feature addon as stored in the database.',
        ],
    ];
});

/**
 * Alternatively the 'icontype' value can be set to 'url' to allow for the use of URLs and file paths.
 */
add_hook('AdminPredefinedAddons', 1, function () {
    return [
        [
            'module' => 'yourmodule',
            'icontype' => 'url',
            'iconvalue' => 'https://www.whmcs.com/images/logo.png',
            'paneltitle' => 'Sample Title',
            'paneldescription' => 'Description to be displayed in the Predefined Addon panel.',
            'addonname' => 'On addon creation, this value will be used as the addon name.',
            'addondescription' => 'On addon creation, this value will be used as the addon description.',
            'featureaddon' => 'Name of feature addon as stored in the database.',
        ],
    ];
});
```

## AdminProductConfigFields

Executes as a product is being edited.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int |  |

#### Response

An array of key -> value pairs to display on the Other tab.

#### Example Code

```
<?php
add_hook('AdminProductConfigFields', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminProductConfigFieldsSave

Executes as a product is being saved. Access The Request variables to save custom config fields.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| pid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminProductConfigFieldsSave', 1, function($vars) {
    // Perform hook code here...
});
```

## AdminServiceEdit

Executes when the Service has been edited by an Admin. After the changes have been made.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userid | int |  |
| serviceid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AdminServiceEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## AuthAdmin

Executes during Admin form-based password authentication

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| userInput | string | The user-provided password value |
|  | \WHMCS\User\Admin | The admin attempting to authenticate |

#### Response

TRUE on success FALSE on failure

#### Example Code

```
<?php

// EXAMPLE SERVICE CLASS ONLY; NOT VALID FOR PRODUCTION
class MyAuthService
{
    public static function getAdminHash($adminUniqueId)
    {
        $hashes = [
            'admin@localhost.local' => '$2y$10$VKrc/52lKfl1FZWFTsmUpeORk18adQAulXlv634q6wkMseBDGbilO'
        ];

        if (array_key_exists($adminUniqueId, $hashes)) {
            return $hashes[$adminUniqueId];
        }

        return null;
    }
}

add_hook(
    'AuthAdmin',
    0,
    function ($userInput, WHMCS\User\Admin $admin) {
        $adminUniqueId = $admin->email;
        $adminHash = MyAuthService::getAdminHash($adminUniqueId);
        if (!$adminHash) {
            return false;
        }

        return password_verify($userInput, $adminHash);
    }
);
```

## AuthAdminApi

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| $userInput | | |
| $admin | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('AuthAdminApi', 1, function($vars) {
    // Perform hook code here...
});
```

## InvoiceCreationAdminArea

Executes as an invoice is being created in the admin area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| source | string | When the invoice is being created |
| user | int|string | The id of the user completing the action dependant on source |
| invoiceid | int | The id of the newly created invoice |
| status | string | The status of the newly created invoice |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('InvoiceCreationAdminArea', 1, function($vars) {
    // Perform hook code here...
});
```

## PreAdminServiceEdit

Executes as the service is being saved, before any changes have been made.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('PreAdminServiceEdit', 1, function($vars) {
    // Perform hook code here...
});
```

## ViewOrderDetailsPage

Executes as the order details page is being displayed

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| orderid | int |  |
| ordernum | int |  |
| userid | int |  |
| amount | float |  |
| paymentmethod | string |  |
| invoiceid | int |  |
|  | string | status |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ViewOrderDetailsPage', 1, function($vars) {
    // Perform hook code here...
});
```

