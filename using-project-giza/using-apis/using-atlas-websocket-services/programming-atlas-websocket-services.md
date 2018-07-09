# Programming Atlas WebSocket services

Here is code sample written in JavaScript™ using features from ES6 to establish a new WebSocket connection to listen to the syslog output.

```text
const BASE_WS_URL = 'hostname.com:port/Atlas/api/sockets';

// Establish a new WebSocket connection to listen to the syslog output
function initWebsocket(){
    const syslogURI = `${BASE_WS_URL}/syslog`;

    this.websocket = new WebSocket(syslogURI);
    this.websocket.onopen = function() {
        //handle socket opening
        console.log("Websocket connection opened");
    }
    this.websocket.onmessage = function(event) {
        //handle receiving of new data
        console.log(event.data);
    }
    this.websocket.onclose = function() {
        //handle socket closing
        console.log("Websocket connection closed");
    }
}
```

**Parent topic:** [Using Atlas WebSocket services](./)

