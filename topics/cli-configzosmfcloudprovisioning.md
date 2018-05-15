# Configure z/OS Management Facility Cloud Provisioning

As a systems programmer, complete the following z/OSMF cloud provisioning configurations tasks to supplement your Brightside CLI implementation with z/OSMF cloud provisioning:


  - [Install and configure the IBM z/OS Provisioning Toolkit](#install-and-configure-the-ibm-zos-provisioning-toolkit)
  - [Configure z/OSMF Cloud Provisioning](#configure-zosmf-cloud-provisioning)
  - [Set Up the z/OSMF Cloud Provisioning Service](#set-up-the-zosmf-cloudprovisioningservice)
  - [Implement the z/OS Cloud Portal Plug-in](#implement-the-zos-cloud-portal-plug-in)

**Important!** The [IBM z/OS Management Facility](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izu/izu.htm)
guide on the IBM Knowledge Center is your primary source of information about how to install and configure z/OSMF. Throughout the IBM procedures, we provide Brightside CLI-specific tips or requirements. We recommend that you open IBM documentation in a separate browser tab.


**Tip:** Cloud provisioning is the process of providing resources to a cloud provider's customers. With z/OSMF cloud provisioning enabled, you can issue Brightside CLI commands to provision CICS, DB2, development environments, and more. To learn more about z/OSMF and cloud
provisioning, see [What Cloud Provisioning is](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CloudProvSecurityIntro.htm#SummaryCloudProvisioning) on the IBM Knowledge Center.

For supplemental information about how security administrators configure the security for z/OSMF cloud provisioning, see [Configure z/OSMF Cloud Provisioning Security](cli-configzosmfcloudprovisioningsecurity.md).

## Install and configure the IBM z/OS Provisioning Toolkit

The [IBM® z/OS® Provisioning Toolkit](https://developer.ibm.com/mainframe/products/zospt/) is a
command line utility that lets systems programmers and application developers provision z/OS *development* environments. The toolkit lets application developers with minimal z/OS specific administration skills provision and deprovision z/OS applications quickly. The toolkit also lets system programmers easily manage the provisioning process by preconfiguring the environments, control developer access through z/OS security, and set appropriate provisioning
limits.

IBM provides the z/OS Provisioning Toolkit with the following pax file: `zospt_v#######.pax`. The toolkit runs on z/OS using UNIX System Services (USS).

**Follow these steps:**

1.  [Install the toolkit](#install-the-toolkit).
2.  [Configure the z/OSMF properties file and templates](#configure-the-zosmfproperties-file-and-templates).

### Install the toolkit

You acquire the z/OS Provisioning Toolkit installation files directly from IBM. You must have an IBM account to download the files.

**Follow these steps:**

1.  Download the following IBM Provisioning Toolkit zip file
    from [IBM](https://developer.ibm.com/mainframe/products/zospt/) (log
    in required).
            zospt_vx.x.x.zip
    `vx.x.x` represents the current version level of the
    toolkit.
        
    **Note:** The toolkit is fully supported and available to all IBM z/OS V2 clients at no additional charge.
        
2.  Unzip the file that you downloaded.

3.  Read the Readme file. The Readme file contains information about installing and configuring the toolkit. 
   
    **Note:** We extracted some of the subsequent steps from the Readme file and modified the steps as needed.
  
4.  Transfer the pax file in binary format to a USS directory on the system on which you want to run `zospt`.

5.  Unpackage the pax file.
        
    `pax -rf zospt_v#######.pax`
    
    The command creates a `zospt` directory.

6.  Ensure that the user ID that is associated with the `IZUSVR1` started task has read and  execute permissions to all directories in the `zospt` path. The z/OSMF setup refers to this     user ID as `IZUSVR`.

7.  Add `zospt` to the `PATH`.  
    
    `export PATH=$PATH:<zospt directory>/bin=`
        
    **Note:** The variable that is named `<zospt directory>` is the full path to the `zospt` installation directory.
      
8.  Add the toolkit bin to the default profile that resides in
    the `etc` directory. For example:    
   
    ```
    PATH=./:/bin:/usr/sbin:/usr/lpp/NFS:/usr/lpp/Printsrv/bin
    PATH=$PATH:/sys/s390util/bin
    PATH=$PATH:/var/zospt/zospt/bin
    ```

9.  Run z/OS Provisioning Toolkit. 
    
    ```zospt --help```
       
    If the installation was successful, the `zospt --help` output prints to the command line.

### Configure the z/OSMF properties file and templates

After you install the toolkit, you configure the z/OSMF properties file and the sample templates. We extracted the following steps from the Readme file that IBM provides with the installation files and modified these steps as needed for your z/OSMF implementation.

**Note:** The toolkit contains a properties file named `zosmf.properties`. You configure the properties file to let the toolkit communicate with z/OSMF. The properties file resides in the `zospt/config` directory.

**Follow these steps:**

1.  Test that the properties file is configured properly:    
    
    ```zospt ps```
    
2.  Configure the templates. The sample templates reside in the `zospt/templates` directory. To configure templates for your environment, copy the sample template directory into a new directory
    within the templates directory. For example, to copy the contents of the `..../zospt/templates/cics_53` directory to
    the `.../.zospt/templates/cics_53_copy` directory, issue the following command:    
       
    ```cp -R /var/zospt/zospt/templates/cics_53/var/zospt/zospt/templates/cics_53_copy```      

3.  Update (configure) the files and templates that you copied.

4.  Load the copies of the templates into z/OSMF so that you can test
    them.

5.  Edit the associated workflow using the workflow editor. To edit your
    templates, click Edit on the template definition
    page.
   
    **Important!** Do not edit the supplied sample workflow. Instead, copy the sample workflow directory contents into a new directory and update your template definition to refer to the copy.

After you complete these steps, you can use the provisioning toolkit to manage your z/OS development environment. For more information, see [Getting started with z/OS Provisioning Toolkit](https://www.ibm.com/support/knowledgecenter/SSXH44E_1.0.0/zospt/zospt-gettingstarted.html).

## Configure z/OSMF Cloud Provisioning

As a systems administrator, you set up the components and plug-ins that
z/OSMF cloud provisioning requires and set up the z/OSMF cloud
provisioning service.
  - [Required z/OS Components and Plug-ins](#zos-requirements-and-zosmf-plug-ins)
  - [How z/OSMF Resource Management Works](#how-zosmf-resource-management-works)
  - [How z/OSMF Software Services Works](#how-zosmf-software-services-work)

### z/OS requirements and z/OSMF plug-ins

For information about the components and plug-ins for z/OSMF cloud provisioning that are required for Brightside CLI, see [Configure z/OS Management Facility](cli-configzosmf.md#install-and-configure-zosmf).

### View the z/OSMF Cloud Provisioning branch

The z/OSMF Cloud Provisioning branch in the z/OSMF navigation tree consists of **Resource Management** and **Software Services**. The information that displays on the navigation
tree in IBM z/OS Management Facility behaves in a manner that is contingent upon the existence of user IDs in various cloud provisioning user groups. Consider the following requirements:

  - To view and access Resource Management in the navigation tree, the user IDs must be a member of the user group that is designated as the Landlord group for the site. Or, the user IDs must be a member of a  Domain Administrators group.
  - To view and access Software Services in the navigation tree, the user IDs must be a member of the Landlords group, the Domain Administrators group, the Approvers group, or a consumer. A consumer is a user or a user group that is associated with a tenant.
  - Members of the Resource Pool Administrators group can view and access Configuration and Configuration Assistant in the navigation tree in the IBM z/OS Management Facility.
  - Members of the WLM Resource Pool Administrators group can view and access Performance and Workload Management in the navigation tree in IBM z/OS Management Facility.
  - Landlords have access to all domains.
  - Domain Administrators can access only the domains for which they are designated as
Administrators.

**More information:**

  - [How z/OSMF Resource Management Works](#how-zosmf-resource-management-works)
  - [How z/OSMF Software Services Works](#how-zosmf-software-services-work)

### How z/OSMF Resource Management works

As a systems programmer, Resource Management lets you provision domains, tenants, and resource pools. Resource Management also lets you create and maintain domains and tenants.

**Tip:** To learn more about z/OSMF and cloud provisioning, see [What Cloud Provisioning is](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CloudProvSecurityIntro.htm#SummaryCloudProvisioning)
on the IBM Knowledge Center.

**Key roles:**

  - **Landlords**  
    Define cloud domains and their associated resources. Designates domain administrators.
  - **Domain administrators**  
    Manage domains, define, and manage the relationships for and between domain services, tenants, and resource pools.
  - **Resource pool administrators**  
    Manage networking and workload management (WLM) resources in clouds.
  - **Domain Approvers**  
    Approve pending approval records for templates.
  - **Security administrators**  
    Maintain the security management systems for installations. 

With Resource Management, you can perform the following tasks:

  - **Create domains**  
    Users that are designated as Landlords can perform the following tasks:
    
      - Specify Resource Pool administrators (Network and WLM)    
      - Specify Domain Approvers    
      - Specify the Security Administrator for the Domain    
      - Specify Domain Administrators

  - **Create tenants**
    
    Users that are designated as Landlords or Domain Administrators can perform the following tasks:
    
      - Add Template and Resource Pool    
      - Add users or user groups for the domain 

### How z/OSMF Software Services works

As a systems programmer, Software Services lets you create and manage templates and domains, and create, manage, and provision software instances.

**Tip:** To learn more about z/OSMF and cloud provisioning, see [What Cloud Provisioning is](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CloudProvSecurityIntro.htm#SummaryCloudProvisioning) on the IBM Knowledge Center.

**Key roles:**

  - **Landlords**  
    Define cloud domains and their associated resources. Designates domain administrators.
  - **Domain administrators**  
    Manage domains, define, and manage the relationships for and between domain services, tenants, and resource pools.
  - **Domain approvers**  
    Approve pending approval records for templates.

With Software Services, you can perform the following tasks:

  - **Add templates to domains**  
    Users that are designated as Service Providers prepare the templates. The user ID for the Service Provider must be identified as the Landlord or the Domain Administrator. The user ID for the Service Provider must also have read access to the following
    resource profile in the `ZMFAPLA` class:
    
    ``` <SAF-prefix>.ZOSMF.PROVISIONING.SOFTWARE_SERVICES```

  - **Approve templates**  
    Users that are designated as Approvers for the domain or users that can be found in the following properties files for the CICS template can approve templates. Changes to the domain, tenant, template, or resource pools can change the status of templates, which in turn can cause approval records to require re-approval. For example, when z/OSMF recognizes changes to the WLM, the template added under the previous version of the WLM is invalidated until the WLM under z/OSMF is updated with the change.   
    
    ```
    DFH_APPROVER_TSO
    DFH_APPROVER_ZFS
    DFH_APPROVER_CONSOLE
    DFH_APPROVER_SECURITY
    ```
    
  - **Provision software from templates**

    This task lets you create an instance of the software. To provision software from templates, the user ID for the user that is performing this task must be defined as a consumer of the template. By default, members of the Landlord and the Domain Administrator groups are defined as consumers of the templates.

  - **Manage software instances**
    
    To manage software instances, the user ID for the user that is performing this task must be defined as a consumer of the template. By default, members of the Landlord and the Domain
    Administrator groups are defined as consumers.

## Set Up the z/OSMF Cloud Provisioning service

As a systems programmer, you set up the cloud provisioning service in z/OSMF so that users can submit Brightside CLI provisioning commands.

**Follow these steps:**

1.  Open the IBM z/OS Management Facility.

2.  Create your domains. From the z/OSMF navigation tree, expand Cloud Provisioning, click Resource Management, click the Actions menu, and then click Create Domain. Complete the required fields on the screen to create a domain.

3.  Add your templates. From the z/OSMF navigation tree, expand Cloud Provisioning, click Software Services, Templates, click the Actions menu, and then click Add Template to a Domain. Specify the workflow, action, and variable files that the software vendor provided.

4.  (Optional) Add your Network Resource Pools. From the z/OSMF navigation tree, expand Configuration, click Configuration Assistant, click the Actions menu, and then click Manage z/OS Cloud. Complete the required fields to add a Network Resource Pool.  
 
    **Note:** You perform this step only when the template requires a
    Network Resource Pool.  

5.  Create your tenants. From the z/OSMF navigation tree, expand Cloud Provisioning, click Resource Management, click the Actions menu, and then click Create Tenant. Complete the required fields on the screen to create a tenant, specify users, the template to use, and the information about the Network Resource Pool.
    
    **Note:** From Cloud Provisioning, Software Services, there is also an action option to associate a tenant.
    
6.  Approve your templates. From the z/OSMF navigation tree, expand Cloud Provisioning, click Software Services, click Templates, click the Actions menu, and then click Approve Templates. You approve your templates under Perform Approvals.

7.  Test your templates. Click the Templates tab and click the check box next to the templates that you want to test. Click the Actions menu and then click Test. Verify that the templates create your instances successfully.

8.  Publish your templates to make them available to users. From the Templates tab, click the check boxes next to the templates that you want to publish. Click the Actions menu and then click Publish to publish your templates.

9.  Create your software instances. From the navigation tree, click Cloud Provisioning, click Software Services, and then click the Instances tab. Click the Actions menu and then click Run Templates on the menu to create your software instances.

    **Note:** For information about how security administrators configure the security
for z/OSMF cloud provisioning, see [Configure z/OSMF Cloud Provisioning
Security](cli-configzosmfcloudprovisioningsecurity.md).

## Implement the z/OS Cloud Portal Plug-in

Cloud Provisioning for z/OS includes a sample marketplace and market administration to make published software services easily available to consumers. The plug-in lets you make software services available to marketplace consumers and it adds the Marketplace and Marketplace Administration tasks to the z/OSMF navigation tree.

Use the z/OSMF Import Manager to implement and remove the plug-in.

**Note:** The z/OS Cloud Portal Plug-in is an optional component. As a systems programmer, you can implement the plug-in based on the requirements of your site. For more information about the plug-in, see [Updating z/OS for the Cloud Portal plug-in](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CloudProvPortalSetup.htm) on the IBM Knowledge Center.

### Implement the plug-in

To implement the plug-in, specify the following file and click Import:

```/usr/lpp/zosmf/samples/cloudportal/cloudportal.properties```

### Remove the plug-in

To remove the plug-in, specify the following file and then click Import:

```/usr/lpp/zosmf/samples/cloudportal/cloudportaldelete.properties```

### Modify the plug-in

As a systems programmer, you can modify the plug-in at any time to meet site requirements. To modify the plug-in, create a copy of your directory into your directory and then edit and import the copy.
