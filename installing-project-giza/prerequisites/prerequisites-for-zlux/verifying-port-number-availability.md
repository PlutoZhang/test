# Verifying port number availability

Before you begin your zLUX configuration, it is a good idea to verify the availability of the various port numbers the you will need to specify for zLUX communications.

zLUX requires you to configure these port numbers in the `zlux-example-server/config/zluxserver.json` configuration file:

* `zssPort`, which is the port through which the Giza Node server communicates with the zLUX Secure Services address space. By default, zLUX uses port 8542 for this purpose.
* An HTTP port for unencrypted access from the browser. By default, zLUX uses port 8543 for this purpose.
* An HTTPS port for encrypted access from the browser. By default, zLUX uses port 8544 for this purpose.
* Determine which port numbers are in use and which are reserved: 1. Run TSO NETSTAT PORTLIST to display a list of reserved ports. 2. Run TSO NETSTAT to display a list of ports that are in use.
* For the `zssPort`, HTTP and HTTPS ports, select port numbers that are not reserved or already in use. You will need to specify the selected port numbers to complete the procedure in [Setting up the Giza Node server and the zLUX Secure Services address space on z/OS](../../installing-components-of-project-giza/installing-zlux/setting-up-the-giza-node-server-and-the-zssas-on-z-os.md) topic. 

After you have verified the availability of the port numbers that you will need to complete your Giza Node server and zLUX Secure Services address space set up, you can go on to [Setting up the Giza Node server and the zLUX Secure Services address space on z/OS](../../installing-components-of-project-giza/installing-zlux/setting-up-the-giza-node-server-and-the-zssas-on-z-os.md).

