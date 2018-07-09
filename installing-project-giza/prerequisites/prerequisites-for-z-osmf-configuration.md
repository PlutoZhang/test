# Prerequisites for z/OSMF configuration

IBM z/OS Management Facility \(z/OSMF\) is a prerequisite for the Project Giza microservice that must be installed and running before you use Project Giza. This article consists of the following information:

* z/OSMF Requirements for Project Giza
* Configuring z/OSMF
* Verifying your z/OSMF configuration

**Important!** The IBM z/OS Management Facility guides on the IBM Knowledge Center are your primary source of information about how to install and configure z/OSMF. In the following topics, we provide procedures and tips for the configuration required for Project Giza. We recommend that you open the following IBM documentation in a separate browser tab \(The z/OSMF process differs depending on whether you have z/OS v2.2 or v2.3\):

IBM z/OSMF documentation:

* [IBM z/OS Management Facility Help](https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izu/izu.htm)
* [IBM z/OS Management Facility Configuration Guide](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua300/IZUHPINFO_PartConfiguring.htm)

## z/OSMF Requirements for Project Giza

Meet the following requirements before you use Project Giza:

### z/OS requirements

Ensure that your z/OS system meets the following requirements for z/OSMF to function properly with Project Giza:

* **AXR \(System Rexx\)** -

    The AXR \(System Rexx\) component lets z/OS perform Incident Log tasks. It also lets REXX execs execute outside of conventional TSO and batch environments.

* **CEA \(Communications Enabled Applications\) Server** -

    CEA server is a co-requisite for the CIM server. The CEA server lets z/OSMF deliver z/OS events to C-language clients.

  * Start the CEA server before you start the start z/OSMF \(the IZU\* started tasks\).
  * Set up CEA server in Full Function Mode and assign the TRUSTED attribute to the CEA started task.
  * For more information, see Customizing for CEA on the IBM Knowledge Center.

* **CIM \(Common Information Model\) Server** -

   z/OSMF requires the CIM server to perform capacity provisioning and workload management tasks. Start the CIM server before you start z/OSMF \(the IZU\* started tasks\).

  * For more information, see Reviewing your CIM server setup on the IBM Knowledge Center.

* **Console Command** -

    The CONSOLE and CONSPROF commands must exist in the authorized command table.

* **IBM z/OS Provisioning Toolkit** -

    The IBM® z/OS® Provisioning Toolkit is a command line utility that lets you provision z/OS development environments. The product is required if you want to provision CICS or Db2 environments with Brightside CLI.

* **Java version** -

    IBM® 64-bit SDK for z/OS®, Java Technology Edition V7.1 or higher is required.

  * For more information, see Software prerequisites for z/OSMF on the IBM Knowledge Center.

* **Maximum region size** -

    To prevent exceeds maximum region size errors, ensure that you have a TSO maximum region size of at least 65536 KB for the z/OS system.

* **User IDs** -

    User IDs require a TSO segment \(access\) and an OMVS segment. During workflow processing and REST API requests, z/OSMF may start one or more TSO address spaces under the following job names:

  * userid
  * substr\(userid, 1, 6\)\|\|CN \(Console\)

For more information, refer to the IBM z/OSMF documentation.

### z/OSMF plug-in requirements

Ensure that the following IBM z/OSMF plug-ins are installed and configured:

* **\(Optional\) Cloud Portal** -

    The Cloud Portal plug-in lets you make software services available to marketplace consumers and it adds the Marketplace and Marketplace Administration tasks to the z/OSMF navigation tree.

* **Configuration Assistant** -

    The Configuration Assistant plug-in lets z/OSMF configure TCP/IP policy-based networking functions.

* **ISPF** -

    The ISPF plug-in lets z/OSMF access traditional ISPF applications.

* **Workload Management** -

    The Workload Management plug-in lets z/OSMF operate and manage workload management service definitions and policies.

For more information about configuring each z/OSMF plug-in and the related security, refer to the IBM z/OSMF documentation for each plug-in.

### REST services requirements

Ensure that the following REST services are configured and available when you run Project Giza:

* **Cloud provisioning services** -

    Cloud provisioning for development environments. Cloud provisioning services are required for the Brightside CLI cics and db2 command groups to function properly. Endpoints begin with `/zosmf/provisioning/`

* **TSO/E address space services** -

    Required to issue TSO commands in Brightside CLI. Endpoints begin with `/zosmf/tsoApp`

* **z/OS console** -

    Required to issue console commands in Brightside CLI. Endpoints begin with `/zosmf/restconsoles/`

