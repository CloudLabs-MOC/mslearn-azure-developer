# Getting Started with Lab 5: Azure Container Services

### Estimated Duration: 50 Minutes

## Overview

Welcome to **Lab 5: Azure Container Services**.  
In this lab, you will work with multiple Azure container platforms to build, deploy, and verify containerized applications. This Getting Started page provides all required instructions to navigate your lab environment, access Azure, and begin the exercises.

---

## Lab Objectives

By the end of this lab, you will be able to:

- Build and push a container image to Azure Container Registry (ACR)  
- Deploy containers to Azure Container Instances (ACI)  
- Deploy a containerized application to Azure Container Apps  
- Verify deployment status and application behavior across all services  

---

## Pre-requisites

Participants should have:

- **Basic Understanding of Containers:** Familiarity with Docker images and containerized workloads.  
- **Azure Portal Skills:** Ability to navigate Azure services like ACR, ACI, and Container Apps.  
- **Container Deployment Concepts:** Awareness of registries, images, and runtime environments.  
- **Command-Line Experience:** Basic usage of Azure CLI or terminal commands.  
- **Browser Access:** A modern web browser to interact with CloudLabs and Azure Portal.  

---

## Architecture

This lab demonstrates a multi-service container deployment workflow across Azure.

**Architecture Flow:**

1. A container image is built locally and pushed to **Azure Container Registry (ACR)**.  
2. The image is deployed to **Azure Container Instances (ACI)** for quick execution.  
3. The same image is used to deploy a scalable microservice on **Azure Container Apps**.  
4. Each service exposes endpoints for testing and validation.  

**Key Components in Flow:**  
Developer → ACR → ACI → Container Apps → Public Endpoints → Application Verification

---

## Explanation of Components

1. **Azure Container Registry (ACR)**  
   A private image registry for storing and managing Docker container images.

2. **Azure Container Instances (ACI)**  
   Provides serverless container execution without managing virtual machines.

3. **Azure Container Apps**  
   A fully managed environment for running microservices and event-driven containers.

4. **Docker / Container CLI**  
   Used to build and push images to ACR.

5. **Azure CLI**  
   Command-line tool used to authenticate, manage container resources, and automate workflows.

---

## Accessing Your Lab Environment

Your virtual machine and lab guide are available directly in your browser.

### Virtual Machine Access
You will see your VM loading on the left side of the screen:

![VM Screenshot](media/17-7-25-g1.png)

### Lab Guide Access
The lab guide appears on the right panel and will be your reference throughout the exercises.

---

## Exploring Lab Resources

Navigate to the **Environment** tab to view credentials and resources:

![Environment](media/G2.png)

---

## Split-Window Feature

To open the lab guide in a separate window, click **Split Window**:

![Split View](media/G3.png)

---

## Managing Your Virtual Machine

You can Start, Stop, or Restart your virtual machine at any time via the **Resources** tab:

![VM Manage](media/G4.png)

---

## Adjusting Zoom

To zoom in/out of the environment view, use the **A↕ 100%** button near the timer:

![Zoom](media/17-7-25-g4.png)

---

## Accessing Azure Portal

Follow these steps to begin working in Azure:

1. On your VM desktop, click the **Azure Portal** icon:

   ![](media/G6.png)

2. Enter your credentials:

   - **Email/Username:** `<inject key="AzureAdUserEmail"></inject>`  
     ![](media/G7.png)

3. Enter your password:

   - **Password:** `<inject key="AzureAdUserPassword"></inject>`  
     ![](media/G8.png)

4. If prompted to **Stay signed in**, select **No**.  
   ![](media/G9.png)

---

## Support

CloudLabs offers **24/7 support** for all learners.

**Learner Support:**  
- Email: cloudlabs-support@spektrasystems.com  
- Live Chat: https://cloudlabs.ai/labs-support  

If you face login, VM, or Azure issues, reach out anytime.

---

## Move to the Next Page

Click **Next** at the bottom-right corner to begin the first exercise.

![](media/G10.png)

---

## Happy Learning!