+++
title = "Client Area Interface"
weight = 10

+++

The following hooks are provided for Client Area Interface related events.

## ClientAreaDomainDetails

Executes when the domain details page is loaded within the client area. This hook runs regardless of domain status, so be sure to check for the appropriate statuses if required.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| domain | \WHMCS\Domain\Domain | A domain object representing the domain being rendered. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaDomainDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaHomepage

Executes on rendering of the client area homepage.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

Return HTML to be output on the page.

#### Example Code

```
<?php
add_hook('ClientAreaHomepage', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaHomepagePanels

Executes prior to rendering the Client Area Homepage panels. This can be used to manipulate and add additional panels. For more information on working with Homepage Panels, and further examples, please see [Client Area Homepage Panels](https://go.whmcs.com/1965/client-area-homepage-panels)

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| item | \WHMCS\View\Menu\Item |  |

#### Response

No response supported

#### Example Code

```
<?php

add_hook('ClientAreaHomepagePanels', 1, function($homePagePanels) {
    $newPanel = $homePagePanels->addChild(
        'unique-css-name',
        array(
            'name' => 'Friendly Name',
            'label' => 'Translated Language String',
            'icon' => 'fas fa-calendar-alt', //see http://fortawesome.github.io/Font-Awesome/icons/
            'order' => '99',
            'extras' => array(
                'color' => 'pomegranate', //see Panel Accents in template styles.css
                'btn-link' => 'https://www.whmcs.com',
                'btn-text' => Lang::trans('go'),
                'btn-icon' => 'fas fa-arrow-right',
            ),
        )
    );
// Repeat as needed to add enough children
    $newPanel->addChild(
        'unique-css-name-id1',
        array(
            'label' => 'Panel Row Text Goes Here',
            'uri' => 'index.php?m=yourmodule',
            'order' => 10,
        )
    );
});
```

## ClientAreaNavbars

Executes when generating the navigation bars in the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaNavbars', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPage

Executes on all pages of the client area and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPage', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAddContact

Executes on the client area add contact page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageAddContact', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAddFunds

Executes on the client area add funds page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageAddFunds', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAddonModule

Executes on client pages created by an addon module and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageAddonModule', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAffiliates

Executes on the client area affiliates page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageAffiliates', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageAnnouncements

Executes on the client area announcements page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageAnnouncements', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageBanned

Executes on the banned user page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageBanned', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageBulkDomainManagement

Executes on the client area bulk domain management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageBulkDomainManagement', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCancellation

Executes on the client area cancellation request page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageCancellation', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCart

Executes on the shopping cart page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageCart', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageChangePassword

Executes on the client area change password page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageChangePassword', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageConfigureSSL

Executes on the client area SSL configuration page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageConfigureSSL', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageContact

Executes on the contact form page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageContact', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageContacts

Executes on the client area contacts/sub-accounts management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageContacts', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCreditCard

Executes on the client area manage credit card page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageCreditCard', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageCreditCardCheckout

Executes on the credit card payment page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageCreditCardCheckout', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainAddons

Executes on the client area domain add-ons page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainAddons', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainContacts

Executes on the client area domain WHOIS contact information page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainContacts', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainDNSManagement

Executes on the client area domain DNS Host Record management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainDNSManagement', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainDetails

Executes on the client area domain overview page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainEPPCode

Executes on the client area domain EPP Code page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainEPPCode', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainEmailForwarding

Executes on the client area domain Email Forwarding rules page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainEmailForwarding', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomainRegisterNameservers

Executes on the client area domain Register Private Nameservers page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomainRegisterNameservers', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDomains

Executes on the client area domains list page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDomains', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageDownloads

Executes on the client area downloads page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageDownloads', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageEmails

Executes on the client area email history page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageEmails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageHome

Executes on the client area homepage and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageHome', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageInvoices

Executes on the client area invoices page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageInvoices', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageKnowledgebase

Executes on the client area knowledgebase page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageKnowledgebase', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageLogin

Executes on the login page of the client area. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php

add_hook('ClientAreaPageLogin', 1, function($vars) {
    $extraVariables = [
        'newVariable1' => 'thisValue',
        'newVariable2' => 'thatValue',
    ];
    return $extraVariables;
});
```

## ClientAreaPageLogout

Executes on the client area logout page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageLogout', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageMassPay

Executes on the client area mass invoice payment page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageMassPay', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageNetworkIssues

Executes on the client area network issues page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageNetworkIssues', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPagePasswordReset

Executes on the client area password reset page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPagePasswordReset', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageProductDetails

Executes on the client area product overview page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageProductDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageProductsServices

Executes on the client area product and services list page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageProductsServices', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageProfile

Executes on the client area profile page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageProfile', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageQuotes

Executes on the client area quotes page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageQuotes', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageRegister

Executes on the client registration page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageRegister', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageSecurity

Executes on the client area security page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageSecurity', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageServerStatus

Executes on the client area server status page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageServerStatus', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageUnsubscribe

Executes on the email unsubscribe page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageUnsubscribe', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageUpgrade

Executes on the client area upgrade/downgrade page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageUpgrade', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewEmail

Executes on the client area view email page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageViewEmail', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewInvoice

