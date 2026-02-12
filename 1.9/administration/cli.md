---
layout: page
title:  "Command Line Interface (CLI)"
categories: [administration]
---

MyBB packages include a command-line interface (CLI), which provides various administrative tools.

Usage (from MyBB root directory):
```sh
$ bin/cli <command> [options] [arguments]
```

Invoke `bin/cli` to see available options and commands. Use `bin/cli <command> --help` to print help for the given command.

The interface supports [Symfony Console global options](https://symfony.com/doc/current/console/input.html#command-global-options).

## Execution
The command-line interface is a PHP script contained in the `bin/cli` file, relative to the MyBB root directory (which includes folders like `admin/`, `bin/` and `cache/`).

The CLI requires a PHP interpreter and installed Composer dependencies. A MyBB forum installation is not required to run the CLI.

- On Unix-like systems, you may need to make the script executable:
  ```sh
  $ chmod +x bin/cli
  ```
  And invoke it directly:
  ```sh
  $ ./bin/cli <command>
  ```

- On Windows, you can invoke the CLI using the `php` command available on your system:
  ```bat
  > php bin/cli <command>
  ```

## Commands

### `status`
Returns a human-friendly description of the current installation state.

```sh
$ bin/cli status [--code]
```

Possible values:
- _Not installed_
- _Configuration file with no working database connection_
- _Configuration file with valid credentials, no data in database_
- _Installed version ... or newer_

**Options**
- `--code`
  Returns the corresponding integer instead of a human-friendly string.

See also:
- [`InstallationState`](https://github.com/mybb/mybb/blob/dev-1.9/inc/src/Maintenance/InstallationState.php)
