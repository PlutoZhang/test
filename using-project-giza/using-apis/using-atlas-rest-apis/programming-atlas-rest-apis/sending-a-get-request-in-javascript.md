# Sending a GET request in JavaScript

Here is sample code written in JavaScript™ using features from ES6 to send a `GET`request to Atlas.

```text
const BASE_URL = 'hostname.com:port/Atlas/api';

// Call the jobs GET api to get all jobs with the userID IBMUSER
function getJobs(){
    let parameters = "prefix=*&owner=IBMUSER";     
    let contentURL = `${BASE_URL}/jobs?${parameters}`;     
    let result = fetch(contentURL, {credentials: "include"})
                    .then(response => response.json())
                        .catch((e) => {                             
                            //handle any error                             
                            console.log("An error occoured: " + e);      
                        });     
     return result;
}
```

**Parent topic:** [Programming Atlas REST APIs](https://github.com/PlutoZhang/test/tree/549112db023388c89a9750459e98a7b204fad073/topics/programrestapi.md)

