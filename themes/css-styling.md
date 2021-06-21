+++
next = "/themes/navigation/"
prev = "/themes/customising/"
title = "CSS Styling"
toc = true
weight = 30

+++

## Custom CSS

If you want to make changes to any of the CSS that is applied by default, we recommend creating a `css/custom.css` file and making those customisations within it. This file is included after `styles.css`, allowing you to override any of the CSS defined within it. It will not be affected by future updates to the WHMCS software.

{{% notice tip %}}
* We strongly recommend creating a `css/custom.css` file to contain your additional custom CSS rules and **not** editing `css/styles.css` directly because it will make updating easier.
* You may also wish to consider creating a [child theme](/themes/child-themes/).
{{% /notice %}}

## Using Font Awesome

To use Font Awesome icons, you may include the latest Font Awesome release shipped with WHMCS by including the line below within the `<head>` section of your template:

`<link href="{$WEB_ROOT}/assets/css/fontawesome-all.min.css" rel="stylesheet">`

Themes that do not include the above line will have it injected automatically. If you wish to prevent this behaviour, include the following line:

`<!-- /css/fontawesome-all.min.css -->`
