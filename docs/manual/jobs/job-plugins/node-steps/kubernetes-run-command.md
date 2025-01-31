# Kubernetes Clusters - Run Command
:::enterprise
:::

## Overview

This plugin executes a command in a specified pod within a Kubernetes cluster. Since this is a node-step plugin, multiple Kubernetes clusters or namespaces can be targeted within a single Job.

## Configuration

### Prerequisites

Before configuring the Kubernetes Object Logs plugin, the target clusters must be added to the Runbook Automation instance and the authentication method must be configured. This is done by following the steps outlined in the [Kubernetes Plugins Overview](/manual/plugins/kubernetes-plugins-overview.md).

### Add Kubernetes Run Command Step

When building a Job, add the **Kubernetes / Clusters / Run Command** node step:

![Kubernetes Run Command](/assets/img/k8s-cluster-run-command.png)<br>

Configure the following fields:

* **Pod Name**: The name of the pod to execute the command in.
* **Namespace**: The namespace where the pod resides.
* **Command**: The command to execute in the pod.
* **Container**: (Optional) Specify a particular container within the pod to execute the command in.
* **Shell**: Specific shell to use for executing the command in the container. Default is `/bin/sh`.