# Verifying that your system meets the software requirements

Your system must meet the software requirements for zLUX.

1. Confirm that your environment meets the requirements for zLUX:
   * z/OS Version 2.2 or later.
   * Whatever maintenance is required by the Node.js and Java installations.
   * 833 MB of HFS file space for the installation.
   * To verify that the most recent version of Java Version 8 is installed on z/OS, type **java -version**.
   * Confirm that the machine from which you plan to run zLUX runs one of the following supported browsers:

     * Chrome version 54 or later
     * Firefox version 44 or later
     * Safari version 11 or later
     * Microsoft Edge

     **Note:** Microsoft Internet Explorer is not yet supported at any version level.
2. When building zLUX applications, npm is used. The version of npm needed for the build to succeed should be at least 5.4. You can update npm by executing the `npm install -g npm` command.
3. If your environment does not meet these requirements, consult your system administrator. 

When you have confirmed that your environment meets the software requirements, go on to [Confirming that Node.js is installed](confirming-that-node.js-is-installed-on-the-z-os-host.md).

