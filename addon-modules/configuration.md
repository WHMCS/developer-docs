+++
next = "/addon-modules/installation-uninstallation"
prev = "/addon-modules/getting-started"
title = "Configuration"
toc = true
weight = 20

+++

The first step in the module is defining the configuration data.
This includes the module name, version number, author, description.
Also, this contains any custom configuration fields.
Below is an example of the config function:

## Config Function Example <a id="config-example-function"></a>

```
function demo_config() {
    $configarray = array(
    "name" => "Addon Example",
    "description" => "This is a sample config function for an addon module",
    "version" => "1.0",
    "author" => "WHMCS",
    "fields" => array(
        "option1" => array ("FriendlyName" => "Option1", "Type" => "text", "Size" => "25",
                              "Description" => "Textbox", "Default" => "Example", ),
        "option2" => array ("FriendlyName" => "Option2", "Type" => "password", "Size" => "25",
                              "Description" => "Password", ),
        "option3" => array ("FriendlyName" => "Option3", "Type" => "yesno", "Size" => "25",
                              "Description" => "Sample Check Box", ),
        "option4" => array ("FriendlyName" => "Option4", "Type" => "dropdown", "Options" =>
                              "1,2,3,4,5", "Description" => "Sample Dropdown", "Default" => "3", ),
        "option5" => array ("FriendlyName" => "Option5", "Type" => "radio", "Options" =>
                              "Demo1,Demo2,Demo3", "Description" => "Radio Options Demo", ),
        "option6" => array ("FriendlyName" => "Option6", "Type" => "textarea", "Rows" => "3",
                              "Cols" => "50", "Description" => "Description goes here", "Default" => "Test", ),
    ));
    return $configarray;
}
```

The first 4 fields: name, version, author & description should all be self-explanatory.
These contain the display name for the module which will show within the admin area.
Also, the version number, name/company of the creator, and a brief description of the addon.

The fields section is where you can define the input you need from end users to be able to make the module work.
In this example we are asking for some API related information.
Supported field types are “text”, “password”, “yesno” (checkboxes), “textarea”, “dropdown” and “radio”.
If using the textarea option, a “Rows” parameter is used to show the height of the box.
If using the dropdown type, then you must provide an “Options” parameter with comma separated values.

There is a language variable you can also include if you will be using language files for your module.
We’ll look at languages in more [detail later on][language].

[language]: /addon-modules/multi-language "Multi Language Support"
