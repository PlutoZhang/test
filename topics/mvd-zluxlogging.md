# zLUX logging

By default, zLUX generates logs in the following locations:

- Giza Node server: `zlux-example-server/log/nodeServer.log`
- ZSS: `zlux-example-server /log/zssServer.log`
 

## Controlling the logging location

The server logs to a file and to the screen.

You can control the logging location through the environment variables ZLUX_NODE_LOG_DIR (the Giza Node server) and ZSS_LOG_DIR (ZSS). While these variables are intended to specify a directory, if you specify a location that is a file name, zLUX will write the logs to the specified file instead (for example: `/dev/null`). 


**NOTE**: If zLUX encounters a problem in creating the folder or file, the server runs (but it might not perform logging properly).
