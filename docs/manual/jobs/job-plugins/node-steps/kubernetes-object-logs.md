# Kubernetes Clusters - Object Logs
:::enterprise
:::

## Overview

This plugin allows you to view the logs of an object within a Kubernetes cluster. It is designed to work in conjunction with the AWS EKS, GCP GKE, and Azure AKS [Resource Model Source plugins](/manual/projects/resource-model-sources/)

## Configuration

### Required Fields

* **Name**: The name of the object to view logs from, such as Pod name or Deployment name.
* **Namespace**: The namespace where the object resides. Default is `default`.

### Optional Fields

* **Container**: Specify a particular container to view logs from within the object.
* **Number of Log Lines**: The number of log lines to retrieve. Default is 50.
* **Time-span (seconds)**: A relative time in seconds before the current time from which to show logs.
* **Follow Logs**: If selected, the plugin will follow the log output. Note that the Job may continue to run until manually stopped.

## Usage

1. Provide the name of the object you want to view logs from.
2. Specify the namespace where the object is located.
3. Optionally, specify a particular container, number of log lines, time-span, or choose to follow logs.

## Authentication

Kubernetes Clusters plugins operate on a per-cluster basis and authenticate in one of two ways, as configured in the [Resource Model Plugin](/manual/projects/resource-model-sources/) used to fetch the nodes. This configuration is controlled by the `Use Pod Service Account for Node Steps` option:

1. When disabled, the plugin uses the cloud provider credentials set in the resource model to retrieve the
   kube-config for the targeted cluster.

2. When enabled, the [Enterprise Runner](/administration/runner/) must be placed in the cluster and uses its pod's K8s service account for authentication.

## Notes

- When using the "Follow Logs" option, be aware that the Job will continue running until it's manually stopped.
- The Time-span option allows you to view logs from a specific point in time, which can be useful for troubleshooting recent issues.