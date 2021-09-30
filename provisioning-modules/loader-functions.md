+++
prev = "/provisioning-modules/simple-mode"
next = "/provisioning-modules/meta-data-params"
title = "Loader Functions"
toc = true
weight = 19

+++

Setting a loader function allows you to create a field that offers a dropdown of options for an end user to choose from.

Unlike the standard "dropdown" setting field type which allows you to offer a predefined and hard-coded choice of options to the user, a field with a loader function will display a list of options that have been fetched dynamically from a remote API service.

An example use case for this is for a Package or Plan name field, where the values need to be fetched via an API from the remote system where the Packages or Plans are defined. Without a loader function, the end user would have to manually enter the package or plan name for the product. With a loader being used, WHMCS will poll the remote API service for a list of possible values when the field is rendered to the end user and allow them to make a choice.

To use a loader function for a field, when defining the field in the **ConfigOptions** function, you must also define a loader function that will be called to populate the field with a list of available options.

Each field can have its own unique loader function defined. These fields will be populated with the return values of the associated loader function when simple mode is used.

Here is an example of a field that defines a loader function with the name **provisioningmodule_LoaderFunction**:

```
function provisioningmodule_ConfigOptions($params)
{
    return [
        // Text field powered by the Loader function
        'Loader Populated Field' => [
            'Type' => 'text',
            'Size' => '25',
            'Loader' => 'provisioningmodule_LoaderFunction',
            'SimpleMode' => true,
        ],
    ];
}
```

The loader function you define must be created and should return an array of key value pairs.

The key should be the value that your module expects to receive, and the value should be a human friendly display label for the key value. In many cases these may be the same.

## Error Handling

If the connection to the remote API service needed to fetch the dynamically loaded values fails, your code should throw an Exception.

WHMCS will recognize an Exception and display the error message returned in that exception to the end user.

```
/**
 * Loader function that will populate the field in ConfigOptions
 * @return array The list of package names
 */
function provisioningmodule_LoaderFunction($params) {
    // Make a call to the remote API endpoint
    $ch = curl_init('https://www.example.com/api/function');
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    $response = curl_exec($ch);

    // Check for any curl errors or an empty response
    if (curl_error($ch)) {
        throw new Exception('Unable to connect: ' . curl_errno($ch) . ' - ' . curl_error($ch));
    } elseif (empty($response)) {
        throw new Exception('Empty response');
    }

    // We're done with curl so we can release the resource now
    curl_close($ch);

    // Attempt to decode the response
    $packageNames = json_decode($response, true);  

    // Check to make sure valid json was returned
    if (is_null($packageNames)) {
        throw new Exception('Invalid response format');
    }

    // Format the list of values for display
    // ['value' => 'Display Label']
    $list = [];
    foreach ($packageNames as $packageName) {
        $list[$packageName] = ucfirst($packageName);
    }

    return $list;
}
```