Executes on the client area view invoice page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageViewInvoice', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPageViewQuote

Executes on the client area view quote page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPageViewQuote', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPaymentMethods

Executes on the client area payment methods management page and accepts a return of key/value pairs to be made available as additional Smarty template parameters. Input parameters include all currently defined template variables. The following is a list of template variables common to all pages. Additional variables will vary depending upon the page being rendered.

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

A key/value pair array of additional template variables to define.

#### Example Code

```
<?php
add_hook('ClientAreaPaymentMethods', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaPrimaryNavbar

Executes when generating the primary navigation bar in the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | \WHMCS\View\Menu\Item | The currently defined items so further additions can be made |

#### Response

No response supported

#### Example Code

```
<?php

add_hook('ClientAreaPrimaryNavbar', 1, function($primaryNavbar) {
    /** @var \WHMCS\View\Menu\Item $primaryNavbar */
    $newMenu = $primaryNavbar->addChild(
        'uniqueMenuItemName',
        array(
            'name' => 'Home',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'clientarea.php',
            'order' => 99,
            'icon' => 'fas fa-calendar-alt',
        )
    );
    $newMenu->addChild(
        'uniqueSubMenuItemName',
        array(
            'name' => 'Item Name 1',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'cart.php',
            'order' => 10,
            'icon' => 'fa-cart-plus',
        )
    );
});
```

## ClientAreaPrimarySidebar

Executes when generating the primary side bar in the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | \WHMCS\View\Menu\Item | The currently defined items so further additions can be made |

#### Response

No response supported

#### Example Code

```
<?php

add_hook('ClientAreaPrimarySidebar', 1, function($primarySidebar) {
    /** @var \WHMCS\View\Menu\Item $primarySidebar */
    $newMenu = $primarySidebar->addChild(
        'uniqueMenuItemName',
        array(
            'name' => 'Home',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'clientarea.php',
            'order' => 99,
            'icon' => 'fas fa-calendar-alt',
        )
    );
    $newMenu->addChild(
        'uniqueSubMenuItemName',
        array(
            'name' => 'Item Name 1',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'cart.php',
            'order' => 10,
            'icon' => 'fa-cart-plus',
        )
    );
});
```

## ClientAreaProductDetails

Executes when the product details page is loaded within the client area. This hook runs regardless of service status, so be sure to check for the appropriate statuses if required.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| service | \WHMCS\Service\Service | A service object representing the service being rendered. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaProductDetails', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaProductDetailsPreModuleTemplate

Executes when rendering the client area product details page prior to module template invocation allowing to define additional template parameters.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| serviceid | int |  |
| groupname | string |  |
| product | string |  |
| modulename | string |  |
| domain | string |  |
| systemStatus | string |  |
| username | string |  |
| password | string |  |

#### Response

Return an array of template parameters to make available to the template.

#### Example Code

```
<?php
add_hook('ClientAreaProductDetailsPreModuleTemplate', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaRegister

Executes after a client has used the register.php file to create a client account.

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| user_id | int | The id of the user owning the newly created client. |
| client_id | int | The id of the newly created client. |
| ~~userid~~ | ~~int~~ | ~~The id of the newly created client.~~ |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaRegister', 1, function($vars) {
    // Perform hook code here...
});
```

## ClientAreaSecondaryNavbar

Executes when generating the secondary navigation bar in the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | \WHMCS\View\Menu\Item | The currently defined items so further additions can be made |

#### Response

No response supported

#### Example Code

```
<?php

add_hook('ClientAreaSecondaryNavbar', 1, function($secondaryNavbar) {
    /** @var \WHMCS\View\Menu\Item $secondaryNavbar */
    $newMenu = $secondaryNavbar->addChild(
        'uniqueMenuItemName',
        array(
            'name' => 'Home',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'clientarea.php',
            'order' => 99,
            'icon' => 'fas fa-calendar-alt',
        )
    );
    $newMenu->addChild(
        'uniqueSubMenuItemName',
        array(
            'name' => 'Item Name 1',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'cart.php',
            'order' => 10,
            'icon' => 'fa-cart-plus',
        )
    );
});
```

## ClientAreaSecondarySidebar

Executes when generating the secondary side bar in the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| N/A | \WHMCS\View\Menu\Item | The currently defined items so further additions can be made |

#### Response

No response supported

#### Example Code

```
<?php

add_hook('ClientAreaSecondarySidebar', 1, function($secondarySidebar) {
    /** @var \WHMCS\View\Menu\Item $secondarySidebar */
    $newMenu = $secondarySidebar->addChild(
        'uniqueMenuItemName',
        array(
            'name' => 'Home',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'clientarea.php',
            'order' => 99,
            'icon' => 'fas fa-calendar-alt',
        )
    );
    $newMenu->addChild(
        'uniqueSubMenuItemName',
        array(
            'name' => 'Item Name 1',
            'label' => Lang::trans('languageStringVariable'),
            'uri' => 'cart.php',
            'order' => 10,
            'icon' => 'fa-cart-plus',
        )
    );
});
```

## ClientAreaSidebars

Executes when generating the side bars in the client area

#### Parameters

| Variable | Type | Notes |
| -------- | ---- | ----- |
| No input parameters for this hook point. |

#### Response

No response supported

#### Example Code

```
<?php
add_hook('ClientAreaSidebars', 1, function($vars) {
    // Perform hook code here...
});
```

