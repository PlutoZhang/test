# Installing Atlas

Installing Atlas involves obtaining the Atlas Archive, running the install script, and configuring files.

Before installing Atlas, ensure that your environment meets the [prerequisites for Atlas](topics/atlas-prereqs.md).

To install Atlas, complete the following steps:

1. [Follow instructions to obtain the Project Giza installation media](https://github.com/gizafoundation/Downloads/releases). Once completed, you should have an Atlas PAX file along with the Atlas install script (scripts/atlas/atlas-wlp-package-0.0.3.sh).

2. Move the Atlas PAX file and install script to the preferred installation directory, for example, gizaInstallDir/Atlas.

3. Run the Atlas install script.

    Run the install script in the installation directory with a user ID that has the authority to:

    -   Unpack the Atlas PAX archive and install Atlas into the installation directory, for example, `/var/atlas`. About 205 MB is needed to unpack the archive and more space is needed for Liberty operation and logging.
    -   Set the file group ownership to IZUADMIN.
    -   Create symbolic links to the files that z/OSMF owns.  

    Therefore, use super user authority to run the Atlas install script.

    Give the install script execute permission using the following command:

    ```
    chmod u+x atlas-wlp-package-0.0.3.sh
    ```
    
    Then, execute the install script using the following commmand:
    
    ```
    ./atlas-wlp-package-0.0.3.sh
    ```

4. Change the ownership of Atlas installation directory and files.

    The user who runs the Atlas Liberty server needs the access to the Atlas installation directory and files. You can use the same user ID that runs the z/OSMF IZUSVR1 started task to run the Atlas Liberty server. By default, it is the user IZUSVR.

    To change the ownership of the Atlas installation directory and files, enter the following z/OS UNIX™ System Services command from the Atlas installation directory:

    ```
    chown -R IZUSVR *
    ```

    You might need super user authority to run this command. Use an alternative user ID if you chose not to use the default z/OSMF IZUSVR1 started task user.

5. Create a member FEKATLS in your system PROCLIB data set.

    The install script creates a file that is called `FEKATLS.jcl` is created in your Atlas installation directory. Copy this file to a system PROCLIB data set by using the following TSO command:

    ```
    oget '/atlasInstallPath/FEKATLS.jcl' 'hlq.proclib(FEKATLS)'
    ```

    The FEKATLS procedure starts a Liberty profile server running the Atlas microservice application.

6. Configure the FEKATLS started procedure.

    To run the FEKATLS procedure as the user IZUSVR, define the procedure to the STARTED class by using RACF® or equivalent, for example:

    ```
    •	RDEF STARTED (FEKATLS.*) STDATA(USER(IZUSVR) GROUP(IZUADMIN))
    •	SETR RACLIST(STARTED) REFRESH
    ```

    Here is an example of the FEKATLS procedure JCL:

    ```
    //********************************************************************
    //*   Licensed Materials - Property of IBM                           *
    //*                                                                  *
    //*   5655-EX1                                                       *
    //*                                                                  *
    //*   Copyright IBM Corp. 2017. All rights reserved.                 *
    //*                                                                  *
    //*   US Government Users Restricted Rights - Use,                   *
    //*   duplication or disclosure restricted by GSA ADP                *
    //*   Schedule Contract with IBM Corp.                               *
    //*                                                                  *
    //********************************************************************
    //*                                                                  *
    //* ATLAS WLP PROCEDURE                                              *
    //*                                                                  *
    //* This is a procedure to start the Atlas web server platform,      *
    //* running on the WebSphere Liberty Profile. This procedure         *
    //* requires a WebSphere Liberty Angel procedure is running, such as *
    //* z/OSMF procedure "IZUANG*".                                      *
    //*                                                                  *
    //* NOTE: THIS JCL IS MODIFIED BY THE ATLAS INSTALLATION PROCESS TO  *
    //* SET THE ATLAS INSTALLATION PATH. IF THE INSTALLATION PATH        *
    //* CHANGES, MODIFY THE SRVRPATH VALUE ACCORDINGLY.                  *
    //*                                                                  *
    //********************************************************************
    //ATLAS PROC
    //*-------------------------------------------------------------------
    //* SRVRPATH - The path to the HFS directory where the Atlas server
    //*            was installed.
    //*-------------------------------------------------------------------
    //EXPORT EXPORT SYMLIST=*
    //  SET SRVRPATH='${atlaspath}'
    //*-------------------------------------------------------------------
    //* Start the Atlas WebSphere Liberty Profile server
    //*-------------------------------------------------------------------
    //STEP1   EXEC PGM=BPXBATSL,REGION=0M,TIME=NOLIMIT,
    //  PARM='PGM &SRVRPATH/wlp/lib/native/zos/s390x/bbgzsrv Atlas'
    //WLPUDIR  DD PATH='&SRVRPATH/wlp/usr'
    //STDOUT   DD SYSOUT=*
    //STDERR   DD SYSOUT=*
    //*-------------------------------------------------------------------
    //* Optional logging parameters that can be configured if required
    //*-------------------------------------------------------------------
    //*STDOUT   DD PATH='&SRVRPATH/std.out',
    //*            PATHOPTS=(OWRONLY,OCREAT,OTRUNC),
    //*            PATHMODE=SIRWXU
    //*STDERR   DD PATH='&SRVRPATH/std.err',
    //*            PATHOPTS=(OWRONLY,OCREAT,OTRUNC),
    //*            PATHMODE=SIRWXU                                              

    ```

7. Add Atlas users to the z/OSMF users group \(IZUUSER\).

    Atlas uses z/OSMF to access data sets, z/OS UNIX System Services files, and job spool files. To use these z/OSMF services, Atlas users must be authorized to z/OSMF resources. For more information, see the *IBM z/OS Management Facility Configuration Guide*, Appendix A.

    To add Atlas users to the z/OSMF IZUUSER group, use RACF or equivalent. For example,

    ```
    CONNECT userid GROUP(IZUUSER) AUTH(USE)
    ```

8. Start the Atlas server.

    To start Atlas manually, enter the `START` operator command:

    ```
    S FEKATLS
    ```

    To start Atlas automatically at IPL, add the `START` command to your active COMMNDxx parmlib member.

9. Optional: Configure the Atlas apps to launch within zLUX, navigate to AtlasInstallDirectory/wlp/atlasZluxInjection, run the install script, and restart zLUX.

    **Note:** The install script will require conversion. Run the following icon command:

    ```
    iconv -f ISO8859-1 -t IBM-1047 install.sh > install-CONVERTED.sh
    ```
    
    Give the new script execute permissions using the following command:
    ```
    chmod u+x install-CONVERTED.sh
    ```

    Execute the install script using the following command:
    ```
    ./install-CONVERTED.sh
    ```

10. Optional: Change your language in Atlas by adding the following line to the `jvm.options` file, for example,

    ```
    -Duser.language=de
    ```

    where `de` can be replaced with other language codes.

**What to do next**

Verify whether Atlas is successfully installed. For more information, see [Verifying Atlas Installation](atlas-verifyinstal.md).

**Parent topic:** [Installing Project Giza](../topics/installandconfig.md)
