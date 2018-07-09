# Using Atlas WebSocket services

Atlas provides WebSocket services that can be accessed by using the WSS scheme. With Atlas WebSocket services, you can view the system log in the System log UI that is refreshed automatically when messages are written. You can also open a JES spool file for an active job and view its contents that refresh through a web socket.

| Server Endpoint | Description | Prerequisites |
| --- | --- | --- |
| `/api/sockets/syslog` | Get current syslog content. Use this WSS endpoint to read the system log in real time. | SDSF |
| `/api/sockets/jobs/{jobname}/ids/{jobid}/files/{fileid}` | Tail the output of an active job. Use this WSS endpoint to read the tail of an active job's output file in real time. | z/OSMF restjobs |

