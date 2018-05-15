# Setting up the Giza Node server and the zLUX Secure Services address space on z/OS

Setting up the Giza Node server and the zLUX Secure Services address space on z/OS is a multi-step installation and configuration process.

The zLUX archive is distributed as a pax archive. When you unpack the archive, both the Giza Node server and the zLUX Secure Services \(ZSS\) are installed on the z/OS host.

1.   If you have not already done so, follow the procedures in these prerequisite sections: 
    -   [Verifying that your system meets the software requirements](mvd-verifysystemswreqs.md)
    -   [Confirming that Node.js is installed](mvd-instconfirmnodejsinstalled.md)
    -   [Verifying port number availability](mvd-instverifyportnumavailable.md)
 
2. To obtain the installation media, follow the instructions in [Obtain the Project Giza installation media](installing.md).
3. Navigate to the `scripts/zlux` subdirectory of the Project Giza contents directory (where you unpacked the Project Giza pax file) and run `zlux-install-script.sh`
5.   Upon startup, the Giza Node server loads the `zluxserver.json` configuration file \(from `zlux-example-server/deploy/instance/ZLUX/serverConfig/zluxserver.json\`). The JSON configuration file adheres to a specific structure, as shown in the following figure:

    ```
      "node": {
        "http": {
          "port": 8543
        },
        "https": {
          "port": 8544,
          //pfx (string), keys, certificates, certificateAuthorities, and 
    certificateRevocationLists are all valid here.
          "keys": ["../deploy/product/ZLUX/serverConfig/server.key"],
          "certificates": ["../deploy/product/ZLUX/serverConfig/server.cert"]
          }
        },
        "childProcesses": [
          {
            "path": "../bin/zssServer.sh"
          }
        ]
      },
    ```

 Note the following about specifying values in the JSON configuration file:

 -   **Port field for the http field of the node object**

     Required if you intend to access the zLUX Secure Services address space through unencrypted HTTP. Specify a port number that is available on your system.

 -   **Port field for the https field of the node object**

     Required if you intend to access the zLUX Secure Services address space through encrypted HTTPS. Specify a port number that is available on your system. Requires `keys` and `certificates`

     **Note:** Currently, the zLUX Secure Services address space configuration JSON file at `zlux-example-server/config/zluxserver.json` contains an example node configuration, so you can refer to one file for both the zLUX Secure Services address space and the Giza Node server.
     

To update the server configuration, run `zlux-example-server/build/deploy.sh`


     
Go on to [Starting the zLUX server](mvd-startzluxserver.md).
