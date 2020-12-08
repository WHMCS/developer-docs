+++
next = "/themes/debugging/"
prev = "/themes/php/"
title = "Testing"
toc = true
weight = 80

+++

## Testing Your Customizations

WHMCS allows you to preview themes and Order Form Templates before making them live. This is done using URL parameters.

* For themes, use the `?systpl=xxxx` URL parameter.
* For Order Form Templates, use the `?carttpl=xxxx` URL parameter.

For example, to preview a custom system theme named `mytemplate` in a WHMCS Client Area at `http://www.yourdomain.com/whmcs/`, you would navigate to:

```
http://www.yourdomain.com/whmcs/?systpl=mytemplate
```

When you view a system theme or order form template through this method, the system will validate whether all of the theme or order form template's dependencies are met. If they aren't, the page will not display.

If the dependencies were met and the theme or order form template displayed successfully, the system theme or Order Form Template will be stored for the duration of your browser session, allowing you to exercise all areas of the Client Area with your new system theme.

## Activating Themes

Once you're happy with your new theme and are ready to make it live, follow the steps below:

1. Log in to your WHMCS Admin Area.
2. Navigate to **Configuration > System Settings > General Settings**.
3. Under the **System Theme** setting on the **General** tab, select the name of the theme you created above.
4. Click **Save Changes** and visitors to your site will immediately begin seeing your new theme.

Visitors to your site will immediately seeing your new system theme.

## Activating Order Form Templates

There are two places in the WHMCS Admin Area in which you can set Order Form Templates:

* You can set the system default Order Form Template at **Configuration > System Settings > General Settings** in the **Ordering** tab.
* You can set the Order Form Template for specific product groups at **Configuration > System Settings > Products/Services**.
