# Store and Validate JSON (Commercial)

## Log Filter Store and Validate JSON

The "Store and Validate JSON" Log filter plugin validate and store a JSON string in the job context. 
It can be used to pass the input JSON parameter to the [Loop / Step / Run Script from a JSON Array](/manual/jobs/job-plugins/workflow-steps/loop-plugins.md) and [Loop / Node Step / Run Script from a JSON Array](/manual/jobs/job-plugins/node-steps/loop-plugins.md) plugins

### Plugin Configuration

* **_Group_** The group of the context variable
* **_Path_** The path of the context variable
* **_Log Data_** Print the captured value

you will access the context variable using `${group.path}`

![plugin-config](/assets/img/loop-log-filter.png)
