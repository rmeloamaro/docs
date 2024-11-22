# Kubernetes Clusters - List Objects
:::enterprise
:::

## Overview

This plugin lists objects of a selected kind within a Kubernetes cluster. It is designed to work in conjunction with the AWS EKS, GCP GKE, and Azure AKS [Resource Model Source plugins](/manual/projects/resource-model-sources/).

## Configuration

### Required Fields

* **Namespace**: The namespace to list objects from. Default is `default`.

### Optional Fields

* **Object Type**: Select the type of object to list (e.g., Pods, ConfigMaps, Deployments). Default is "Pods".
* **All Namespaces**: If selected, retrieve objects from across all namespaces. The 'Namespace' field will be ignored.
* **Label Selector**: Filter objects based on labels. Supports equality-based and set-based selectors.
* **Field Selector**: Filter objects based on fields. Supports equality-based and set-based selectors.
* **Output Format**: Choose the format for the output (Simple List, JSON, or YAML). Default is "Simple List".

## Usage

1. Select the desired object type from the dropdown menu.
2. Specify the namespace or choose to list from all namespaces.
3. Optionally, add label or field selectors to filter the results.
4. Choose the preferred output format.

## Authentication

Kubernetes Clusters plugins operate on a per-cluster basis and authenticate in one of two ways, as configured in the [Resource Model Plugin](/manual/projects/resource-model-sources/) used to fetch the nodes. This configuration is controlled by the `Use Pod Service Account for Node Steps` option:

1. When disabled, the plugin uses the cloud provider credentials set in the resource model to retrieve the
   kube-config for the targeted cluster.

2. When enabled, the [Enterprise Runner](/administration/runner/) must be placed in the cluster and uses its pod's K8s service account for authentication.

## Notes

- For detailed information on label selectors, refer to the [Kubernetes documentation on label selectors](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/#label-selectors).
- For detailed information on field selectors, refer to the [Kubernetes documentation on field selectors](https://kubernetes.io/docs/concepts/overview/working-with-objects/field-selectors/).