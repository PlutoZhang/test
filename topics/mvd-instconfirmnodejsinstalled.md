# Confirming that Node.js is installed

Node.js version 6.11.2 or later must be present on the z/OS host where you intend to install the Giza Node server.

1.   If Node.js has not yet been installed on the z/OS host, follow the procedure for doing so: [https://developer.ibm.com/node/sdk/ztp](https://developer.ibm.com/node/sdk/ztp). 
2.   Set the `NODE_HOME` environment variable to the directory where your Node.js is installed \(`NODE\_HOME=/proj/mvd/node/installs/node-v6.10.3-os390-s390x`, for example\). 

After you have confirmed that Node.js is installed and the `NODE_HOME` environment variable has been set appropriately, you can verify that the necessary port numbers are available. Go on to [Verifying port number availability](mvd-instverifyportnumavailable.md).
