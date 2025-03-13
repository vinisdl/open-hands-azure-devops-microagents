---
name: azure_devops
type: knowledge
version: 1.0.0
agent: CodeActAgent
triggers:
  - "clone"
  - "azuredevops"
  - "azure devops"
---

You have access to environment variables that allow you to clone repositories from Azure DevOps using the Azure DevOps CLI.  

The following variables are used:  
- `AZURE_DEVOPS_ORG`: Your Azure DevOps organization service URL.  
- `AZURE_DEVOPS_PAT`: Your Personal Access Token (PAT) for authentication in Azure DevOps.  
- `AZURE_DEVOPS_PROJECT`: The project name in Azure DevOps.  

**Important Notes:**  
* Ensure that the Azure DevOps CLI and its extension are installed.  
* This agent simplifies authentication and the repository cloning process from Azure DevOps.  
* Use CD into repository name


### Installation  

Run the following commands to install the Azure DevOps CLI and configure the environment:  

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
az extension add --name azure-devops
```

### Configuration  

Before using the CLI, set default values for your organization and project:  

```bash
az devops configure --defaults organization="https://dev.azure.com/$AZURE_DEVOPS_ORG" project="$AZURE_DEVOPS_PROJECT"
```

### Cloning a Repository  

To clone a repository, use the following command:  

```bash
az repos clone --repository "$REPOSITORY_NAME"
```

### How to Use This Agent  

1. **Export the environment variables** (if not already set):  

   ```bash
   export AZURE_DEVOPS_ORG="digital-office"
   export AZURE_DEVOPS_PAT="your_personal_access_token"
   export AZURE_DEVOPS_PROJECT="project"
   ```

2. **Authenticate with the Azure DevOps CLI**:  

   ```bash
   az devops login --organization $AZURE_DEVOPS_ORG_SERVICE_URL --token $AZURE_DEVOPS_PAT
   ```

3. **Clone a repository**:  

   ```bash
      git clone https://$AZURE_DEVOPS_PAT@dev.azure.com/$AZURE_DEVOPS_ORG/$AZURE_DEVOPS_PROJECT$/_git/<repository_name>
   ```

4. **CD projet*

  ```bash
  cd <repository_name>
  ```