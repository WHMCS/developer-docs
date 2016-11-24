+++
next = "/themes/testing"
prev = "/themes/getting-started"
title = "Navigation"
toc = true
weight = 40

+++

There are two navigation bars in WHMCS’ client area. The primary navigation bar contains the bulk of the menu and floats to the left of the secondary navigation bar. The secondary navigation bar contains user-specific items and changes if a client is logged in to WHMCS. When a client is not logged in then the secondary navigation contains a login link, and when a client is logged in then the secondary menu contains links to the client’s account.

Responsive mode is activated when WHMCS’ client area is viewed on a smaller screen device such as a phone or tablet. At that point, WHMCS will collapse the navbar into a fold out menu.

The navigation bar elements are controlled in a programmatic way allowing modules and hooks to dynamically interact with the navigation menu elements.

The look and feel of the navigation bar can be customised via the header.tpl and navbar.tpl (located in /includes/) template files.

To change the items within a menu, please refer to the [Editing Client Area Menus](#) documentation.

## Sidebars

There are two sidebars in WHMCS’ client area. The primary sidebar contains sidebar elements that are displayed above the body content when in responsive mode. The secondary sidebar contains sidebar elements that are displayed below the body content when in responsive mode. In desktop mode, there will be no noticeable difference between primary and secondary sidebar items.

The sidebar elements and panels are controlled in a programmatic way allowing modules and hooks to dynamically interact with the sidebar items.

The look and feel of the sidebar can be customised via the header.tpl and sidebar.tpl (located in /includes/) template files.

To change the items within a sidebar, please refer to the [Editing Client Area Menus](#) documentation.
