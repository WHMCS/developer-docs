+++
next = "/themes/variables/"
prev = "/themes/navigation/"
title = "Sidebars"
toc = true
weight = 45

+++

## Sidebars

{{% notice tip %}}
This guide assumes you are already familiar with creating and using [Hook files in WHMCS](/hooks/).
{{% /notice %}}

There are two sidebars in WHMCS's client area. The primary sidebar contains sidebar elements that are displayed above the body content when in responsive mode. The secondary sidebar contains sidebar elements that are displayed below the body content when in responsive mode. In desktop mode, there will be no noticeable difference between primary and secondary sidebar items.

The sidebar elements and panels are controlled in a programmatic way, allowing modules and hooks to dynamically interact with the sidebar items.

The look and feel of the navigation bar can be customised via the `/header.tpl` and `/includes/navbar.tpl` system theme template files.

## Finding a Sidebar Name

Every sidebar menu item has a unique name that is used to reference it. You will need this name in order to manipulate it. To make it easier, we have made the name of each sidebar menu item available in the HTML source of the page, which means it can be retrieved using the *Inspect Element* option available in most modern browsers. For example:

![Sidebar Menus: Finding a Sidebar Name](find-sidebar-name.png)

Once you have the menu item name that you wish to manipulate, which in the example above is `Account Details`, you can manipulate it as described below.

{{% notice tip %}}
The client area's sidebar menu system is defined in a tree structure. Each menu item has one parent item and can have many child items. To manipulate a menu item within a sidebar panel, you first need to retrieve the parent menu item, which in the case above is `Account`, followed by the `Account Details` menu item within it.
{{% /notice %}}

## Changing the Text Label of a Sidebar Item

All sidebar menu items that are supplied by default use display names controlled by language file. Simply search in your active language file for the text you see in the menu item label, and you can adjust or change it there as required.

Alternatively, you can manipulate the display text via a hook as follows:

```
<?php

use WHMCS\View\Menu\Item as MenuItem;

add_hook('ClientAreaPrimarySidebar', 1, function(MenuItem $primarySidebar)
{
    $primarySidebar->getChild("My Account")
        ->getChild("Billing Information")
        ->setLabel("Custom Text Here");
});
```

Notice how in the above we first retrieve the `Support` menu item, followed by the `Announcements` menu item, which is a child within that. The same logic should be applied to all dropdown menu items.

## Changing where a Sidebar Item Points To

You can change where a menu item points using the `setUri` method. For example, if you use an external system to control announcements, you could do something like the following:

```
<?php

use WHMCS\View\Menu\Item as MenuItem;

add_hook('ClientAreaPrimarySidebar', 1, function(MenuItem $primarySidebar)
{
    $primarySidebar->getChild('My Account')
        ->getChild('Billing Information')
        ->setUri('https://www.example.com/billingInfo');
});
```

## Rearranging Sidebar Items

You can change the display order of menu items as follows:

```
<?php

use WHMCS\View\Menu\Item as MenuItem;

add_hook('ClientAreaPrimarySidebar', 1, function(MenuItem $primarySidebar)
{
    $primarySidebar->getChild('My Account')
        ->getChild('Billing Information')
        ->setOrder(25); // default menu items have orders 10, 20, 30, etc...
});
```

The following helpers are also available:

```
// Moves a menu item up one position
$primaryNavbar->getChild('My Account')->getChild('Billing Information')->moveUp();
// Moves a menu item down one position
$primaryNavbar->getChild('My Account')->getChild('Billing Information')->moveDown();
// Moves a menu item to the first position
$primaryNavbar->getChild('My Account')->getChild('Billing Information')->moveToFront();
// Moves a menu item to the last position
$primaryNavbar->getChild('My Account')->getChild('Billing Information')->moveToBack();
```

## Adding an Additional Sidebar Menu Item

To add an additional item to a menu, check that the sidebar exists on the particular page before specifying it. You can add additional menu items as follows:

```
<?php

use WHMCS\View\Menu\Item as MenuItem;

add_hook('ClientAreaPrimarySidebar', 1, function (MenuItem $primarySidebar)

{
    if (!is_null($primarySidebar->getChild('My Account'))) {
        $primarySidebar->getChild('My Account')
            ->addChild('Mailing List Subscription Prefs')
                ->setLabel('Subscription Preferences')
                ->setUri('subscriptionprefs.php')
                ->setOrder(100);
    }
});
```

## Hiding or Removing a Sidebar Menu Item

You can remove a menu item as follows:

```
<?php

use WHMCS\View\Menu\Item as MenuItem;

add_hook('ClientAreaPrimarySidebar', 1, function(MenuItem $primarySidebar)
{
    $primarySidebar->getChild('My Account')
        ->removeChild('Billing Information');
});
```
