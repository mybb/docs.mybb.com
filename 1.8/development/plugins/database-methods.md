---
layout: page
title:  "Database Methods"
categories: [plugins]
---

The database class provides a wrapper of most common functions used for database access, and also others which simplify common queries. All queries performed with the database through the database abstraction layer can be analyzed for the execution time and further optimization.

## `$db->query`

Executes an SQL query with your database. Note that the `write_query` method is now preferred.

## `$db->write_query`

Similar to the `query` method, except `write_query` executes the query on the slave database in case you happen to have a multi-database server setup. `write_query` is now preferred over `query`.

## `$db->simple_select`

Used to perform a simple select query (with no joins) on a table.

It receives four parameters:

<dl>
    <dt>table</dt>
    <dd>The table name to be queried.</dd>

    <dt>field(s)</dt>
    <dd>Comma delimited list of fields to be selected.</dd>

    <dt>conditions</dt>
    <dd>SQL formatted list of conditions to be matched.</dd>

    <dt>options</dt>
    <dd>List of options: group by, order by, order direction, limit, limit start. Returns a resource on success, or false on error.</dd>
</dl>

### Example

```php
global $db;

$query = $db->simple_select("settings", "*", "name='boardclosed_reason'", array(
    "order_by" => 'name',
    "order_dir" => 'DESC',
    "limit" => 1
));

$settings = $db->fetch_array($query);

echo "<pre>";
print_r($settings);
echo "</pre>";
```

### Output

```php
Array
(
    [sid] => 6
    [name] => boardclosed_reason
    [title] => Board Closed Reason
    [description] => If your forum is closed, you can set a message here that your visitors will be able to see when they visit your forums.
    [optionscode] => textarea
    [value] => These forums are currently closed for maintenance. Please check back later.
    [disporder] => 2
    [gid] => 2
)
```

## `$db->fetch_array`

Returns an array of values for the first row (can be iterated through with a while statement).

### Example

```php
$query = $db->query("SELECT * FROM table WHERE field='value'");

while($result = $db->fetch_array($query))
{
    $data1 = $result['FieldName1'];
    $data2 = $result['FieldName2'];
    // ...
}
```

## `$db->fetch_field`

Returns the value of the field specified from the resource query.  Receives three parameters:

<dl>
    <dt>resource</dt>
    <dd>The resource query.</dd>
    
    <dt>field</dt>
    <dd>The field name to retrieve.</dd>
    
    <dt>row</dt>
    <dd>The row number to get the data from.  Default is current row.</dd>
</dl>

## `$db->num_rows`

Returns the number of rows in the query.  Receives one parameter:

<dl>
    <dt>resource</dt>
    <dd>The resource query.</dd>
</dl>

It is preferable to use a count query then do $db->fetch_field to get this value.

## `$db->insert_id`

Returns the insert id (The id of the primary key) of the insert query just run.

## `$db->insert_query`

Runs an insert query on a table in a database. Receives two parameters:

<dl>
    <dt>string</dt>
    <dd>The table name to perform the query on.</dd>

    <dt>array</dt>
    <dd>An array of fields and their values.</dd>
</dl>

## `$db->insert_query_multiple`

Runs an insert query on a table in the database.  Multiple rows can be inserted with one query. Receives two parameters:

<dl>
    <dt>string</dt>
    <dd>The table name to perform the query on.</dd>
    
    <dt>array</dt>
    <dd>A multidimensional array of fields and values.  Each array key for the individual arrays must be the same, even if blank.

## `$db->update_query`

Runs an update query on a table in a database.

It receives three parameters:

* the table name
* an update array
* the `WHERE` clause

## `$db->delete_query`

Used to perform a delete query on a table in a database.  Receives three parameters:

<dl>
    <dt>string</dt>
    <dd>The name of the table.</dd>
    
    <dt>string</dt>
    <dd>The where clause.</dd>
    
    <dt>limit</dt>
    <dd>The maximum amount of rows to be deleted.  Default is unlimited.</dd>
</dl>

## `$db->escape_string`

Replaces addslashes, escapes data before being used in a query.

## `$db->connect`

Connects a new database.

## `$db->select_db`

Selects the database for the current MySQL Session

## `$db->explain_query`

Helps to explain queries run from on database from the current session for debugging purposes.

## `$db->data_seek`

Moves the internal pointer to the specified row.  Receives two parameters:

<dl>
    <dt>resource</dt>
    <dd>The resource query.</dd>
    
    <dt>int</dt>
    <dd>The row to move the internal pointer to.</dd>
</dl>

## `$db->close`

Closes the connection to the currently open database.

## `$db->error_number`

Returns the error number (if any) of the specified query resource.

## `$db->error`

Returns the error string (if any) of the specified query resource.

## `$db->dberror`

Outputs an error message (if any) of the specified query resource.

## `$db->affected_rows`

Returns the amount of affected rows from a "write" query.

## `$db->num_fields`

Returns the number of fields of the specified query resource.

## `$db->list_tables`

Returns the tables in the current open database.

## `$db->table_exists`

Returns true if the specified table exists.

## `$db->field_exists`

Returns true if the specified field exists.

## `$db->shutdown_query`

Runs a query thats performed when php is done parsing the file.

## `$db->select_query`

Runs a complex query (join queries). (Note: Depreciated in MyBB 1.4).

## `$db->get_version`

Returns the version number of the database server being used.

## `$db->optimize_table`

Runs an optimize query on a table.

## `$db->analyze_table`

Runs an analyze query on a table.

## `$db->show_create_table`

Return the "create table" command for a specific table.

## `$db->show_fields_from`

Show the "show fields from" command for a specific table.

## `$db->is_fulltext`

Returns whether or not the table contains a fulltext index.

## `$db->supports_fulltext`

Returns whether or not this database engine supports fulltext indexing.

## `$db->supports_fulltext_boolean`

Returns whether or not this database engine supports boolean fulltext matching.

## `$db->create_fulltext_index`

Creates a fulltext index on the specified column in the specified table with optional index name.

## `$db->drop_index`

Drop an index with the specified name from the specified table.

## `$db->add_column`

Adds a new column to the specified table.

## `$db->modify_column`

Changes the definition of the specified column in the specified table.

## `$db->rename_column`

Renames the specified column.

## `$db->drop_column`

Drops the specified column from the specified table.

## `$db->rename_table`

Renames the specified table.

## `$db->drop_table`

Drops the specified table.
