# Prerequisites for Atlas

Before installing Atlas, check whether your environment meets the following requirements to ensure a successful installation.

* Atlas must be installed on z/OS® version 2.2 or later.
* Atlas requires a 64-bit Java™ 8 JRE or later.
* [IBM® z/OS Management Facility \(z/OSMF\)](https://www.ibm.com/support/knowledgecenter/en/SSLTBW_2.3.0/com.ibm.zos.v2r3.izu/izu.htm) must be installed and running. z/OSMF is a prerequisite for the Atlas microservice. For details, see [Prerequisites for z/OSMF configuration](https://github.com/PlutoZhang/test/tree/549112db023388c89a9750459e98a7b204fad073/topics/topics/prezosmf.md).
* \(Optional\) To enable real-time access to SYSLOG, SDSF must be installed.

## Pre-installation checklist

The following information is required during the installation process. Make the decisions before you install Atlas.

* The HFS directory where you install Atlas, for example, `/var/atlas`.
* The HFS directory path that contains a 64-bit Java™ 8 JRE.
* The z/OSMF installation directory `/lib` that contains `derby.jar`, for example, `/usr/lpp/zosmf/lib`.
* The z/OSMF configuration user directory path that contains z/OSMF `/bootstrap.properties`, `/jvm.security.override.properties`, and `/resources/security/ltpa.keys files`.
* The Atlas http and https port numbers. By default, they are 7080 and 7443.
* The user ID that runs the Liberty Atlas started task.

  **Tip:** Use the same user ID that runs the z/OSMF IZUSVR1 task, or a user ID with equivalent authorizations.

* \(Optional\) The SDSF java installation directory, for example, `/usr/lpp/sdsf/java`.

**Parent topic:** [Prerequisites](./)

