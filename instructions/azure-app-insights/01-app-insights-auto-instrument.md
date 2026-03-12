# Lab 03: Monitor an Application with Autoinstrumentation

## Lab Scenario
In this lab, you will learn how to monitor an application in Application Insights by configuring autoinstrumentation without modifying your application code. You will create an Azure App Service web app with Application Insights enabled, configure instrumentation at the service level, deploy a Blazor application, and then view application metrics and error data in Application Insights. This approach simplifies deployments and migrations by providing comprehensive monitoring without requiring code changes.

## Lab Objectives
In this lab, you will perform:

+ Exercise 1: Create a web app resource with Application Insights enabled  
+ Exercise 2: Configure instrumentation for the web app  
+ Exercise 3: Create a new Blazor app and deploy it to the web app resource  
+ Exercise 4: View application activity in Application Insights  

# Exercise 1: Create resources in Azure

### Task 1: Create a Web App with Application Insights enabled

1. In the portal, select **+ Create a resource** located under the **Azure Services** heading on the homepage.

   ![](./media/C1.png)

2. In the **Search services and Marketplace** search bar, enter **web app (1)** and press **Enter**.
3. In the Web App tile, select the **Create (2)** dropdown and then select **Web App (3)**.

   ![](./media/C2.png)

5. On the **Basics** tab, configure the following settings:

   | Setting | Action |
   |--|--|
   | **Subscription** | Retain the default value **(1)** |
   | **Resource group** | Choose an existing resource group **MonitoredAssets-<inject key="DeploymentID" enableCopy="false"/> (2)**  |
   | **Name** | **webapp-<inject key="DeploymentID" enableCopy="false"/> (3)**|
   | Slider under **Name** | Turn it off (if visible) **(4)** |
   | **Publish** | Select **Code (5)** |
   | **Runtime stack** | Select **.NET 8 (LTS) (6)** |
   | **Operating system** | Select **Windows (7)**. |
   | **Region** | Select **South Central US (8)** |
   | **Windows Plan** | Retain the default selection. |
   | **Pricing plan** | Select **F1 (9)**. |

     ![](./media/lab3-03-2.png)

6. Navigate to the **Monitor + secure (10)** tab and configure the following:

   | Setting | Action |
   |--|--|
   | **Enable Application Insights** | Select **Yes (1)**. |
   | **Application Insights** | Select **Create new (2)**. |

   ![](./media/C17.png)

   >**Note:** If the **Enable Application Insights** option is disabled and cannot be selected, follow these steps:

   1. Navigate back to the **Basics** tab

      ![](./media/lab3-03-8.png)

   2. Change the **Region** temporarily to West US or East US.

   3. Change the Region back to **South Central US (1)** and Ensure the Pricing plan is set to **F1 (2)**.

      ![](./media/lab3-03-9.png)

   4. Navigate again to the **Monitor + secure** tab and You should now be able to select **Enable Application Insights → Yes**.

7. In the **Create new Application Insights** pane, configure the following and click **OK (5)**:

   | Setting | Action |
   |--|--|
   | **Name** | Enter **autoinstrument-insights-<inject key="DeploymentID" enableCopy="false"/> (1)**. |
   | **Workspace** | Select **Create new (2)**, enter **Workspace-<inject key="DeploymentID" enableCopy="false"/> (3)**, and then select **OK (4)**. |

   ![](./media/C19.png)

8. After configuring the **Monitor + secure** settings, select **Review + create**.

    ![](./media/lab3-03-3.png)

9. On the **Review + create** tab, review the configuration settings, and then select **Create**.

   ![](./media/lab3-03-4.png)

8. After deployment completes, select **Go to resource**.

    ![](./media/lab3-03-5.png)

> **Congratulations** on completing the task! Now, it's time to validate it.
<validation step="7f755203-93a5-4792-b097-4e6048291dd8" />

# Exercise 2: Configure instrumentation settings

### Task 1: Enable autoinstrumentation for the web app

1. On the **webapp-<inject key="DeploymentID" enableCopy="false"/>** page, in the left navigation menu, expand **Monitoring (1)** and select **Application Insights (2)**.

2. Locate the **Instrument your application** section and select **.NET Core (3)**.

3. Under **Collection level**, select **Recommended (4)**.

4. Select **Apply (5)** and confirm the changes.

   ![](./media/C22.png)

   - If a popup appears prompting **Apply Monitoring Settings**, select **Yes**.

      ![](./media/C5.png)

5. In the left navigation menu, select **Overview**.

# Exercise 3: Create and deploy a Blazor app

> All steps in this exercise are performed in the Azure Cloud Shell.

### Task 1: Create the Blazor application

1. Open Cloud Shell using the **[\>_]** button at the top of the Azure portal, and choose a **Bash** environment.  

   ![](./media/A01.png)

   ![](./media/A02.png)

