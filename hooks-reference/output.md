+++
title = "Output"
weight = 10

+++

The following hooks are provided for Output related events.

## AdminAreaFooterOutput

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

Accepts HTML to be output before the closing body tag of the admin area output

#### Example Code

```
<?php

add_hook('AdminAreaFooterOutput', 1, function($vars) {
    return <<<HTML
<b>This is a custom output on the footer</b>
<script type="text/javascript">
    //custom javascript here
</script>
HTML;
});
```

## AdminAreaHeadOutput

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

Accepts HTML to be output within the head tag of the admin area output

#### Example Code

```
<?php

add_hook('AdminAreaHeadOutput', 1, function($vars) {
    return <<<HTML
    <link href="path/to/custom/css/custom.css" rel="stylesheet" type="text/css" />
<script type="text/javascript">
//custom javascript here
</script>
HTML;

});
```

## AdminAreaHeaderOutput

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

Accepts HTML to be output within the body tag of the admin area output

#### Example Code

```
<?php

add_hook('AdminAreaHeaderOutput', 1, function($vars) {
    $return = '';
    if (array_key_exists('project_management', $vars['addon_modules'])) {
        $return = '<b>This is a custom output on the header when Project Management is enabled</b>';
    }
    return $return;
});
```

## AdminInvoicesControlsOutput

Allows returning of output for display on the invoice edit page

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| invoiceid | int |  |
| userid | int |  |
| subtotal | float |  |
| tax | float |  |
| tax2 | float |  |
| credit | float |  |
| total | float |  |
| balance | float |  |
| taxrate | float |  |
| taxrate2 | float |  |
| paymentmethod | string |  |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php

add_hook('AdminInvoicesControlsOutput', 1, function($vars) {
    $return = '';

    if ($vars['paymentmethod'] == 'mypaymentmethod') {
        $return = "<br />Field 1 Value <input type=\"text\" name=\"myPaymentMethodName\" value=\"xyz\" class=\"form-control input-150\" />";
    }
    return $return;
});
```

## ClientAreaDomainDetailsOutput

Allows returning of output for display in the client area domain details page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | \WHMCS\Domain\Domain | A domain object representing the domain being rendered. |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php

add_hook('ClientAreaDomainDetailsOutput', 1, function($domain) {
    $domainName = $domain->domain;
    $clientModel = $domain->client;
    $domainStatus = $domain->status;
    $clientName = $clientModel->firstName . ' ' . $clientModel->lastName;
    return 'You can place any HTML here that will be output in the $hookOutput smarty variable array';
});
```

## ClientAreaFooterOutput

Executes when a client area page is being output. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| companyname | string |  |
| logo | string |  |
| systemurl | string |  |
| charset | string |  |
| pagetitle | string |  |
| filename | string |  |
| template | string |  |
| language | string |  |
| LANG | array | Active language translation strings |
| todaysdate | string | Human friendly formatted version of todays date |
| date_day | string | Current day of the month |
| date_month | string | Current month |
| date_year | string | Current year |
| WEB_ROOT | string | The web path to the WHMCS doc root |
| BASE_PATH_CSS | string |  |
| BASE_PATH_JS | string |  |
| BASE_PATH_FONTS | string |  |
| BASE_PATH_IMG | string |  |
| token | string | CSRF token value |
| servedOverSsl | bool | True if page was loaded via `https://` |

#### Response

Return HTML to be output before the closing body tag of the page output.

#### Example Code

```
<?php

add_hook('ClientAreaFooterOutput', 1, function($vars) {
    $language = $vars['language'];
    $sslPage = $vars['servedOverSsl'];
    return '<b>This is a custom output on the footer</b>';
});
```

## ClientAreaHeadOutput

Executes when a client area page is being output. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| companyname | string |  |
| logo | string |  |
| systemurl | string |  |
| charset | string |  |
| pagetitle | string |  |
| filename | string |  |
| template | string |  |
| language | string |  |
| LANG | array | Active language translation strings |
| todaysdate | string | Human friendly formatted version of todays date |
| date_day | string | Current day of the month |
| date_month | string | Current month |
| date_year | string | Current year |
| WEB_ROOT | string | The web path to the WHMCS doc root |
| BASE_PATH_CSS | string |  |
| BASE_PATH_JS | string |  |
| BASE_PATH_FONTS | string |  |
| BASE_PATH_IMG | string |  |
| token | string | CSRF token value |
| servedOverSsl | bool | True if page was loaded via `https://` |

