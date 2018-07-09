# How to display Brightside CLI help

Brightside CLI contains a help system that is embedded directly into the CLI. When you want help with Brightside CLI, you issue various help commands that provide you with information about Brightside CLI, the usage, syntax, actions, and options. You can also display all help, group-level help, and information about the structure of Brightside CLI syntax.

## Get started with Brightside CLI syntax

If you are using Brightside CLI for first time and want to learn more about how to use the syntax \(and how Brightside CLI works\), open a command line window and issue the following command:

```text
bright help explain brightside
```

To learn how to perform a specific task, or if you want to search for information about a specific command, issue the following command:

```text
bright help search all <term>
```

With this command, Brightside CLI searches and displays help for information about commands, syntax, descriptions, options, and so on.

**Example:**

```text
bright help search all console
```

## Display top-level help

To to display top-level Brightside CLI help, open a command line window and issue the following command:

```text
bright --help
```

\(Optional\) Issue the following command to display top-level Brightside CLI help using the alias for the help command:

```text
bright -h
```

## Display group-level help

You can use group-level help to get more information about a specific command group. Use the following syntax to display group-level help and learn more about specific command groups \(for example, zos-jobs and zos-files\):

```text
bright <group name> --help
```

**Example:**

```text
bright zos-files --help
```

\(Optional\) Issue the following command to view Brightside CLI group-level help using the alias for the help command:

```text
bright compiler -h
```

