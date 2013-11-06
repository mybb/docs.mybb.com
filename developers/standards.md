---
layout: page
title: Development Standards
---

The purpose of this document is to outline the development standards for use whilst developing MyBB. Plugin and modification authors are recommended to use these coding standards when developing plugins and modifications.

These coding standards were written for the MyBB 1.4.x, 1.6.x and 1.8.x series.

## Coding Standards

### File Formats

All files must be saved as UNIX formatted files using the ASCII character set.

### Indenting

All indentation should be performed using the [TAB] key. The text editor should also be set to save tabs and indentation as the TAB character and not spaces.

### New Lines

All new lines should be the UNIX line feed (`\n`) and not the Windows carriage return (`\r`).

### Whitespace

Whitespace (new lines) should be used to separate logical areas of code so that it’s easier to read.

Trailing whitespace on the end of lines or end of files is not permitted. Most text editors have a preference to automatically trim trailing whitespace.

### PHP Code Demarcation

Short PHP open and close tags (`<? ?>` or `<?= ?>`) are not permitted. To 
delimit PHP code, the full `<?php ?>` tags must be used as this is the most portable way to include PHP code on differing PHP configurations.

### Strings

When a string is literal (contains no variable substitutions), the apostrophe or ‘single quote’ must be used to demarcate the string:

    $a = 'Example String';

When a literal string itself contains apostrophes, it is permitted to demarcate the string with quotation marks or “double quotes”. This is especially encouraged for SQL statements:

    $query = "SELECT id, name FROM people WHERE name='Joe Bloggs'";

Variable substitution is permitted in strings using either of the following forms:

    $example = "Hello ".$name.", welcome back";
    $example = 'Hello '.$name.', welcome back!';
    $example = "Hello {$name}, welcome back!";

String concatenation should be performed by terminating the string with a period (`.`). To help improve readability, if concatenation is required in a large string, it’s recommended to separate it in to appended variables:

    $example = 'Hello'; $example .= $name;

### Variables

Variable names may only contain alphanumeric characters. To promote variable readability, underscores may be used in variable names to indicate a space or new word.

For class member variables, the variable declaration must be prefixed as either public, private or protected. Declaration as var, is discouraged. Examples include:

    $var = "example";

    class Example {
        private $sample_variable = true;
        public $example_variable_name = 'sample';
    }

Verbosity is encouraged. Variables should always be as verbose as possible to describe what they contain. Terse variable names such as `$i` and `$n` are discouraged for anything other than small loop contexts. The use of variables such as $tmp and $temp are also not permitted.

### Arrays

Array item declarations should each be on their own new line and indented to promote readability in the block.

    $array = array(
        "item"  => "value",
        "item2" => array(
            1,
            2
        )
    );

### Control Structures

Control structures include `if`, `for`, `while`, and `switch` statements. Curly braces should always be used even in situations where they are optional. Ternary operators are not permitted and should not be used.

Within a control structure, operators must be separated by spaces for readability. The opening brace must be written on its own line directly under the conditional. The closing brace is also written on its own line. Any content within braces must be indented.

    if($example != "sample")
    {
        $example = "sample";
    }
    else {
        $example = "test";
    }

Control structures should be kept as simple as possible and large nested if structures should also be avoided. An alternative to using an `else` would be to return before the if statement.

Example switch statement:

    switch($example) {
        case "example":
            $example = "sample";
            break;
    }

For the sake of code simplicity, variable assignment in conditionals is also not supported. The variable should be assigned out of the conditional and the conditional simply check the variable value. For example:

    if(($result = $db->query("SELECT * FROM table")) && ($row = $db->fetch_array($result)) && $example == 1)
    {
        // Example
    }

Should be written as:

    $result = $db->query(“SELECT * FROM table”);
    $row = $db->fetch_array($query);

    if($row && $example == 1)
    {
        // Example
    }

### Functions and Methods

Function names may only contain lowercase alphanumeric characters. Underscores are also permitted to increase function naming readability and should be used when a function name consists of more than one word. The opening brace for a function should be placed on a new line.

Every function must have a documentation block that conforms to the PHPDocumentor standard (covered below).

Function names should start with a verb describing the action that is being performed. Acceptable function names include:

- `filter_input()`
- `get_element_by_id()`
- `cache_file()`
- `get_thread()`

When calling a function, arguments should be separated by spaces:

    $example = get_thread($terms, $argument2);
    $threads->get_threads($terms, $argument3);

With regards to including/requiring files, the language construct should be used over the function.

    require_once(MYBB_ROOT."inc/functions.php"); // Function

    require_once MYBB_ROOT."inc/functions.php"; // Language construct

### Passing by Reference

Passing variables by reference to functions/methods is permitted on the following terms:

- The function needs to modify/return several variables and returning an array of the data is not plausible.
- The function does not contain a true/false return value. In this case, the return value of the function should be the variable or false in the case of an error.

### Class Declarations

Class names should be as descriptive as possible. Avoid using abbreviations where possible. Class names should begin with an uppercase character and words should be separated by an underscore. The brace must always be written on the line underneath the class name (“one true brace” form).

Every class must have a documentation block that conforms to the PHPDocumentator standard (covered below).

    class Plugin_System {
        private $example;
    }

### Constants

Constants may contain both underscores and alphanumeric characters. All letters must be capitalized and to enhance readability, words in constant names must be separated by underscore characters. For example, `MYBB_ROOT`.

Boolean and null value constants (`true`, `false` and `null`), however, should be completely lowercase.

### Comments

