# Setting environment variables for plug-in development

The UNIX environment variables must be set appropriately before you can use the zLUX build procedures to develop your own plug-ins.

To set up the environment, the node must be accessible on the PATH.

1. To determine if the node is on the PATH, type "node --version" on the command line. If data is returned, the node is already on the PATH and no action is required.  
2. If nothing is returned from the command, you can set the PATH using the `NODE_HOME` variable. The `NODE_HOME` variable must be set to the directory of the node install. \(You can use the export command to set the directory. For example: export `NODE_HOME`=node\_installation\_directory\) Using this directory, the node will be included on the PATH in `nodeServer.sh`. \(`nodeServer.sh` is located in `zlux-example-server/bin`\). 

**Parent topic:** [Creating an application plug-in](./)

