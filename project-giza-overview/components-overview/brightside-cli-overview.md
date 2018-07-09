# Brightside CLI Overview

Brightside Command Line Interface \(Brightside CLI\) lets application developers interact with the mainframe in a format that is natively familiar to them. Brightside CLI helps to increase overall productivity, reduce the learning curve for developing mainframe applications, and exploit the ease-of-use of off-platform tools. Brightside CLI lets application developers use common tools such as Integrated Development Environments \(IDEs\), shell commands, bash scripts, and build tools for mainframe development. It provides a set of utilities and services for application developers who need to quickly become efficient in supporting and building z/OS applications.

Brightside CLI provides the following benefits:

* Enables and encourages developers with limited z/OS expertise to

  build, modify, and debug z/OS applications.

* Fosters the development of new and innovative tools from a personal

  computer that can interact with z/OS operating systems.

* Ensure that business critical applications running on z/OS can be

  maintained and supported by existing and generally available

  software development resources.

* Provides a more streamlined way to build software that integrates

  with z/OS platforms. 

The following sections explain the key features and details for Brightside CLI.

**Note:** For installation, upgrade, and software requirements, see [Installing Brightside CLI](../../installing-project-giza/installing-components-of-project-giza/installing-brightside-cli.md).

## Solution video

Watch this [short video](https://www.youtube.com/watch?v=0MvAv5ApolI) about how Brightside CLI works.

## Brightside CLI capabilities

With Brightside CLI, you can interact with z/OS remotely in the following ways:

* **Interact with mainframe files**

  Create, edit, download, and upload mainframe files \(data sets\) directly from Brightside CLI.

* **Submit jobs**

  Submit JCL from data sets or local storage, monitor the status, and view and download the output automatically.

* **Issue TSO and z/OS console commands**

  Issue TSO and console commands to the mainframe directly from Brightside CLI.

* **Provision mainframe environments**

  Exploit z/OSMF cloud provisioning features to provision environments on-demand.

* **Integrates z/OS actions**

  Build local scripts that accomplish both mainframe and local tasks.

* **Produce responses as JSON documents**

  Return data in JSON format on request for consumption in other programming languages.

For more information about the available functionality in Brightside CLI, see [Brightside CLI Command Groups](../../using-project-giza/using-brightside-cli/brightside-cli-command-groups.md).

## Prerequisites

For information about prerequisite software and configuration for Brightside CLI, see [Prerequisites for Brightside CLI](../../installing-project-giza/prerequisites/prerequisites-for-brightside-cli.md)

## Experimental commands

The Brightside CLI contains features that are still under development and have not been tested to GA quality. You can enable or disable these commands. The experimental commands are disabled by default.

**Important!** You might encounter problems when using experimental commands.

For more information, see [Enable and Disable Experimental Commands](../../using-project-giza/using-brightside-cli/enabling-and-disabling-experimental-commands.md).

## Third-party software agreements

Brightside CLI uses the following third-party software:

* ag-grid
* body-parser
* chalk
* cli-table2
* csv
* definitelytyped
* express
* filewatcher
* getmdl-select
* glob
* i18n
* jsonschema
* js-yaml
* levenshtein
* lodash
* log4js
* material-design-lite
* mustache
* Nested-property
* node.js
* node-forge
* node-progress
* node-tmp
* opn
* prettyjson
* prompt
* reflect-metadata
* rimraf
* simple-ssh
* stack-trace
* string-argv
* wrap-ansi
* yamljs
* yargs

**Note:** All trademarks, trade names, service marks, and logos referenced herein belong to their respective companies.

To read each complete license, navigate to the [GitHub repository](https://github.com/gizafoundation/Downloads/releases) and download the file named `Brightside_TPSRs.zip`. The .zip file contains the licenses for all of the third-party components that Brightside CLI uses.