Non-documentation comments are strongly encouraged. As a general rule of thumb, if you look at a block of code and think “Wow, I don’t want to try and describe that”, it obviously needs to be commented to explain what’s happening.

C style comments (`/* */`) and standard C++ comments (`//`) are both permitted whilst the use of Perl and shell style comments (`#`) are not.

### Regular Expressions

Use of the POSIX Extended based regular expression functions (`eregi()`, `eregi_replace()`, etc) is not permitted. Instead, the Perl Compatible (PCRE) regular expression functions such as `preg_replace()`, `preg_match()` should be used.

Regular expression patterns should be encapsulated in single quotes (although double are permitted) to prevent the possibility of interference with reserved PHP characters (such as `$`).

Careful attention needs to be paid when using regular expressions, as there may be a standard PHP string or other function that performs the same task much quicker than a regular expression.

### Arithmetic Operators

When increasing or decreasing the value of a variable, the arithmetic operator (`++` or `--`) should be on the left hand side of the variable. For example:

    $test = 1;
    ++$test;

    echo $test // Will echo 2

### Banned Practices

It is not permitted to use the `sprintf()` function for variable substitution in strings. Instead, standard string concatenation should be used. Use of a `sprintf()` statement with 20 replacement values spread over 10 lines is far more difficult to maintain than substituted variables.
Use of the ereg regular expression library is also not permitted. Instead, the PCRE regular expression library should be used.

### Sanitizing Data for Output

Before any data is output to the browser that has had the possibility of user-manipulation (such as data pulled from the database that has been previously inserted through a web interface), the data must be cleaned/filtered to its expected format.

For example, if you are expecting an integer, you may typecast the item to that format:

    $variable = (int)$variable;

For other kinds of data, such as a thread name where the value is user generated text, it should be sanitized using the `htmlspecialchars_uni()` function that will replace unwanted characters with their HTML entity equivalents:

    $variable = htmlspecialchars_uni($variable);

### PHPDocumenter Standards

PHPDoc comments are a way of documenting what a function, class, or variable is used for. They’re used to build developer documentation and provide general reference.

Preceding every function, class or method declaration, there should be an associated PHPDoc comment block. The documentation block must describe the function (on one or more lines), provide a list of parameter variables and a possible return values.

Each line of the PHPDoc comment must contain an asterisk that sits below the previous asterisk.

    /**
     *
     */

#### Class Member Variables

The accepted format for class member variables (`@var`) is as follows:

    @var (lowercase variable type) (variable description)
    @access (public|private|protected)

For example:

    @var object The database object.
    @access private

#### Parameter Variables

The accepted format for parameter variables (@param) is as follows:

    @param (lowercase variable type) (variable description)

For example:

    @param string The name of the thread to search for.

#### Return Value

The accepted format for the return value (@return) is as follows:

    @return (lowercase variable type) (variable description)

For example:

    @return array Array of matching threads.

#### Example

A complete example is shown below.

    /**
     * A class for searching for threads in the database.
     */
    class Thread_Search
    {
        /**
         * @var object The database object.
         * @access private
         */
        private $db;
        
        /**
         * Get a list of threads with the specified name.
         *
         * @param string The thread name to search for.
         * @param int Find threads in this particular forum (Forum ID)
         * @return array An array of matching threads.
         */
        public function get_threads($terms, $forum_id=0)
        {
            // ...
        }
    }

## Database Standards

### Database Queries

Database queries should be broken up over multiple lines to promote code readability. Reserved words such as `SELECT`, `WHERE` and `ORDER BY` should be written us uppercase characters. Table and column names may be lowercase. All variable values must be enclosed within quotes. Each query should start on a new line, indented from the variable above to also promote readability. An example is shown below.

    $query = " SELECT * FROM test ";
    $query = "SELECT t1.column1, t2.column2 FROM table1 t1 LEFT JOIN table2 t2 ON (t1.column1=t2.column2) ORDER BY t1.column1 ASC; ";

### Simple Select Queries

Database select queries which do not involve any joins or advanced grouping, etc can use `simple_select()`. This method takes a table name, the rows to be returned, a where clause and an array of ordering and limiting options. Example use is as follows:

    $query = $db->simple_select("table", "*", "id='123'", array(
        'order_by' => 'column2',
        'order_dir' => 'DESC',
        'limit_start' => 0,
        'limit' => 5
    ));

### Insert Queries

Database insert queries should be performed using the `insert_query()` method. This method takes both a table name and an associative array of values to be inserted. Values *must* be escaped using the `escape_string` method. Example use is as follows:

    $new_record = array(
        "column" => $db->escape_string('test'),
        "column2" => 1
    );
    
    $db->insert_query('table', $new_record);

### Update Queries

Update queries follow a similar structure to insert queries, however make use of the `update_query()` method. This method takes a table name, an associative array of values to update, and optionally any conditions that must be matched (the `WHERE` clause of an update query).

Values *must* be escaped and any conditions need to be explicitly escaped using the `escape_string()` method. Example use is as follows:

    $updated_record = array(
        "column" => $db->escape_string('Value')
    );

    $db->update_query('table', $updated_record, "condition1='".$db->escape_string('test')."'");

### Delete Queries

Delete queries should be performed using the `delete_query()` method. This method takes the table name, and optionally any conditions that will need to be matched. The conditions need to be escaped using the `escape_string()` method as mentioned below. Example use is as follows:

    $db->delete_query('table', 'condition1=value1');

### Sanitization

Before any data, values or variables are used within a query they must be adequately escaped or formatted to their required value for that column. In some cases this may mean typecasting the value to an integer or calling the `escape_string()` method of the database class to sanitize (escape) the content of the string.