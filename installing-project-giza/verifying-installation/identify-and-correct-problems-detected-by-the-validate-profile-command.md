# Identify and correct problems detected by the validate profile command

Brightside CLI includes a profile validation command that runs a series of tests on z/OSMF REST APIs \(and their endpoints\) and prints a report that can help you identify problems with profiles and connection details. As a systems programmer, issue this command to test the end-to-end integration of Brightside CLI with your z/OSMF and your z/OS environment.

**Note:** Application developers that use Brightside CLI can issue the command at any time and provide the report to systems programmers for problem resolution. For more information about how application developers use the profile validation command, see [Validate Installation](validating-brightside-cli-installation.md).

## Use the report to resolve problems

You can use the results of the validate profile command to troubleshoot and fix problems with your z/OSMF configuration. The result of each test returns as _OK_, _Warning_, or _Failed_. If you receive a _Warning_ or _Failed_ result on a test, you can refer to IBM documentation for information on how to configure that particular REST API. For information on which of the z/OSMF REST APIs Brightside CLI uses, see [z/OSMF requirements](../prerequisites/prerequisites-for-z-osmf-configuration.md). We provide links to IBM documentation for configuring each REST API.

For example, you receive a _Failed_ result on the "Issue Console command" task. Refer to the list of REST APIs in [z/OSMF requirements](../prerequisites/prerequisites-for-z-osmf-configuration.md) and follow the links to the corresponding IBM documentation for the z/OS console services API.

