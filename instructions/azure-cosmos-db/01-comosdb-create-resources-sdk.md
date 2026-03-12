# Lab 06: Create resources in Azure Cosmos DB for NoSQL using .NET

## Lab Overview

In this exercise, you create an Azure Cosmos DB account and build a .NET console application that uses the Microsoft Azure Cosmos DB SDK to create a database, container, and sample item. You learn how to configure authentication, perform database operations programmatically, and verify your results in the Azure portal.

## Lab Objectives

In this lab, you will perform:

- **Exercise 1:** Create Azure Cosmos DB resources  
- **Exercise 2:** Build a .NET console application to interact with Cosmos DB  
- **Exercise 3:** Run the application and verify results  

## Estimated Timing: 30 Minutes

## Exercise 1: Create resources in Azure Cosmos DB for NoSQL using .NET

### Task 1: Create an Azure Cosmos DB account

1. Open **Cloud Shell**, choose **Bash**, select **No storage account required (1)**, choose the available **Subscription (2)**, and select **Apply (3)**.

   ![](./media/A01.png)
   ![](./media/A02.png)
   ![](./media/A03.png)

2. Switch to **Classic version** in Cloud Shell.

   ![](./media/E9.png)

3. Create variables to store the resource group name and a unique Cosmos DB account name.

    ```bash
    resourceGroup=CosmosDB-<inject key="DeploymentID" enableCopy="false"/>
    accountName=cosmosexercise$RANDOM
    ```

4. Create the Azure Cosmos DB account.

    ```bash
    az cosmosdb create --name $accountName --resource-group $resourceGroup
    ```

5. Copy the **Azure Cosmos DB account endpoint** displayed in the output and paste it into a text editor (such as Notepad), as it will be required in the upcoming steps.

    ```bash
    az cosmosdb show --name $accountName --resource-group $resourceGroup   --query "documentEndpoint" --output tsv
    ```

6. Retrieve the **primary access key** for the Azure Cosmos DB account, as it will be used in the upcoming steps.

    ```bash
    az cosmosdb keys list --name $accountName --resource-group $resourceGroup   --query "primaryMasterKey" --output tsv
    ```    
    ![](./media/E2.png)

## Exercise 2: Build a .NET console application to interact with Cosmos DB

### Task 1: Create the .NET console application

1. Create a project folder and navigate into it.

    ```bash
    mkdir cosmosdb
    cd cosmosdb
    ```

2. Create a new .NET console application.

    ```bash
    dotnet new console
    ```

3. Add the required NuGet packages.

    ```bash
    dotnet add package Microsoft.Azure.Cosmos --version 3.*
    dotnet add package Newtonsoft.Json --version 13.*
    dotnet add package dotenv.net
    ```
### Task 2: Configure environment variables and application code

1. Create and open a `.env` file.

    ```bash
    touch .env
    code .env
    ```

2. Add the **Azure Cosmos DB account endpoint** and **account key** that were copied in the previous tasks to the application configuration.

    ```text
    DOCUMENT_ENDPOINT="YOUR_DOCUMENT_ENDPOINT"
    ACCOUNT_KEY="YOUR_ACCOUNT_KEY"
    ```

3. Replace the contents of **Program.cs** with the provided template and add the required implementation code.

    ![](./media/E4.png)

### Task 3 Add required implementation code

1. Insert the following code blocks into **Program.cs** at the appropriate locations.
The code provides the overall structure of the app. Review the comments in the code to get an understanding of how it works. To complete the application, you add code in specified areas later in the exercise. 

    ```csharp
    using Microsoft.Azure.Cosmos;
    using dotenv.net;
    
    string databaseName = "myDatabase"; // Name of the database to create or use
    string containerName = "myContainer"; // Name of the container to create or use
    
    // Load environment variables from .env file
    DotEnv.Load();
    var envVars = DotEnv.Read();
    string cosmosDbAccountUrl = envVars["DOCUMENT_ENDPOINT"];
    string accountKey = envVars["ACCOUNT_KEY"];
    
    if (string.IsNullOrEmpty(cosmosDbAccountUrl) || string.IsNullOrEmpty(accountKey))
    {
        Console.WriteLine("Please set the DOCUMENT_ENDPOINT and ACCOUNT_KEY environment variables.");
        return;
    }
    
    // CREATE THE COSMOS DB CLIENT USING THE ACCOUNT URL AND KEY
    
    
    try
    {
        // CREATE A DATABASE IF IT DOESN'T ALREADY EXIST
    
    
        // CREATE A CONTAINER WITH A SPECIFIED PARTITION KEY
    
    
        // DEFINE A TYPED ITEM (PRODUCT) TO ADD TO THE CONTAINER
    
    
        // ADD THE ITEM TO THE CONTAINER
    
    
    }
    catch (CosmosException ex)
    {
        // Handle Cosmos DB-specific exceptions
        // Log the status code and error message for debugging
        Console.WriteLine($"Cosmos DB Error: {ex.StatusCode} - {ex.Message}");
    }
    catch (Exception ex)
    {
        // Handle general exceptions
        // Log the error message for debugging
        Console.WriteLine($"Error: {ex.Message}");
    }
    
    // This class represents a product in the Cosmos DB container
    public class Product
    {
        public string? id { get; set; }
        public string? name { get; set; }
        public string? description { get; set; }
    }
    ```

- Next, you add code in specified areas of the projects to create the: client, database, container, and add a sample item to the container.

1.  Create the Cosmos DB client

- In this step, you create a Cosmos DB client using the account endpoint and access key.

   ```csharp
   CosmosClient client = new(
      accountEndpoint: cosmosDbAccountUrl,
      authKeyOrResourceToken: accountKey
   );
   ```

