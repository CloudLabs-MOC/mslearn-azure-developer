## Lab 05 - Module 3: Deploy a container to Azure Container Apps with the Azure CLI

## Lab Scenario

In this exercise, you deploy a containerized application to Azure Container Apps using Azure CLI. You learn how to create a container app environment, deploy your container, and verify that your application is running in Azure.

## Lab Objectives

In this lab, you will perform:

- **Exercise 1:** Create an Azure Container Apps environment  
- **Exercise 2:** Deploy a container app to the environment  

## Estimated Timing: 15 Minutes

## Exercise 1: Create an Azure Container Apps environment

In this exercise, you will create an Azure Container Apps environment that provides the secure and shared infrastructure needed to host your container apps.

1. Ensure the Azure Container Apps CLI extension is installed and up to date.

   ```bash
   az extension add --name containerapp --upgrade
   ```

1. Create a Container Apps environment.  
   It may take a few minutes for the operation to complete.

   ```bash
   az containerapp env create   --name my-container-env<inject key="DeploymentID" enableCopy="false"/>   --resource-group ConfidentialStack-<inject key="DeploymentID" enableCopy="false"/>   --location <inject key="Region" enableCopy="false"/>
   ```

![](./media/lab5-e3-1.png)

---

## Exercise 2: Deploy a container app to the environment

In this exercise, you deploy a containerized application to the Container Apps environment and verify that it is accessible through a public endpoint.

1. Deploy a sample container app using the following command:

   ```bash
   az containerapp create   --name my-container-app<inject key="DeploymentID" enableCopy="false"/>   --resource-group ConfidentialStack-<inject key="DeploymentID" enableCopy="false"/>   --environment my-container-env<inject key="DeploymentID" enableCopy="false"/>   --image mcr.microsoft.com/azuredocs/containerapps-helloworld:latest   --target-port 80   --ingress external   --query properties.configuration.ingress.fqdn
   ```

![](./media/lab5-e3-2.png)

> **Note:**  
> Setting **--ingress** to **external** exposes the container app to public requests.  
> The command returns the fully qualified domain name (FQDN) used to access the application.

   ```
   Container app created. Access your app at <url>
   ```

1. Select the returned URL to verify that the container app is running.

![](./media/lab5-e3-3.png)

<validation step="31b12d09-bb81-4d99-bad5-4533168f612a" />

---

## Summary

In this lab, you:

- Created an Azure Container Apps environment  
- Deployed a container app to the environment  
- Verified successful deployment by accessing the public endpoint  

## You have successfully completed the lab.