# Kubernetes Plugins

## Overview

![](/assets/img/kubernetes-icon.png)

Runbook Automation integrates with Kubernetes through a variety of plugins. By integrating Runbook Automation with Kubernetes, users can automate and provide self-service interfaces for operations in their Kubernetes Clusters.

There are two suites of Kubernetes plugins:

1. [**Kubernetes Plugins in Runbook Automation**](#kubernetes-plugins-in-runbook-automation) (**Commercial Only Products**): These plugins are only available in Runbook Automation and are suited for environments with multiple Kubernetes clusters. This suite also includes native integrations with AWS Elastic Kubernetes Service (EKS), Azure Kubernetes Service (AKS), and Google Kubernetes Engine.
2. [**Open Source Kubernetes Plugins**](#open-source-kubernetes-plugins): These plugins are available in Rundeck Open Source and provide basic functionality for interacting with Kubernetes clusters.

## Kubernetes Plugins in Runbook Automation

:::enterprise
:::

### Configuration
There are two methods for adding Kubernetes clusters to Runbook Automation and authenticating with the Kubernetes API:

1. **Pod-based Service Account**
2. **Cloud Provider Integration**

#### Pod-based Service Account

With this method, clusters are added to the inventory by installing a Runner in the cluster and adding the Runner as a node to the inventory. The Runner uses the Service Account of the pod that it is hosted in to authenticate with the Kubernetes API.




## Open Source Kubernetes Plugins
<details><summary> <font size="5">List of Open Source Plugins</font>
</summary>

**Available in Rundeck Open Source**

|Plugin Name| Plugin Type| Description|
|:---------------------------------------------------------|:---------------------------------------------------------:|:---------------------------------------------------------|
|[**Create Deployment**](/manual/jobs/job-plugins/node-steps/kubernetes-deployment-plugins.md#kubernetes-deployment-create)|Node Step|Create a new deployment.|
|[**Delete Deployment**](/manual/jobs/job-plugins/node-steps/kubernetes-deployment-plugins.md#kubernetes-deployment-delete)|Node Step|Delete an existing deployment.|
|[**Deployment Status**](/manual/jobs/job-plugins/node-steps/kubernetes-deployment-plugins.md#kubernetes-deployment-status)|Node Step|Get the status of an existing deployment.|
|[**Update Deployment**](/manual/jobs/job-plugins/node-steps/kubernetes-deployment-plugins.md#kubernetes-deployment-update)|Node Step|Update an existing deployment.|
|[**Waitfor Deployment**](/manual/jobs/job-plugins/node-steps/kubernetes-deployment-plugins.md#kubernetes-deployment-waitfor)|Node Step|Pause workflow until deployment is complete.|
|[**Create Job**](/manual/jobs/job-plugins/node-steps/kubernetes-job-plugins.md#kubernetes-job-create)|Node Step|Create a new Kubernetes job.|
|[**Delete Job**](/manual/jobs/job-plugins/node-steps/kubernetes-job-plugins.md#kubernetes-job-delete)|Node Step|Delete an existing Kubernetes job.|
|[**Re-run Job**](/manual/jobs/job-plugins/node-steps/kubernetes-job-plugins.md#kubernetes-job-re-run)|Node Step|Re-runs an existing Kubernetes job.|
|[**Waitfor Job**](/manual/jobs/job-plugins/node-steps/kubernetes-job-plugins.md#kubernetes-job-waitfor)|Node Step|Pause workflow until Kubernetes job is complete.|
|[**Create Service**](/manual/jobs/job-plugins/node-steps/kubernetes-service-plugins.md#kubernetes-service-create)|Node Step|Create a new Kubernetes service.|
|[**Update Service**](/manual/jobs/job-plugins/node-steps/kubernetes-service-plugins.md#kubernetes-service-update)|Node Step|Update an existing Kubernetes service.|
|[**Delete Service**](/manual/jobs/job-plugins/node-steps/kubernetes-service-plugins.md#kubernetes-service-delete)|Node Step|Delete an existing Kubernetes service.|
|[**Pods Node Source**](/manual/projects/resource-model-sources/kubernetes.md)|Resource Model|Populates node inventory with Kubernetes pods.|
|[**Create Pod**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-create)|Node Step|Create a new Kubernetes pod.|
|[**Delete Pod**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-delete)|Node Step|Delete an existing Kubernetes pod.|
|[**Describe Pod**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-describe)|Node Step|Describe a running Kubernetes pod.|
|[**Execute Command**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-execute-command)|Node Step|Execute a command inside a container in a running pod.|
|[**Execute Script**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-execute-script)|Node Step|Execute a script inside a container in a running pod.|
|[**Pod Logs**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-logs)|Node Step|View the logs of a running pod.|
|[**Waitfor Pod**](/manual/jobs/job-plugins/node-steps/kubernetes-pod-plugins.md#kubernetes-pod-waitfor)|Node Step|Pause workflow until pod is in "ready" state.|
|[**Debug Pod**](/manual/jobs/job-plugins/node-steps/kubernetes-debug-plugins.md#kubernetes-debug-ephemeral-container)|Node Step|Debug a running container inside an existing pod using an ephemeral container.|
|[**Waitfor StatefulSet**](/manual/jobs/job-plugins/node-steps/kubernetes-statefulset-plugins.md#kubernetes-statefulset-waitfor)|Node Step|Pause workflow until StatefulSet has been successfully deployed.|

**Plugins available only in Commercial products**
> Note: All Open Source plugins also included.

|Plugin Name| Plugin Type| Description|
|:---------------------------------------------------------|:---------------------------------------------------------:|:---------------------------------------------------------|
|[**Amazon EKS Node Source**](/manual/projects/resource-model-sources/aws-eks.md)|Node Source|Imports Amazon Web Services EKS Clusters as Nodes.|
|[**Azure AKS Node Source**](/manual/projects/resource-model-sources/azure-aks.md)|Node Source|Imports Azure AKS Clusters as Nodes.|
|[**Google Cloud GKE Node Source**](/manual/projects/resource-model-sources/gcp-gke.md)|Node Source|Imports Google Cloud GKE Clusters as Nodes.|
|[**Kubernetes Cluster Create Object**](/manual/jobs/job-plugins/node-steps/kubernetes-create-object)|Node Step|This plugin creates an object of a selected kind within a Kubernetes cluster.|
|[**Kubernetes Cluster Delete Object**](/manual/jobs/job-plugins/node-steps/kubernetes-delete-object)|Node Step|This plugin deletes an object of a selected kind within a Kubernetes cluster.|
|[**Kubernetes Cluster Describe Object**](/manual/jobs/job-plugins/node-steps/kubernetes-describe-object)|Node Step|This plugin describes an object of a selected kind within a Kubernetes cluster.|
|[**Kubernetes Cluster List Objects**](/manual/jobs/job-plugins/node-steps/kubernetes-list-objects)|Node Step|This plugin lists objects of a selected kind within a Kubernetes cluster.|
|[**Kubernetes Cluster Object Logs**](/manual/jobs/job-plugins/node-steps/kubernetes-object-logs)|This plugin allows you to view the logs of an object within a Kubernetes cluster.|
|[**Kubernetes Cluster Run Command**](/manual/jobs/job-plugins/node-steps/kubernetes-run-command)|Node Step|This plugin allows you to execute a command in a pod within a Kubernetes cluster.|
|[**Kubernetes Cluster Run Script**](/manual/jobs/job-plugins/node-steps/kubernetes-run-script)|Node Step|This plugin executes a script using a predefined container image within a Kubernetes cluster.|
|[**Kubernetes Cluster Update Object**](/manual/jobs/job-plugins/node-steps/kubernetes-update-object)|Node Step|This plugin updates a specified object of a selected kind within a Kubernetes cluster.|


</details>
<br>

:::tip
Click above see the full list of plugins for Kubernetes.
:::

### Set up the Open Source Kubernetes Plugins

#### Python Dependencies

In order to use the Open Source Kubernetes plugins listed in the Summary above, Python must be installed on the Runbook Automation cluster-members or on the [Enterprise Runner](/administration/runner/index.md) - depending on where the connection to Kubernetes will originate.  _(These steps are also needed for Commercial versions using the listed Open Source plugins.)_

The plugins will work with both **Python 2.7.x** and **Python 3.x.x**.

Once python is installed, download and install the **`kubernetes`** python client.  For **Python 2.7.x** this can be done with **`pip install kubernetes`** and for **Python 3.x.x** this can be done with **`pip3 install kubernetes`**.

Optionally test that the Kubernetes client has been installed successfully by executing the following at the command-line: **`python`** followed by **`from kubernetes import client, config`**:

```
ubuntu@ip-172-31-13-91:~$ python
Python 2.7.17 (default, Mar  8 2023, 18:40:28) 
[GCC 7.5.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from kubernetes import client, config
>>>
```

#### Kubernetes Authentication for Open Source Plugins

By default, the Kubernetes plugins look for a Kube Config file at **`$RDECK_BASE/.kube/config`**.  For **Deb** and **RPM** this would translate to **`/var/lib/rundeck/.kube/config`**.
The Kube Config file can be saved to a different location, just be sure to take note of where it is saved for later steps.

If it is preferred to use a Kubernetes API Token, then follow the instructions outlined [here](https://www.cncf.io/blog/2020/07/31/kubernetes-rbac-101-authentication/) to generate the Service Account Token.
Once created, save the Token to [Key Storage](/manual/system-configs.md#key-storage) as a **Password** secret type.

#### Upload Kubernetes Plugins (Rundeck OSS Only)

Rundeck OSS does not come preloaded with the Kubernetes plugins. To install the Kubernetes plugins, use the following steps:

1. Navigate to the [latest plugin release](https://github.com/rundeck-plugins/kubernetes/releases/latest) on Github and download the **`kubernetes-X.X.XX.zip`** file.<br><br>
2. In Rundeck, click the **Gear Icon** and then click the **Plugins > Upload Plugin**:
   ![Upload Plugins Menu](/assets/img/upload-plugins-menu.png)
3. Click **Browse** and select the downloaded **`.zip`** file from Step 2.
4. Click **Install**:
   ![Upload Kubernetes Plugins](/assets/img/upload-k8s-plugins.png)

### Test Open Source Kubernetes Plugins

To test that the dependencies and authentication have been configured correctly, use a Kubernetes Node Step plugin - as this will provide the option to easily
execute the plugin in _debug_ mode.

1. Create a new Job.
2. Navigate to the **Workflow** tab.
3. Click **+ Add a step**.
4. In the **Search step** field type **`Kubernetes`**.
5. Select the **Kubernetes / Pod / Describe** plugin from the list.
6. Type in a pod name into the **Name** field.
![K8s Describe Pod](/assets/img/k8s-describe-pod.png)
7. Type in the namespace of the pod in the **Namespace** field.
8. If the Kube Config file is saved in the directory **`$RDECK_BASE/.kube/config`** (`/var/lib/rundeck/.kube/config`for RPM and Deb), then the authentication fields can be left blank.
   * Otherwise, specify the custom Kube Config location.
9. Optionally chance the **Python Interpreter** if python scripts are not invoked using `python my_script.py` but rather `python2 my_script.py` or `python3 my_script.py`.
10. Click **Save** on the Job Step and then **Save** to save the Job.
11. Click **Run Job Now** to test that the configuration is correct.

Now that configuration is complete, take a look at use-cases for Runbook Automation with Kubernetes such as 
[Capturing Debug Data from Apps in Kubernetes](/learning/solutions/automated-diagnostics/examples/k8s-app-debug-capture) 
or [Managing Kubernetes with Rundeck](/learning/howto/how2kube.md#managing-kubernetes-with-rundeck).







