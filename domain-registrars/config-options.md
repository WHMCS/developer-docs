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
