# ConferenceAPI
Substitute for the former conference API web app used in Microsoft Learn courses (e.g. AZ-204 APIM)

## Conference API

The Conference API is an ASP.NET Core Web API designed to manage sample conference data items such as sessions, speakers, and topics. This API is inspired by the original ConferenceAPI web app used in Microsoft Learn modules, which is no longer available.

### Key Features

- **Swagger/OpenAPI Integration**: The API is configured with Swagger/OpenAPI to provide an interactive UI for exploring and testing the endpoints.
- **Minimal APIs**: The API uses minimal APIs to define routes and return data from JSON files.
- **Data Management**: The API reads data from JSON files and provides endpoints to retrieve sessions, speakers, and topics.

### Endpoints

- **Sessions**
  - `GET /sessions`: Retrieves a list of all sessions.
  - `GET /session/{id}`: Retrieves a specific session by its ID.
- **Speakers**
  - `GET /speakers`: Retrieves a list of all speakers.
  - `GET /speaker/{id}`: Retrieves a specific speaker by their ID.
- **Topics**
  - `GET /topics`: Retrieves a list of all topics.
  - `GET /topics/{id}`: Retrieves a specific topic by its ID.

### Data Structure

The data is structured in JSON files and mapped to the following classes:

- **Session**
  - `session_id`: The unique identifier for the session.
  - `title`: The title of the session.
  - `timeslot`: The timeslot for the session.
  - `speaker`: The speaker of the session.
  - `description`: A brief description of the session.
- **Speaker**
  - `speakerID`: The unique identifier for the speaker.
  - `name`: The name of the speaker.
- **Topic**
  - `topicid`: The unique identifier for the topic.
  - `topicvalue`: The value or name of the topic.

### Getting Started

To run the API, ensure you have .NET 8 installed. You can start the application using Visual Studio or the .NET CLI. The Swagger UI will be available at `/swagger` for easy exploration of the API endpoints.

## Publishing the API App to Azure App Services

Follow these steps to publish the Conference API to Azure App Service:

### Prerequisites

- An active Azure subscription.
- .NET 8 SDK installed.
- Visual Studio or VS Code installed with the Azure development workload.

### Step 1: Create an Azure App Service

1. Log in to the [Azure Portal](https://portal.azure.com/).
2. Click on "Create a resource" and select "App Service".
3. Fill in the required details:
   - **Subscription**: Select your Azure subscription.
   - **Resource Group**: Create a new resource group or select an existing one.
   - **Name**: Provide a unique name for your App Service.
   - **Publish**: Select "Code".
   - **Runtime stack**: Select ".NET 8". Can either be Windows or Linux for your App Service Plan
   - **Region**: Choose a region close to your users.
4. Click "Review + create" and then "Create".

### Step 2: Publish from Visual Studio

1. Open your ConferenceAPI project in Visual Studio.
2. Right-click the project in Solution Explorer and select "Publish".
3. In the "Pick a publish target" dialog, select "Azure" and click "Next".
4. Select "Azure App Service (Windows)" and click "Next".
5. Select your existing App Service instance created in Step 1 and click "Finish".
6. Click "Publish" to deploy your application to Azure.

### Step 3: Configure the App Service

1. Once the deployment is complete, go to the Azure Portal and navigate to your App Service.
2. In the left-hand menu, select "Configuration".
3. Add any necessary application settings or connection strings required by your application.
4. Save the changes and restart the App Service if needed.

### Step 4: Verify the Deployment

1. Navigate to the URL of your App Service **adding the Swagger UI to the path ** (e.g., `https://<your-app-service-name>.azurewebsites.net/swagger/index.html`).
2. Ensure that the Swagger UI is accessible at `/swagger/index.html` and that the API endpoints are functioning correctly.
3. If you want to connect to the data JSON dataset directly, browse to the `/data` path in the URL (e.g., `https://<your-app-service-name>.azurewebsites.net/sessions` or /speakers or /topics directly).

### Additional Resources

- [Azure App Service Documentation](https://docs.microsoft.com/en-us/azure/app-service/)
- [Deploy an ASP.NET Core app to Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/quickstart-dotnetcore)

By following these steps, you should be able to successfully publish your Conference API to Azure App Service.

## Screenshots of the Solution

Here are some screenshots after the app got deployed to Azure App Service

#### SwaggerUI
![Swagger UI](/images/SwaggerUI.png)

#### Speakers
![Speakers](/images/Speakers_Endpoint.png)

#### Topics
![Topics](/images/Topics_Endpoint.png)

#### Sessions
![Sessions](/images/Sessions_Endpoint.png)

#### Sessions filter by id
![Sessions filter by id](/images/Session_id_Endpoint.png)

#### SwaggerUI - Try It Out
![Swagger UI - Try It Out](/images/SwaggerUI_TryOut_Speakers.png)