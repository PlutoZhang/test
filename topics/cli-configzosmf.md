# Configure z/OS Management Facility

As a systems programmer, complete the following z/OSMF configuration
tasks for your Brightside CLI implementation:

  - [Obtain z/OSMF installation and configuration materials](#obtain-zosmf-installation-and-configuration-materials)
  - [Install and configure z/OSMF](cli-configzosmf.md#install-and-configure-zosmf)  
  - [Select and configure your z/OSMF plug-ins](#select-and-configure-your-zosmf-plug-ins)

**Important!** The [IBM z/OS Management
Facility](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izu/izu.htm)
guide on the IBM Knowledge Center is your primary source of information about how to install and configure z/OSMF. Throughout the IBM procedures, we provide Brightside CLI-specific tips or requirements. We recommend that you open IBM documentation in a separate browser tab.

## Obtain z/OSMF installation and configuration materials

Before you start the configuration process, we recommend that you
review [Overview of z/OSMF](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_OverviewMain.htm) on
the IBM Knowledge Center. You can use the [First-Time
Installation Checklist from
IBM](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_Checklist.htm) to
plan your installation and complete all the required
steps. 

## Install and configure z/OSMF

Brightside CLI was designed and tested to integrate with z/OS Management Facility (z/OSMF) running on IBM version 2.2 z/OS mainframe systems. To use Brightside CLI, ensure that your z/OS system meets the requirements that are described in the following table:

<div class="table-wrap">

<table>
<thead>
<tr class="header">
<th>Requirement</th>
<th>Description</th>
<th> </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span>AXR (System Rexx)</span></td>
<td><p>The AXR (System Rexx) component lets z/OS perform Incident Log tasks. It also lets REXX execs execute outside of conventional TSO and batch environments.</p>
<p>For more information, see <a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.ieag100/m3modaxr.htm" class="external-link">Communicating with System REXX</a> on the IBM Knowledge Center.</p></td>
<td> </td>
</tr>
<tr class="even">
<td>CEA (Communications Enabled Applications)  Server</td>
<td><div class="content-wrapper">
<p>CEA server is a co-requisite for the CIM server. The CEA server lets z/OSMF deliver z/OS events to C-language clients.</p>
<p>z/OSMF requires the CEA server to perform the following types of tasks:</p>
<ul>
<li>Problem determination</li>
<li>Sysplex</li>
<li><p>z/OS classic interfaces</p></li>
<li><p>z/OS Operator Console<br />
</p></li>
</ul>
</div>
<div class="confluence-information-macro confluence-information-macro-note">
<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
<p><strong>Notes:</strong></p>
<ul>
<li>Start the CEA server before you start the start z/OSMF (the <code>IZU*</code> started tasks).</li>
<li>Set up CEA server in <code>Full Function Mode</code> and assign the <code>TRUSTED</code> attribute to the CEA started task.</li>
</ul>
</div>
</div>
<p><span>For more information, see </span><a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.e0zb100/custcea.htm" class="external-link">Customizing for CEA</a><span> on the IBM Knowledge Center.</span></p></td>
<td> </td>
</tr>
<tr class="odd">
<td>CIM
<div class="WordSection1">
<p>(Common Information Model) </p>
</div>
Server</td>
<td><div class="content-wrapper">
<p>z/OSMF requires the CIM server to perform the following types of tasks:</p>
<ul>
<li>Capacity provisioning</li>
<li>Problem determination</li>
<li>Workload management</li>
</ul>
<div class="confluence-information-macro confluence-information-macro-note">
<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
<strong>Note:</strong> Start the CIM server before you start z/OSMF (the <code>IZU*</code> started tasks).
</div>
</div>
<p>For more information, see <a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_AdditionalCIMStepsForZOS.htm" class="external-link">Reviewing your CIM server setup</a> on the IBM Knowledge Center.</p>
</div></td>
<td> </td>
</tr>
<tr class="even">
<td>Console Command</td>
<td>The <code>CONSOLE</code> and <code>CONSPROF</code> commands must exist in the authorized command table.</td>
<td> </td>
</tr>
<tr class="odd">
<td>Java version</td>
<td><div class="content-wrapper">
<p>I<span style="color: rgb(0,0,0);">BM® 64-bit SDK for z/OS®, Java Technology Edition V7.1 or higher is required. </span>However, we experienced problems accessing z/OSMF 2.2 using Java version 8. If you use z/OSMF 2.3, Java version 8.0_64 is required.</p>
<div class="code panel caCodePanel">
<div class="codeContent panelContent">
<pre class="ca-code-default"><code>SYS1.PARMLIB member  IZUPRMxx.... JAVA_HOME(&#39;/sys/java64bt/v7r1m0/usr/lpp/java/J7.1_64&#39;
/etc/profile ............................................... export JAVA_HOME=/sys/java31bt/v7r1m0/usr/lpp/java/J7.1</code></pre>
</div>
</div>
For more information, see <a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_SoftwarePrereqs.htm" class="external-link">Software prerequisites for z/OSMF</a> on the IBM Knowledge Center.
</div></td>
<td> </td>
</tr>
<tr class="even">
<td>Maximum region size</td>
<td>To prevent exceeds maximum region size errors, ensure that you have a TSO maximum region size of at least 65536 KB for the z/OS system.</td>
<td> </td>
</tr>
<tr class="odd">
<td>User IDs</td>
<td><div class="content-wrapper">
<p>User IDs require a TSO segment (access) and an OMVS segment. During workflow processing and REST API requests, z/OSMF may start one or more TSO address spaces under the following job names:</p>
<ul>
<li><em>userid</em></li>
<li><p><em>substr(userid, 1, 6)||CN</em> (Console)</p>
<p><strong>Example:</strong></p>
<div class="code panel caCodePanel">
<div class="codeContent panelContent">
<pre class="ca-code-default"><code>(userid = USRMY01, USRMY0CN )</code></pre>
</div>
</div></li>
</ul>
</div></td>
<td> </td>
</tr>
</tbody>
</table>

</div>

## Select and configure your z/OSMF plug-ins

Brightside CLI requires that z/OS Management Facility (z/OSMF) is
installed with the following plug-ins:

<div class="table-wrap">

<table>
<thead>
<tr class="header">
<th>Plug-in</th>
<th>Functionality</th>
<th>Task</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Optional) Cloud Portal</td>
<td>The Cloud Portal plug-in lets you make software services available to marketplace consumers and it adds the Marketplace and Marketplace Administration tasks to the z/OSMF navigation tree.</td>
<td>For information about how to enable the plug-in, see <a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/izuconfig_CloudProvPortalSetup.htm" class="external-link">Updating z/OS for the Cloud Portal plug-in</a> on the IBM Knowledge Center. For supplemental information about enabling the plug-in, see <a href="433363264.html">Configure z/OS Cloud Provisioning</a>.</td>
</tr>
<tr class="even">
<td>Configuration Assistant</td>
<td><p><span style="color: rgb(0,0,0);">The Configuration Assistant plug-in lets z/OSMF configure TCP/IP policy-based networking functions.</span></p>
<p>For more information about the functionality that the plug-in provides, see <a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_OverviewConfigurationAssistant.htm" class="external-link">Configuration Assistant task overview </a>on the IBM Knowledge Center.</p></td>
<td>For information about how to enable the plug-in, see <a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_ConfigAssistSetup.htm" class="external-link">Updating z/OS for the Configuration Assistant plug-in</a> on the IBM Knowledge Center.</td>
</tr>
<tr class="odd">
<td>ISPF</td>
<td><p>The ISPF plug-in lets z/OSMF access traditional ISPF applications.</p>
<p>For information about the functionality that the plug-in provides, see <a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_OverviewISPF.htm" class="external-link">ISPF task overview</a> on the IBM Knowledge Center.</p></td>
<td>For information about how to enable the plug-in, see <a href="https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_ISPFPluginSetup.htm" class="external-link">Updating z/OS for the ISPF plug-in</a> on the IBM Knowledge Center.</td>
</tr>
<tr class="even">
<td>Workload Management</td>
<td><p>The Workload Management plug-in lets z/OSMF operate and manage workload management service definitions and policies.</p>
<p>For information about the functionality that the plug-in provides, see <a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_OverviewWorkloadManagement.htm" class="external-link">Workload Management task overview</a> on the IBM Knowledge Center.</p></td>
<td>For information about how to enable the plug-in, see <a href="https://www.ibm.com/support/knowledgecenter/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_AuthorizingUsersToWLM.htm" class="external-link">Updating z/OS for the Workload Management plug-in</a> on the IBM Knowledge Center.</td>
</tr>
</tbody>
</table>

</div>

 

For information about all available z/OSMF plug-ins, see [Selecting
which optional z/OSMF plug-ins to
add](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.2.0/com.ibm.zos.v2r2.izua300/IZUHPINFO_PluginsPlanning.htm) on
the IBM Knowledge Center.