* **z/OS data set and file interface** -

    Required to work with mainframe data sets and USS files in Brightside CLI. Endpoints begin with `/zosmf/restfiles/`

* **z/OS jobs interface** -

    Required to use the zos-jobs command group in Brightside CLI. Endpoints begin with `/zosmf/restjobs/`

* **z/OSMF workflow services** -

    Cloud provisioning for development environments. Cloud provisioning services are required for the Brightside CLI cics and db2 command groups to function properly. Endpoints begin with `/zosmf/workflow/`

Additionally, Project Giza uses z/OSMF configuration by using symbolic links to the z/OSMF `bootstrap.properties`, `jvm.security.override.properties`, and the `ltpa.keys` files. Specifically, Project Giza reuses z/OSMF's SAF, SSL, and LTPA configuration; therefore, these configurations must be valid and complete to operate Project Giza successfully.

For more information, refer to the IBM z/OSMF documentation for each REST service.

## Configuring z/OSMF

1. Verify your system requirements.

   For z/OS v2.2 or later, use any of the following options to determine which version is installed:

   * If you have access to the console, for example, in SDSF, issue the command:

     ```text
       /D IPLINFO
     ```

     Part of the output contains the release, for example,

     ```text
       RELEASE z/OS 02.02.00.
     ```

   * If you don't have access to the console, use SDSF and select the menu option **MAS**. Two columns of the output show the SysName \(LPAR name\) and the z/OS version, for example:

     ```text
       SysName  Version

       S001     z/OS 2.2
     ```

     Identify the z/OS Version for the LPAR on which you are going to use z/OSMF.

   * If you don't have access to SDSF, use ISPF option **7.3** \(Dialog Test Variables\) and scroll down to the variable `ZOS390RL`, for example,

     ```text
       ZOS390RL S N z/OS   02.02.00
     ```

   * On the ISPF Primary Option Menu, the last entry is the ISPF Release, which corresponds to the z/OS version as follows:

     ```text
       Release . : ISPF 7.1    --> z/OS v2.1
       Release . : ISPF 7.2    --> z/OS v2.2
       Release . : ISPF 7.3    --> z/OS v2.3
     ```

2. Configure z/OSMF.

   For z/OS V2.2 users, take the following steps to configure z/OSMF:

   z/OSMF is a base element of z/OS v2.2 and v2.3, so it should already be installed. However, it is not guaranteed to be configured and running on every z/OS V2.2 and V2.3 system.

   Configuring an instance of z/OSMF is done by running the IBM-supplied jobs IZUSEC and IZUMKFS, and then starting the z/OSMF server in the following order:

   1. Security setup \(the IZUSEC job\)
   2. Configuration \(the IZUMKFS job\)
   3. Server initialization \(the START command\)

      For z/OS V2.3 users, the base element z/OSMF is started by default at system IPL. This means that z/OSMF is available for use as soon as the system is up. If you prefer not to have z/OSMF started automatically, you can disable the autostart function by checking for `START` commands for the z/OSMF started procedures in the COMMNDxx parmlib member.

      The z/OS Operator Consoles task is new in this release. Applications that depend on access to the operator console such as Brightside's RestConsoles API require version 2.3.

