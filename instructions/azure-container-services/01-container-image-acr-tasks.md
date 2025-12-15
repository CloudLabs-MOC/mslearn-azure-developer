# Lab 05 - Module 01 : Azure Container Services

## Lab Scenario

In this exercise, you build a container image from your application code and push it to Azure Container Registry using Azure CLI. You learn how to prepare your app for containerization, create an Azure Container Registry (ACR) instance, and store your container image in Azure.

## Lab Objectives

In this lab, you will perform:

- **Exercise 1:** Build and run a container image with Azure Container Registry Tasks  

## Estimated Timing: 20 Minutes

## Exercise 1: Build and run a container image with Azure Container Registry Tasks

### Task 1: Create an Azure Container Registry resource

In this task, you will create an Azure Container Registry instance that will store and manage your container images.

1. In the lab VM, click on the **Azure Portal icon** as shown below:

   ![](./media/lab2-12-0.png)

   - On the **Sign in to Microsoft Azure** tab, enter your credentials:
     - **Email/Username:** <inject key="AzureAdUserEmail"></inject>  
     - **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject>  

1. On the Azure portal homepage, select **[>_] Cloud Shell (1)** next to the **Copilot** tab.  
   In the **Welcome to Azure Cloud Shell** window, choose **Bash (2)**.

   ![](./media/lab5-12-1.png)
   ![](./media/lab5-12-2.png)

1. In the **Getting started** window, select **No storage account required (1)**, choose **Default subscription (2)**, and select **Apply (3)**.

   ![](./media/lab5-12-3.png)

1. Create an Azure Container Registry:

    ```bash
    az acr create --resource-group ConfidentialStack-<inject key="DeploymentID" enableCopy="false"/>   --name mycontainerregistry<inject key="DeploymentID" enableCopy="false"/>   --sku Basic
    ```

    ![](./media/lab5-12-4.png)

> **Note:** This command creates a *Basic* registry, a cost-optimized option suitable for learning and development scenarios.

> **Congratulations** on completing the task! Now, it's time to validate it.
<validation step="dd962eb8-d886-4bb8-a640-e9bf11f0668a" />

---

### Task 2: Build and push an image from a Dockerfile

In this task, you will build a container image from a Dockerfile and push it to your Azure Container Registry using ACR Tasks.

1. Create a Dockerfile:

    ```bash
    echo FROM mcr.microsoft.com/hello-world > Dockerfile
    ```

1. Build and push the image:

    ```bash
    az acr build --image sample/hello-world:v1   --registry mycontainerregistry<inject key="DeploymentID" enableCopy="false"/>   --file Dockerfile .
    ```

    ![](./media/lab5-12-5.png)
    ![](./media/lab5-12-6.png)

---

### Task 3: Verify the results

In this task, you will verify that the image was successfully pushed to your registry.

1. List repositories in the registry:

    ```bash
    az acr repository list --name mycontainerregistry<inject key="DeploymentID" enableCopy="false"/> --output table
    ```

    ![](./media/lab5-12-7.png)

1. List tags for the repository:

    ```bash
    az acr repository show-tags --name mycontainerregistry<inject key="DeploymentID" enableCopy="false"/>   --repository sample/hello-world --output table
    ```

    ![](./media/lab5-12-8.png)

---

### Task 4: Run the image in Azure Container Registry

In this task, you will run the container image directly from Azure Container Registry to validate successful execution.

```bash
az acr run --registry mycontainerregistry<inject key="DeploymentID" enableCopy="false"/>  --cmd '$Registry/sample/hello-world:v1' /dev/null
```

 ![](./media/lab5-12-9.png)

---

## Summary

In this lab, you:

- Created an Azure Container Registry  
- Built and pushed a container image using ACR Tasks  
- Verified repositories and image tags  
- Ran a container image directly from Azure Container Registry  

## You have successfully completed the lab. Click on Next >>

![](./media/next.png)