# Sending a `POST` request in JavaScript

Here is sample code written in JavaScript™ using features from ES6 to send a `POST` request to Atlas.

```
// Call the jobs POST api to submit a job from a dataset (ATLAS.TEST.JCL(TSTJ0001))                
function submitJob(){
    let payload = "{\"file\":\"'ATLAS.TEST.JCL(TSTJ0001)'\"}";
    let contentURL = `${BASE_URL}/jobs`;
    let result = fetch(contentURL,
                    {
                        credentials: "include",
                        method: "POST",
                        body:   payload
                    })
                        .then(response => response.json())
                            .catch((e) => {
                                //handle any error
                                console.log("An error occoured: " + e);
                        });
    return result;
}
```

**Parent topic:** [Programming Atlas REST APIs](../topics/programrestapi.md)
