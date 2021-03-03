+++
next = "/advanced/admin-area/"
prev = "/advanced/logging/"
title = "Widgets"
weight = 60

+++

Widgets are the building blocks of the WHMCS Admin Dashboard.

Widgets are pluggable and can be created as part of a custom module.

Widgets that ship with WHMCS by default can be found in the `/modules/widgets/` directory. They are shipped unencoded to allow for expansion and customisation.

## Widget Sample

The following code sample demonstrates how to create a custom widget using a hook file.

```
<?php

/**
 * Standard add_hook call @see https://developers.whmcs.com/hooks/getting-started/
 */
add_hook('AdminHomeWidgets', 1, function() {
    /**
     * Return a new instance of the widget object for display
     */
    return new SampleWidget();
});

/**
 * Sample Widget example
 */
class SampleWidget extends \WHMCS\Module\AbstractWidget
{
    /**
     * @type string The title of the widget
     */
    protected $title = 'Hello World';

    /**
     * @type string A description/purpose of the widget
     */
    protected $description = '';

    /**
     * @type int The sort weighting that determines the output position on the page
     */
    protected $weight = 150;

    /**
     * @type int The number of columns the widget should span (1, 2 or 3)
     */
    protected $columns = 1;

    /**
     * @type bool Set true to enable data caching
     */
    protected $cache = false;

    /**
     * @type int The length of time to cache data for (in seconds)
     */
    protected $cacheExpiry = 120;

    /**
     * @type string The access control permission required to view this widget. Leave blank for no permission.
     * @see Permissions section below.
     */
    protected $requiredPermission = '';

    /**
     * Get Data.
     *
     * Obtain data required to render the widget.
     *
     * We recommend executing queries and API calls within this function to enable
     * you to take advantage of the built-in caching functionality for improved performance.
     *
     * When caching is enabled, this method will be called when the cache is due for
     * a refresh or when the user invokes it.
     *
     * @return array
     */
    public function getData()
    {
        $clients = localAPI('getclients', []);

        return array(
            'welcome' => 'Hello World!',
            'clients' => $clients['clients'],
        );
    }

    /**
     * Generate Output.
     *
     * Generate and return the body output for the widget.
     *
     * @param array $data The data returned by the getData method.
     *
     * @return string
     */
    public function generateOutput($data)
    {
        $clientOutput = [];
        foreach ($data['clients']['client'] as $client) {
            $clientOutput[] = "<a href=\"clientsprofile.php?id={$client['id']}\">{$client['firstname']} {$client['lastname']}</a>";
        }

        if (count($clientOutput) == 0) {
            $clientOutput[] = 'No Clients Found';
        }

        $clientOutput = implode('<br>', $clientOutput);

        return <<<EOF
<div class="widget-content-padded">
    <div>{$data['welcome']}</div>
    <div id="sampleWidgetClientOutput">{$clientOutput}</div>
</div>
EOF;
    }
}


```

### Widget Sample Output

Using the sample code, the widget will output will look something like:

 <img src="../sample-widget-output.png" alt="Widget Output Sample" />

### Naming Convention

The widget filename and folder should be in the same format as PHP class names due to how WHMCS imports the files from the respective folder.

The following file naming conventions are acceptable formats:
```
PascalCase or StudlyCaps
camelCase
snake_case
```

## Permissions

Widgets use the administrator role access control permissions system.

The permission you define for a widget must match one of the access control permissions defined in WHMCS.

The most commonly used permissions are:

* List Clients
* View Clients Summary
* Perform Server Operations
* Perform Registrar Operations
* Add New Order
* Create Invoice
* List Support Tickets
* Configure General Settings

For a full list of permissions, see \WHMCS\User\Admin\Permission::all();

## AbstractWidget

More information on the AbstractWidget class used in the sample can be found at http://docs.whmcs.com/classes/7.1/WHMCS/Module/AbstractWidget.html
