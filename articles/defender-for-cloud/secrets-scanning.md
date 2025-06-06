---
title: Protecting secrets in Microsoft Defender for Cloud
description: Learn how to protect secrets with Microsoft Defender for Server's agentless secrets scanning.
ms.topic: overview
ms.date: 02/19/2025
---


# Protecting secrets in Defender for Cloud

Microsoft Defender for Cloud helps security teams to minimize the risk of attackers exploiting security secrets.

After gaining initial access, attackers try to move laterally across networks, accessing resources to exploit vulnerabilities and damage critical information systems.Lateral movement often involves credentials threats that typically exploit sensitive data such as exposed credentials and secrets such as passwords, keys, tokens, and connection strings to gain access to additional assets.

Secrets are often found across multicloud deployments in files, on VM disks, or on containers. Exposed secrets happen for a number of reasons:

- **Lack of awareness**: Organizations might not be aware of the risk and consequences of secrets exposure.
- **Lack of policy**: There might not be a clear company policy on handling and protecting secrets in code and configuration files.
- **Lack of discovery tools**: Tools might not be in place to detect and remediate secrets leaks.
- **Complexity and speed**: Complex environments that might include multiple cloud platforms, open-source software, and third-party code. Developers might use secrets to access and integrate resources and services, and store secrets in source code repositories for convenience and reuse. This can lead to accidental exposure of secrets in public or private repositories, or during data transfer or processing.
- **Trade-off between security and usability**: Organizations might keep secrets exposed in cloud environments for ease-of-use, to avoid the complexity and latency of encrypting and decrypting data at-rest and in-transit. This can compromise the security and privacy of data and credentials.

## Scanning types and plans

Defender for Cloud provides different types of secrets scanning.

**Scanning type** | **Details** | **Plan support**
--- | --- | ---
**Machine scanning** |  Agentless secrets scanning on multicloud VMs. | Defender for Cloud Security Posture Management (CSPM) plan, or Defender for Servers Plan 2.
**Cloud deployment resource scanning** | Agentless secrets scanning across multicloud infrastructure-as-code deployment resources. | Defender CSPM plan.
**Code repository scanning** | [Scanning to discover exposed secrets in Azure DevOps](defender-for-devops-introduction.md). | Defender CSPM plan.

## Scanning permissions

To use secrets scanning, the following permissions are needed:

- Security Reader

  - Security Admin

    - Reader

      - Contributor

        - Owner

## Reviewing secrets findings

There are a number of methods available to identify and mitigate secrets issues. Not every method is supported for every secret.

- **Review secrets in the asset inventory**: The inventory shows the security state of resources connected to Defender for Cloud. From the inventory you can view the secrets discovered on a specific machine.
- **Review secrets recommendations**: When secrets are found on assets, a recommendation is triggered under the Remediate vulnerabilities security control on the Defender for Cloud Recommendations page. Recommendations are triggered as follows:
- **Review secrets with cloud security explorer**. Use cloud security explorer to query the cloud security graph for secrets insights. You can build your own queries, or use one of the built-in templates to query for VM secrets across your environment.
- **Review attack paths**: Attack path analysis scans the cloud security graph to expose exploitable paths that attacks might use to breach your environment and reach high-impact assets. VM secrets scanning supports a number of attack path scenarios.

## Secrets support

Defender for Cloud supports discovery of the types of secrets summarized in the table. The **Review using** column indicates the methods you can use to investigate and remediate secrets recommendations.

**Secrets type** | **VM secrets discovery** | **Cloud deployment secrets discovery** | **Review using**
--- | --- | --- | ---
Insecure SSH private keys<br/>Supports RSA algorithm for PuTTy files.<br/>PKCS#8 and PKCS#1 standards<br/>OpenSSH standard |Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure SQL connection strings support SQL PAAS.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure database for PostgreSQL.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure database for MySQL.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure database for MariaDB.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure Cosmos DB, including PostgreSQL, MySQL and MariaDB.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext AWS RDS connection string supports SQL PAAS:<br/>Plaintext Amazon Aurora with Postgres and MySQL flavors.<br/>Plaintext Amazon custom RDS with Oracle and SQL Server flavors.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure storage account connection strings|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure storage account connection strings.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Azure storage account SAS tokens.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext AWS access keys.|Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext AWS S3 presigned URL. |Yes |Yes | Inventory, cloud security explorer, recommendations, attack paths
Plaintext Google storage signed URL. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure AD Client Secret. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure DevOps Personal Access Token. |Yes |Yes | Inventory, cloud security explorer.
Plaintext GitHub Personal Access Token.|Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure App Configuration Access Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Cognitive Service Key.|Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure AD User Credentials. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Container Registry Access Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure App Service Deployment Password. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Databricks Personal Access Token. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure SignalR Access Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure API Management Subscription Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Bot Framework Secret Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Machine Learning Web Service API Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Communication Services Access Key.|Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Event Grid Access Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Amazon Marketplace Web Service (MWS) Access Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Maps Subscription Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Web PubSub Access Key.|Yes |Yes | Inventory, cloud security explorer.
Plaintext OpenAI API Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Batch Shared Access Key. |Yes |Yes | Inventory, cloud security explorer.
Plaintext NPM Author Token. |Yes |Yes | Inventory, cloud security explorer.
Plaintext Azure Subscription Management Certificate. |Yes |Yes | Inventory, cloud security explorer.
Plaintext GCP API Key. |No |Yes | Inventory, cloud security explorer.
Plaintext AWS Redshift credentials.|No |Yes | Inventory, cloud security explorer.
Plaintext Private key.|No |Yes | Inventory, cloud security explorer.
Plaintext ODBC connection string.|No |Yes | Inventory, cloud security explorer.
Plaintext General password.|No |Yes | Inventory, cloud security explorer.
Plaintext User login credentials.|No |Yes | Inventory, cloud security explorer.
Plaintext Travis personal token.|No |Yes | Inventory, cloud security explorer.
Plaintext Slack access token. |No |Yes | Inventory, cloud security explorer.
Plaintext ASP.NET Machine Key.|No |Yes | Inventory, cloud security explorer.
Plaintext HTTP Authorization Header. |No |Yes | Inventory, cloud security explorer.
Plaintext Azure Redis Cache password. |No |Yes | Inventory, cloud security explorer.
Plaintext Azure IoT Shared Access Key. |No |Yes | Inventory, cloud security explorer.
Plaintext Azure DevOps App Secret.|No |Yes | Inventory, cloud security explorer.
Plaintext Azure Function API Key. |No |Yes | Inventory, cloud security explorer.
Plaintext Azure Shared Access Key. |No |Yes | Inventory, cloud security explorer.
Plaintext Azure Logic App Shared Access Signature. |No |Yes | Inventory, cloud security explorer.
Plaintext Azure Active Directory Access Token.|No |Yes | Inventory, cloud security explorer.
Plaintext Azure Service Bus Shared Access Signature.|No |Yes | Inventory, cloud security explorer.

## Related content

- [Machine secrets scanning](secrets-scanning-servers.md).
- [Cloud deployment secrets scanning](secrets-scanning-cloud-deployment.md)
- [Code secrets scanning](secrets-scanning-code.md)
