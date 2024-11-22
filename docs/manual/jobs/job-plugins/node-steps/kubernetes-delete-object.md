# Kubernetes Clusters - Delete Object
:::enterprise
:::

## Overview

This plugin deletes an object of a selected kind within a Kubernetes cluster. It is designed to work in conjunction with the AWS EKS, GCP GKE, and Azure AKS [Resource Model Source plugins](/manual/projects/resource-model-sources/).


## Configuration

### Required Fields

* **Name**: The name of the object to be deleted, such as Pod name or Deployment name.
* **Namespace**: The namespace where the object resides. Default is `default`.

### Optional Fields

* **Object Type**: Select the type of object to delete (e.g., Pods, ConfigMaps, Deployments). Default is "Pods".
* **Output Format**: Choose the format for the output (JSON or YAML). Default is JSON.

## Usage

1. Select the desired object type from the dropdown menu.
2. Provide the name of the object you want to delete.
3. Specify the namespace where the object is located.
4. Choose the preferred output format.

## Authentication

Kubernetes Clusters plugins operate on a per-cluster basis and authenticate in one of two ways, as configured in the [Resource Model Plugin](/manual/projects/resource-model-sources/) used to fetch the nodes. This configuration is controlled by the `Use Pod Service Account for Node Steps` option:

1. When disabled, the plugin uses the cloud provider credentials set in the resource model to retrieve the
   kube-config for the targeted cluster.

2. When enabled, the [Enterprise Runner](/administration/runner/) must be placed in the cluster and uses its pod's K8s service account for authentication.