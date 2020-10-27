+++
next = "/advanced/db-interaction/"
prev = "/advanced/authentication/"
title = "Creating Pages"
weight = 10

+++

Creating your own client area pages should ordinarily be done by creating an Addon Module with client area output.

However, if you wish to, you can create a standalone page using the following template.

```
<?php

use WHMCS\Authentication\CurrentUser;
use WHMCS\ClientArea;
use WHMCS\Database\Capsule;

define('CLIENTAREA', true);

require __DIR__ . '/init.php';

$ca = new ClientArea();

$ca->setPageTitle('Your Page Title Goes Here');

$ca->addToBreadCrumb('index.php', Lang::trans('globalsystemname'));
$ca->addToBreadCrumb('mypage.php', 'Your Custom Page Name');

$ca->initPage();

//$ca->requireLogin(); // Uncomment this line to require a login to access this page

// To assign variables to the template system use the following syntax.
// These can then be referenced using {$variablename} in the template.

//$ca->assign('variablename', $value);

$currentUser = new CurrentUser();
$authUser = $currentUser->user();

// Check login status
if ($authUser) {

    /**
     * User is logged in - put any code you like here
     *
     * Use the User model to access information about the authenticated User
     */

    $ca->assign('userFullname', $authUser->fullName);


    $selectedClient = $currentUser->client();
    if ($selectedClient) {

        /**
         * If the authenticated User has selected a Client Account to manage,
         * the model will be available - put any code you like here
         */

        $ca->assign(
            'clientInvoiceCount',
            $selectedClient->invoices()->count()
        );
    }

} else {

    // User is not logged in
    $ca->assign('userFullname', 'Guest');

}

/**
 * Set a context for sidebars
 *
 * @link http://docs.whmcs.com/Editing_Client_Area_Menus#Context
 */
//Menu::addContext();

/**
 * Setup the primary and secondary sidebars
 *
 * @link http://docs.whmcs.com/Editing_Client_Area_Menus#Context
 */
Menu::primarySidebar('announcementList');
Menu::secondarySidebar('announcementList');

# Define the template filename to be used without the .tpl extension

$ca->setTemplate('mypage');

$ca->output();
```

The example demonstrates the attributes for a page:

* How to initiate the page
* How to reference the language file variables (Lang::trans)
* How to check if a User is logged in and Client Account is selected ([Authentication](https://developers.whmcs.com/advanced/authentication/) with CurrentUser)
* How to define template variables ($ca->assign)
* How to set the template to use and then output it

The template file should be a filename in the active WHMCS system template folder. So, for the example above the path would be `/templates/default/mypage.tpl`.

Now when ready to test, upload the PHP file to the root WHMCS directory and the template file to your active template directory. Then visit the PHP file in your browser to try it.

{{% notice info %}}
Custom pages created in this way should always be located in the root WHMCS directory. Attempting to use this code outside of the root directory is unsupported.
{{% /notice %}}
