# z/OSMF requirements
**Important!** The following information contains procedures and tips for meeting z/OSMF requirements. For complete information, go to [IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3/en/homepage.html) and read the following documents:
- [IBM z/OS Management Facility Help](https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izu/izu.htm)
- [IBM z/OS Management Facility Configuration Guide](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua300/IZUHPINFO_PartConfiguring.htm)


<!--Meet the following requirements before you install and use Project Zowe:
- z/OS requirements
- REST requirements for the Zowe Brightside
- z/OSMF Configuration-->



### z/OS requirements
Ensure that the z/OS system meets the following requirements:
Requirements                          | Description                                                                                                                                                                                                                                | Resources in IBM Knowledge Center
--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------
AXE (System REXX)                     | z/OS uses AXR (System REXX) component to perform Incident Log tasks. The component enables REXX executable files to run outside of conventional TSO and batch environments.                                                                | [System REXX][6d9592f7]
Common Event Adapter (CEA) server     | The CEA server, which is a co-requisite of the Common Information Model (CIM) server, enables the ability for z/OSMF to deliver z/OS events to C-language clients.                                                                         | [Customizing for CEA][d3914be4]
Common Information Model (CIM) server | z/OSMF uses the CIM server to perform capacity-provisioning and workload-management tasks. Start the CIM server before you start z/OSMF (the IZU* started tasks).                                                                          | [Reviewing your CIM server setup][b36cadc1]
CONSOLE and CONSPROF commands         | The CONSOLE and CONSPROF commands must exist in the authorized command table.                                                                                                                                                              | [Customizing the CONSOLE and CONSPROF commands][dde6ef38]
IBM z/OS Provisioning Toolkit         | The IBM® z/OS® Provisioning Toolkit is a command line utility that provides the ability to provision z/OS development environments. If you want to provision CICS or Db2 environments with the Zowe Brightside, this toolkit is required.  | [What is IBM Cloud Provisioning and Management for z/OS?][a5e58cc1]
Java level                            | IBM® 64-bit SDK for z/OS®, Java Technology Edition V7.1 or higher is required.                                                                                                                                                             | [Software prerequisites for z/OSMF][2a360548]
TSO region size                       | To prevent **exceeds maximum region size** errors, verify that the TSO maximum region size is a minimum of 65536 KB for the z/OS system.                                                                                                   | N/A
User IDs                              | User IDs require a TSO segment (access) and an OMVS segment. During workflow processing and REST API requests, z/OSMF might start one or more TSO address spaces under the following job names: userid; substr(userid, 1, 6) CN (Console). | N/A
  [dde6ef38]: https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.ikjb400/consol.htm "Customizing the CONSOLE and CONSPROF commands"
  [d3914be4]: https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.e0zb100/custcea.htm "Customizing for CEA"
  [b36cadc1]: https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua300/IZUHPINFO_AdditionalCIMStepsForZOS.htm "Reviewing your CIM server setup"
  [a5e58cc1]: https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.izsc300/cloudProvOverview.htm "What is IBM Cloud Provisioning and Management for z/OS?"
  [2a360548]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua300/IZUHPINFO_SoftwarePrereqs.htm "Software prerequisites for z/OSMF"
  [6d9592f7]: https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.ieaa800/systemrexx.htm "System REXX"

<!--**AXR (System REXX)** -
    The AXR (System REXX) component lets z/OS perform Incident Log tasks. It also lets REXX execs execute outside of conventional TSO and batch environments.
- **CEA (Communications Enabled Applications) Server** -
    CEA server is a co-requisite for the CIM server. The CEA server lets z/OSMF deliver z/OS events to C-language clients.
    - Start the CEA server before you start the z/OSMF (the IZU* started tasks).
    - Set up CEA server in Full Function Mode and assign the TRUSTED attribute to the CEA started task.
    - For more information, see Customizing for CEA on the IBM Knowledge Center.
- **CIM (Common Information Model) Server** -
   z/OSMF requires the CIM server to perform capacity provisioning and workload management tasks. Start the CIM server before you start z/OSMF (the IZU* started tasks).
    - For more information, see Reviewing your CIM server setup on the IBM Knowledge Center.
- **Console Command** -
    The CONSOLE and CONSPROF commands must exist in the authorized command table.
- **IBM z/OS Provisioning Toolkit** -
    The IBM® z/OS® Provisioning Toolkit is a command line utility that lets you provision z/OS development environments. The product is required if you want to provision CICS or Db2 environments with the Zowe Brightside.
- **Java version** -
    IBM® 64-bit SDK for z/OS®, Java Technology Edition V7.1 or higher is required.
    - For more information, see Software prerequisites for z/OSMF on the IBM Knowledge Center.
- **Maximum region size** -
    To prevent exceeds maximum region size errors, ensure that you have a TSO maximum region size of at least 65536 KB for the z/OS system.
- **User IDs** -
    User IDs require a TSO segment (access) and an OMVS segment. During workflow processing and REST API requests, z/OSMF may start one or more TSO address spaces under the following job names:
    - userid
    - substr(userid, 1, 6)||CN (Console)

