+++
prev = "/provisioning-modules/getting-started"
next = "/provisioning-modules/simple-mode"
title = "Configuration Options"
toc = true
weight = 15

+++

This function defines the settings that can be configured on a per product basis for your module.

The name of this function must be `yourmodulename_ConfigOptions`.

The supported configuration field types include the following:

* Text
* Password
* Yes/No Checkboxes
* Dropdown Menus
* Radio Buttons
* Text Areas

Below are examples of the available parameters for each type of field. Provisioning modules support up to 24 options defined in this way.

```
function yourmodulename_ConfigOptions() {
    return [
        "username" => [
            "FriendlyName" => "UserName",
            "Type" => "text", # Text Box
            "Size" => "25", # Defines the Field Width
            "Description" => "Textbox",
            "Default" => "Example",
        ],
        "password" => [
            "FriendlyName" => "Password",
            "Type" => "password", # Password Field
            "Size" => "25", # Defines the Field Width
            "Description" => "Password",
            "Default" => "Example",
        ],
        "usessl" => [
            "FriendlyName" => "Enable SSL",
            "Type" => "yesno", # Yes/No Checkbox
            "Description" => "Tick to use secure connections",
        ],
        "package" => [
            "FriendlyName" => "Package Name",
            "Type" => "dropdown", # Dropdown Choice of Options
            "Options" => "Starter,Advanced,Ultimate",
            "Description" => "Sample Dropdown",
            "Default" => "Advanced",
        ],
        "packageWithNVP" => [
            "FriendlyName" => "Package Name v2",
            "Type" => "dropdown", # Dropdown Choice of Options
            "Options" => [
                'package1' => 'Starter',
                'package2' => 'Advanced',
                'package3' => 'Ultimate',
            ],
            "Description" => "Sample Dropdown",
            "Default" => "package2",
        ],
        "disk" => [
            "FriendlyName" => "Disk Space",
            "Type" => "radio", # Radio Selection of Options
            "Options" => "100MB,200MB,300MB",
            "Description" => "Radio Options Demo",
            "Default" => "200MB",
        ],
        "comments" => [
            "FriendlyName" => "Notes",
            "Type" => "textarea", # Textarea
            "Rows" => "3", # Number of Rows
            "Cols" => "50", # Number of Columns
            "Description" => "Description goes here",
            "Default" => "Enter notes here",
        ],
    ];
}
```
