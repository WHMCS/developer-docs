+++
next = "/themes/css-styling/"
prev = "/themes/nexus-cart/"
title = "Customising"
toc = true
weight = 20

+++

## Customising Themes

{{% notice tip %}}
For information on customising Order Forms, see [Order Form Templates](/themes/order-form-templates/).
{{% /notice %}}

The header and footer system theme template files are common to every page and act as a wrapper around the primary body content. They are an excellent place to begin customising a theme.

* We strongly recommend that you maintain all of the template includes and output variables in the default template files in your custom header and footer. This will help ensure compatibility with addons and extensions you install later.
* Navigation bar and sidebar content is defined within WHMCS and passed to the templates for output. This allows modules and addons to interact with and manipulate these areas of the client area dynamically. The output styling of these is controlled by include files which are explained in more detail below.
* The footer template file includes a number of lines of JavaScript code immediately prior to the closing `</body>` tag. These are essential to the correct operation of the client area. **Do not** remove these lines.
* You may also wish to consider creating [child themes](/themes/child-themes/), which have simpler development and maintenance requirements.

## Custom Logo

The Nexus, Twenty-One, and Six themes display either your company name or logo in the top-left corner of the Client Area. If you supply a logo, the `$assetLogoPath` variable contains the relative path to the logo file. 

To set a custom logo, you can upload the logo in the **Setup Wizard** or at **Configuration > System Settings > General Settings** in the **General** tab.

A logo can be manually uploaded to the `/assets/img` directory, but the logo must be saved as either `logo.png` or `logo.jpg`.

## Include Files

Include templates are templates that are shared and used by multiple pages. They are located within the `/includes/` subdirectory.

The following list of include files is accurate for WHMCS 8.1 and later:

**Common to All Pages**

* `confirmation.tpl` — Controls the display of a confirmation modal.
* `flashmessage.tpl` — Controls the display of flash messages (messages that the interface shows once).
* `head.tpl` — Defines the CSS and Javascript files included within the `<head>` section of a page.
* `modal.tpl` — Controls the display of all Client Area modals.
* `navbar.tpl` — Controls the rendering of the primary navigation bar menu items.
* `social-accounts.tpl` — Controls the display of any configured social media icons in the footer. This include file is specific to Nexus or Twenty-One.
* `verifyemail.tpl` — Controls the display of the email verification notice below the header.

**Used as Required**

* `alert.tpl` — Controls the rendering of a single alert (for example, a success message or warning).
* `breadcrumb.tpl` — Controls the display of the breadcrumbs in the page header.
* `captcha.tpl` — Renders the CAPTCHA verification image.
* `domain-search.tpl` — Controls the display of the domain search.
* `generate-password.tpl` — Controls the display of the password generation modal when a user opens it.
* `index.tpl` — Controls the display of store landing pages.
* `linkedaccounts.tpl` — Controls the display of the page for configuring third-party services like Facebook and Google.
* `network-issues-notifications.tpl` — Controls the display of the network status alert bar under the header. This include file is specific to Nexus or Twenty-One.
* `panel.tpl` — Controls the display of a card-style display panel.
* `pwstrength.tpl` — Controls the display of the password strength meter and tooltip.
* `sidebar.tpl` — Controls the display of the sidebar menu items.
* `tablelist.tpl` — Controls the display of all filterable data list tables.

Editing any of these template files will affect everywhere that the respective elements are used. One place to edit and one place to maintain during upgrades will help make applying and preserving your customisations easier.
