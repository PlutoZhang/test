# USS File APIs

Use USS File APIs to read and list UNIX Files. See the following table for the available operations and their descriptions and prerequisites.

|REST API|Description|Prerequisite|
|--------|-----------|-------------|
|`POST /Atlas/api/uss/files`|Use this API to create new USS directories and files.|z/OSMF restfiles|
|`DELETE /Atlas/api/uss/files{path}`|Use this API to delete USS directories and files.|z/OSMF resfiles|
|`GET /Atlas/api/files/{path}`|Use this API to get a list of files in a USS directory along with their attributes.|z/OSMF restfiles|
|`GET /Atlas/api/files/{path}/content`|Use this API to get the content of a USS file.|z/OSMF restfiles|
|`PUT /Atlas/api/files/{path}/content`|Use this API to update the content of a USS file.|z/OSMF resfiles|

**Parent topic:** [Using Atlas REST APIs](../topics/usingatlasrestapis.md)
