# Reindexing a PostgreSQL Database

Reindexing a database can solve the world's problems


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