1. If prompted to choose storage, select **No storage account required**, choose your subscription, and select **Apply**.

   ![](./media/A03.png)

   > **Note:** If Cloud Shell is currently set to **PowerShell**, switch to **Bash**.

      ![](./media/C23.png)

2. Run the following commands to create a folder and move into it:

   ```
   mkdir blazor
   cd blazor
   ```

3. Creates a new Blazor app:
   ```
   dotnet new blazor
   ```

4. Builds the application:
   ```
   dotnet build
   ```
---
### Task 2: Publish and package the application

1. Publish the application into a **publish** directory:
   
   ```
   dotnet publish -c Release -o ./publish
   ```

2. Create a `.zip` file of the published output:
   ```
   cd publish
   zip -r ../app.zip .
   cd ..
   ```
   ![](./media/C24.png)
---

### Task 3: Deploy the application to App Service

1. Run the following command to deploy the application, using the correct App Service name and resource group:

   - Replace the placeholders with the names shown below:  

      - **Web App Name:** webapp-<inject key="DeploymentID" enableCopy="false"/>
       - **Resource Group Name:** MonitoredAssets-<inject key="DeploymentID" enableCopy="false"/>

         ```
         az webapp deploy --name webapp-<inject key="DeploymentID" enableCopy="false"/> \
            --resource-group MonitoredAssets-<inject key="DeploymentID" enableCopy="false"/> \
            --src-path ./app.zip
         ```

2. Once the deployment is complete, open the application from the **Overview (1)** page copy the **Default domain (2)** link and open it in new tab .

    ![](./media/C25.png)

    ![](./media/C06.png)

---

<details>
<summary>Troubleshooting Steps for Deploy the application to App Service Error</summary>

# Troubleshooting Steps for Deployment Error

**Note:** If you face an error in **Task 3: Deploy the application to App Service**, please follow the steps below and then run the deployment code again.

## **Step 1: Identify the Error**

If you receive the following message:

```
A Cloud Shell credential problem occurred.
Audience https://appservice.azure.com is not a supported MSI token audience.
```

## **Step 2: Log out of Azure CLI**

Run:

```bash
az logout
```

## **Step 3: Log in again using the correct scope**

Run:

```bash
az login --scope "https://appservice.azure.com/.default"
```

This will display a device login link and a code.

![](./media/C16.png)

## **Step 4: Authenticate using Device Login**

1. Open **https://microsoft.com/devicelogin**
2. Enter the code provided in Cloud Shell.
3. Select **Next**.

![](./media/C15.png)

## **Step 5: Select Your ODL_User Account**

Select the displayed **ODL_User** account.

![](./media/C14.png)

## **Step 6: Approve Azure CLI Sign-in**

Click **Continue** to allow Azure CLI access.

![](./media/C013.png)

## **Step 7: Select Subscription**

When prompted:

```
Select a subscription and tenant:
```

Enter:

```
1
```
## **Step 8: Re-run the Deployment Command**

Run:


   - **Web App Name:** webapp-<inject key="DeploymentID" enableCopy="false"/>
   - **Resource Group Name:** MonitoredAssets-<inject key="DeploymentID" enableCopy="false"/>

      ```
      az webapp deploy --name YOUR-WEB-APP-NAME \
         --resource-group YOUR-RESOURCE-GROUP \
         --src-path ./app.zip
      ```
</details>
---

# Exercise 4: View metrics in Application Insights

1. Return to the Azure portal and navigate to the resource group **MonitoredAssets-<inject key="DeploymentID" enableCopy="false"/>**. From the list of resources, select the **Application Insights** resource **autoinstrument-insights-<inject key="DeploymentID" enableCopy="false"/>**.

   ![](./media/lab3-03-6.png)

2. In the **Application Insights** resource, select **Overview** from the left navigation menu to view the basic monitoring charts.

   - Failed requests  
   - Server response time  
   - Server requests  
   - Availability 

     ![](./media/lab3-03-6.png)

### Generate telemetry:

1. Navigate through **Home**, **+ Counter**, and **Weather** navigation options in the menu of the web app.

   ![](./media/C12.png)

   ![](./media/C11.png)

   ![](./media/C10.png)

2. Refresh the web page multiple times to generate request and response data.

3. To generate errors, append `/failures` to the application URL.  
   (This route does not exist and will create failures.)  
   Refresh several times.

   ![](./media/C9.png)

4. Return to Application Insights and wait 1–2 minutes for telemetry to appear.

5. In the left navigation menu, open **Investigate → Failures** to view detailed breakdowns.

   ![](./media/C7.png)

---

# Summary
In this lab, you:

- Created a web app with Application Insights enabled  
- Configured autoinstrumentation at the service level  
- Built and deployed a Blazor application  
- Viewed telemetry, errors, and performance data in Application Insights  

## You have successfully completed the lab.
