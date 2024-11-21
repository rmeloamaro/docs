# Kubernetes Clusters - Run Command
:::enterprise
:::

## Overview

This plugin allows you to execute a command in a pod within a Kubernetes cluster. It is designed to work in conjunction with the AWS EKS, GCP GKE, and Azure AKS [Resource Model Source plugins](/manual/projects/resource-model-sources/).
## Configuration

### Required Fields

* **Pod Name**: The name of the pod to execute the command in.
* **Namespace**: The namespace where the pod resides. Default is `default`.
* **Command**: The command to execute in the pod.

### Optional Fields

* **Container**: Specify a particular container within the pod to execute the command in.
* **Shell**: Specific shell to use for executing the command in the container. Default is `/bin/sh`.

## Usage

1. Provide the name of the pod you want to execute the command in.
2. Specify the namespace where the pod is located.
3. Enter the command you want to execute.
4. Optionally, specify a particular container and/or shell to use.

## Authentication

Kubernetes Clusters plugins operate on a per-cluster basis and authenticate in one of two ways, as configured in the [Resource Model Plugin](/manual/projects/resource-model-sources/) used to fetch the nodes. This configuration is controlled by the `Use Pod Service Account for Node Steps` option:

1. When disabled, the plugin uses the cloud provider credentials set in the resource model to retrieve the
   kube-config for the targeted cluster.

2. When enabled, the [Enterprise Runner](/administration/runner/) must be placed in the cluster and uses its pod's K8s service account for authentication.

## Notes

- Make sure the command you're executing is available in the specified container.
- If no specific container is specified, the command will be executed in the first container of the pod.
- The shell option allows you to choose a different shell if the default `/bin/sh` is not available or if you need to use a different shell for specific commands.