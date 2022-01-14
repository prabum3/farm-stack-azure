# FARM Stack on Azure 🧑‍🌾

Use this stack to deploy react website connected with a fastapi backend on Azure Web App

## What's in this Stack ?

- React app generated with `create-react-app` coupled with tailwindcss 🌟
- FastApi server with `motor` for db connections 🚀
- Deployed with a nginx reverse proxy
- Docker-compose file for local development

## Prerequisites

You would require
 - Azure Webapp configured to work with a Docker Container
 - Azure Container Registry to store container images
 - MongoDB for all your DB needs

## Required Inputs

- Web App Name: Name of the app that you have provisioned on Azure.
(Note that this should be configured for Docker deploy)
<img width="738" alt="Screenshot 2022-01-12 at 7 01 56 PM" src="https://user-images.githubusercontent.com/39593587/149175613-6bc8cdf0-1835-41b4-8cd3-3164e7f9bc06.png">

- Azure Container Registry URL: Login url of your container registry (example: stack.azurecr.io)

- Azure Resource Group Name : Name of the Resource Group under which your Web app is provisioned

- MongoDB Connection String : Connection string for your MongoDB

- Azure Credentials : You would need to generate Azure Credentials scoped to the resource-group/subscription of all the Azure resources mentioned above.
This can be done by running the Azure cli command

```bash
az ad sp create-for-rbac --name "GHActions" --role contributor --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} -sdk-auth

```
More detailed documentation can be found [here](https://docs.microsoft.com/en-us/azure/developer/github/connect-from-azure?tabs=azure-portal%2Clinux#use-the-azure-login-action-with-a-service-principal-secret)

**Your app would be hosted at https://<azure_app_name>.azurewebsites.net**

 ## Local Development

 You can get started with your project locally by running the command

 ```bash
   docker compose -f docker-compose-local.yml up --build -d
 ```

 This sets up the website at port:5000

