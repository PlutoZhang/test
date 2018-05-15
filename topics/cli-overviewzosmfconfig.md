# Overview of the z/OS Management Facility configuration process

Before application developers can use Brightside CLI to interact with
z/OS systems, systems programmers and security administrators must
install and configure IBM z/OS
Management Facility (z/OSMF) in your environment.

z/OSMF provides remote system management functions so that you can use
Brightside CLI to more easily manage the operations and administration
of your z/OS
systems.

**Important!** The [IBM z/OS Management Facility](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izu/izu.htm)
guide on the IBM Knowledge Center is your primary source of information
about how to install and configure z/OSMF. Throughout the IBM
procedures, we provide Brightside CLI-specific tips or requirements. We
recommend that you open IBM documentation in a separate browser tab.

The following table describes the recommended configurations and the
role of the individual that is most suited to perform the
configurations.

<div class="table-wrap">

<table>
<thead>
<tr class="header">
<th>Role</th>
<th>Title</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Systems Programmers</td>
<td><a href="cli-configzosmf.md">Configure z/OS Management Facility</a></td>
<td><p>Describes how systems programmers perform the following z/OSMF configuration tasks:</p>
<ul>
<li>Obtain z/OSMF Installation and Configuration Materials</li>
<li>Install z/OSMF</li>
<li>Select and Configure your z/OSMF Plug-ins</li>
</ul></td>
</tr>
<tr class="even">
<td>Security Administrators</td>
<td><a href="cli-configzosmfsecurity.md">Configure z/OS Management Facility Security</a></td>
<td><p>Describes how security administrators perform the following <span>z/OSMF</span> security configuration tasks:</p>
<ul>
<li>Configure z/OS REST Services SAF Security</li>
<li>Configure z/OSMF Plugin Security</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Systems Programmers</p></td>
<td><a href="cli-configzosmfcloudprovisioning.md">Configure z/OS Management Facility Cloud Provisioning</a></td>
<td><p>Describes how systems programmers perform the following <span>z/OSMF</span> cloud provisioning configuration tasks:</p>
<ul>
<li>Install and Configure the IBM z/OS Provisioning Toolkit</li>
<li>Configure z/OSMF Cloud Provisioning</li>
<li>Set Up the z/OSMF Cloud Provisioning Service</li>
<li><span class="sv-ti-done">Implement the z/OS Cloud Portal Plug-in</span></li>
</ul></td>
</tr>
<tr class="even">
<td>Security Administrators</td>
<td><a href="cli-configzosmfcloudprovisioningsecurity.md">Configure z/OS Management Facility Cloud Provisioning Security</a></td>
<td><p>Describes how systems programmers perform the following <span>z/OSMF</span> cloud provisioning security configuration tasks:</p>
<ul>
<li>Configure z/OSMF Cloud Provisioning to Use RACF Security</li>
</ul></td>
</tr>
</tbody>
</table>

</div>