For more information, refer to the IBM z/OSMF documentation.-->


### z/OSMF REST services for the Zowe Brightside
the Zowe Brightside uses z/OSMF Representational State Transfer (REST) APIs to work with system resources and extract system data. Ensure that the following REST services are configured and available:

- **[Cloud provisioning services][aab6df02]** -
    Cloud provisioning services are required for the Zowe Brightside CICS and Db2 command groups. Endpoints begin with `/zosmf/provisioning/`
- **[TSO/E address space services][a5ec5a22]** -
    TSO/E address space services are required to issue TSO commands in the Zowe Brightside. Endpoints begin with `/zosmf/tsoApp`
- **[z/OS console services][cec53ca4]** -
    z/OS console services are required to issue console commands in the Zowe Brightside. Endpoints begin with `/zosmf/restconsoles/`
- **[z/OS data set and file REST interface][6bbf5bfd]** -
    z/OS data set and file REST interface is required to work with mainframe data sets and UNIX System Services files in the Zowe Brightside. Endpoints begin with `/zosmf/restfiles/`
- **[z/OS jobs REST interface][9d372fb1]** -
    z/OS jobs REST interface is required to use the zos-jobs command group in the Zowe Brightside. Endpoints begin with `/zosmf/restjobs/`
- **[z/OSMF workflow services][4e443fd6]** -
    z/OSMF workflow services is required to create and manage z/OSMF workflows on a z/OS system. Endpoints begin with `/zosmf/workflow/`

  [a5ec5a22]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua700/izuprog_API_TSOServices.htm "TSO/E address space services"
  [aab6df02]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua300/izuconfig_CloudProvSecuritySetup.htm "Cloud provisioning services"
  [cec53ca4]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua700/IZUHPINFO_API_RESTCONSOLE.htm "z/OS console"
  [6bbf5bfd]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua700/IZUHPINFO_API_RESTFILES.htm "z/OS data set and file interface"
  [9d372fb1]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua700/IZUHPINFO_API_RESTJOBS.htm "z/OS jobs interface"
  [4e443fd6]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua700/izuprog_API_WorkflowServices.htm "z/OSMF workflow services"

Project Zowe uses symbolic links to the z/OSMF `bootstrap.properties`, `jvm.security.override.properties`, and `ltpa.keys` files. Project Zowe reuses SAF, SSL, and LTPA configurations; therefore, they must be valid and complete.

For more information, see [Using the z/OSMF REST services][022415d0] in IBM z/OSMF documentation.

  [022415d0]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua700/IZUHPINFO_RESTServices.htm "Using the z/OSMF REST services"

## Configuring z/OSMF

1. Use one of the following commands to verify the version of z/OS:



    - From the console, issue the following command:

        ```
        /D IPLINFO
        ```

        Part of the output contains the release, for example,
        ```
        RELEASE z/OS 02.02.00.
        ```

    - Use SDSF and select the menu option **MAS**. The output displays the SysName (LPAR name) and the z/OS version, for example:

        ```
        SysName  Version

        S001     z/OS 2.2
        ```

    - Use ISPF option **7.3** (Dialog Test Variables). Scroll down to the variable `ZOS390RL`, for example,

        ```
        ZOS390RL S N z/OS   02.02.00
        ```

    - From the ISPF Primary Option Menu, the last entry is the ISPF Release, which corresponds to the z/OS version, for example:
        ```
        Release . : ISPF 7.1    --> z/OS v2.1
        Release . : ISPF 7.2    --> z/OS v2.2
        Release . : ISPF 7.3    --> z/OS v2.3
        ```
2. Configure z/OSMF.

    z/OSMF is a base element of z/OS V2.2 and V2.3, so it is already installed. But it might not be configured and running on every z/OS V2.2 and V2.3 system.

    For details about how to configure z/OSMF, see [IBM® z/OS Management Facility Configuration Guide][ebfc91e0].


  [ebfc91e0]: https://www.ibm.com/support/knowledgecenter/SSLTBW_2.3.0/com.ibm.zos.v2r3.izua300/toc.htm "IBM® z/OS Management Facility Configuration Guide"
<!--    Configuring an instance of z/OSMF is done by running the IBM-supplied jobs IZUSEC and IZUMKFS, and then starting the z/OSMF server in the following order:

    1. Security setup (the IZUSEC job)
    2. Configuration (the IZUMKFS job)
    3. Server initialization (the START command)     

    For z/OS V2.3 users, the base element z/OSMF is started by default at system IPL. This means that z/OSMF is available for use as soon as the system is up. If you prefer not to have z/OSMF started automatically, you can disable the autostart function by checking for `START` commands for the z/OSMF started procedures in the COMMNDxx parmlib member.

    The z/OS Operator Consoles task is new in this release. Applications that depend on access to the operator console such as Brightside's RestConsoles API require version 2.3.

