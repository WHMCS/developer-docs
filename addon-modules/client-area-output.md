+++
next = "/addon-modules/multi-language"
prev = "/addon-modules/admin-area-output"
title = "Client Area Output"
toc = true
weight = 50

+++

Addon Modules also support generating client area output.
This is done with the use of an **_clientarea** function within the module.

The functionality allows for modules to return output in the form of template files.
The template files are stored within the module folder.

You can return a page title, breadcrumb path, and template variables.
You can also require a client login with a simple true/false response.
Language strings from the modules language file ([see here][language]) are also available.

Access Client area modules using an URL in the format **index.php?m=modulename**

## Example Client Area Function <a id="example-function"></a>

Here is a sample client area function demonstrating all the available return variables:

```
function demo_clientarea($vars) {
 
    $modulelink = $vars['modulelink'];
    $version = $vars['version'];
    $option1 = $vars['option1'];
    $option2 = $vars['option2'];
    $option3 = $vars['option3'];
    $option4 = $vars['option4'];
    $option5 = $vars['option5'];
    $option6 = $vars['option6'];
    $LANG = $vars['_lang'];
 
    return array(
        'pagetitle' => 'Addon Module',
        'breadcrumb' => array('index.php?m=demo'=>'Demo Addon'),
        'templatefile' => 'clienthome',
        'requirelogin' => true, # accepts true/false
        'forcessl' => false, # accepts true/false
        'vars' => array(
            'testvar' => 'demo',
            'anothervar' => 'value',
            'sample' => 'test',
        ),
    );
 
}
```

The above assumes a template, **clienthome.tpl**, existing within the module folder to use for the output.


[language]: /addon-modules/multi-language "Multi Language Support"
