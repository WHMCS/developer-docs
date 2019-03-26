+++
next = "/advanced/widgets/"
prev = "/advanced/logging/"
title = "Using Models"
weight = 55

+++

WHMCS 6.0 introduces a code-driven method for interacting with data stored in the database. Many tables in the WHMCS installation are modeled as classes available both internally to WHMCS and to third party code. These classes, based on the Eloquent ORM library, model tables, columns, and relationships between tables in WHMCS' backend database. Use these classes to easily interact with WHMCS' backend data without the need for complex SQL statements.

A model-based class in WHMCS corresponds to a single table in the database and has properties that map to the columns in that table. For instance, the `\WHMCS\User\Client` class models data in the `tblclients` table. It includes the properties `$id`, `$firstName`, `$lastName`, and others that map to the `id`, `firstname`, `lastname`, and other columns in that table. Model-based classes also have properties that relate to other model-based classes. For example, a client can have more than one domain or contact on their account. The client's $domains and $contacts properties contain collections of `\WHMCS\Domain\Domain` and `\WHMCS\User\Client\Contact` instances, which in turn model data in the `tbldomains` and `tblcontacts` tables, and each have their own column and relational properties.

This page describes basic interactivity with model classes. Please see Laravel's Eloquent ORM manual for a much more detailed reference.

# Table of Contents
1. [Creating Records](#creating-records)
2. [Retrieving Records](#retrieving-records)
3. [Updating Records](#updating-records)
4. [Deleting Records](#deleting-records)
5. [Current Models](#current-models)
6. [See Also](#see-also)

## Creating Records

Creating new records using model-based classes is as simple as creating a local object.

1. Declare a new instance of the class of data to insert.
2. Populate the object's properties.
3. Call the `save()` method to insert the new record into the database.

Models with a primary key have that key automatically populated on save. In most model-based classes the $id property is the classes' primary key. As with all all backend interaction it's helpful to place the save() call in a try/catch block to intelligently handle any error situations.

```
<?php

use WHMCS\User\Client;

$newClient = new Client;
$newClient->firstName = 'John';
$newClient->lastName = 'Doe';
$newClient->email = 'jdoe@example.org';

try {
    $newClient->save();
    echo "I just created John Doe's client record. His id number is {$newClient->id}.";
} catch (Exception $e) {
    echo "Uh oh. I couldn't create John Doe's client record. {$e->getMessage()}";
}
```

## Retrieving Records

Use a model's static find() method to locate a record by its primary key. find() retrieves the record or returns null if the record doesn't exist in the database. Alternatively, use the static findOrFail() method to throw an exception instead of retuning a null value if the record isn't found.

```
<?php

use WHMCS\User\Client;

$clientId = 1234;

// Look for John Doe by id. $johnDoe will be null if id 1234 doesn't exist.
$johnDoe = Client::find($clientId);

// Look for John Doe by id, but throw an exception if id 1234 doesn't exist.
try {
    $johnDoe = Client::findOrFail($clientId);
} catch (Exception $e) {
    echo "I couldn't find John Doe. {$e->getMessage()}";
}
```

Querying for data is also possible with chains of `where()` method calls. Call it statically first with the names of the property and value to search for. End the chain with a `get()` method call to query the database and retrieve a collection of the results.

```
<?php

use WHMCS\User\Client;

// Look for all clients with the name "John Doe".
$johnDoes = Client::where('firstName', 'John')->where('lastName', 'Doe')->get();

foreach ($johnDoes as $john) {
    echo "I found a John Doe from {$john->city}, {$john->state} with the id number {$client->id}.";
}
```

Once models are retrieved then their related properties to other models are also immediately available. Relational model properties in turn have other relational properties that can be chained together in multiple ways.

```
<?php

use WHMCS\User\Client;

$clientId = 1234;
$johnDoe = Client::find($clientId);

echo 'John Doe has ' . $johnDoe->services->count() . ' service(s).';
echo 'John Doe also has ' . $johnDoe->contacts->count() . "contacts. The first one goes by " . $johnDoe->contacts->first()->firstName . '.';

foreach ($johnDoe->services as $service) {
    echo 'Service ' . $service->domain . ' is based from the product ' . $service->product->name . '.';
}
```

## Updating Records

A model's `save()` method can also update existing records in addition to creating new records.

```
<?php

use WHMCS\User\Client;

$clientId = 1234;

try {
    $johnDoe = Client::findOrFail($clientId);

    $johnDoe->address1 = '1234 Main Street';
    $johnDoe->city = 'Anytown';
    $johnDoe->state = 'TX';
    $johnDoe->postcode = '12345';

    $johnDoe->save();

    echo "I've updated John Doe's address.";
} catch (Exception $e) {
    echo "Uh oh. I couldn't update John Doe's address. {$e->getMessage()}";
}
```

## Deleting Records

Call a model object's `delete()` method to delete its associated table row. Deletions are permanent and cannot be undone.

```
<?php

use WHMCS\User\Client;

$clientId = 1234;

try {
    Client::findOrFail($clientId)->delete();
    echo "So long, John!";
} catch (Exception $e) {
    echo "Uh oh. I couldn't delete John Doe's client record. {$e->getMessage()}";
}
```

It is also possible to delete an object's related properties.

```
<?php

use WHMCS\User\Client;

$clientId = 1234;

try {
    // Delete John Doe's first domain.
    Client::findOrFail($clientId)->domains->first()->delete();
    echo "Take that, domain!";
} catch (Exception $e) {
    echo "Uh oh. I couldn't delete John Doe's first domain. {$e->getMessage()}";
}
```

## Current Models

Not every table in WHMCS has an associated model yet. These are the current model classes in WHMCS and their associated tables. This list is updated on new version releases. Please check here often for new functionality.

| Table | Class |
|-------|-------|
| tblaccounts | \WHMCS\Billing\Payment\Transaction |
| tbladmins | \WHMCS\User\Admin |
| tbladminsecurityquestions | \WHMCS\User\Client\SecurityQuestion |
| tblaffiliates | \WHMCS\User\Client\Affiliate |
| tblannouncements | \WHMCS\Announcement\Announcement |
| tblcancelrequests | \WHMCS\Service\CancellationRequest |
| tblclients | \WHMCS\User\Client |
| tblcontacts | \WHMCS\User\Client\Contact |
| tbldomains | \WHMCS\Domain\Domain |
| tbldomainsadditionalfields | \WHMCS\Domain\AdditionalField |
| tbldownloadcats |	\WHMCS\Download\Category |
| tbldownloads | \WHMCS\Download\Download |
| tblemailtemplates | \WHMCS\Mail\Template |
| tblhosting | \WHMCS\Service\Service |
| tblhostingaddons | \WHMCS\Service\Addon |
| tblinvoices |	\WHMCS\Billing\Invoice |
| tblnetworkissues | \WHMCS\Network\NetworkIssue |
| tblproductgroups | \WHMCS\Product\Group |
| tblproducts |	\WHMCS\Product\Product |
| tblquoteitems | \WHMCS\Billing\Quote\Item |
| tblquotes | \WHMCS\Billing\Quote |


## See also

[Internal Class Documentation](https://docs.whmcs.com/classes/)

[Interacting With The Database](https://developers.whmcs.com/advanced/db-interaction/)
