+++
next = "/addon-modules/hooks"
prev = "/addon-modules/client-area-output"
title = "Multi-Language Support"
toc = true
weight = 60

+++

Modules can support multiple languages should you wish.

For this, the addon module needs a lang subfolder created within it.
Within that, language files can be created matching the names of the main WHMCS admin area language files.
The admin language files are located in the /admin/lang/ folder.

WHMCS has the language variables for custom modules separate to make installation and updating easier.

If language files exist, WHMCS will then load these whenever the custom module is accessed.
WHMCS will select the appropriate language file based on the current administrators language setting.
If no matching language file exists within the module folder, it will fall back to the default language set in the module’s config array.

A language file would be located at `/modules/addons/youraddonname/lang/english.php`

## Example Language File <a id="example-file"></a>

```
$_ADDONLANG['intro'] = "This is an example module to be used as a starting point for developers.";
$_ADDONLANG['description'] = "Creating an addon module is easy and this example demonstrates all the functionality an addon module can utilise.<br /><br />Addon modules offer the ultimate flexibility allowing you to create anything from a simple extra admin area page, to advanced fully custom modules interfacing with remote third party systems and hooking into & extending the core system.";
$_ADDONLANG['documentation'] = "This file is not protected so you can have a look at it";
```

The language variables are then passed into the _output and _sidebar functions array using “_lang”.

Below is a demonstration of how you specify the default language for your module in the config array.

## Specifying Default Addon Module Language <a id="default-language"></a>

```
function demo_config() {
    $configarray = array(
    "name" => "Addon Example",
    "description" => "This is a sample config function for an addon module",
    "version" => "1.0",
    "author" => "WHMCS",
    "language" => "english",
    "fields" => etc...
```
