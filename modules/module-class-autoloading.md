+++
prev = "/modules/marketplace/"
title = "Module Class Autoloading"
weight = 50

+++

Module class autoloading enables the automatic loading of classes stored in a prescribed way in WHMCS modules. It is provided as a tool to make it easier for module developers to create helper classes. They can then call on and load these modules throughout the WHMCS product from modules, hooks, and other custom integration code.

**Note**: This is **not** intended to be a replacement for modern PHP development practices like the use of Composer or more complex custom-made autoloaders.

## Supported Module Types

The following module types support autoloading:

* Addon
* Fraud
* Gateway
* Registrar
* Report
* Server
* Widget

## Usage

Store your class file(s) in a `lib` subdirectory that is relative to the deployed module. For example:

```
/path/to/whmcs/modules/{ModuleType}/{ModuleName}/lib/{ClassName}.php
```

Add the module namespace to the top of your class file(s):

```
namespace WHMCS\Module\{ModuleType}\{ModuleName};
```

To invoke the class, add the `use` statement and invoke it normally:

```
use WHMCS\Module\{ModuleType}\{ModuleName}\{ClassName};

$hello = new {ClassName}();
```

**Note**: For module types that do not have a directory per module by default (for example, gateways and reports), you will need to create the directory and subdirectory `lib` to use autoloading.

## Example Usage

The following example demonstrates module namespace autoloading for a class named `HelloWorld` within the `Sample Addon Module` module:

### `/modules/addons/sample_addon_module/lib/HelloWorld.php`

```
namespace WHMCS\Module\Addon\SampleAddonModule;

/**
 * Hello World Class
 *
 * @copyright Copyright (c)
 * @license http://www.whmcs.com/license/ WHMCS Eula
 */
class HelloWorld {

    /**
     * Print hello world.
     */
    public function printHello()
    {
        print 'Hello World';
    }

}
```

### `/modules/addons/sample_addon_module/sample_addon_module.php`

```
use WHMCS\Module\Addon\SampleAddonModule\HelloWorld;

// Other code goes here...

function sample_addon_module_output() {
    $hello = new HelloWorld();
    $hello->printHello();
}
```
