The admin area of WHMCS can be customised through the use of themes and hooks.

# Getting Started

The default template that ships with WHMCS is called the Blend theme.

If you wish to make changes, we recommend first creating a copy of the theme with a custom name. This ensures your customisations can be preserved when applying future updates.

Make a copy of the Blend theme directory.

* Copy the `~/admin/templates/blend/` directory to `~/admin/templates/yourname/`

 

If the admin directory name has been customised, adjust the path accordingly.

{{% notice info %}}
Theme names should be a single word, consisting of only lowercase letters and numbers.
{{% /notice %}}

Now it’s time to customise your theme.

# Customising

The header and footer template files that are common to every page and act as a wrapper around the primary body content are a good place to start for this.

* We strongly recommend you maintain all of the output variables present in the default template files in your custom header/footer as this will help ensure compatibility with addons and extensions you later install

* The footer template file includes a number of lines of code which are essential to the correct operation of the admin area, particularly the client limit notifications. admin user notes, and the intelligent search option on each page. Please take care not to remove these lines.

## Logo

In order to make changes to the logo displayed on the top left corner of admin area pages, in the `~/admin/templates` folder, replace the `images/logo.gif` file.

# CSS Styling

In order to make changes to any of the CSS that is applied by default, please create a custom CSS file in your theme and load it using the header template file.

# Templates

All admin themes contain the following template files:

* authconfirm.tpl - This template file is used to display the Password Confirmation prompt on any admin area page that requires it. For example: Setup > General Settings.

* clientssummary.tpl - Controls the display of the Summary Tab and associated information within an individual Clients Profile.

* footer.tpl - This template file controls the footer of each admin area page.

* header.tpl - This template file controls the header of each admin area page.

* homepage.tpl - Controls the display of the Admin Dashboard. Widgets are the building blocks of the admin dashboard and are the recommended way to add additional data and information. We have documentation on creating and working with widgets available at [Widgets](https://developers.whmcs.com/advanced/widgets/).

* menu.tpl - Controls the primary navigation dropdown menu bar.

* sidebar.tpl - This template file controls the left sidebar menu of each admin area page.

* systemhealthandupdates.tpl - Controls the display and styling of the System Health Status page.

* viewticket.tpl - Controls the display of the view for an individual support ticket when viewed within the admin area.

* viewticketcustomfields.tpl - Controls the display of custom fields and their data when viewing an individual support ticket within the admin area.

# Testing

When you are ready with your new template and wish to test it, follow the steps below:

* Login to the Admin Area

* Navigate to *My Account* using the menu located at the top of any page

* Under the Template setting, select the name of the template you created above

* Hit Save Changes and you will immediately begin seeing your new template

# Making your template live

To apply the change to other admin users, please navigate to Setup > Staff Management > Administrators and edit the Template setting the applicable admin users.

# Further Customisation via Hooks

There are a number of hook points that can be used to introduce customisations. For a full list and the latest documentation, please visit our [Admin Area Hook Reference](https://developers.whmcs.com/hooks-reference/admin-area/)

Some example hook use cases are provided below.

{{% notice info %}}
If you wish to output custom javascript, we recommend using the AdminAreaFooterOutput hook point for best performance.
{{% /notice %}}

## Adding a link to the Actions section on the Client Summary page
```
<?php
/**
 * Hook that will link directly to an addon module with the userid, useful if the addon needs to do a client-specific task
*/

if (!defined('WHMCS')) {
    die('This hook should not be run directly');
}

add_hook('AdminAreaClientSummaryActionLinks', 1, function ($vars) {
    $userid = $vars['userid'];
    $return = [];
    $return[] = '<a href="addonmodules.php?module=addon_module&userid=$userid">Custom addon link for this client</a>';
    return $return;
});

```

## Adding link to view ticket page

Displays a box on the ticket details page in the admin area that could be used to includes any URL or just standard text. In this example, it includes the unique URL WHMCS gives to clients to view their ticket directly in the client area. Useful if they don't have it already (or lost it) and it needs to be provided to them in a ticket reply. 

```
<?php
/**
 * Hook that will display the Direct ticket
 * link for the client area of WHMCS.
*/

use WHMCS\Config\Setting;

if (!defined('WHMCS')) {
    die('This hook should not be run directly');
}

add_hook('AdminAreaViewTicketPage', 1, function ($vars) {
    $payLoad = localAPI('getticket', array(
        'ticketid' => $vars['ticketid']
    ));

    $systemUrl = Setting::getValue('SystemURL');

    $ticketUrl = $systemUrl . '/viewticket.php?tid=' . $payLoad['tid'] . '&c=' . $payLoad['c'];

    $jQuery = '<script>

$( document ).ready(function() {
 $(\'<div class="alert alert-info text-center"><a href="' . $ticketUrl . '" target="_blank">' . $ticketUrl . '</a></div>\').prependTo("#contentarea");
 });
 </script>';

    return $jQuery;
});

```

## Manipulating the dom to hide options or settings

In the below example, it shows how to use jQuery to untick the box to send the welcome e-mail when adding a client via the Clients > Add New Client page in the admin area.

```
<?php
/**
 * This hook will untick the checkbox to send new account information on the clientadd.php page
*/

add_hook('AdminAreaFooterOutput', 1, function ($vars) {
    if (strpos($_SERVER['REQUEST_URI'], 'clientsadd.php') !== false) {
        return '<script>
        $( document ).ready(function() {
            $("input[name=sendemail]").attr("checked", false);
        });
    </script>';
    }
});

```
