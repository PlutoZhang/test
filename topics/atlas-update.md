# Updating Atlas

You can monitor the [GitHub repository](https://github.com/gizafoundation/Downloads/releases) for service availability of Atlas. When maintenance is available, you can apply the service to Atlas by replacing the WAR files only or the whole service package.

To replace the WAR files, take the following steps:

1.  Download the update package as a .zip file.
2.  Extract the .zip file on your personal machine or by using zip utilities on the mainframe.
3.  Back up and delete the existing WAR files located at *"\{server root folder\}/wlp/usr/servers/Atlas/apps"*.
4.  Transfer the new WAR files to the server at the same location *"\{server root folder\}/wlp/usr/servers/Atlas/apps"*.
5.  Restart the Atlas server:
    Stop:
    Enter the `STOP` operator command:
    ```
    P FEKATLS
    ```
    Start:
    Enter the `START` operator command:
    ```
    S FEKATLS
    ```

To replace the whole service package, take the following steps:

1.  Stop the Atlas server:
    Enter the `STOP` operator command:
    ```
    P FEKATLS
    ```
2.  Follow instructions to [uninstall Atlas](../topics/atlas-uninstall.md).
3.  Follow instructions to [install Atlas](../topics/atlas-install.md) with the desired install package.

    **Note:** By default, Atlas server configuration switches off application monitoring in the Liberty *server.xml* file. For "hot deploy", you can remove this setting in the *server.xml* file to avoid the need to stop and restart your Atlas server. For more information, see WebSphere® Liberty Profile documentation.


After restarting the Atlas server, you can check the version of Atlas that you installed from the swagger interface, which is `Atlas/api/system/version` under System APIs.

**Parent topic:** [Updating Project Giza](../topics/update.md)