3. Verify other requirements.

    - Perform any maintenance that is required by Node.js.

        Connect to your target z/OS system, for example, with ssh to port 22 to get a UNIX System Services command window. Issue the command:

        ```
        node -v
        ```
        or

        ```
        node --version
        ```

        The response should be:
        ```
        v6.11.2
        ```

        or later. If the version displayed is not right, set and/or download the right version of node by using npm and nvm. You might want to refer to the following links for tutorials on npm and nvm:

        https://www.sitepoint.com/beginners-guide-node-package-manager/

        https://www.sitepoint.com/quick-tip-multiple-versions-node-nvm/

        If you don’t have node installed, go to https://nodejs.org/en/download/package-manager/, select your operating system, and follow the instructions to install node. Ensure that you download only official versions of these products. For z/OSMF, you need only one version of node.js. You can find the complete procedure for installing Node.js at https://developer.ibm.com/node/sdk/ztp/.

        When completed, set the `NODE_HOME` environment variable to the directory where your Node.js is installed, for example,

        ```
        NODE_HOME=/proj/mvd/node/installs/node-v6.10.3-os390-s390x
        ```

    - Issue the following command to check the Java installation.

        ```
        java -version
        ```

        The response should be
        ```
        java version "1.8.0"
        ```

        or later. If the version displayed is not right, set the `JAVA_HOME` variable to point to the preferred java version. If the preferred java version is not installed, install it.

    - Verify that you have 400 MB of free HFS file space for the installation. You can use the `df` command to check the available space in your chosen file system, for example,

        ```
        df -k /usr/lpp/zosmf
        ```

        The output should be as follows:
        ```
        Mounted on       Filesystem               Avail/Total

        /Z22C/usr/lpp/zosmf  (ZFS.S001.Z22C.ZOSMF)      26711/535680
        ```

        From the output above, you can see that only 26.711 MB is available (because z/OSMF is already installed), but the total in that file system is 535.68 MB, so enough space was available when the file system was created.

    - Verify your browser support. Confirm that the machine from which you plan to run the Zowe desktop runs one of the supported browsers:
        - Chrome version 54 or later
        - Firefox version 44 or later
        - Microsoft Edge

      **Note**: Microsoft Internet Explorer is not yet supported at any version.

4. After configuring z/OSMF, verify the following items to ensure z/OSMF is ready for Project Zowe.

    Check that the z/OSMF server and angel processes are running. From SDSF on z/OS, use the `DA` command or issue the following command on the command input line:

    ```
    /D A,IZU*
    ```

    If you don't see jobs like IZUANG1 and IZUSVR1 active, start the angel process with the following command:

    ```
    /S IZUANG1
    ```

    When you see the message **CWWKB0056I INITIALIZATION COMPLETE FOR ANGEL**, start the server with the following command:

    ```
    /S IZUSVR1
    ```

    The server might take a couple of minutes to fully initialize. The z/OSMF server is available when the following message **CWWKF0011I: The server zosmfServer is ready to run a smarter planet.** is displayed.

    You can test z/OSMF with your browser by first finding the startup messages in the SDSF log of the z/OSMF server by using the following find command:

    ```
    f IZUG349I
    ```

    You should see these lines:
    ```
    IZUG349I: The z/OSMF STANDALONE Server home page can be accessed at  https://mvs.hursley.ibm.com:443/zosmf after the z/OSMF server is started on your system.
    ```

    From the lines above, the port number is 443. You will need this port number later.

    Point your browser at the nominated z/OSMF STANDALONE Server home page and you should see its Welcome Page where you can log in.
    ## Verifying your z/OSMF configuration
    To verify that IBM z/OSMF REST services are configured correctly in your environment, type the REST endpoint into your browser. For example: https://mvs.ibm.com:443/zosmf/restjobs/jobs

    **Notes:**
    - Browsing z/OSMF endpoints requests your user ID and password for defaultRealm; these are your TSO user credentials.

    - Your browser should return you a status code 200 with a list of all jobs on your z/OS system. The list is in raw JSON format.

    ### Optional method for verifying z/OSMF configuration with the Zowe Brightside    

    To verify that IBM z/OSMF is configured correctly, follow these steps to create and validate a profile in the Zowe Brightside:

    1. [Meet the prerequisites for the Zowe Brightside](cli-precli.md).
    2. [Installing the Zowe Brightside](cli-installcli.md).
    3. Create a zosmf profile in the Zowe Brightside. Issue the `bright help explain profiles` command to learn more about creating profiles in the Zowe Brightside. See [How to display the Zowe Brightside help](cli-howtodisplaybrightsidehelp.md) for more information.
    4. [Validate your profile](cli-validateInstallation.md).
    5. [Use the profile validation report to identify and correct errors](cli-validateInstallation.md) with your z/OSMF configuration.
        If you receive a perfect score on the validation report, Project Zowe can communicate with z/OSMF properly.

    **Note:** Before your run the profile validation, check that JES2 is accepting jobs with CLASS=C by issuing the following command in SDSF:

    ```
    /$D I
    ```
    You will see responses like the following in SYSLOG:
    ```
    $HASP892 INIT(3)   STATUS=ACTIVE,CLASS=AB,...
    ```
    If none of the initiators has **C** in its CLASS list, add **C** to the list of any initiator. For example, initiator 3 as shown above, with the following command:
    ```
    /$T I3,CL=ABC
    ```
-->
