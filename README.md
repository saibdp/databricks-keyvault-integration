# **Databricks Key Vault Integration**

## **Overview**
This repository demonstrates how to securely integrate **Azure Databricks** with **Azure Key Vault** to dynamically fetch secrets (like service credentials) and configure **Azure Data Lake Storage (ADLS)** for secure data access using OAuth.

By leveraging **Databricks Secret Scopes** and Azure Key Vault, this solution avoids hardcoding sensitive information, ensuring a secure and scalable approach for managing credentials in cloud environments.

---

## **Features**
- Securely fetch secrets from Azure Key Vault via Databricks Secret Scopes.
- Configure OAuth-based access to Azure Data Lake Storage (ADLS).
- Dynamically read, write, and list files in ADLS using Databricks and PySpark.
- Avoid hardcoding sensitive credentials like `client secret` in code.

---

## **Getting Started**

### **Prerequisites**
1. **Azure Services**:
   - Azure Key Vault with stored secrets.
   - Azure Data Lake Storage (ADLS) account.
   - Azure Active Directory Application (App Registration) with:
     - `Application (client) ID`
     - `Directory (tenant) ID`
     - Secret (stored in Key Vault).

2. **Databricks Setup**:
   - Access to a Databricks workspace.
   - Permissions to create and manage secret scopes.

---

### **Setup Guide**

#### 1. **Create a Databricks Secret Scope**
Run the following command in your Databricks notebook to create a secret scope linked to Azure Key Vault:

```bash
databricks secrets create-scope \
    --scope my-keyvault-scope \
    --scope-backend-type AZURE_KEYVAULT \
    --resource-id "/subscriptions/<subscription-id>/resourceGroups/<resource-group>/providers/Microsoft.KeyVault/vaults/<your-keyvault-name>" \
    --dns-name "https://<your-keyvault-name>.vault.azure.net/"
