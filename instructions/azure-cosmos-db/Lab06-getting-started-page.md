# Getting Started with Lab 06: Create Resources in Azure Cosmos DB for NoSQL using .NET

### Estimated Duration: 40 Minutes

## Overview

Welcome to **Lab 06: Create resources in Azure Cosmos DB for NoSQL using .NET**.  
In this lab, you will build a .NET application that connects to Azure Cosmos DB, creates databases, containers, and items programmatically, and verifies results in the Azure portal.

This Getting Started page provides all essential environment setup steps, navigation instructions, and support details.

---

## Lab Objectives

By completing this lab, you will learn to:

- Create an Azure Cosmos DB for NoSQL account  
- Build and configure a .NET console application  
- Authenticate and connect using the Cosmos DB SDK  
- Create a database, container, and items programmatically  
- Verify created resources in the Azure Portal  

---

## Pre-requisites

Participants should have:

- **Basic C# / .NET Knowledge:** Ability to build console apps and manage NuGet packages.  
- **Azure Portal Experience:** Familiarity with navigating Azure services like Cosmos DB.  
- **NoSQL Concepts:** Understanding of databases, containers, partitions, and JSON documents.  
- **Azure SDK Basics:** Awareness of connecting to Azure services programmatically.  
- **Browser Access:** A modern browser to work in CloudLabs and Azure Portal.  

---

## Architecture

This lab demonstrates a typical development workflow using Cosmos DB and .NET.

**Architecture Flow:**

1. A .NET application initializes a Cosmos DB client using an endpoint and key.  
2. The app creates a **database** and **container** if they do not exist.  
3. The application inserts JSON items programmatically.  
4. Azure Cosmos DB stores and indexes the data automatically.  
5. The user verifies created resources using the Azure portal.

**Key Components in Flow:**  
Developer → .NET SDK → Cosmos DB Account → Database → Container → Items → Azure Portal Verification

---

## Explanation of Components

1. **Azure Cosmos DB for NoSQL**  
   A globally distributed, high-performance NoSQL database service optimized for JSON storage.

2. **CosmosClient (.NET SDK)**  
   The .NET class used to connect, create databases, containers, and perform CRUD operations.

3. **Database & Container**  
   Logical structures in Cosmos DB used for organizing and partitioning JSON data.

4. **Partition Key**  
   A value used to distribute data for performance and scalability.

5. **Azure Portal**  
   Used to view, validate, and monitor the Cosmos DB resources created by the application.

---

## Accessing Your Lab Environment

Your virtual machine and lab guide are available directly in your browser.

### Virtual Machine Access  
You will see your VM loading on the left side of the screen:

### Lab Guide Access  
The lab guide appears on the right panel and will be your reference throughout the exercises.

   ![VM Screenshot](media/GS6.png)

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

   ![Zoom](media/ZZ01.png)

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