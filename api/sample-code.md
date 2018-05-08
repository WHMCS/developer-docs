+++
next = "/api/internal-api/"
prev = "/api/response-types/"
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

// For WHMCS 7.2 and later, we recommend using an API Authentication Credential pair.
// Learn more at http://docs.whmcs.com/API_Authentication_Credentials
// Prior to WHMCS 7.2, an admin username and md5 hash of the admin password may be used.
$api_identifier = 'D4j1dKYE3g40VROOPCGyJ9zRwP0ADJIv';
$api_secret = 'F1CKGXRIpylMfsrig3mwwdSdYUdLiFlo';

$postfields = array(
    'identifier' => $api_identifier,
    'secret' => $api_secret,
    'action' => $api_call,
    'responsetype' => 'json',
);

// Call the API
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $whmcsUrl . 'includes/api.php');
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_TIMEOUT, 30);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 1);
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 2);
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

?>

```
