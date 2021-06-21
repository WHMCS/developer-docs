+++
prev = "/api/sample-code/"
next = "/api/api-index/"
title = "Internal API"
toc = true
weight = 60

+++

The Internal API should be used when making API calls from within the WHMCS system.

Common uses for this include from modules, hooks, or other custom code local to the WHMCS installation.

The import of `init.php` is not required when you’re already in a WHMCS runtime (like in a hook) where `init.php` has already been imported.

## Usage Example

```
<?php

/**
 * WHMCS Sample Local API Call
 *
 * @package    WHMCS
 * @author     WHMCS Limited <development@whmcs.com>
 * @copyright  Copyright (c) WHMCS Limited 2005-2016
 * @license    http://www.whmcs.com/license/ WHMCS Eula
 * @version    $Id$
 * @link       http://www.whmcs.com/
 */

require_once 'init.php';

// Define parameters
$command = 'SendEmail';
$values = array(
    'messagename' => 'Test Template',
    'id' => '1',
);
$adminuser = 'AdminUsername';

// Call the localAPI function
$results = localAPI($command, $values, $adminuser);
if ($results['result'] == 'success') {
    echo 'Message sent successfully!';
} else {
    echo "An Error Occurred: " . $results['message'];
}

```
