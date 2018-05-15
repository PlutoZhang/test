# Configure z/OS Management Facility security

As a security administrator, complete the following z/OSMF security
configuration tasks for your Brightside CLI implementation:

  - [Configure z/OS REST services SAF security](#configure-zos-rest-services-saf-security)
  - [Configure z/OS console REST interface](#configure-zos-console-rest-interface)
  - [Configure z/OS data set and file REST interface](#configure-zos-data-set-and-file-rest-interface)
  - [Configure z/OSMF plug-in security](#configure-zosmf-plug-in-security)

**Important!** The [IBM® z/OS Management Facility](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izu/izu.htm)
guide on the IBM Knowledge Center is your primary source of information about how to install and configure z/OSMF. Throughout the IBM procedures, we provide Brightside CLI-specific tips or requirements. We recommend that you open IBM documentation in a separate browser tab.

## Configure z/OS REST services SAF security 

A security administrator must configure security to allow z/OSMF System Authorization Authority (SAF) access to the resources that Brightside CLI requires. Brightside CLI uses REST endpoints that are associated with each z/OSMF REST API. After you complete all z/OSMF and z/OSMF cloud provisioning configurations, you can [issue the validate profile command](cli-validateInstallationcorrectproblems.md) to verify that Brightside CLI can communicate with z/OS systems through the REST APIs. 

**Important!** Before you allow users to issue z/OS console commands with Brightside CLI, security administrators should ensure that they provide access to commands that are appropriate for their organization.

The following table details the required z/OSMF REST services and examples of the Brightside CLI features they enable. If the profile validation command returns any errors, use this table to find IBM documentation for the z/OSMF REST APIs.

<div class="table-wrap">

<table>
<thead>
<tr class="header">
<th style="text-align: left;">z/OSMF REST Service</th>
<th>REST Endpoint</th>
<th style="text-align: left;">Description</th>
<th style="text-align: left;">More Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Cloud provisioning services </td>
<td>Endpoints that begin with: <code>/zosmf/provisioning/</code></td>
<td style="text-align: left;"><span>C</span><span>loud provisioning for development environments.</span></td>
<td style="text-align: left;"><ul>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/izuprog_CloudProvisioning.htm" class="external-link">Cloud provisioning services</a></li>
<li><a href="433363265.html">Configure z/OS Management Facility Cloud Provisioning Security</a></li>
</ul></td>
</tr>
<tr class="even">
<td style="text-align: left;">TSO/E address space services </td>
<td><p>Endpoints that begin with:</p>
<p><code>/zosmf/tsoApp</code></p></td>
<td style="text-align: left;">TSO commands (<code>bright zos-tso issue</code>).</td>
<td style="text-align: left;"><ul>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/izuprog_API_TSOServices.htm" class="external-link">TSO/E address space services</a></li>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_SecurityStructuresForZosmf.htm#DefaultSecuritySetupForZosmf__ResourceAuthorizationsForRESTapi" class="external-link">Class activations that z/OSMF requires</a></li>
</ul></td>
</tr>
<tr class="odd">
<td style="text-align: left;">z/OS console services </td>
<td><p>Endpoints that begin with:</p>
<p><code>/zosmf/restconsoles/</code></p>
<p>Example:</p>
<p><code>/zosmf/restconsoles/defcn</code></p></td>
<td style="text-align: left;">Console commands (<code>bright zos-console issue</code>). Any MVS console command such as MODIFY and DISPLAY.</td>
<td style="text-align: left;"><ul>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/IZUHPINFO_API_RESTCONSOLE.htm" class="external-link">z/OS console services</a></li>
<li><a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CommonLogonProcSetup.htm" class="external-link">Updating your system for the z/OS console REST interface</a></li>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_SecurityStructuresForZosmf.htm#DefaultSecuritySetupForZosmf__ResourceAuthorizationsForRESTapi" class="external-link">Resource authorizations for the z/OS console services REST interface</a></li>
</ul></td>
</tr>
<tr class="even">
<td style="text-align: left;">z/OS data set and file REST interface</td>
<td><p>Endpoints that begin with:</p>
<p><code>/zosmf/restfiles/</code></p>
<p>Example:</p>
<p><span style="font-family: monospace;">/zosmf/restfiles/ds/&lt;dsname&gt;</span></p></td>
<td style="text-align: left;"><p>Create data sets (<code>bright zos-files create</code>), delete data sets (<code>bright zos-files delete</code>), read (download) data sets (<code>bright zos-files download</code>), and write (upload) data sets (<code>bright zos-files upload</code>). </p>
<p>Access to access method services (IDCAMS) (<code>bright zos-files invoke access-method-services</code>).</p></td>
<td style="text-align: left;"><ul>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/IZUHPINFO_API_RESTFILES.htm" class="external-link">z/OS data set and file REST interface</a></li>
<li><a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_LogonProcSetup.htm" class="external-link">Updating your system for the z/OS data set and file REST interface</a></li>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_SecurityStructuresForZosmf.htm#DefaultSecuritySetupForZosmf__ResourceAuthorizationsForRESTapi" class="external-link">Resource authorizations for the z/OS data set and file REST it</a></li>
</ul></td>
</tr>
<tr class="odd">
<td style="text-align: left;">z/OS jobs REST interface</td>
<td><p>Endpoints that begin with:</p>
<p><code>/zosmf/restjobs/</code></p>
<p>Example:</p>
<p><span style="font-family: monospace;">/zosmf/restjobs/jobs/&lt;jobname&gt;/&lt;jobid&gt;</span></p></td>
<td style="text-align: left;"><p>Submit jobs (<code>bright zos-jobs submit)</code>, purge jobs, and read job output.</p>
<p>List jobs (<code>bright zos-jobs list</code>).</p></td>
<td style="text-align: left;"><ul>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/IZUHPINFO_API_RESTJOBS.htm" class="external-link">z/OS jobs REST interface</a></li>
<li><a href="https://docops.ca.com/Resource%20authorizations%20for%20the%20z/OS%20jobs%20REST%20interface">Resource authorizations for the z/OS jobs REST interface</a></li>
</ul></td>
</tr>
<tr class="even">
<td style="text-align: left;">z/OSMF workflow services </td>
<td><p><span>Endpoints that begin with:</span></p>
<p><code>/zosmf/workflow/</code></p></td>
<td style="text-align: left;">Cloud provisioning for development environments.</td>
<td style="text-align: left;"><ul>
<li><a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/izuprog_API_WorkflowServices.htm" class="external-link">z/OSMF workflow services</a></li>
</ul></td>
</tr>
</tbody>
</table>

## Configure z/OS console REST interface

Review the following recommendations for configuring the security for z/OS console REST services:

  - Add the `COMMON_TSO` statement to the `IZUPRMxx` parmlib member to customize the z/OSMF options for the logon procedure. 
  - Define a value of at least 50000 KB as the size of the address space for the user's logon procedure. To help you prevent system memory exception errors from occurring, confirm that this value is acceptable in your environment. 
  - Ensure that the members in your z/OSMF user security group can issue `TSO` and `CONSOLE` commands. IBM provides RACF statements for user group `IZUUSER`. To prevent all z/OSMF users from issuing `TSO` and `CONSOLE` commands, you can create more z/OSMF user groups for more granular security.
  - Ensure that the `OPERCMD` class is active and that your MVS commands are protected. MVS commands include, but are not limited to, the `MVS` and `MVS.MCSOPER` resource prefixes.
  - Ensure that the z/OSMF user security groups can access (authorized) the logon procedure name and account number that is specified in the `COMMON_TSO` statement.
  - Define a `TSO` segment for all the z/OSMF users.

**Note:** For detailed instructions for how to configure the z/OS console REST services, see [Updating your system for the z/OS console REST interface](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CommonLogonProcSetup.htm) on the IBM Knowledge Center.

## Configure z/OS data set and file REST interface

Review the following recommendations for configuring z/OS the security for data set and file REST services:

  - Add the `COMMON_TSO` statement to the `RESTAPI_FILE` parmlib member to customize the z/OSMF options for the logon procedure.

  - Define a value of at least 65536 KB as the size of the address space for the user's logon procedure. To help you prevent system memory exception errors from occurring, confirm that this value is acceptable in your environment.

  - Authorize z/OSMF user groups and the z/OSMF server to CEA TSO/E address space services.

  - Ensure that the <span class="ph">z/OSMF</span> user security groups can access (authorized) the logon procedure name and account number that is specified on the `COMMON_TSO` statement.

  - Define a `TSO` segment for all the span z/OSMF users.

  - Define at least 20971520 KB (20 MB) the `IPCMSGQBYTES` option of your parmlib member named `BPXPRMxx`. IBM recommends this value to let TSO and z/OSMF communicate using z/OS USS interprocess communications.

**Note:** For detailed instructions for how to configure the z/OS data set and file REST services, see [Updating your system for the z/OS data set and file REST interface](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_LogonProcSetup.htm) on the IBM Knowledge Center.

## Configure z/OSMF plug-in security

Ensure that you implement all the required security for the plug-ins. For more information, see [Setting up security for the z/OSMF plug-ins](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_EstablishingSecurity.htm) on the IBM Knowledge Center.

**Notes:**

  - For systems that are secured by RACF, ensure that the TRUSTED attribute is assigned to the CEA started task.
  - If you want to implement the use of certificates to access Brightside CLI, security administrators can configure the certificates for Brightside CLI users. For more information, see [Using the z/OSMF REST services](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua700/IZUHPINFO_RESTServices.htm).