# Kubernetes Clusters - Run Script
:::enterprise
:::

## Overview

This plugin executes a script using a predefined container image within a Kubernetes cluster. It deploys a Kubernetes Job to run the script in a container, then deletes the Job after execution. Since this is a node-step plugin, multiple Kubernetes clusters or namespaces can be targeted within a single Job.

## Configuration

### Prerequisites

Before configuring the Kubernetes Run Script plugin, the target clusters must be added to the Runbook Automation instance and the authentication method must be configured. This is done by following the steps outlined in the [Kubernetes Plugins Overview](/manual/plugins/kubernetes-plugins-overview.md).

### Add Kubernetes Run Script Step

When building a Job, add the **Kubernetes / Clusters / Run Script** node step:

![Kubernetes Run Script](/assets/img/k8s-cluster-run-script.png)<br>

Configure the following fields:

* **Script**: The script to execute in the container.
* **Invocation Command**: The command to execute the script in the container. Default is `sh -c`.
* **Container Image**: The container image to use for script execution. Default is `amazon/aws-cli`.
* **Namespace**: The namespace where the Kubernetes Job will be deployed. Default is `default`.
* **Environment Variables**: Environment variables to pass to the container (YAML syntax).
* **Image Pull Policy**: The image pull policy for the container. Options include: 
  * `Always`
  * `IfNotPresent`
  * `Never`

## Notes

- The pod that was used to execute the script is automatically deleted after script execution.
- Environment variables support the 'valueFrom' field for referencing secrets and other sources. See [Kubernetes Docs](https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container/) for detailed syntax and examples.
- Predefined container images include options like `amazon/aws-cli`, `bitnami/kubectl`, `mcr.microsoft.com/azure-cli`, `google/cloud-sdk`, and `dtzar/helm-kubectl`, but other images may be used.