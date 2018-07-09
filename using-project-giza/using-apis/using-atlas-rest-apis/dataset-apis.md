# Dataset APIs

Use Dataset APIs to create, read, update, delete, and list data sets. See the following table for the operations available in Dataset APIs and their descriptions and prerequisites.

| REST API | Description | Prerequisite |
| --- | --- | --- |
| `GET /Atlas/api/datasets/{filter}` | Get a list of data sets by filter. Use this API to get a starting list of data sets, for example, **userid.\*\***. | z/OSMF restfiles |
| `GET /Atlas/api/datasets/{dsn}/attributes` | Retrieve attributes of a data set\(s\). If you have a data set name, use this API to determine attributes for a data set name. For example, it is a partitioned data set. | z/OSMF restfiles |
| `GET /Atlas/api/datasets/{dsn}/members` | Get a list of members for a partitioned data set. Use this API to get a list of members of a partitioned data set. | z/OSMF restfiles |
| `GET /Atlas/api/datasets/{dsn}/content` | Read content from a data set or member. Use this API to read the content of a sequential data set or partitioned data set member. Or use this API to return a checksum that can be used on a subsequent `PUT` request to determine if a concurrent update has occurred. | z/OSMF restfiles |
| `PUT /Atlas/api/datasets/{dsn}/content` | Write content to a data set or member. Use this API to write content to a sequential data set or partitioned data set member. If a checksum is passed and it does not match the checksum that is returned by a previous `GET` request, a concurrent update has occurred and the write fails. | z/OSMF restfiles |
| `POST /Atlas/api/datasets/{dsn}` | Create a data set. Use this API to create a data set according to the attributes that are provided. The API uses z/OSMF to create the data set and uses the syntax and rules that are described in the _z/OSMF Programming Guide_. | z/OSMF restfiles |
| `POST /Atlas/api/datasets/{dsn}/{basedsn}` | Create a data set by using the attributes of a given base data set. When you do not know the attributes of a new data set, use this API to create a new data set by using the same attributes as an existing one. | z/OSMF |
| `DELETE /Atlas/api/datasets/{dsn}` | Delete a data set or member. Use this API to delete a sequential data set or partitioned data set member. | z/OSMF restfiles |

**Parent topic:** [Using Atlas REST APIs](https://github.com/PlutoZhang/test/tree/549112db023388c89a9750459e98a7b204fad073/topics/usingatlasrestapis.md)

