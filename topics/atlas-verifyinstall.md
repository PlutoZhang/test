# Verifying Atlas installation

After Atlas is installed and the FEKATLS procedure is started, you can verify the installation from an internet browser by using the following URL:

https://*your.server*:*atlasport*/Atlas/api/system/version

where *your.server* matches the host name or IP address of your z/OS® system where Atlas is installed, and *atlasport* matches the port number that is chosen during installation. You can verify the port number in the server.xml file that is located in the Atlas installation directory, which is */var/atlas/wlp/usr/servers/Atlas/server.xml* by default. Look for the httpsPort assignment in the *server.xml* file, for example: httpPort="7443".

**Important:** This URL is case-sensitive.

This URL sends an HTTP GET request to your Liberty Profile Atlas server. If Atlas is installed correctly, a JSON payload that indicates the current Atlas application version is returned. For example:

```
{ "version": "V0.0.1" }
```

**Note:** For the first interaction with the Atlas server, you are prompted to enter an MVS™ user ID and password. The MVS user ID and password are passed over the secure HTTPS connection to establish authentication.

After you verify that Atlas was successfully installed, you can access the UI at:

https://*your.server:atlasport*/ui/\#/

## Verifying the availability of Atlas REST APIs

To verify the availability of all Atlas REST APIs, use the Liberty Profile's REST API discovery feature from an internet browser with the following URL:

https://*your.server:atlasport*/ibm/api/explorer

**Note:** This URL is case-sensitive.

With the discovery feature, you can also try each discovered API. The users who verify the availability must have access to their data sets and job information by using relevant Atlas APIs. This ensures that your z/OSMF configuration is valid, complete, and compatible with the Atlas application. For example, try the following APIs:

 Atlas : JES Jobs APIs  
       `GET  /Atlas/api/jobs`  
       This API returns job information for the calling user.   
 Atlas : Dataset APIs  
       `GET /Atlas/api/datasets/userid.**`  
       This API returns a list of the userid.** MVS datasets.

If Atlas is not installed successfully, see [Troubleshooting installation](troubleshoot.md) for solutions.

**Parent topic:** [Installing Atlas](../topics/install.md)
