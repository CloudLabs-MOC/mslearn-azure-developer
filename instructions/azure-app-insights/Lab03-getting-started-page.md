# Getting Started with Lab 03: Monitor an Application with Autoinstrumentation

### Estimated Duration: 30-40 Minutes

## Overview

Welcome to **Lab 03: Monitor an Application with Autoinstrumentation**.  
In this lab, you will configure monitoring for a web application using Application Insights with zero code changes. You will enable autoinstrumentation, deploy a Blazor app, and observe real‑time telemetry including requests, failures, and performance metrics.

This Getting Started guide provides environment setup, navigation instructions, and support details before you begin the exercises.

---

## Lab Objectives

By completing this lab, you will learn to:

- Create an Azure Web App with Application Insights enabled  
- Configure autoinstrumentation for monitoring  
- Deploy a Blazor web application  
- Analyze telemetry and application activity in Application Insights  

---

## Pre-requisites

Participants should have:

- **Basic Web App Knowledge:** Understanding of creating and deploying web applications.  
- **Azure Portal Experience:** Ability to navigate Azure services like Web Apps and Application Insights.  
- **Monitoring Concepts:** Awareness of APM tools, metrics, and logs.  
- **.NET Application Experience:** Basic familiarity with building and running a Blazor application.  
- **Browser & Editor:** Access to a modern web browser and optional editor if making changes to the Blazor app.  

---

## Architecture

![](media/Lab03-dig01.png)

**Architecture Flow:**

This lab demonstrates monitoring using Azure Application Insights with autoinstrumentation.

1. A Blazor application is deployed to an Azure Web App.  
2. Autoinstrumentation is enabled at the App Service level with no code modifications.  
3. The Web App automatically emits telemetry (requests, failures, traces).  
4. Application Insights collects, processes, and visualizes the telemetry.  
5. Logs and metrics are viewed in Azure Monitor and Application Insights workbooks.

---

## Explanation of Components

1. **Azure Web App**  
   Hosts the Blazor application and provides built‑in integration with Application Insights.

2. **Application Insights**  
   Collects telemetry such as requests, dependencies, exceptions, and performance metrics.

3. **Autoinstrumentation**  
   Enables monitoring without modifying application code—configured directly at App Service level.

4. **Blazor Application**  
   The sample web application deployed for observing telemetry during this lab.

5. **Azure Monitor**  
   Provides dashboards, logs, metrics, and end‑to‑end observability for applications.

---

## Accessing Your Lab Environment

Your virtual machine and lab guide are available within the CloudLabs interface.

### Virtual Machine Access
You will see your VM loading on the left side of the lab environment:

### Lab Guide Access
The lab guide appears on the right-hand panel.

![VM Screenshot](media/GS3.png)

---

## Exploring Lab Resources

Navigate to the **Environment** tab to view credentials and resource details:

![Environment](media/G2.png)

---

## Split‑Window Feature

To view the lab guide in a separate window, select **Split Window**:

![Split Window](media/G3.png)

---

## Managing Your Virtual Machine

Start, stop, or restart your virtual machine using the **Resources** tab:

![VM Manage](media/G4.png)

---

## Adjusting Zoom

Modify the zoom level using the **A↕ 100%** control near the timer:

![Zoom](media/ZZ01.png)

---

## Accessing Azure Portal

Follow these steps to begin working in Azure:

1. From the VM desktop, select the **Azure Portal** icon:

   ![](media/G6.png)

2. You will see the **Sign in to the Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

      ![](media/G7.png)

3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
     ![](media/G8.png)

4. If prompted to **Stay signed in**, choose **No**.  
   ![](media/G9.png)

---

## Support

CloudLabs provides **24/7 support** for all learners.

**Learner Support Contacts:**  
- Email: cloudlabs-support@spektrasystems.com  
- Live Chat: https://cloudlabs.ai/labs-support  

---

## Move to the Next Page

Select **Next** at the bottom‑right corner to begin **Exercise 1**.

![](media/G10.png)

---

## Happy Learning!