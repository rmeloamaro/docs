# Reindexing a PostgreSQL Database

Reindexing a PostgreSQL database is often necessary to maintain optimal performance and data integrity. Over time, as data is inserted, updated, and deleted, indexes can become fragmented or bloated, leading to decreased query performance and increased storage usage. Reindexing rebuilds these indexes, reorganizing the data structures to improve efficiency. This process can be particularly important after large bulk operations, significant data changes, or when upgrading to a new PostgreSQL version. Additionally, reindexing can help recover from index corruption, which may occur due to hardware failures or software bugs. By periodically reindexing, database administrators ensure that queries continue to execute quickly and that the database maintains its overall health and performance.


## Pre-requisites & Environment Setup

- Environment setup with Enterprise Runner active.
- The `psql` command must be installed on the same machine as the Enterprise Runner and be available in the default path.
- The Enterprise Runner must have access to an existing PostgreSQL instance.

## Notes
Note: The verbose output text of the index command will be shown in red, but it does not represent a failure if the step ends in `REINDEX` or no error messages are presented.

**Database Host Name**: The host name or IP address of the PostgreSQL server.

**Database Name**: The name of the database to reindex.

**Database User Name**: The login name to authenticate to the PostgreSQL server.

**Login Password**: The password for the login name.  >(Note: The password can be provided directly as part of the input options. For production use we recommend using a Key Storage entry.)

![job-options](/assets/img/solution-postgres-reindex-joboptions.png)<br>


## Successful Execution

![success-output](/assets/img/solutions-postgres-reindex-success.png)<br>