+++
next = "/addon-modules/client-area-output"
prev = "/addon-modules/installation-uninstallation"
title = "Admin Area Content/Output"
toc = true
weight = 40

+++

The output from modules is defined in the function your_module_name_output.
This should be actually output (i.e. echo’d) not returned.
All output is captured by WHMCS and displayed within the admin interface template.
The module name/title is prefixed to the output.

## Variables <a id="variables"></a>

The output function is passing all the fields defined in your modules config,
along with the values users have set for them, as well as a "_modulelink_" variable which you can use to link back to the module.

## Linking/Actions <a id="linking"></a>

Using the modulelink variable passed into the output function, you can then create links and forms that post back to your module.
The modulelink will be in the format "_addonmodules.php?module=xxxxxx_". For links you can then append “_&var1=x&var2=y_”.
For forms, use the POST form method to receive user input.

Within the output function, the $_GET or $_POST variables can be checked.
This can be used to display other output or perform various tasks, once links have been followed.

## Admin User Data <a id="admin-user-data"></a>

To access the currently logged in admin ID should the module need that, in the session, use `$_SESSION[‘adminid’]`.
From that, the module can find any extra information you need in tbladmins.

## Example Output Function <a id="example-function"></a>

```
function demo_output($vars) {
 
    $modulelink = $vars['modulelink'];
    $version = $vars['version'];
    $option1 = $vars['option1'];
    $option2 = $vars['option2'];
    $option3 = $vars['option3'];
    $option4 = $vars['option4'];
    $option5 = $vars['option5'];
    $option6 = $vars['option6'];
    $LANG = $vars['_lang'];
 
    echo '<p>The date & time are currently '.date("Y-m-d H:i:s").'</p>';
 
}
```

Things aren't of course limited to just one file.
Use the **_output** function to include other files, call templates, etc.
The system is flexible.
