# Kubernetes Clusters - Delete Object
:::enterprise
:::

## Overview

This plugin deletes an object of a selected kind within a Kubernetes cluster. Since this is a node-step plugin, multiple Kubernetes clusters or namespaces can be targeted within a single Job.

The types of objects that can be deleted within a Kubernetes cluster include:

- **ConfigMaps**
- **DaemonSets**
- **Deployments**
- **Jobs**
- **Namespaces**
- **PersistentVolumes**
- **Pods**
- **ReplicaSets**
- **Secrets**
- **Services**
- **StatefulSets**

## Configuration

### Prerequisites

Before configuring the Kubernetes Delete Object plugin, the target clusters must be added to the Runbook Automation instance and the authentication method must be configured. This is done by following the steps outlined in the [Kubernetes Plugins Overview](/manual/plugins/kubernetes-plugins-overview.md).

### Add Kubernetes Delete Object Step

When building a Job, add the **Kubernetes / Clusters / Delete Object** node step:

![Kubernetes Delete Object](/assets/img/k8s-clusters-delete-object.png)<br>

Configure the following fields:

* **Object Type**: Select the type of object to delete (e.g., Pods, ConfigMaps, Deployments).
* **Name**: The name of the object to be deleted, such as Pod name or Deployment name.
* **Namespace**: The namespace where the object resides.
* **Output Format**: Choose the format for the output (JSON or YAML).

### Invocation Output

The output of the step will be the object that was deleted in the Kubernetes cluster. The output format will be the same as the format selected in the step configuration:

![Kubernetes Delete Object Output](/assets/img/k8s-delete-object-output.png)<br>

