# Persistent Data APIs

Use Persistent Data APIs to create, read, update, delete metadata from persistent repository. See the following table for the operations available in Persistent Data APIs and their descriptions and prerequisites.

| REST API | Description | Prerequisite |
| --- | --- | --- |
| `PUT /Atlas/api/data` | Update metadata in persistent repository for a given resource and attribute name. With Atlas, you can store and retrieve persistent data by user, resource name, and attribute. A resource can have any number of attributes and associated values. Use this API to set a value for a single attribute of a resource. You can specify the resource and attribute names. | None |
| `POST /Atlas/api/data` | Create metadata in persistent repository for one or more resource/attribute elements. Use this API to set a group of resource or attributes values. | None |
| `GET /Atlas/api/data` | Retrieve metadata from persistent repository for a given resource \(and optional attribute\) name. Use this API to get all the attribute values or any particular attribute value for a given resource. | None |
| `DELETE /Atlas/api/data` | Remove metadata from persistent repository for a resource \(and optional attribute\) name. Use this API to delete all the attribute values or any particular attribute value for a given resource. | None |

**Parent topic:** [Using Atlas REST APIs](https://github.com/PlutoZhang/test/tree/549112db023388c89a9750459e98a7b204fad073/topics/usingatlasrestapis.md)

