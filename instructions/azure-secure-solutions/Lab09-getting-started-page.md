# Getting Started with Lab 09: Secure Solutions in Azure

### Estimated Duration: 45–60 Minutes

## Overview

Welcome to **Lab 09: Secure Solutions in Azure**.  
In this lab, you will secure applications using Azure Key Vault and Azure App Configuration. This Getting Started page provides essential environment setup steps, navigation instructions, and support details.

---

## Lab Objectives

By completing this lab, you will learn to:

### Module 1 — Create and Retrieve Secrets from Azure Key Vault
- Create an Azure Key Vault  
- Store and retrieve secrets using Azure CLI  
- Build a .NET console application that interacts with Key Vault  

### Module 2 — Retrieve Configuration Settings from Azure App Configuration
- Create an App Configuration resource  
- Add configuration data  
- Build a .NET console application to retrieve settings  

---

## Pre-requisites

Participants should have:

- **Basic C# / .NET Skills:** Ability to build console applications and install NuGet packages.  
- **Azure Portal Familiarity:** Ability to navigate Key Vault, App Configuration, and Resource Groups.  
- **Security Concepts:** Basic understanding of secrets, configuration management, and secure storage.  
- **CLI Knowledge:** Ability to run Azure CLI commands in Cloud Shell or local terminal.  
- **Browser Access:** A modern browser to interact with CloudLabs and Azure Portal.  

---

## Architecture

This lab demonstrates secure application configuration using Azure Key Vault and App Configuration.

**Architecture Flow:**

1. A secret is stored in **Azure Key Vault** and retrieved via the .NET application.  
2. Application settings are stored in **Azure App Configuration**.  
3. The .NET application fetches configuration values securely at runtime.  
4. Azure services provide managed identity access and secure retrieval.  

**Key Components in Flow:**  
Developer → .NET App → Managed Identity → Key Vault → App Configuration → Secure Output

---

## Explanation of Components

1. **Azure Key Vault**  
   Securely stores secrets, keys, and certificates with controlled access.

2. **Azure App Configuration**  
   Centralized service for storing app configuration settings and feature flags.

3. **Managed Identity**  
   Provides secure identity for applications without storing credentials.

4. **Azure CLI**  
   Used to create resources and manage Key Vault secrets and configuration settings.

5. **.NET Console Application**  
   Demonstrates secure secret and configuration retrieval programmatically.


---

## Accessing Your Lab Environment

Your virtual machine and lab guide are available directly in your browser.

### Virtual Machine Access  

You will see your VM loading on the left side of the screen:

![VM Screenshot](media/lab9-vm.png)

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

![Zoom](media/zoom.png)

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

## Begin the Lab

Click **Next** at the bottom-right corner to begin **Module 1: Create and Retrieve Secrets from Azure Key Vault**.

   ![](media/G10.png)

## Happy Learning!