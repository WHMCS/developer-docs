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

Executes prior to rendering the Client Area Homepage panels. This can be used to manipulate and add additional panels. For more information on working with Homepage Panels, and further examples, please see [Working with ClientArea Homepage Panels](http://docs.whmcs.com/Working_With_Client_Area_Home_Page_Panels)

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
            'icon' => 'fa-calendar-o', //see http://fortawesome.github.io/Font-Awesome/icons/
            'order' => '99',
            'extras' => array(
                'color' => 'pomegranate', //see Panel Accents in template styles.css
                'btn-link' => 'http://www.whmcs.com',
                'btn-text' => Lang::trans('go'),
                'btn-icon' => 'fa-arrow-right',
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
            'icon' => 'fa-calendar-o',
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
            'icon' => 'fa-calendar-o',
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

Executes when rendering the client area product details page prior to module template invokation allowing to define additional template parameters.

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
| userid | int | The id of the newly created client. |

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
            'icon' => 'fa-calendar-o',
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
            'icon' => 'fa-calendar-o',
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

