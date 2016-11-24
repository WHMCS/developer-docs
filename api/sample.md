+++
next = "/api/internal-api"
prev = "/api/getting-started"
title = "Sample Code"
toc = true
weight = 50

+++

The following demonstrates how to connect to the WHMCS API from a PHP script using CURL.

```
<?php
/**
 * WHMCS Sample API Call
 *
 * @package    WHMCS
 * @author     WHMCS Limited <development@whmcs.com>
 * @copyright  Copyright (c) WHMCS Limited 2005-2016
 * @license    http://www.whmcs.com/license/ WHMCS Eula
 * @version    $Id$
 * @link       http://www.whmcs.com/
 */

// API Connection Details
$whmcsUrl = "https://www.yourdomain.com/path/to/whmcs/";
$username = "yourusername";
$password = "yourpassword";

// Set post values
$postfields = array(
    'username' => $username,
    'password' => md5($password),
    'action' => 'GetClients',
    'responsetype' => 'json',
);

// Call the API
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $whmcsUrl . 'includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_TIMEOUT, 30);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
$response = curl_exec($ch);
if (curl_error($ch)) {
    die('Unable to connect: ' . curl_errno($ch) . ' - ' . curl_error($ch));
}
curl_close($ch);

// Decode response
$jsonData = json_decode($response, true);

// Dump array structure for inspection
var_dump($jsonData);
```