2. Create database

- In this step, you create a database in Azure Cosmos DB that will be used to store containers and items for the application.

   ```csharp
   Database database = await client.CreateDatabaseIfNotExistsAsync(databaseName);
   Console.WriteLine($"Created or retrieved database: {database.Id}");
   ```

3. Create container

- In this step, you create a container within the database to store application items using a specified partition key.

   ```csharp
   Container container = await database.CreateContainerIfNotExistsAsync(
      id: containerName,
      partitionKeyPath: "/id"
   );
   Console.WriteLine($"Created or retrieved container: {container.Id}");
   ```

4. Define product item

- In this step, you define a sample item that will be inserted into the Cosmos DB container.

   ```csharp
   Product newItem = new Product
   {
      id = Guid.NewGuid().ToString(),
      name = "Sample Item",
      description = "This is a sample item in my Azure Cosmos DB exercise."
   };
   ```

5. Add item to container

- In this step, you add the sample item to the Cosmos DB container and review the request charge.

   ```csharp
   ItemResponse<Product> createResponse = await container.CreateItemAsync(
      item: newItem,
      partitionKey: new PartitionKey(newItem.id)
   );

   Console.WriteLine($"Created item with ID: {createResponse.Resource.id}");
   Console.WriteLine($"Request charge: {createResponse.RequestCharge} RUs");
   ```
### Task 4 Verify the complete Program.cs code

- Save the file using **Ctrl + S**, then exit the editor using **Ctrl + Q**.

- Now that the code is complete. Verify it with below code, save your progress use **ctrl + s** to save the file, and **ctrl + q** to exit the editor.

    ```
    using Microsoft.Azure.Cosmos;
    using dotenv.net;

    string databaseName = "myDatabase"; // Name of the database to create or use
    string containerName = "myContainer"; // Name of the container to create or use

    // Load environment variables from .env file
    DotEnv.Load();
    var envVars = DotEnv.Read();
    string cosmosDbAccountUrl = envVars["DOCUMENT_ENDPOINT"];
    string accountKey = envVars["ACCOUNT_KEY"];

    if (string.IsNullOrEmpty(cosmosDbAccountUrl) || string.IsNullOrEmpty(accountKey))
    {
        Console.WriteLine("Please set the DOCUMENT_ENDPOINT and ACCOUNT_KEY environment variables.");
        return;
    }

    // CREATE THE COSMOS DB CLIENT USING THE ACCOUNT URL AND KEY
    CosmosClient client = new(
        accountEndpoint: cosmosDbAccountUrl,
        authKeyOrResourceToken: accountKey
    );

    try
    {
        // CREATE A DATABASE IF IT DOESN'T ALREADY EXIST
        Database database = await client.CreateDatabaseIfNotExistsAsync(databaseName);
        Console.WriteLine($"Created or retrieved database: {database.Id}");

        // CREATE A CONTAINER WITH A SPECIFIED PARTITION KEY
        Container container = await database.CreateContainerIfNotExistsAsync(
            id: containerName,
            partitionKeyPath: "/id"
        );
        Console.WriteLine($"Created or retrieved container: {container.Id}");

        // DEFINE A TYPED ITEM (PRODUCT) TO ADD TO THE CONTAINER
        Product newItem = new Product
        {
            id = Guid.NewGuid().ToString(), // Generate a unique ID for the product
            name = "Sample Item",
            description = "This is a sample item in my Azure Cosmos DB exercise."
        };

        // ADD THE ITEM TO THE CONTAINER
        ItemResponse<Product> createResponse = await container.CreateItemAsync(
            item: newItem,
            partitionKey: new PartitionKey(newItem.id)
        );

        Console.WriteLine($"Created item with ID: {createResponse.Resource.id}");
        Console.WriteLine($"Request charge: {createResponse.RequestCharge} RUs");

    }
    catch (CosmosException ex)
    {
        // Handle Cosmos DB-specific exceptions
        // Log the status code and error message for debugging
        Console.WriteLine($"Cosmos DB Error: {ex.StatusCode} - {ex.Message}");
    }
    catch (Exception ex)
    {
        // Handle general exceptions
        // Log the error message for debugging
        Console.WriteLine($"Error: {ex.Message}");
    }

    // This class represents a product in the Cosmos DB container
    public class Product
    {
        public string? id { get; set; }
        public string? name { get; set; }
        public string? description { get; set; }
    }
    ```

    ![](./media/E8.png)

## Exercise 3: Run the application and verify results

### Task 1 : Run the application and verify results

1. Build the application.

   ```bash
   dotnet build
   ```

2. Run the application.

   ```bash
   dotnet run
   ```

1. Sample output:

    ![](./media/E5.png)

### Task 2 Verify the item in Azure Cosmos DB

1. Open the **Azure Portal** and navigate to the resource group  
   **CosmosDB-<inject key="DeploymentID" enableCopy="false"/> (1)**.

   ![](./media/E10.png)

2. Select the **Azure Cosmos DB account (2)**.

   ![](./media/E11.png)

3. Open **Data Explorer (3)**.

   ![](./media/E12.png)

4. Expand **myDatabase (4)** → select **myContainer (5)** → open **Items (6)**  
   to view the created item **(7)**.

   ![](./media/E13.png)

> **Congratulations** on completing the task! Now, it's time to validate it.
<validation step="6035a827-10fe-4abe-9c5f-af88966b9ba3" />

## Summary

In this lab, you:

- Created an Azure Cosmos DB account  
- Built a .NET application that interacts with Azure Cosmos DB  
- Inserted and verified data programmatically using the Azure portal  

## You have successfully completed this lab.
