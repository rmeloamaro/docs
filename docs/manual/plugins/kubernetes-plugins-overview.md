# Kubernetes Plugins
:::enterprise
:::
![](/assets/img/kubernetes-icon.png)

Runbook Automation integrates with Kubernetes through a variety of plugins. By integrating Runbook Automation with Kubernetes, users can automate and provide self-service interfaces for operations in their Kubernetes Clusters.

:::warning Open Source Plugins
This document covers the plugins available in the commercial Runbook Automation products.  For a list of Kubernetes plugins available for Rundeck Community (open-source), see documentation for the [**Open Source Kubernetes plugins**](/manual/plugins/kubernetes-open-source.md).
:::

## Kubernetes Plugins in Runbook Automation

### Configuration
There are multiple methods for adding Kubernetes clusters to Runbook Automation and authenticating with the Kubernetes API:

1. [**Pod-based Service Account**](#pod-based-service-account): Install a Runner in each cluster (or namespace), and target the Runner as the cluster or particular namespace. The Runner uses the Service Account of the pod that it is hosted in to authenticate with the Kubernetes API.
2. [**Cloud Provider Integration**](#cloud-provider-integration): Use the cloud provider's API to dynamically retrieve all clusters and add them as nodes to the inventory. The cloud provider's API can also optionally be used to retrieve the necessary Kubernetes authentication to communicate with the clusters.
3. [**Manual Authentication Configuration**](#manual-authentication-configuration): Clusters are added to the inventory either manually or through method 1 or 2. The Kubernetes API Token or Kube Config file is manually added to Key Storage and configured as node-attributes.

:::tip Prerequisite Configuration
Note that all of these methods require the use of the **Automatic** mode for the Project's use of Runners. See [this documentation](/administration/runner/runner-management/project-dispatch-configuration.md) to confirm that your project is configured correctly.
:::

### Pod-based Service Account

With this method, clusters are added to the inventory by installing a Runner in the cluster and adding the Runner as a node to the inventory. The Runner uses the Service Account of the pod that it is hosted in to authenticate with the Kubernetes API.

This method is recommended if you want to have a 1:1 relationship between Runners and Kubernetes clusters or between Runners and namespaces within clusters, or if you are unable to use the Cloud Provider Integration method outlined in the next section.

Follow these steps to set up a Runner in a Kubernetes cluster:

1. Create a new Runner within your Project using the API. Replace **`URL`** with your Runbook Automation instance URL, **`PROJECT`** with the project name, and **`API_TOKEN`** with your API Token:
   ```bash
   curl --location --request POST 'https://[URL]/api/42/project/[PROJECT]/runnerManagement/runners' \
   --header 'Accept: application/json' \
   --header 'X-Rundeck-Auth-Token: [API_TOKEN]' \
   --header 'Content-Type: application/json' \
   --data-raw '{
      "name": "K8s Runner US-WEST-1 Cluster 1",
      "description": "Runner installed in US-WEST-1 Cluster 1",
      "tagNames": ["K8S-RUNNER", "us-west-1", "cluster-1"]
     }'
      ```
   :::tip Tip
      It is recommended to add at least one **Tag** through the `tagNames` field to the Runner, as this simplifies adding the Node Enhancer in step 4.
   :::
   The response will provide the following. Be sure to capture the **`runnerId`** and the **`token`**:
   ```
   {"description":"Runner installed in US-WEST-1 Cluster 1",
   "downloadTk":"fbc12393-3454-426d-9dd0-6e72ce53b9d5",
   "name":"K8s Runner","projectAssociations":{"network-infra":".*"},
   "runnerId":"acc00df8-fbb8-497a-8f7f-07eaaa0c5b78","token":"6Y4bHjk4TCU1MUGBaso9Ak7sHOokwRkw"}
   ```
2. Create a deployment YAML for the Runner. Be sure to replace **`[namespace]`**, **`[runnerId]`** with the value from the previous step, **`[token]`**, and **`[Runbook Automation Instance URL]`**:
   ```
   apiVersion: v1
   kind: Pod
   metadata:
     namespace: [namespace]
     name: rundeck-runner
     labels:
       app: rundeck-runner
   spec:
     containers:
     - image: rundeckpro/runner
       imagePullPolicy: IfNotPresent
       name: rundeck-runner
       env:
       - name: RUNNER_RUNDECK_CLIENT_ID
         value: "[runnerId]"
       - name: RUNNER_RUNDECK_SERVER_TOKEN
         value: "[token]"
       - name: RUNNER_RUNDECK_SERVER_URL
         value: "https://[Runbook Automation Instance URL]"
       lifecycle:
         postStart:
           exec:
             command:
             - /bin/sh
             - -c
             - touch this_is_from_rundeck_runner
     restartPolicy: Always
   ```
3. Create the deployment: **`kubectl apply -f deployment.yml`**.
4. Add a Node Attribute to the Runner's node in the inventory through an  [**Attribute Match Node Enhancer**](/manual/node-enhancers.md#attribute-match).
   - Set the **Attribute Match** to use one of the tags set in **Step 1**: **`tags=~.*K8S-RUNNER.*`**
   - Set the **Attributes to Add** as: **`kubernetes-use-pod-service-account=true`**
   :::tip Tip
   This step is only required one time if you use the same tag for all Runners that are deployed into Kubernetes clusters and use the Pod-based Service Account method.
   :::

The Runner will now be able to authenticate with the Kubernetes API using the Service Account of the pod that it is hosted in. 

### Cloud Provider Integration

The Cloud Provider Integration method can be used to dynamically retrieve all clusters from the cloud provider's API and add them as nodes to the inventory. 
The cloud provider's API can _also_ be used to retrieve the necessary Kubernetes authentication to communicate with the clusters.

#### Cloud Provider for Cluster Discovery

Use the Node Source plugins for the cloud provider to add the clusters to the Node Inventory:

- [**Amazon EKS Node Source**](/manual/projects/resource-model-sources/aws-eks.md)
- [**Azure AKS Node Source**](/manual/projects/resource-model-sources/azure-aks.md)
- [**Google Cloud GKE Node Source**](/manual/projects/resource-model-sources/gcp-gke.md)

Note that a Runner does _not_ need to be installed to configure these Node Source plugins.

#### Cloud Provider for Kubernetes Authentication

The Cloud Provider Integration method can also be used to retrieve the necessary Kubernetes authentication to communicate with the clusters.
This is useful when there are multiple clusters and you wish to have a single Runner that can communicate with all of them.

Follow the instructions in the **Node Source Plugins** linked in the prior sections to use the Cloud Provider Integration method.

:::tip Cloud Provider for Discovery and Pod Service Account for Authentication
It is possible to use the Cloud Provider Integration method for cluster discovery and the Pod-based Service Account method for authentication. This is useful when you want to dynamically discover clusters but have a 1:1 relationship between Runners and clusters or do not have the option to use the cloud provider for retrieving cluster credentials.
To take this approach, be sure to select the **Use Pod Service Account for Node Steps** when configuring the Node Source plugins.
:::

### Manual Authentication Configuration

If you do not have the option to place the Runner inside the target cluster or use the Cloud Provider Integration method, you can manually configure the Kubernetes authentication.

1. Create an API token for a service account following the steps outlined [here](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#manually-create-a-long-lived-api-token-for-a-serviceaccount).
2. Retrieve the `token` and the `ca.crt` from the secret created in the previous step: **`kubectl get secret/[secret-name] -o yaml`**.
3. Add both the `token` and the `ca.crt` to Key Storage.
4. Next, retrieve the cluster's API endpoint.  This can be found by running **`kubectl cluster-info`**.
5. Add a node to the inventory and add the following as node attributes:
   ```
   kubernetes-cloud-provider=self-hosted
   kubernetes-cluster-endpoint=<<cluster endpoint>>
   kubernetes-token-path=<<path to token in key storage>>
   kubernetes-ca-cert-path=<<path to CA cert in key storage>>
   ```

This node can now be targeted by the Kubernetes node-step plugins.