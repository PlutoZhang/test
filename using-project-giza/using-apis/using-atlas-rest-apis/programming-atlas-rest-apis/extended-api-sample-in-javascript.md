# Extended API sample in JavaScript

Here is an extended API sample that is written using JavaScript™ with features from ES62015 \(map\).

```text
/////////////////////////////////////////////////////////////////////////////
// Extended API Sample 
// This Sample is written using Javascript with features from ES62015 (map).
// The sample is also written using JSX giving the ability to return HTML elements 
// with javascript variables embedded. This sample is based upon the codebase of the 
// sample UI (see- hostname:port/ui) which is written using Facebook's React, Redux,
// Router and Google's material-ui
/////////////////////////////////////////////////////////////////////////////

// Return a table with rows detailing the name and jobID of all jobs matching      
// the specified parameters
function displayJobNamesTable(){
    let jobsJSON = getJobs("*","IBMUSER");
    return  (<table>
                {jobsJSON.map(job => {
                    return <tr><td>{job.name}</td><td>{job.id}</td></tr>
                })}
            </table>);
}

// Call the jobs GET api to get all jobs with the userID IBMUSER
function getJobs(owner, prefix){
    const BASE_URL = 'hostname.com:port/Atlas/api';
    let parameters = "prefix=" + prefix + "&owner=" + owner;     
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

