+++
next = "/themes/css-styling/"
prev = "/themes/getting-started"
title = "Customising"
toc = true
weight = 20

+++

The header and footer template files that are common to every page and act as a wrapper around the primary body content are a good place to start for this.

* We strongly recommend you maintain all of the template includes and output variables present in the default template files in your custom header/footer as this will help ensure compatibility with addons and extensions you later install
* Navigation bar and Sidebar content is defined within WHMCS and passed to the templates for output. This allows modules and addons to interact with and manipulate these areas of the client area dynamically. The output styling of these is controlled by include files which are explained in more detail below.
* The footer template file includes a number of lines of javascript code immediately prior to the closing </body> tag which are essential to the correct operation of the client area. Please take care not to remove these lines.

## Custom Logo

The Six theme uses a conditional based on the ```$assetLogoPath``` variable to either display a custom logo or the name of the company as defined in Setup > General Settings > Company Name. In order to set a custom logo it must either exist as `/assets/img/logo.png` or `/assets/img/logo.jpg`.

## Include Files

Include templates are templates that are shared and used by multiple pages. They are located within the `/includes/` sub-directory.

**Common to All Pages**

* head.tpl - Defines the CSS & Javascript files included within the <head> section of a page
* navbar.tpl - Controls the output of the primary navigation bar menu items
* sidebar.tpl - Controls the output of the sidebar menu items

**Used as Required**

* captcha.tpl - Used to output the captcha verification image wherever used
* pwstrength.tpl - Used to output the password strength meter and tooltip wherever used
* tablelist.tpl - Controls the output of all filterable data list tables throughout the client area

Editing any of these template files will affect everywhere that the respective elements are used. One place to edit, and one place to maintain during upgrades, will help make applying and preserving your customisations easier.
