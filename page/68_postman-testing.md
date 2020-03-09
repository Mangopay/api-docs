# Testing MANGOPAY API with Postman
>Test the MANGOPAY API  calls in seconds. 

[alert type="info"] In order to test the API you will have to create a [MANGOPAY sandbox account](https://www.mangopay.com/start/)  [/alert]

### What is Postman?

Postman is an app for easy RESTful API exploration.  It allows you to test API calls without writing the code or installing the SDKs. 


### Step 1: Get the Postman collection

Visit [https://www.getpostman.com/](https://www.getpostman.com/) and install the preferred version for your system.

Get the **full MANGOPAY API library**

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/82ebbb72db2de02b6ed0)


### Step 2: Create your Postman environment

Our collection makes use of Postman's environment variables to easily manage your API credentials. Start by creating a sandbox environment.

1. Open the "Environment options" panel by clicking on the gear icon, then click **Manage Environments.** To create a new environment, click **Add**.
2. Name your environment something that indicates it is using sandbox credentials, for example "MANGOPAY Sandbox".
3. Add a variable/value pair with "CLIENT_ID" as the variable and your client ID as the value.
4. Add a variable/value pair with "API_KEY" as the variable and your api key as the value.
5. Add a variable/value pair with "SERVER_URL" as the variable and "https://api.sandbox.mangopay.com" as the value.
6. Add a variable/value pair with "VERSION" as the variable and "V2.01" as the value.
5. When you are finished adding variable/value pairs, click Add. Now, any test calls you make using this environment will automatically fill in the `CLIENT_ID` , `SERVER_URL`,  `VERSION`, `API_KEY` with your sandbox credentials.


### Step 3: Send a call to create your first user

Send a call to create your first user using your sandbox environment.

1. Click the dropdown menu next to the gear icon and choose your sandbox environment from the menu.
2. Open the  collection then click on create “natural” user under the **0.2 Users folder.**
3. Click “Send”. Postman will use your Basic Auth credentials to make the call.


### Marketplace light collection

Click the Run in Postman button below to open Postman and import the **light collection ** for a MANGOPAY **Marketplace** .

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/c8f5f08b69a16a340ce7)

### Crowdfunding light collection

Click the Run in Postman button below to open Postman and import the **light collection ** for a MANGOPAY **Crowdfunding** .

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/63ed350ee7d050fc45c2)