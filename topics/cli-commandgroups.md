# Brightside CLI command groups

Brightside CLI contains command groups that focus on specific business processes that you (application developers and systems programmers) perform during your day-to-day activities. For example, the compiler command group lets you perform tasks that relate to compiling source code on mainframe systems. The projects command group lets you perform tasks that relate to managing source code that you store in version control systems, such as Git and CA Endevor. You can perform all the tasks that relate to these business processes using a unified command-line interface - Brightside CLI.

The command groups contain commands that let you perform actions on specific objects. For each action on an object, you can specify options that you apply as the Brightside CLI commands execute.

In this article, we review all the Brightside CLI command groups and provide you with a brief synopsis of the tasks that you can perform using the commands in each group. For more information see [How to display Brightside CLI help](cli-howtodisplaybrightsidehelp.md). 

**Important:** Before you issue these commands, ensure that you create and [validate your zosmf profile](cli-validateInstallation.md) so that Brightside CLI can communicate with z/OS systems.

Brightside CLI contains the following command groups:

## ca-disk

The ca-disk command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with [CA Disk Backup and Restore](https://docops.ca.com/ca-disk-backup-and-restore/12-5/en) from a familiar command-line interface. To execute commands using the ca-disk command group, [CA Disk Backup and
Restore](https://support.ca.com/cadocs/0/CA%20Disk%20%20Backup%20and%20Restore%2012%205-ENU/Bookshelf.html) must be installed on your system.

With the ca-disk command group, you can perform the following tasks:

  - Archive and restore data sets that you archived using [CA Disk
    Backup and
    Restore](https://docops.ca.com/ca-disk-backup-and-restore/12-5/en).

**Note:** For more information about ca-disk syntax, actions, and options, open Brightside CLI, and issue the following command:

## cics

The cics command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with CICS regions from a familiar command-line interface. 

With the cics command group, you can perform the following tasks:

  - Start or stop a CICS region.
  - Manage CICS resources such as DB2CONN, MQCONN, PROGRAM, and TRANSACTION.
  - Issue MVS modify commands against a CICS region.
  - Run a CICS 3270 MQ Bridge transaction. 
  - Submit batch utilities such as DFHCSDUP.

**Note:** For more information about cics syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright cics -h
```

## compiler

The compiler command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you compile code on mainframe systems. As a developer, you can use Brightside CLI to work on mainframe code locally and compile the code.

With the compiler command group, you can perform the following tasks:

  - Build and compile COBOL (common business-oriented language) and HLASM (IBM High Level Assembler) source code on mainframe systems.

**Note:** For more information about compiler syntax, actions, and options, open Brightside CLI, and issue the following command: 
```
bright compiler -h
```

## config

The config command group lets you display and configure Brightside CLI settings and values to fit your needs. 

With the config command group, you can perform the following tasks:

  - Display the location of the Brightside CLI configuration directory on your PC.
  - Display the status of experimental features and commands (enabled or disabled).
  - Enable and disable experimental features and commands.

**Note:** For more information about config syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright config -h
```

## contribute

The contribute command group lets you generate code that you can contribute to help improve Brightside CLI. 

With the contribute command group, you can perform the following tasks:

  - Submit feedback to the Brightside CLI engineering team.

**Note:** For more information about contribute syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright contribute -h
```

## db2

The db2 command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with the IBM Db2 Databases.

To execute commands in the db2 command group, IBM Db2 Database must be installed and configured on your system. With the db2 command group, you can perform the following tasks:

  - Submit batch jobs to execute Db2 SQL and interact with databases.
  - Export Db2 tables to stdout or a local file on your PC. 
  - Create and manage Db2 profiles that allow you to target specific Db2 regions, libraries, and plan names. To use Db2 commands, you must also specify a basic zosmf profile. 

**Note:** For more information about db2 syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright db2 -h
```

## endevor 

The endevor command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with CA Endevor remotely.

To execute commands in the endevor command group, CA Endevor must be installed and configured on your system. With the endevor command group, you can perform the following tasks:

  - Submit Software Control Language (SCL) to CA Endevor SCM to manage elements, packages, symbols, systems, and more. To learn more about the flexibility of SCL, see the IBM SCL Reference Guide. 
  - Generate, delete, and move CA Endevor elements.

**Note:** For more information about endevor syntax, actions, and options, open Brightside CLI, and issue the following command:

```
bright endevor -h
```

## help

The help command group provides context-sensitive help in Brightside CLI.

With the help command group, you can perform the following tasks:

  - Get general information about Brightside CLI and learn how to create profiles and job cards. 
  - Get context-sensitive help for any command, action, object, and option.
  - Learn about common mainframe terms and concepts. For example, you can display a description of how data set naming conventions work on z/OS.
  - Search all Brightside CLI help text for a specific term or
phrase.

**Note:** For more information, see [How to Display Brightside CLI Help](cli-howtodisplaybrightsidehelp.md).

## ipcs

The ipcs command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with Interactive Problem Control System (IPCS) on z/OS. With the ipcs command group, you can perform the following tasks:

  - Submit a command to IPCS and review the dump data in a data set of your choice. 
  - Parse the IPCS dump data with a JSON options document to isolate specific data.

**Note:** For more information about ipcs syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright ipcs -h
```

## profiles

The profiles command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you create, manage, and validate profiles for use with other Brightside CLI command groups. Profiles allow you to issue commands to different systems quickly, without specifying your connection details with every command.

With the profiles command group, you can perform the following tasks:

  - Create, update, and delete profiles for anyBrightside CLI command group that supports profiles. 
  - Set the default profile to be used within any Brightside CLI command group.
  - List profile names and details for any Brightside CLI command group, including the default active profile.
  - Validate profiles for other Brightside CLI command groups. For more information, see [Validate Installation](cli-validateInstallation.md).

**Note:** For general information about profiles, open Brightside CLI, and issue the following command:
```
bright help explain profiles
```

For more information about profiles syntax, actions, and options, open Brightside CLI, and issue the following commands:
```
bright profiles -h
```

## projects

The projects command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with projects in CA Endevor, Git, or other version control software. If you use Git, a minimum of Git version 2.9 is required.

With the projects command group, you can perform the following tasks:

  - Generate an element from your CA Endevor project.
  - Create/initialize a new project (CA Endevor, Git, Mercurial, or data set) from mainframe source code. 
  - Generate a list of all files that are tracked by the current project.
  - Pull changes from version control software of your choice, or retrieve element listings from CA Endevor. 
  - Synchronize element listings and upload elements to your project.

**Note:** For more information about projects syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright projects -h
```

## provisioning

The provisioning command group lets you perform IBM z/OSMF provisioning tasks with templates and provisioned instances from Brightside CLI.

With the provisioning command group, you can perform the following tasks:

  - Provision cloud instances using z/OSMF Software Services templates.
  - List information about the available z/OSMF Service Catalog published templates and the templates that you used to publish cloud instances.
  - List summary information about the templates that you used to provision cloud instances. You can filter the information by application (for example, DB2 and CICS) and by the external name of the provisioned instances.
  - List detail information about the variables used (and their corresponding values) on named, published cloud instances.

**Note:** For more information about provisioning syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright provisioning -h
```

## zos-console

The zos-console command group lets you issue commands to the z/OS console by establishing an extended Multiple Console Support (MCS) console.

With the zos-console command group, you can perform the following tasks:

**Important!** Before you issue z/OS console commands with Brightside CLI, security administrators should ensure that they provide access to commands that are appropriate for your organization.

  - Issue commands to the z/OS console.
  - Collect command responses and continue to collect solicited command responses on-demand.

**Note:** For more information about zos-console syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright zos-console -h
```

## zos-files

The zos-files command group lets you interact with USS files and data sets on z/OS systems.

With the zos-files command group, you can perform the following tasks:

  - Create partitioned data sets (PDS) with members, physical sequential data sets (PS), and other types of data sets from templates. You can specify options to customize the data sets you create.   
  - Edit data sets locally in your preferred Integrated Development Environment (IDE). Your changes are reflected on the mainframe when you save the local file.
  - Download data sets or USS files from a mainframe to your local PC. 
  - Upload local files to mainframe data sets.
  - Interact with VSAM data sets directly, or invoke Access Methods Services (IDCAMS) to work with VSAM data sets.
  - List data sets, print data sets, and search the contents of a data set. 

**Note:** For more information about zos-console syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright zos-files -h
```

See [Submit a Job and Print Job Output](cli-scenarios.md) for a use-case that demonstrates some zos-files commands.

## zos-jobs

The zos-jobs command group lets you submit jobs and interact with jobs on z/OS systems.

With the zos-jobs command group, you can perform the following tasks:

  - Submit jobs from JCL that resides on the mainframe or a local file.
  - Delete jobs.
  - Download job output to your PC. 
  - List jobs. You can view finished jobs, active jobs, jobs in INPUT status, or all jobs.
  - Print various information about jobs and spool, such as spool content, JCL, JES messages, and more.
  - Create zos-jobs profiles that store your configuration details so that you can quickly interact with jobs.  To use zos-jobs commands, you must also specify a basic zosmf profile. 

**Note:** For more information about zos-jobs syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright zos-jobs -h
```

See [Submit a Job and Print the Job Output](cli-scenarios.md) for a use case that demonstrates some zos-jobs commands.

## zos-ssh

The zos-ssh command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you interact with UNIX System Services (USS) on z/OS systems.

With the zos-ssh command group, you can perform the following tasks:

  - Issue USS commands via SSH (secure shell) protocol. 

**Note:** For more information about zos-ssh syntax, actions, and options, open Brightside CLI and issue the following command:
```
bright zos-ssh -h
```

## zos-tso

The zos-tso command group lets you issue TSO commands and interact with TSO address spaces on z/OS systems.

With the zos-tso command group, you can perform the following tasks:

  - Create a TSO address space and issue TSO commands to the address space.
  - Review TSO command response data in Brightside CLI.

**Note:** For more information about zos-tso syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright zos-tso -h
```

## zos-utils

The zos-utils command group is an [experimental command group](cli-enabledisablexperimentalcommands.md) that lets you use common mainframe utilities remotely.

With the zos-utils command group, you can perform the following tasks:

  - Transfer a file across systems with a File Transfer Protocol (FTP) command. 
  - Copy data between data sets with the IEBCOPY utility.
  - Overwrite content in a data set with the IMASZAP utility.

**Note:** For more information about zos-utils syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright zos-utils -h
```

## zosmf

The zosmf command group lets you work with Brightside CLI profiles and get general information about z/OSMF.

With the zosmf command group, you can perform the following tasks:

  - Create and manage your Brightside CLI zosmf profiles. You must have at least one zosmf profile to issue most commands. Issue the `bright help explain profiles` command in Brightside CLI to learn more about using profiles.
  - Verify that your profiles are set up correctly to communicate with z/OSMF on your system. For more information, see [Validate Installation](cli-validateInstallation.md).
  - Get information about the current z/OSMF version, host, port, and plug-ins installed on your
system.

**Note:** For more information about zosmf syntax, actions, and options, open Brightside CLI, and issue the following command:
```
bright zosmf -h
```

