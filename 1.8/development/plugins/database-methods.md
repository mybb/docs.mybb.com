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
    <dt>query</dt>
    <dd>The resource query.</dd>
</dl>

It is preferable to use a count query then do $db->fetch_field to get this value.

## `$db->insert_id`

Returns the insert id (The id of the primary key) of the insert query just run.

## `$db->insert_query`

Runs an insert query on a table in a database. Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name to perform the query on.</dd>

    <dt>array</dt>
    <dd>An array of fields and their values.</dd>
</dl>

## `$db->insert_query_multiple`

Runs an insert query on a table in the database.  Multiple rows can be inserted with one query. Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name to perform the query on.</dd>

    <dt>array</dt>
    <dd>A multidimensional array of fields and values.  Each array key for the individual arrays must be the same, even if blank.</dd>
</dl>

## `$db->update_query`

Runs an update query on a table in a database.  It receives five parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>array</dt>
    <dd>An array of fields and their values.</dd>

    <dt>where</dt>
    <dd>The SQL where clause.</dd>

    <dt>limit</dt>
    <dd>An optional limit clause.</dd>

    <dt>no_quote</dt>
    <dd>An option to quote incoming values of the array.</dd>
</dl>

## `$db->delete_query`

Used to perform a delete query on a table in a database.  Receives three parameters:

<dl>
    <dt>table</dt>
    <dd>The name of the table.</dd>

    <dt>where</dt>
    <dd>The where clause.</dd>

    <dt>limit</dt>
    <dd>The maximum amount of rows to be deleted.  Default is unlimited.</dd>
</dl>

## `$db->escape_string`

Replaces addslashes, escapes data before being used in a query according to the SQL escape format for the database being used.  Receives one parameter:

<dl>
    <dt>string</dt>
    <dd>The string to be escaped.</dd>
</dl>

## `$db->free_result`

Frees the resources of an SQL query.  Receives one parameter:

<dl>
    <dt>query</dt>
    <dd>The query to destroy.</dd>
</dl>

## `$db->escape_string_like`

Escapse a string used within a like command.  Receives one parameter:

<dl>
    <dt>string</dt>
    <dd>The string to be escaped.</dd>
</dl>

## `$db->connect`

Connects a new database.

## `$db->select_db`

Selects the database for the current SQL session.  Receives one parameter:

<dl>
    <dt>database</dt>
    <dd>The database name.</dd>
</dl>

## `$db->explain_query`

Helps to explain queries run from on database from the current session for debugging purposes.  Receives two parameters:

<dl>
    <dt>string</dt>
    <dd>The query SQL.</dd>

    <dt>qtime</dt>
    <dd>The time it took to perform the query.</dd>
</dl>

## `$db->data_seek`

Moves the internal pointer to the specified row.  Receives two parameters:

<dl>
    <dt>query</dt>
    <dd>The resource query.</dd>

    <dt>row</dt>
    <dd>The row to move the internal pointer to.</dd>
</dl>

## `$db->close`

Closes the connection to the currently open database.

## `$db->error_number`

Returns the error number (if any) of the specified query resource.

## `$db->error_string`

Returns the error string (if any) of the specified query resource.

## `$db->error`

Output a database error.  Receives one parameter:

<dl>
    <dt>string</dt>
    <dd>The string to present as an error.</dd>
</dl>

## `$db->affected_rows`

Returns the amount of affected rows from a "write" query.

## `$db->num_fields`

Returns the number of fields of the specified query resource.  Receives one parameter:

<dl>
    <dt>query</dt>
    <dd>The query data.</dd>
</dl>


## `$db->list_tables`

Returns the tables in the current open database.  Receives two parameters:

<dl>
    <dt>database</dt>
    <dd>The database name.</dd>

    <dt>prefix</dt>
    <dd>Prefix of the table (optional).</dd>
</dl>

## `$db->table_exists`

Returns true if the specified table exists.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->field_exists`

Returns true if the specified field exists.  Receives two parameters:

<dl>
    <dt>field</dt>
    <dd>The field name.</dd>

    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->shutdown_query`

Runs a query thats performed when PHP is done parsing the file.  Receives two parameters:

<dl>
    <dt>query</dt>
    <dd>The query data.</dd>

    <dt>name</dt>
    <dd>An optional name for the query.</dd>