#### Response

Return HTML to be output within the HEAD tags of the page output.

#### Example Code

```
<?php

add_hook('ClientAreaHeadOutput', 1, function($vars) {
    $template = $vars['template'];
    return <<<HTML
    <link href="path/to/custom/css/custom.css" rel="stylesheet" type="text/css" />
<script type="text/javascript">
//custom javascript here
</script>
HTML;

});
```

## ClientAreaHeaderOutput

Executes when a client area page is being output. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| companyname | string |  |
| logo | string |  |
| systemurl | string |  |
| charset | string |  |
| pagetitle | string |  |
| filename | string |  |
| template | string |  |
| language | string |  |
| LANG | array | Active language translation strings |
| todaysdate | string | Human friendly formatted version of todays date |
| date_day | string | Current day of the month |
| date_month | string | Current month |
| date_year | string | Current year |
| WEB_ROOT | string | The web path to the WHMCS doc root |
| BASE_PATH_CSS | string |  |
| BASE_PATH_JS | string |  |
| BASE_PATH_FONTS | string |  |
| BASE_PATH_IMG | string |  |
| token | string | CSRF token value |
| servedOverSsl | bool | True if page was loaded via `https://` |

#### Response

Return HTML to be output at the top of the body tag of the page output.

#### Example Code

```
<?php

add_hook('ClientAreaHeaderOutput', 1, function($vars) {
    $return = '';
    if (
        $vars['filename'] == 'index.php'
        && isset($_REQUEST['m'])
        && $_REQUEST['m'] == 'project_management'
    ) {
        $return = '<b>This is a custom output on the header when in the client area for Project Management</b>';
    }
    return $return;
});
```

## ClientAreaProductDetailsOutput

Allows returning of output for display in the client area product details page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| service | \WHMCS\Service\Service | A service object representing the service being rendered. |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php

add_hook('ClientAreaProductDetailsOutput', 1, function($service) {
    if (!is_null($service)) {
        $orderID = $service['service']->orderId;
        return 'OrderID: ' . $orderID;
    }
    return '';
});
```

## FormatDateForClientAreaOutput

Allows for transformation of a date prior to output within the Client Area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| date | \Carbon | A Carbon object representing the date/time. |

#### Response

Return a string containing the formatted date to display.

#### Example Code

```
<?php

add_hook('FormatDateForClientAreaOutput', 1, function ($vars) {
    // Perform hook code here...
});
```

## FormatDateTimeForClientAreaOutput

Allows for transformation of a date/time prior to output within the Client Area.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| date | \Carbon | A Carbon object representing the date/time. |

#### Response

Return a string containing the formatted date and time to display.

#### Example Code

```
<?php

add_hook('FormatDateTimeForClientAreaOutput', 1, function ($vars) {
    // Perform hook code here...
});
```

## ReportViewPostOutput

Executes as a report is being displayed, after the output occurs

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| report | string |  |
| moduleType | string |  |
| moduleName | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ReportViewPostOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ReportViewPreOutput

Executes as a report is being displayed, before the output occurs

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| report | string |  |
| moduleType | string |  |
| moduleName | string |  |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ReportViewPreOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ShoppingCartCheckoutOutput

Allows returning of output for display on the Shopping Cart Checkout page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| cartData | array |  |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('ShoppingCartCheckoutOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ShoppingCartConfigureProductAddonsOutput

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| billingCycle | | |
| selectedAddons | | |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ShoppingCartConfigureProductAddonsOutput', 1, function($vars) {
    // Perform hook code here...
});
```

## ShoppingCartViewCartOutput

Allows returning of output for display on the Shopping Cart View Cart page.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| cartData | array |  |

#### Response

Return the HTML to be output on the page.

#### Example Code

```
<?php
add_hook('ShoppingCartViewCartOutput', 1, function($vars) {
    // Perform hook code here...
});
```

