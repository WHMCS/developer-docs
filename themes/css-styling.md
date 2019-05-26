+++
next = "/themes/navigation/"
prev = "/themes/customising/"
title = "CSS Styling"
toc = true
weight = 30

+++

If you want to make changes to any of the CSS that is applied by default, we recommend making those customisations inside of the /css/custom.css file.

This file is included after styles.css allowing you to override any of the CSS defined within it and will not be affected by future updates to the WHMCS software.

To utilise Font Awesome icons, you may include the latest Font Awesome release shipped with WHMCS by including the line below within the <head> section of your template:
`<link href="{$WEB_ROOT}/assets/css/fontawesome-all.min.css" rel="stylesheet">`
Themes which do not include the above line will have it injected automatically. If you wish to prevent this behaviour, include the following line:
`<!-- /css/fontawesome-all.min.css -->`

{{% notice tip %}}
We strongly recommend adding your custom CSS rules to the **custom.css** file and not editing /css/styles.css directly as it will make updating easier.
{{% /notice %}}
