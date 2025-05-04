# devops
This repository contains general purpose resources to be used for Infrastructure and DevOps activities.


## Connetion to Azure

This file contains general purpose commands to be used in case you are managing multiple Azure Accounts.

```bash
# Show the list of available accounts
az account list --output table

# Login to Azure on a specific tenant and subscription
# This is the tenant ID of the Azure tenant you want to use
az login --tenant "<tenantId>"
az account set --subscription "<subscrptionId>"

# Simple query
az account list --query "[].{Name:name, Id:id, UserName:user.name}" --output table

# Login to Azure Container Registry
az acr login --name <acrname>

# You may want to use 'az acr login -n <acrname> --expose-token' to get an access token, which does not require Docker to be installed.
az acr login -n <acrname> --expose-token

# Login as service-principal with admin password
az login --service-principal -u "http://<acrname>" -p "<acrpassword>" --tenant "<tenantId>"

# List of repositories that are inside a acr
az acr repository list --name <acrname> --output table

# List of tag that belong to a repository
az acr repository show-tags --name <acrname> --repository <repositoryname>/<imagename> --output table
```

| Name                   | Id           | UserName |
| ---------------------- | :----------- |------- |
Production               | <-tenantid-> | giovanni.nocco@genocs.com |
DEV/QA/TEST              | <-tenantid-> | giovanni.nocco@genocs.com |
Stage                    | <-tenantid-> | giovanni.nocco@genocs.com |
Pay-As-You-Go            | <-tenantid-> | giovanni.nocco@genocs.com |


## Azure Container Registry

```bash
# Tagging and pushing the images to Azure Container Registry (ACR)
docker tag <repositoryname>/<imagename>:tag <acrname>.azurecr.io/<imagename>:tag
```
