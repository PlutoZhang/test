# Troubleshooting installing Atlas

If Atlas REST APIs do not work, check the following items:

-   Check whether your Atlas Liberty server is running.

    You can check this in the Display Active \(DA\) panel of SDSF under ISPF. The FEKATLS task should be running. If the FEKATLS task is not running, start the Atlas server by using the following `START` operator command:

    ```
    S FEKATLS
    ```

    You can also use the operator command `D A, ATLAS` to verify whether the task is active, which alleviates the need for SDSF. If the started task is not running, ensure that your FEKATLS procedure resides in a valid PROCLIB data set, and check the task’s job output for errors.

-   Check whether the Atlas server is started without errors.

    In the Display Active \(DA\) panel of SDSF under ISPF, select the FEKATLS job to view the started task output. If the Atlas server is started without errors, you can see the following messages:

    ```
    CWWKE0001I: The server Atlas has been launched.
    ```

    ```
    CWWKF0011I: The server Atlas is ready to run a smarter planet.
    ```

    If you see error messages that are prefixed with "ERROR" or stack traces in the FEKATLS job output, respond to them.

-   Check whether the URL that you use to call Atlas REST APIs is correct. For example: https://your.server:atlasport/Atlas/api/system/version. The URL is case-sensitive.
-   Ensure that you enter a valid z/OS® user ID and password when initially connecting to the Atlas Liberty server.
-   If testing the Atlas REST API for jobs information fails, check the z/OSMF IZUSVR1 task output for errors. If no errors occur, you can see the following messages in the IZUSVR1 job output:

    ```
    CWWKE0001I : The server zosmfServer has been launched.
    ```

    ```
    CWWKF0011I: The server zosmfServer is ready to run a smarter planet.
    ```

    If you see error messages, respond to them.

    For RESTJOBS, you can see the following message if no errors occur:

    ```
    CWWKZ0001I: Application IzuManagementFacilityRestJobs started in n.nnn seconds.
    ```

    You can also call z/OSMF RESTJOBS APIs directly from your internet browser with a URL, for example,

    https://your.server:securezosmfport/zosmf/restjobs/jobs

    where the *securezosmfport* is 443 by default. You can verify the port number by checking the *izu.https.port* variable assignment in the z/OSMF `bootstrap.properties` file.

    If calling the z/OSMF RESTJOBS API directly fails, fix z/OSMF before Atlas can use these APIs successfully.

-   If testing the Atlas REST API for dataset information fails, check the z/OSMF IZUSVR1 task output for errors and confirm that the z/OSMF RESTFILES services are started successfully. If no errors occur, you can see the following message in the IZUSVR1 job output:

    ```
    CWWKZ0001I: Application IzuManagementFacilityRestFiles started in n.nnn seconds.
    ```

    You can also call z/OSMF RESTFILES APIs directly from your internet browser with a URL, for example,

    https://your.server:securezosmfport/zosmf/restfiles/ds?dslevel=userid.**

    where the *securezosmfport* is 443 by default. You can verify the port number by checking the *izu.https.port* variable assignment in the z/OSMF `bootstrap.properties` file.

    If calling the z/OSMF RESTFILES API directly fails, fix z/OSMF before Atlas can use these APIs successfully.

    **Tip:** The z/OSMF installation step of creating a valid IZUFPROC procedure in your system PROCLIB might be missed. For more information, see the *z/OSMF Configuration Guide*.

    The IZUFPROC member resides in your system PROCLIB, which is similar to the following sample:

    ```
    //IZUFPROC PROC ROOT='/usr/lpp/zosmf'  /* zOSMF INSTALL ROOT     */
    //IZUFPROC EXEC PGM=IKJEFT01,DYNAMNBR=200                          
    //SYSEXEC  DD DISP=SHR,DSN=ISP.SISPEXEC                            
    //         DD DISP=SHR,DSN=SYS1.SBPXEXEC                           
    //SYSPROC  DD DISP=SHR,DSN=ISP.SISPCLIB                            
    //         DD DISP=SHR,DSN=SYS1.SBPXEXEC                           
    //ISPLLIB  DD DISP=SHR,DSN=SYS1.SIEALNKE                           
    //ISPPLIB  DD DISP=SHR,DSN=ISP.SISPPENU                            
    //ISPTLIB  DD RECFM=FB,LRECL=80,SPACE=(TRK,(1,0,1))                
    //         DD DISP=SHR,DSN=ISP.SISPTENU                            
    //ISPSLIB  DD DISP=SHR,DSN=ISP.SISPSENU                            
    //ISPMLIB  DD DISP=SHR,DSN=ISP.SISPMENU                            
    //ISPPROF  DD DISP=NEW,UNIT=SYSDA,SPACE=(TRK,(15,15,5)),            
    //         DCB=(RECFM=FB,LRECL=80,BLKSIZE=3120)                     
    //IZUSRVMP DD PATH='&ROOT./defaults/izurf.tsoservlet.mapping.json'  
    //SYSOUT   DD SYSOUT=H                                              
    //CEEDUMP  DD SYSOUT=H                                              
    //SYSUDUMP DD SYSOUT=H                                              
    //                                                                 
    ```

    **Note:** You might need to change paths and data sets names to match your installation.

    A known issue and workaround for RESTFILES API can be found at [TSO SERVLET EXCEPTION ATTEMPTING TO USE RESTFILE INTERFACE](http://www-01.ibm.com/support/docview.wss?crawler=1&uid=isg1PI63398).

-   Check your system console log for related error messages and respond to them.

If the Atlas server cannot connect to the z/OSMF server, check the following item:

By default, the Atlas server communicates with the z/OSMF server on the localhost address. If your z/OSMF server is on a different IP address to the Atlas server, for example, if you are running z/OSMF with Dynamic Virtual IP Addressing (DVIPA), you can change this by adding a `ZOSMF_HOST` parameter to the server.env file. For example: `ZOSMF_HOST=winmvs27`.


**Parent topic:** [Installing Project Giza](topics/installandconfig.md)
