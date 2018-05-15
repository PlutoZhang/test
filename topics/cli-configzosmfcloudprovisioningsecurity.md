# Configure z/OS Management Facility Cloud Provisioning security

**Important!** The [IBM z/OS Management
Facility](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izu/izu.htm)
guide on the IBM Knowledge Center is your primary source of information
about how to install and configure z/OSMF. Throughout the IBM
procedures, we provide Brightside CLI-specific tips or requirements. We recommend that you open IBM documentation in a separate
browser tab.

## Configure z/OSMF Cloud Provisioning to use IBM RACF security

For RACF installations, IBM provides security commands in `SYS1.SAMPLIB` for Cloud provisioning. If you do not see RACF commands for Cloud Provisioning in member `IZUSEC`, you might need to apply various APAR or PTFs or upgrade your current level of z/OSMF.

  - [Required APARs and PTFs](#required-apars-and-ptfs)
  - [How the RACF security REXX EXEC workflow works](#how-the-racf-security-rexx-exec-workflow-works)
  - [Security groups naming conventions](#security-groups-naming-conventions)
  - [ZMFCLOUD class resource profiles for Cloud Provisioning](#zmfcloud-class-resource-profiles-for-cloud-provisioning)
  - [Restrict access to z/OS UNIX file systems](#restrict-access-to-zos-unix-file-systems)

**Note:** For more information about configuring z/OSMF cloud
provisioning using RACF, see [Security configuration requirements for
z/OSMF](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_SecurityStructuresForZosmf.htm)
on the IBM Knowledge Center.

### Required APARs and PTFs

For z/OS V2R2, our installation requires the following IBM z/OS APARs
and PTFs:

`PI70526 / UI42847`

`PI67837 / UI42849`

`PI73643 / UI43848`

`PI77710 / UI46267`

`PI77388 / UI46543 (`Manual security mode for a domain)

### How the RACF security REXX EXEC workflow works

The RACF REXX exec workflow creates multiple domain-specific user groups and issues commands that permit the user groups to access protected class resources that are also domain-specific.
 
You can find the RACF Security REXX exec workflow in the following file:

```/var/zosmf/configuration/workflow/izu.provisioning.security.config.rexx```

The REXX exec workflow creates and maintains the following user groups:

  - **Domain Landlords:** Define cloud domains and their associated resources. Designates domain administrators.
  - **Domain Administrators:** Manage domains, define, and manage the relationships for and between domain services, tenants, and resource pools.
  - **Resource Pool WLM Resource Pool Administrators:** Manage networking and workload management (WLM) resources in clouds.
  - **Consumers:** Access the software services and resource pools for
tenants.

    **Important!** When Landlords or Domain Administrators create or modify domains, the RACF Security REXX exec workflow is submitted under the user ID that was designated as the security administrator for the domain. The workflows behave in this manner even when the domain security administrator is (or is not) logged in as the user that is creating or modifying the domain. Although landlords or domain administrators might not possess the RACF SPECIAL attribute, they can submit security workflows under a USERID of someone that possesses the RACF SPECIAL attribute. However, there is a security exposure when you use this approach.

  - As a USS file, the Security REXX exec can be modified by anyone that has write access, which includes super users, but not necessarily security administrators.

      IBM's response to this exposure is as follows:

  - After security administrators define the resources and activate the FSACCESS class, the z/OSMF data file system is protected. Only the users that are permitted to this access the resource can update them. Therefore, UID(0) cannot manipulate z/OSMF files unless they are explicitly authorized to do so. IZUSVR (the user ID of the z/OSMF started task server) and IZUSECAD (the z/OSMF security admin group) need to be granted with UPDATE access to this resource.

For more information, see [OA35970: NEW FUNCTION - NEW ACCESS CONTROL CHECK USING FSACCESS CLASS PROFILE. SEE ALSO OA35973 AND OA35974](http://www-01.ibm.com/support/docview.wss?uid=isg1OA35970) on the IBM Support website.

### Security groups naming conventions

By default, the name of the security user group that contains Domain Landlords is **`IYU`**. The Domain Landlord user group name is also used by z/OSMF as a prefix to all the security user groups for a domain when a domain is created.

The name of the Landlord user group should be the same as the name that is identified to z/OSMF in your system `PARMLIB IZUPRMxx` member, for parameter `CLOUD_SAF_PREFIX`.  By default, `CLOUD_SAF_PREFIX('IYU')`.

Only the user IDs that are members of the Domain Landlord group and in the Administrator group for the domain can see the **Resource Management** and **Software Services** options the **Cloud
Provisioning** section of the IBM z/OS Management Facility navigation tree.

![z/OSMF Tree Cloud Provisioning](/images/zosmf/433363266.png "z/OSMF Tree Cloud Provisioning")

**Note:** Both of the Cloud Provisioning options are ***not required*** to provision. As a Landlord, each domain that you create is associated with a Domain ID. The Domain ID is assigned during the process of creating the domain and cannot be modified. The process uses the `CLOUD_SAF_PREFIX` value followed by a number to create the Domain ID.

The naming convention for security user groups in a Domain is the Domain ID followed by a group identifier. For example, `(0, RPAN,RPAW,00).` The following example illustrates the naming convention for security user groups in a Domain: 

  - **Default Domain ID:** `IYU0`  
    **Example: **The CLOUD\_SAF\_PREFIX, is IYU plus the number `0`
  - **Domain Administrators user group:** `IYU0`
  - **Network Resource Pool Administrators user group:** `IYU0RPAN`
  - **WLM Resource Pool Administrators user group:** `IYU0RPAW`
  - **Tenant consumers of the domain resources user group:** `IYU000`

### ZMFCLOUD class resource profiles for Cloud Provisioning

Cloud provisioning for z/OSMF requires the following profiles and
user groups:

```IZUDFLT.ZOSMF.PROVISIONING.RESOURCE_MANAGEMENT.IYU IYU```
```IZUDFLT.ZOSMF.SECURITY.ADMIN IZUSECAD```

You can find the provisioning RACF Security REXX exec Workflow that IBM provides in the following file:

```/var/zosmf/configuration/workflow/izu.provisioning.security.config.rexx```

The Landlord that created the Domain submits the REXX exec workflow under the user ID that was specified as the Domain Security Administrator. To execute the Security REXX exec Workflow successfully,the Domain Security Administrator's user ID must be associated with the RACF SPECIAL attribute, and connected to the IZUSECAD user group.

### Restrict access to z/OS UNIX file systems

Security administrators can use RACF to provide and maintain data and system security to z/OS UNIX file
systems.

**Note:** For more information, see [Using the FSACCESS class profile to restrict access](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.bpxb200/fsastepp.htm) on the IBM Knowledge Center.

**Note:** When the FSACCESS class profile is active, RACF uses the FSACCESS class profile resources to determine whether the user is authorized to access the file system. When the user is authorized to access the file system resource, RACF uses the permission bits, Access Control Lists (ACLs), and various UNIXPRIV class profiles to determine if the user is authorized to access the individual file system objects with the requested access level.

The provisioning RACF Security REXX exec Workflow establishes the following profiles, user groups, and permissions during the process of creating a domain: 

```IZUDFLT.ZOSMF.PROVISIONING.RESOURCE_MANAGEMENT.IYUx IYU (Permit Only) IYUx```

```IZUDFLT.ZOSMF.RESOURCE_POOL.NETWORK.IYUx IYUxRPAN```

```IZUDFLT.ZOSMF.RESOURCE_POOL.WLM.IYUx IYUxRPAW```

```IZUDFLT.ZOSMF.TEMPLATE.APPROVERS.IYUx Individual user access```

The process of creating templates and template instances (where the domain ID is `IYUx`) establishes the following profiles and user groups:

```IZUDFLT.ZOSMF.TEMPLATE.APPROVERS.IYUx.templatename Individual user access or user groups```

```IZUDFLT.ZOSMF.TEMPLATE.INSTANCE.IYUx.templatename_instancename IYUx00```

The process of creating tenants (where the domain ID is `IYUx`) establishes the following profiles and user groups: 

```IZUDFLT.ZOSMF.PROVISIONING.RESOURCE_MANAGEMENT.IYUx00 IYUx00```

## Next steps

After you complete the security administration for z/OSMF and cloud provisioning, systems programmers, security administrators, and application developers can issue the validate profile command. The command tests the end-to-end solution to verify that Brightside CLI can communicate with z/OS systems properly. For more information, see [Identify and Correct Problems Detected by the Validate Profile Command](cli-validateInstallationcorrectproblems.md). 

Work with a systems programmer to correct any problems in the profile validation report. When all tests receive an *OK* result, application developers can install Brightside CLI and issue commands on z/OS systems.