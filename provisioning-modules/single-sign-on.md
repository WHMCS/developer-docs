+++
prev = "/provisioning-modules/core-module-functions"
next = "/provisioning-modules/usage-update"
title = "Single Sign-On"
toc = true
weight = 50

+++

Single sign-on can occur for a service or server.

Whichever method being used, the return should be the same.

The return from either function should always be an array and contain two keys of a possible three.

* success - This is a [boolean][boolean-glossary] value and should indicate success or failure
* redirectTo - This should be a fully formatted URL return from your SSO request
* errorMsg - Any appropriate error message to be displayed to whoever is making the request

## Service Single Sign-On <a id="service-sso"></a>

Service single sign-on is to allow admin and client users to login to the control panel of the service automatically.

```
/**
 * Perform single sign-on for a given instance of a product/service.
 *
 * Called when single sign-on is requested for an instance of a product/service.
 *
 * When successful, returns an URL to which the user should be redirected.
 *
 * @param array $params common module parameters
 *
 * @see https://developers.whmcs.com/provisioning-modules/module-parameters/
 *
 * @return array
 */
function mymodule_ServiceSingleSignOn(array $params)
{
	$return = array(
		'success' => false,
	);
	try {
        /**
         * all the service's single sign-on token retrieval function, using the
         * values provided by WHMCS in `$params`.
         * The variables and response format would depend on your server API
         */

        $response = $formattedResponse = custom_call_to_server();

        $return = array(
            'success' => true,
            'redirectTo' => $response['redirectUrl'],
        );
    } catch (Exception $e) {
        $return['errorMsg'] = $e->getMessage();
        $response = $e->getMessage();
        $formattedResponse = $e->getTraceAsString();
    }

    /**
     * Log any call to the server
     */
	logModuleCall(
        'provisioningmodule',
        __FUNCTION__,
        $params,
        $response,
        $formattedResponse,
        array('username', 'password')
    );

}
```

In order to call your **_ServiceSingleSignOn** function from the Client Area, create a button or link that uses the following URL format:

```
/clientarea.php?action=productdetails&id=SERVICE_ID_HERE&dosinglesignon=1
```

Replace **SERVICE_ID_HERE** with the ID of the client's service that you wish to perform the single sign-on with.

The most common methods of displaying the link are; in the sidebar, or a button in the client area output of the module. The following resources go into further detail on how to use the WHMCS hooks system or client area output in a module:

https://developers.whmcs.com/themes/sidebars/
https://developers.whmcs.com/provisioning-modules/client-area-output/

## Server Single Sign-On <a id="server-sso"></a>

Server single sign-on allows for Admin users to login to the associated server management panel (like WHM for cPanel) automatically.

```
/**
 * Perform single sign-on for a server.
 *
 * Called when single sign-on is requested for a server assigned to the module.
 *
 * This differs from ServiceSingleSignOn in that it relates to a server
 * instance within the admin area, as opposed to a single client instance of a
 * product/service.
 *
 * When successful, returns an URL to which the user should be redirected to.
 *
 * @param array $params common module parameters
 *
 * @see https://developers.whmcs.com/provisioning-modules/module-parameters/
 *
 * @return array
 */
function mymodule_AdminSingleSignOn(array $params)
{
	$return = array(
		'success' => false,
	);
	try {
        /**
         * all the service's single sign-on token retrieval function, using the
         * values provided by WHMCS in `$params`.
         * The variables and response format would depend on your server API
         */

        $response = $formattedResponse = custom_call_to_server();

        $return = array(
            'success' => true,
            'redirectTo' => $response['redirectUrl'],
        );
    } catch (Exception $e) {
        $return['errorMsg'] = $e->getMessage();
        $response = $e->getMessage();
        $formattedResponse = $e->getTraceAsString();
    }

    /**
     * Log any call to the server
     */
	logModuleCall(
        'provisioningmodule',
        __FUNCTION__,
        $params,
        $response,
        $formattedResponse,
        array('username', 'password')
    );

}
```



[boolean-glossary]: http://docs.whmcs.com/Glossary#Boolean
