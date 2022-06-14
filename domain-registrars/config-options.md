+++
next = "/domain-registrars/function-index/"
prev = "/domain-registrars/getting-started/"
title = "Configuration Options"
weight = 20

+++

As with all modules in WHMCS, the configuration function is a required function of all registrar modules.

This defines the settings that are available for your registrar module. The name of this function must be `yourmodulename_getConfigArray`.

The supported configuration field types include the following:

* Text
* Password
* Yes/No Checkboxes
* Dropdown Menus
* Radio Buttons
* Text Areas

Below are examples of the available parameters for each field type. Provisioning modules support up to 24 options defined in this way.

```
<?php
function yourmodulename_getConfigArray($params)
{
    return array(
        "username" => array (
            "FriendlyName" => "UserName",
            "Type" => "text", # Text Box
            "Size" => "25", # Defines the Field Width
            "Description" => "Textbox",
            "Default" => "Example",
        ),
        "password" => array (
            "FriendlyName" => "Password",
            "Type" => "password", # Password Field
            "Size" => "25", # Defines the Field Width
            "Description" => "Password",
            "Default" => "Example",
        ),
        "usessl" => array (
            "FriendlyName" => "Enable SSL",
            "Type" => "yesno", # Yes/No Checkbox
            "Description" => "Tick to use secure connections",
        ),
        "package" => array (
            "FriendlyName" => "Package Name",
            "Type" => "dropdown", # Dropdown Choice of Options
            "Options" => "Starter,Advanced,Ultimate",
            "Description" => "Sample Dropdown",
            "Default" => "Advanced",
        ),
        "disk" => array (
            "FriendlyName" => "Disk Space",
            "Type" => "radio", # Radio Selection of Options
            "Options" => "100MB,200MB,300MB",
            "Description" => "Radio Options Demo",
            "Default" => "200MB",
        ),
        "comments" => array (
            "FriendlyName" => "Notes",
            "Type" => "textarea", # Textarea
            "Rows" => "3", # Number of Rows
            "Cols" => "50", # Number of Columns
            "Description" => "Description goes here",
            "Default" => "Enter notes here",
        ),
    );
}
```
## Configuration Validation

When the configuration settings for your module are being saved, you may wish to validate them first before allowing them to be saved. You can define the `_config_validate` function in your module to do this.

This will allow you to run a block of code to determine if the details that the user has provided and is trying to save are valid or not. If there is a problem with validation, you can throw an exception to prevent the save action from completing.

The example code below demonstrates how to prevent saving the module configuration if an API responded with an error due to a parameter being invalid:

```
<?php

use WHMCS\Exception\Module\InvalidConfiguration;
 
function yourmodulename_config_validate($params) {
    $apiKey = $params['api_key'];
  
    $valid = false;
    // $response = yourmodulename_apicall('validate_credentials', [
    //     'apikey' => $apiKey,
    // ]);
    // $valid = $response['valid'];
  
    if (!$valid) {
        throw new InvalidConfiguration('API Key is invalid.');
    }
}
```
