# Job APIs

Use Jobs APIs to view the information and files of jobs, and submit and cancel jobs. See the following table for the operations available in Job APIs and their descriptions and prerequisites.

| REST API | Description | Prerequisite |
| --- | --- | --- |
| `GET /Atlas/api/jobs` | Get a list of jobs. Use this API to get a list of job names that match a given prefix, owner, or both. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids` | Get a list of job identifiers for a given job name. If you have a list of existing job names, use this API to get a list of job instances for a given job name. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids/{jobId}/steps` | Get job steps for a given job. With a job name and job ID, use this API to get a list of the job steps, which includes the step name, the executed program, and the logical step number. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids/{jobId}/steps/{stepNumber}/dds` | Get dataset definitions \(DDs\) for a given job step. If you know a step number for a given job instance, use this API to get a list of the DDs for a given job step, which includes the DD name, the data sets that are described by the DD, the original DD JCL, and the logical order of the DD in the step. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids/{jobId}/files` | Get a list of output file names for a job. Job output files have associated DSIDs. Use this API to get a list of the DSIDs and DD name of a job. You can use the DSIDs and DD name to read specific job output files. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids/{jobId}/files/{fileId}` | Read content from a specific job output file. If you have a DSID or field for a given job, use this API to read the output file's content. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids/{jobId}/files/{fileId}/tail` | Read the tail of a job's output file. Use this API to request a specific number of records from the tail of a job output file. | z/OSMF restjobs |
| `GET /Atlas/api/jobs/{jobName}/ids/{jobId}/subsystem` | Get the subsystem type for a job. Use this API to determine the subsystem that is associated with a given job. The API examines the JCL of the job to determine if the executed program is CICS®, DB2®, IMS™, or IBM® MQ. | z/OSMF restjobs |
| `POST /Atlas/api/jobs` | Submit a job and get the job id back. Use this API to submit a partitioned data set member or UNIX™ file. | z/OSMF restjobs |
| `DELETE /Atlas/api/jobs/{jobName}/{jobId}` | Cancel a job and purge its associated files. Use this API to purge a submitted job and the logged output files that it creates to free up space. | z/OSMF Running Common Information Model \(CIM\) server |

**Parent topic:** [Using Atlas REST APIs](https://github.com/PlutoZhang/test/tree/549112db023388c89a9750459e98a7b204fad073/topics/usingatlasrestapis.md)

