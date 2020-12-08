+++
next = "/themes/css-styling/"
prev = "/themes/order-form-templates"
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

The Twenty-One and Six themes display either your company name or logo in the top-left corner of the Client Area. If you supply a logo, the `$assetLogoPath` variable contains the relative path to the logo file. You can upload the logo in the **Setup Wizard** or at **Configuration > System Settings > General Settings** in the **General** tab.

To set a custom logo, it must be saved as either `logo.png` or `logo.jpg`.

## Include Files

Include templates are templates that are shared and used by multiple pages. They are located within the `/includes/` subdirectory.

**Common to All Pages**

* `head.tpl` - Defines the CSS and Javascript files included within the `<head>` section of a page.
* `navbar.tpl` - Controls the output of the primary navigation bar menu items
* `sidebar.tpl` - Controls the output of the sidebar menu items.

**Used as Required**

* `captcha.tpl` - Used to output the captcha verification image wherever used.
* `pwstrength.tpl` - Used to output the password strength meter and tooltip wherever used.
* `tablelist.tpl` - Controls the output of all filterable data list tables throughout the client area.

Editing any of these template files will affect everywhere that the respective elements are used. One place to edit and one place to maintain during upgrades will help make applying and preserving your customisations easier.
