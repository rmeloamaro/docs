# Kubernetes Clusters - Update Object
:::enterprise
:::

## Overview

This plugin updates a specified object of a selected kind within a Kubernetes cluster. Since this is a node-step plugin, multiple Kubernetes clusters or namespaces can be targeted within a single Job.

## Configuration

### Prerequisites

Before configuring the Kubernetes Update Object plugin, the target clusters must be added to the Runbook Automation instance and the authentication method must be configured. This is done by following the steps outlined in the [Kubernetes Plugins Overview](/manual/plugins/kubernetes-plugins-overview.md).

### Add Kubernetes Update Object Step

When building a Job, add the **Kubernetes / Clusters / Update Object** node step:

![Kubernetes Update Object](/assets/img/k8s-cluster-update-object.png)<br>

Configure the following fields:

* **Object Name**: The name of the object to be updated.
* **YAML Definition**: The YAML definition of the object to be updated.
* **Namespace**: The namespace where the object resides. Default is `default`.
* **Object Type**: Select the type of object to update (e.g., Pods, Deployments, Services). Default is "Pods".