3. Verify other requirements.
   * Perform any maintenance that is required by Node.js.

     Connect to your target z/OS system, for example, with ssh to port 22 to get a USS command window. Issue the command:

     ```text
       node -v
     ```

     or

     ```text
       node --version
     ```

     The response should be:

     ```text
       v6.11.2
     ```

     or later. If the version displayed is not right, set and/or download the right version of node by using npm and nvm. You might want to refer to the following links for tutorials on npm and nvm:

     [https://www.sitepoint.com/beginners-guide-node-package-manager/](https://www.sitepoint.com/beginners-guide-node-package-manager/)

     [https://www.sitepoint.com/quick-tip-multiple-versions-node-nvm/](https://www.sitepoint.com/quick-tip-multiple-versions-node-nvm/)

     If you don’t have node installed, go to [https://nodejs.org/en/download/package-manager/](https://nodejs.org/en/download/package-manager/), select your operating system, and follow the instructions to install node. Ensure that you download only official versions of these products. For z/OSMF, you need only one version of node.js. You can find the complete procedure for installing Node.js at [https://developer.ibm.com/node/sdk/ztp/](https://developer.ibm.com/node/sdk/ztp/).

     When completed, set the `NODE_HOME` environment variable to the directory where your Node.js is installed, for example,

     ```text
       NODE_HOME=/proj/mvd/node/installs/node-v6.10.3-os390-s390x
     ```

   * Issue the following command to check the Java installation.

     ```text
       java -version
     ```

     The response should be

     ```text
       java version "1.8.0"
     ```

     or later. If the version displayed is not right, set the `JAVA_HOME` variable to point to the preferred java version. If the preferred java version is not installed, install it.

   * Verify that you have 400 MB of free HFS file space for the installation. You can use the `df` command to check the available space in your chosen file system, for example,

     ```text
       df -k /usr/lpp/zosmf
     ```

     The output should be as follows:

     ```text
       Mounted on       Filesystem               Avail/Total

       /Z22C/usr/lpp/zosmf  (ZFS.S001.Z22C.ZOSMF)      26711/535680
     ```

     From the output above, you can see that only 26.711 MB is available \(because z/OSMF is already installed\), but the total in that file system is 535.68 MB, so enough space was available when the file system was created.

   * Verify your browser support. Confirm that the machine from which you plan to run the Giza desktop runs one of the supported browsers:

     * Chrome version 54 or later
     * Firefox version 44 or later
     * Microsoft Edge

     **Note**: Microsoft Internet Explorer is not yet supported at any version.
4. After configuring z/OSMF, verify the following items to ensure z/OSMF is ready for Project Giza.

   Check that the z/OSMF server and angel processes are running. From SDSF on z/OS, use the `DA` command or issue the following command on the command input line:

   ```text
    /D A,IZU*
   ```

   If you don't see jobs like IZUANG1 and IZUSVR1 active, start the angel process with the following command:

   ```text
    /S IZUANG1
   ```

   When you see the message **CWWKB0056I INITIALIZATION COMPLETE FOR ANGEL**, start the server with the following command:

   ```text
    /S IZUSVR1
   ```

   The server might take a couple of minutes to fully initialize. The z/OSMF server is available when the following message **CWWKF0011I: The server zosmfServer is ready to run a smarter planet.** is displayed.

   You can test z/OSMF with your browser by first finding the startup messages in the SDSF log of the z/OSMF server by using the following find command:

   ```text
    f IZUG349I
   ```

   You should see these lines:

   ```text
    IZUG349I: The z/OSMF STANDALONE Server home page can be accessed at  https://mvs.hursley.ibm.com:443/zosmf after the z/OSMF server is started on your system.
   ```

   From the lines above, the port number is 443. You will need this port number later.

   Point your browser at the nominated z/OSMF STANDALONE Server home page and you should see its Welcome Page where you can log in.

## Verifying your z/OSMF configuration

To verify that IBM z/OSMF REST services are configured correctly in your environment, type the REST endpoint into your browser. For example: [https://mvs.ibm.com:443/zosmf/restjobs/jobs](https://mvs.ibm.com:443/zosmf/restjobs/jobs)

**Notes:**

* Browsing z/OSMF endpoints requests your user ID and password for defaultRealm; these are your TSO user credentials.
* Your browser should return you a status code 200 with a list of all jobs on your z/OS system. The list is in raw JSON format.

### Optional method for verifying z/OSMF configuration with Brightside CLI

To verify that IBM z/OSMF is configured correctly, follow these steps to create and validate a profile in Brightside CLI:

1. [Meet the prerequisites for Brightside CLI](prerequisites-for-brightside-cli.md).
2. [Install Brightside CLI](../installing-components-of-project-giza/installing-brightside-cli.md).
3. Create a zosmf profile in Brightside CLI. Issue the `bright help explain profiles` command to learn more about creating profiles in Brightside CLI. See [How to display Brightside CLI help](../../using-project-giza/using-brightside-cli/how-to-display-brightside-cli-help.md) for more information.
4. [Validate your profile](../verifying-installation/validating-brightside-cli-installation.md).
5. [Use the profile validation report to identify and correct errors](../verifying-installation/identify-and-correct-problems-detected-by-the-validate-profile-command.md) with your z/OSMF configuration.

    If you recieve a perfect score on the validation report, Project Giza can communicate with z/OSMF properly.

**Note:** Before your run the profile validation, check that JES2 is accepting jobs with CLASS=C by issuing the following command in SDSF:

```text
/$D I
```

You will see responses like the following in SYSLOG:

```text
$HASP892 INIT(3)   STATUS=ACTIVE,CLASS=AB,...
```

If none of the initiators has **C** in its CLASS list, add **C** to the list of any initiator. For example, initiator 3 as shown above, with the following command:

```text
/$T I3,CL=ABC
```

**Parent topic:** [Prerequisites](./)

