# Validating Brightside CLI installation

After the systems programmer configures z/OSMF and application developers install Brightside CLI, issue the Brightside CLI profile validation command to verify that your z/OSMF profile will function properly. The Brightside CLI profile validation command runs a series of tests on z/OSMF APIs and prints a report that can help you identify problems with your profile and connection details.

Use this command to verify that your Brightside CLI profile can communicate with z/OSMF on z/OS systems. Review the report and inform your systems programmer if there are any failures or warnings.

Before you issue the z/OSMF profile validation command, ensure that the following tasks are complete:

* Your systems programmer configured z/OSMF.
* Brightside CLI is installed.
* You created at least one Brightside CLI `zosmf` profile that lets you access z/OSMF functionality on z/OS systems.

## Command syntax

You issue the z/OSMF validate profile command to verify that your Brightside CLI mainframe security access has been properly configured and that your profile details are correct. With the command, you can verify your default profile or any other specific profile.

Issue the following command to view a list of the tests that the profile validation command will run:

```text
bright zosmf validate profile --print-plan-only
```

Issue the following command to verify that your _default profile_ is configured correctly:

```text
bright zosmf validate profile
```

Issue the following command and specify a `profile_name` to verify that _a specific profile_ is configured correctly:

```text
bright zosmf validate profile --bpn <profile_name>
```

## Profile validation results

When you issue the z/OSMF validate profile command, Brightside CLI runs a series of tests. The command presents you with a table that displays the test results. Review the table and report any failures or warnings to your systems programmer.

The report returns the following information:

* **Task**  

  The type of action that the test performs.

* **Status**  

  The result of the test returns as _OK_, _Warning_, or _Failed_. In

  some cases, a _Failed_ result on one test can result in a

  _Warning_ result on the subsequent tests.

* **Description**  

  Details about the execution and results of the test.

* **Endpoint**  

  The REST API endpoint on which the test acted.

