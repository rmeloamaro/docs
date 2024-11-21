# Kubernetes Clusters - Update Object
:::enterprise
:::

## Overview

This plugin updates a specified object of a selected kind within a Kubernetes cluster. It is designed to work in conjunction with the AWS EKS, GCP GKE, and Azure AKS [Resource Model Source plugins](/manual/projects/resource-model-sources/).

## Configuration

### Required Fields

* **Object Name**: The name of the object to be updated.
* **YAML Definition**: The YAML definition of the object to be updated.
* **Namespace**: The namespace where the object resides. Default is `default`.

### Optional Fields

* **Object Type**: Select the type of object to update (e.g., Pods, Deployments, Services). Default is "Pods".

## Usage

1. Provide the name of the object you want to update.
2. Select the desired object type from the dropdown menu.
3. Enter the updated YAML definition for the object.
4. Specify the namespace where the object is located.

## Authentication

Kubernetes Clusters plugins operate on a per-cluster basis and authenticate in one of two ways, as configured in the [Resource Model Plugin](/manual/projects/resource-model-sources/) used to fetch the nodes. This configuration is controlled by the `Use Pod Service Account for Node Steps` option:

1. When disabled, the plugin uses the cloud provider credentials set in the resource model to retrieve the
   kube-config for the targeted cluster.

2. When enabled, the [Enterprise Runner](/administration/runner/) must be placed in the cluster and uses its pod's K8s service account for authentication.

## Notes

- The plugin uses a field manager named "runbook-automation/apply-patch" for tracking changes.
- Ensure that the YAML definition provided is complete and correct for the object you're updating.