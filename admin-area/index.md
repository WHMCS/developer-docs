Aspects of the admin area can be customised through the use of a theme.

# Getting Started

The default template that ships with WHMCS is called the Blend theme.

Before you begin customising it for your needs, the first step is to create your own copy of the template. This ensures your customisations are not lost when updating.

Make a copy of the Blend template directory.

* Copy the `~/admin/templates/blend/` directory to `~/admin/templates/yourname/`

 

If the admin directory name has been customised, adjust the path accordingly.

{{% notice info %}}
Template names should be a single word, consisting of only lowercase letters and numbers.
{{% /notice %}}

Now it’s time to customise your theme.

# Customising

The header and footer template files that are common to every page and act as a wrapper around the primary body content are a good place to start for this.

* We strongly recommend you maintain all of the output variables present in the default template files in your custom header/footer as this will help ensure compatibility with addons and extensions you later install

* The footer template file includes a number of lines of code which are essential to the correct operation of the admin area, particularly the client limit notifications. admin user notes, and the intelligent search option on each page. Please take care not to remove these lines.

## Logo

In order to make changes to the logo displayed on the admin area login page and the top left corner of admin area pages, there are 2 changes that need to be made.

First, replace the `~/assets/img/whmcs.png` with your desired logo. Then in the custom admin template in the `~/admin/templates` folder, replace the `images/logo.gif` file. This method is recommended to ensure any changes are not overwritten during upgrades. Once this is done, please switch any desired admin users to the new template using the steps at [Making your template live](#making-your-template-live) below.

# CSS Styling

In order to make changes to any of the CSS that is applied by default, it is best to duplicate the currently selected admin template in the /admin/templates folder and edit the /css/styles.css file within it as desired.

# Templates

All admin templates contain the following template files:

* authconfirm.tpl - This template file is used to display the Password Confirmation prompt on any admin area page that requires it. For example: Setup > General Settings.

* clientssummary.tpl - Controls the display of the Summary Tab and associated information within an individual Clients Profile.

* footer.tpl - This template file controls the footer of each admin area page.

* header.tpl - This template file controls the header of each admin area page.

* homepage.tpl - Controls the display of the Admin Dashboard. Widgets(link) are the building blocks of the admin dashboard and are the recommended way to add additional data and information. We have documentation on creating and working with widgets available here.

* menu.tpl - Controls the primary navigation dropdown menu bar.

* sidebar.tpl - This template file controls the left sidebar menu of each admin area page.

* systemhealthandupdates.tpl - Controls the display and styling of the System Health Status page.

* viewticket.tpl - Controls the display of the view for an individual support ticket when viewed within the admin area.

* viewticketcustomfields.tpl - Controls the display of custom fields and their data when viewing an individual support ticket within the admin area.

# Non-Theme Templates

Some admin area pages are templated but are located outside of a theme, instead residing in the /admin/templates folder itself. We do not recommend customising these templates.

* licenseerror.tpl - This template file is used to show various licensing error messages as needed.

* login.tpl - This template file used to show the admin area login form when not logged in.

* whatsnew_modal.tpl - This template file is used to control the look and feel of the Whats New modal that is displayed when logging into the admin area for the first time after performing an update.

# Making your template live

Once you’re happy with your new template and are ready to make it live, follow the steps below:

* Login to the Admin Area

* Click the "My Account" link at the top of any page. If you want to apply the changes to other admins, please edit their settings under Setup > Staff Management > Administrators.

* Under the Template setting, select the name of the template you created above

* Hit Save Changes and you will immediately begin seeing your new template


# Further Customisation via Hooks

There are a number of hook points that can be used to introduce customisations. For a full list and the latest documentation, please visit https://developers.whmcs.com/hooks-reference/admin-area/

Some examples of this can be found below. If you want to use custom JavaScript and/or jQuery, it is best to use the AdminAreaFooterOutput hook point to load it.

## Adding a link to the Actions section on the Client Summary page
```
<?php
/**
 * Hook that will link directly to an addon module with the userid, useful if the addon needs to do a client-specific task
  
if (!defined('WHMCS')) {
 die('This hook should not be run directly');
}
 
add_hook('AdminAreaClientSummaryActionLinks', 1, function($vars) {
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
 
use WHMCS\Config\Setting;
 
if (!defined('WHMCS')) {
 die('This hook should not be run directly');
}
  
add_hook('AdminAreaViewTicketPage', 1, function($vars) {
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
 
add_hook('AdminAreaFooterOutput', 1, function($vars) {
    if (strpos($_SERVER['REQUEST_URI'], 'clientsadd.php') !== false ) {
 return '<script>
        $( document ).ready(function() {
            $("input[name=sendemail]").attr("checked", false);
        });
    </script>';
    }
});
```
