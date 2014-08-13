---
layout: page
title:  "Database Methods"
categories: [plugins]
---

The database class provides a wrapper of most common functions used for database access, and also others which simplify common queries. All queries performed with the database through the database abstraction layer can be analyzed for the execution time and further optimization.

## Commonly Used

<dl>
    <dt>$db->query</dt>
    <dd>Executes an SQL query with your database. Note that the write_query method is now preferred.</dd>

    <dt>$db->write_query</dt>
    <dd>Similar to the query method, except write_query executes the query on the slave database in case you happen to have a multi-database server setup. write_query is now preferred over query.</dd>

    <dt>$db->simple_select</dt>
    <dd>
        <dt>Used to perform a simple select query (with no joins) on a table.</dt>

        <dd>`string simple_select ( string table [,string field(s)] [, string conditions] [, array options])`</dd>

        <dt>Builds a simple query, then sends it off to $db->query().</dt>

        <dt>table</dt>
        <dd>The table name to be queried.</dd>

        <dt>field(s)</dt>
        <dd>Comma delimetered list of fields to be selected.</dd>

        <dt>conditions</dt>
        <dd>SQL formatted list of conditions to be matched.</dd>

        <dt>options</dt>
        <dd>List of options: order by, order direction, limit, limit start
        Returns a resource on success, or FALSE on error.</dd>

        ```php

            global $db;

            $query = $db->simple_select("settings", "*", "name='boardclosed_reason'", array(
                "order_by" => 'name',
                "order_dir" => 'DESC',
                "limit" => 1
                )
            );

            $settings = $db->fetch_array($query);

            echo "<pre>";
            print_r($settings);
            echo "</pre>";

        ```
            <dt>Outputs:</dt>
			<dd>
			`
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
            `
			</dd>
    </dd>

    <dt>$db->fetch_array</dt>
    <dd>
        Returns an array of values for the first row (can be iterated through with a while statement).

        Example:
		```php
            $query = $db->query("SELECT * FROM Table [WHERE Field='Value']");
            while($result = $db->fetch_array($query))
            {
                $data1 = $result['FieldName1'];
                $data2 = $result['FieldName2'];
                // etc.
            }
		```
    </dd>

    <dt>$db->fetch_field</dt>
    <dd>See Fetch_Field.</dd>

    <dt>$db->num_rows</dt>
    <dd>Returns the number of rows in the query</dd>

    <dt>$db->insert_id</dt>
    <dd>Returns the insert id (The id of the primary key) of the insert query just run.</dd>

    <dt>$db->insert_query</dt>
    <dd>
        Runs an insert query on a table in a database. Receive two parameters:

        - string - The table name to perform the query on.
        - array - An array of fields and their values.

        Build an insert query from the array and executes the query using $db->query
    </dd>

    <dt>$db->update_query</dt>
    <dd>
        Runs an update query on a table in a database.
        Parameters: ('table name', 'update array', 'conditional')
    </dd>

    <dt>$db->delete_query</dt>
    <dd>Used to perform a delete query on a table in a database.</dd>

    <dt>$db->escape_string</dt>
    <dd>Replaces addslashes, escapes data before being used in a query.</dd>
</dl>

## Others

<dt>$db->connect</dt>
<dd>Connects a new database.</dd>

<dt>$db->select_db</dt>
<dd>Selects the database for the current MySQL Session</dd>

<dt>$db->explain_query</dt>
<dd>Helps to explain queries run from on database from the current session for debugging purposes.</dd>

<dt>$db->data_seek</dt>
<dd>Moves the internal pointer to the specified column.</dd>

<dt>$db->close</dt>
<dd>Closes the connection to the currently open database.</dd>

<dt>$db->error_number</dt>
<dd>Returns the error number (if any) of the specified query resource.</dd>

<dt>$db->error</dt>
<dd>Returns the error string (if any) of the specified query resource.</dd>

<dt>$db->dberror</dt>
<dd>Outputs an error message (if any) of the specified query resource.</dd>

<dt>$db->affected_rows</dt>
<dd>Returns the amount of affected rows from a "write" query.</dd>

<dt>$db->num_fields</dt>
<dd>Returns the number of fields of the specified query resource.</dd>

<dt>$db->list_tables</dt>
<dd>Returns the tables in the current open database.</dd>

<dt>$db->table_exists</dt>
<dd>Returns true if the specified table exists.</dd>

<dt>$db->field_exists</dt>
<dd>Returns true if the specified field exists.</dd>

<dt>$db->shutdown_query</dt>
<dd>Runs a query thats performed when php is done parsing the file.</dd>

<dt>$db->select_query</dt>
<dd>Runs a complex query (join queries). (Note: Depreciated in MyBB 1.4).</dd>

<dt>$db->get_version</dt>
<dd>Returns the version number of the database server being used.</dd>

<dt>$db->optimize_table</dt>
<dd>Runs an optimize query on a table.</dd>

<dt>$db->analyze_table</dt>
<dd>Runs an analyze query on a table.</dd>

<dt>$db->show_create_table</dt>
<dd>Return the "create table" command for a specific table.</dd>

<dt>$db->show_fields_from</dt>
<dd>Show the "show fields from" command for a specific table.</dd>

<dt>$db->is_fulltext</dt>
<dd>Returns whether or not the table contains a fulltext index.</dd>

<dt>$db->supports_fulltext</dt>
<dd>Returns whether or not this database engine supports fulltext indexing.</dd>

<dt>$db->supports_fulltext_boolean</dt>
<dd>Returns whether or not this database engine supports boolean fulltext matching.</dd>

<dt>$db->create_fulltext_index</dt>
<dd>Creates a fulltext index on the specified column in the specified table with optional index name.</dd>

<dt>$db->drop_index</dt>
<dd>Drop an index with the specified name from the specified table.</dd>

<dt>$db->add_column</dt>
<dd>Adds a new column to the specified table.</dd>

<dt>$db->modify_column</dt>
<dd>Changes the definition of the specified column in the specified table.</dd>

<dt>$db->rename_column</dt>
<dd>Renames the specified column.</dd>

<dt>$db->drop_column</dt>
<dd>Drops the specified column from the specified table.</dd>

<dt>$db->rename_table</dt>
<dd>Renames the specified table.</dd>

<dt>$db->drop_table</dt>
<dd>Drops the specified table.</dd>
