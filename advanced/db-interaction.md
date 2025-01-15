+++
next = "/advanced/date-functions/"
prev = "/advanced/authentication/"
title = "Interacting with the Database"
weight = 20

+++

WHMCS 6.0 and later leverages a database connection library to ensure compatibility with modern PHP environments and best practices. It is based on the Laravel framework's database component. This library includes a Database Abstraction Layer (DBAL) called "Capsule" and an Object Relational Mapping (ORM) library called "Eloquent".

The Capsule DBAL component introduces two libraries to WHMCS, a query manager for running database queries and a schema manager for an abstracted API to table management. Capsule's underlying PDO connection is also available for advanced database usage. Capsule has three static methods to get to these components:

* `Capsule::table(string $tableName)`: Access the query manager for the given table.
* `Capsule::schema()`: Access the schema manager for the WHMCS database.
* `Capsule::connection()`: Access the connection manager to interact with the underlying database connection.

## Deprecated functionality

The previously used SQL Helper Functions are still present in WHMCS but are now deprecated and may be removed in a later version of the product:

* **select_query()**
* **update_query()**
* **insert_query()**
* **full_query()**

We encourage all third party developers to use the Capsule DBAL and PDO connection for all new database interaction.

## Using Capsule

Declare an alias to Laravel's database manager in your project file's use block to access Capsule:

```
<?php

use WHMCS\Database\Capsule;

// Run queries or modify tables as you like.
```

## The Query Manager

Please see [Laravel's query documentation](https://laravel.com/docs/7.x/queries) for more information.

The `Capsule::table(string $tableName)` method provides access to the query manager. Declare it with the name of the table you wish to query as it's first parameter to interact with that table. The query manager has a wide range of functionality to perform advanced select, join, insert, update, and delete statements. Capsule's select calls return rows as stdClass objects.

Capsule escapes all input, so it is not necessary to add escaping slashes to variables passed to these methods.

All of Capsule's methods throw an exception on failure. Please place Capsule calls in try/catch blocks for graceful error handling and to avoid potential fatal errors in your hook, module, or other customization.

```
<?php

use WHMCS\Database\Capsule;

// Print all client first names using a simple select.

/** @var stdClass $client */
foreach (Capsule::table('tblclients')->get() as $client) {
    echo $client->firstname . PHP_EOL;
}

// Rename all clients named "John Deo" to "John Doe" using an update statement.
try {
    $updatedUserCount = Capsule::table('tblclients')
        ->where('firstname', 'John')
        ->where('lastname', 'Deo')
        ->update(
            [
                'lastname' => 'Doe',
            ]
        );

    echo "Fixed {$updatedUserCount} misspelled last names.";
} catch (\Exception $e) {
    echo "I couldn't update client names. {$e->getMessage()}";
}
```

## The Schema Manager

Use the `Capsule::schema()` method to access the schema manager to modify table schema if necessary. The schema manager has support for creating, dropping and truncating tables and for modifying columns, indexes, and keys.

**Note:** WHMCS does not recommend changing default table schema as that can affect product functionality.

```
<?php

use WHMCS\Database\Capsule;

// Create a new table.
try {
    Capsule::schema()->create(
        'my_table',
        function ($table) {
            /** @var \Illuminate\Database\Schema\Blueprint $table */
            $table->increments('id');
            $table->string('name');
            $table->integer('serial_number');
            $table->boolean('is_required');
            $table->timestamps();
        }
    );
} catch (\Exception $e) {
    echo "Unable to create my_table: {$e->getMessage()}";
}
```

## The Connection Manager

The `Capsule::connection()` method provides low-level access to the database connection itself. Use it to initiate transactions with automatic commit and rollback or to access the underlying PDO connection to perform manual database queries outside the DBAL. The connection manager also has methods to retrieve query and schema managers.

```
<?php

use WHMCS\Database\Capsule;

// Perform potentially risky queries in a transaction for easy rollback.
try {
    Capsule::connection()->transaction(
        function ($connectionManager)
        {
            /** @var \Illuminate\Database\Connection $connectionManager */
            $connectionManager->table('my_table')->insert(
                [
                    'name' => $_POST['name'],
                    'serial_number' => $_POST['serialNumber'],
                    'is_required' => (int)(bool) $_POST['isRequired'],
                ]
            );
        }
    );
} catch (\Exception $e) {
    echo "Uh oh! Inserting didn't work, but I was able to rollback. {$e->getMessage()}";
}
```

## Getting to PDO

Use the connection manager's getPdo() method to retrieve the underlying PDO connection instance. Use the PDO connection to perform manual queries and advanced database usage.

```
<?php

use WHMCS\Database\Capsule;

// Perform potentially risky queries in a transaction for easy rollback.
$pdo = Capsule::connection()->getPdo();
$pdo->beginTransaction();

try {
    $statement = $pdo->prepare(
        'insert into my_table (name, serial_number, is_required) values (:name, :serialNumber, :isRequired)'
    );

    $statement->execute(
        [
            ':name' => $_POST['name'],
            ':serialNumber' => $_POST['serialNumber'],
            ':isRequired' => (bool) $_POST['isRequired'],
        ]
    );
    if ($pdo->inTransaction()) {
        $pdo->commit();
    }
} catch (\Exception $e) {
    echo "Uh oh! {$e->getMessage()}";
    if ($pdo->inTransaction()) {
        $pdo->rollBack();
    }
}
```

## Troubleshooting

### Exceptions

All Capsule methods throw an exception on failure. Catch these exceptions and analyze their messages and stack traces to help determine the nature of the failure. WHMCS recommends placing all database interactivity in try/catch blocks for graceful error handling.

### The Capsule Query Log

The connection manager's getQueryLog() method returns an array of all queries made during the life of the page request. Queries are stored in the log as an array containing the query run, the parameter bindings passed to the query, and the time it took for the query to execute, measured in milliseconds.

```
<?php

use WHMCS\Database\Capsule;

// Loop through each Capsule query made during the page request.
foreach (Capsule::connection()->getQueryLog() as $query) {
    echo "Query: {$query['query']}" . PHP_EOL;
    echo "Execution Time: {$query['time']}ms" . PHP_EOL;
    echo "Parameters: " . PHP_EOL;

    foreach ($query['bindings'] as $key => $value) {
        echo "{$key} => {$value}" . PHP_EOL;
    }
}
```

### The WHMCS Activity Log

All uncaught PDO-based query failures, including those made by Capsule and manual PDO queries, are written to to the WHMCS activity log. View the system activity log to view the details of these failed queries.