</dl>

## `$db->get_version`

Returns the version number of the database server being used.

## `$db->optimize_table`

Runs an optimize query on a table.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->analyze_table`

Runs an analyze query on a table.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->show_create_table`

Return the "create table" command for a specific table.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->show_fields_from`

Show the "show fields from" command for a specific table.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->is_fulltext`

Returns whether or not the table contains a fulltext index.  Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>index</dt>
    <dd>Optionally specify the name of the index.</dd>
</dl>

## `$db->supports_fulltext`

Returns whether or not this database engine supports fulltext indexing.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->supports_fulltext_boolean`

Returns whether or not this database engine supports boolean fulltext matching.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>
</dl>

## `$db->index_exists`

Checks to see if an index exists on a specified table.  Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>index</dt>
    <dd>The name of the index.</dd>
</dl>

## `$db->create_fulltext_index`

Creates a fulltext index on the specified column in the specified table with optional index name.  Receives three parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>column</dt>
    <dd>Name of the column to be indexed.</dd>

    <dt>name</dt>
    <dd>Optional index name.</dd>
</dl>

## `$db->drop_index`

Drop an index with the specified name from the specified table.  Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>index</dt>
    <dd>The name of the index.</dd>
</dl>

## `$db->add_column`

Adds a new column to the specified table.  Receives three parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>column</dt>
    <dd>The column name.</dd>

    <dt>definition</dt>
    <dd>The new column definition.</dd>
</dl>

## `$db->modify_column`

Changes the definition of the specified column in the specified table.  Receives three parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>column</dt>
    <dd>The column name.</dd>

    <dt>definition</dt>
    <dd>The new column definition.</dd>
</dl>

## `$db->rename_column`

Renames the specified column.  Receives four parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>old_column</dt>
    <dd>The old column name.</dd>

    <dt>new_column</dt>
    <dd>The new column name.</dd>

    <dt>definition</dt>
    <dd>The new column definition.</dd>
</dl>

## `$db->drop_column`

Drops the specified column from the specified table.  Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>column</dt>
    <dd>The column name.</dd>
</dl>

## `$db->rename_table`

Renames the specified table.  Receives three parameters:

<dl>
    <dt>old_table</dt>
    <dd>The old table name.</dd>

    <dt>new_table</dt>
    <dd>The new table name.</dd>

    <dt>table_prefix</dt>
    <dd>Add table prefix to query. Defaults to true.</dd>
</dl>

## `$db->drop_table`

Drops the specified table.  Receives three parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>hard</dt>
    <dd>Option to perform a hard drop (does not check to see if table exists). Defaults to false.</dd>

    <dt>table_prefix</dt>
    <dd>Add table prefix to query. Defaults to true.</dd>
</dl>

## `$db->replace_query`

Replaces the current contents of table with new values.  Receives two parameters:

<dl>
    <dt>table</dt>
    <dd>The table name.</dd>

    <dt>replacements</dt>
    <dd>An array of fields and their new values.</dd>
</dl>

## `$db->set_table_prefix`

Sets the table prefix used by the simple select, insert, update and delete functions.  Receives one parameter:

<dl>
    <dt>prefix</dt>
    <dd>The new table prefix.</dd>
</dl>

## `$db->fetch_size`

Fetched the total size of all mysql tables or a specific table.  Receives one parameter:

<dl>
    <dt>table</dt>
    <dd>The table name (optional).</dd>
</dl>

## `$db->fetch_db_charsets`

Fetch a list of database character sets this DBMS supports.

## `$db->fetch_charset_collation`

Fetch a database collation for a particular database character set.  Receives one parameter:

<dl>
    <dt>charset</dt>
    <dd>The database character set.</dd>
</dl>

## `$db->build_create_table_collation`

Fetch a character set/collation string for use with CREATE TABLE statements. Uses current DB encoding.

## `$db->get_execution_time`

Time how long it takes for a particular piece of code to run. Place calls above & below the block of code.

## `$db->escape_binary`

Escapes a binary database fields (such as IP addresses).  Receives one parameter:

<dl>
    <dt>string</dt>
    <dd>The binary value.</dd>
</dl>

## `$db->unescape_binary`

Unescape binary data.  Receives one parameter:

<dl>
    <dt>string</dt>
    <dd>The binary value.</dd>
</dl>
