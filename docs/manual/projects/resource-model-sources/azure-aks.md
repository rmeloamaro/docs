# Azure AKS Node Source

::: enterprise
:::

The Azure AKS (Azure Kubernetes Service) Resource Model Source allows you to import your AKS clusters as nodes within Runbook Automation. This plugin provides node source functionality for managing and executing jobs on your Azure Kubernetes clusters directly from Runbook Automation.

### Configuration

To configure the Azure AKS Resource Model Source:

1. In your project, go to "Project Settings" > "Edit Nodes".
2. Click "Add a new Node Source".
3. Select "Azure Kubernetes Clusters" from the list of available node sources.
4. Configure the following settings:
- **Subscription**: The Azure Subscription ID. If not provided, the value from the Azure plugin group at the Project or System context will be used.
- **Tenant ID**: The Azure Tenant ID. If not provided, the value from the Azure plugin group at the Project or System context will be used.
- **Client ID**: The path to the Key Storage entry for the Azure Client ID. If not provided, the Client ID value from the Azure plugin group at the Project or System context will be used. If an "Unauthorized" error occurs, ensure that the proper policy is added to ACLs.
- **Azure Client Secret**: The path to the Key Storage entry for the Client Secret. If not provided, the value from the Azure plugin group at the Project or System context will be used. If an "Unauthorized" error occurs, ensure that the proper policy is added to ACLs.
- **Resource Group**: Optionally filter the clusters listed from a specific Resource Group.
- **Use Pod Service Account for Node Steps**: Choose whether to authenticate with the Pod Service Account for Job steps. Set to `True` if Runbook Automation or a Runner is executing within the targeted cluster.


## Authentication

Follow the steps outlined in the [Azure Plugins Overview](/manual/plugins/azure-plugins-overview) to generate the necessary Azure credentials and set them up at the project or system level. These credentials can be overridden in individual Azure Kubernetes Clusters Node Source configurations if needed.