---
id: baseprojectsetup
title: Base Project SetUp
---

In this tutorial, we will walk through the process of setting up a ui project using Next.js, a popular React framework, while integrating it with Nexus, a private repository for Node packages. We'll cover essential steps such as project initialization, folder structure, styles, components, GraphQL setup, and more. This guide is aimed at developers looking to create a base project environment.

## Prerequisites

- Install nvm (node version manager) from [here](https://github.com/coreybutler/nvm-windows/releases).
- Using nvm, install node **16.x** and node **18.x** (E.g nvm install 16.20.0).
- **Node 16** is used for the **ui application** and the **ui library (core-components).**
- **Node 18** is used for **diep2-service(backend).**

## UI SetUp using NEXTJS

### NextJS

**UI Project is based on react framework NextJS.**

**Reason for using NextJs:**

- File based routing.
- Supports environment variables.
- Supports [Linting](<https://en.wikipedia.org/wiki/Lint_(software)>)

For information refer to this article: [NEXTJS](../prerequisites/reactandnextjs)

### Project Initialization

- Create a folder and open it in VS code.
- Open terminal **(ctrl + `)**
- Write command **npx create-next-app@latest**
- Select following configuration as shown below:

> ![Project_Initialization_Img](../../static/img/docs/baseprojectsetup/bps-1.png)

This will be the folder structure after successful installation:

> ![Project_Initialization_Img](../../static/img/docs/baseprojectsetup/bps-2.png)

### Nexus Setup

This is required to use node packages that are stored in nexus (private repository), e.g @cogitate/diep2-components-core.

**Run following commands in terminal:**

1. npm login --registry=<https://nexus.cogitate.us/repository/npm-private/>
2. Enter cogitate LDAP login
   - **username** : abhatt
   - **password** : YOUR_PASSWORD
3. Enter your email ID
4. After successful login, It will create a **.npmrc** file, on windows it’s at **C >users > your_user > .npmrc**

> ![Nexus_Setup_Img](../../static//img/docs/baseprojectsetup/bps-3.png)

5. Open .npmrc file and append following lines @cogitate:registry=[https://nexus.cogitate.us/repository/npm-private/ ](https://nexus.cogitate.us/repository/npm-private/)
   registry=<https://registry.npmjs.org/>
   email=**YOUR_EMAIL_ID**

**_Above instruction instructs npm to initially access a private repository on Nexus and then proceed to the third-party repository._**

### Folder Structure

1. **Styles**:

> ![Styles](../../static/img/docs/baseprojectsetup/bps-4.png)

- **style.scss**:-<br/>
  Main file that contains custom styling of pages other than bootstrap classes.
- **font.scss**:-<br/>
  Define font styles here.
- **images.scss**:-<br/>
  Paths of images used throughout the application are defined here.
- **responsive.scss**:-<br/>
  All responsive styling here.
- **variables.scss**:-<br/>
  All the variables like backgroundColor, color, font related properties used throughout styles are defined here.

2. **Pages**:-<br/>
   Structure we follow to define pages:<br/>
   **pages -> line -> line of business(LOB) -> business flow -> react component/page** <br/>
   **For example**: If line is **commercial**, LOB is **auto** and flow is **application** then folder structure inside page will be as shown in figure:

   > ![Components](../../static//img/docs/baseprojectsetup/bps-5.png)

3. **Components**:
   All reusable react components are defined here.

4. **Store**:
   Redux store for temporary storage of data.

Refer this article for more information [Folder Structure](../diep2/ui#folder-structure)

### Install Necessary Packages

**List of necessary packages are as follows:**

```json
"dependencies": {
    "@apollo/client": "^3.5.9",
    "@azure/storage-blob": "^12.10.0",
    "@cogitate/diep2-components-core": "^1.1.37",
    "@cogitate/ui-utils-core": "^1.0.12",
    "@fortawesome/fontawesome-svg-core": "^1.3.0",
    "@fortawesome/free-regular-svg-icons": "^6.0.0",
    "@fortawesome/free-solid-svg-icons": "^6.2.1",
    "@fortawesome/react-fontawesome": "^0.1.17",
    "@microsoft/applicationinsights-react-js": "^3.3.4",
    "@microsoft/applicationinsights-web": "^2.8.3",
    "@reduxjs/toolkit": "^1.7.2",
    "axios": "^0.26.0",
    "bootstrap": "^5.1.3",
    "chart.js": "^3.7.1",
    "deep-diff": "^1.0.2",
    "deps": "^1.0.0",
    "graphql": "^16.3.0",
    "history": "^5.3.0",
    "install": "^0.13.0",
    "jsonwebtoken": "^8.5.1",
    "moment": "^2.29.4",
    "next": "^13.0.6",
    "npm": "^8.5.3",
    "nprogress": "^0.2.0",
    "react": "^18.2.0",
    "react-bootstrap": "^2.2.0",
    "react-bootstrap-table-next": "^4.0.3",
    "react-bootstrap-table2-paginator": "^2.1.2",
    "react-bootstrap-table2-toolkit": "^2.1.3",
    "react-chartjs-2": "^4.1.0",
    "react-datetime-picker": "^4.1.1",
    "react-dom": "^18.2.0",
    "react-error-boundary": "^3.1.4",
    "react-google-places-autocomplete": "^3.3.4",
    "react-loader-spinner": "^6.0.0-0",
    "react-redux": "^7.2.6",
    "react-select": "^5.6.0",
    "react-toastify": "^8.2.0",
    "read-excel-file": "^5.2.28",
    "redux-persist": "^6.0.0",
    "redux-persist-transform-encrypt": "^3.0.1",
    "sass": "^1.49.8",
    "uuidv4": "^6.2.13"
  },
```

**Note**: To install this packages use `npm install --legacy-peer-deps`

**_Here, --legacy-peer-deps flag ignores compatibility of the various packages ( ignore all peerDependencies when installing)_**

### Setting Environment Variables

- **Copy .env files from any existing application.**

**List of env variables are as follows:**

<table>
<tr><th colspan="1"><b>Variable</b></th><th colspan="1"><b>Type</b></th><th colspan="1"><b>Description</b></th></tr>
<tr><td colspan="1" valign="top"><b>NEXT_PUBLIC_GQL_END_POINT</b></td><td colspan="1" valign="top">API</td><td colspan="1">GraphQL endpoint to query and mutate data.</td></tr>
<tr><td colspan="1" valign="top"><b>NEXT_PUBLIC_PROXY_GQL_END_ POINT</b></td><td colspan="1" valign="top">API</td><td colspan="1"><p>Proxy GraphQL endpoint to query and mutate data.</p><p><b>Not required for every application</b>.</p></td></tr>
<tr><td colspan="1" valign="top"><b>NEXT_PUBLIC_TEMPLATE_URL</b></td><td colspan="1" valign="top">API</td><td colspan="1">Provides HTML or PDF which is sent as a part of notification.</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_SCHEMA_URL</b></td><td colspan="1">API</td><td colspan="1">Endpoint to get ui schema stored on blob.</td></tr>
<tr><td colspan="1" rowspan="2" valign="top"><b>NEXT_PUBLIC_JSON_END_POINT</b></td><td colspan="1" rowspan="2" valign="top">API</td><td colspan="1" valign="bottom">[Adaptive api endpoint](https://uatapps.cogitate.us/diep-docs/docs/diep2/adaptiveapi#components-of-adaptive-api)</td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1" valign="top"><b>NEXT_PUBLIC_SSO_URL</b></td><td colspan="1" valign="top">API</td><td colspan="1" valign="top">Endpoint that returns jwt token on valid username and password.</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_DMS_API_BASE_U RL</b></td><td colspan="1" valign="top">API</td><td colspan="1" valign="top">DMS endpoint</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_FORM_FACTORY_API_AUTHURL, 
NEXT_PUBLIC_FORM_FACTORY_API_URL, 
NEXT_PUBLIC_FORM_FACTORY_LCNC_API_URL</b></td><td colspan="1" valign="top">API</td><td colspan="1" valign="top">Formfactory apis</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_FORM_FACTORY_API_USERNAME, 
NEXT_PUBLIC_FORM_FACTORY_API_PASSWORD, 
NEXT_PUBLIC_FORM_FACTORY_API_VALIDATION_METHOD,
NEXT_PUBLIC_FORM_FACTORY_API_TYPE, NEXT_PUBLIC_LOB_FORM_FACTORY
</b></td><td colspan="1" valign="top">Keys</td><td colspan="1" valign="top">Keys required to access Formfactory.</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_CLIENT</b></td><td colspan="1" valign="top">Keys</td><td colspan="1" valign="top">Client name, used as a relative path for accessing endpoints.</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_DEFAULT_LINE, 
NEXT_PUBLIC_DEFAULT_STATE,
 NEXT_PUBLIC_LINE_OF_BUSINESS
</b></td><td colspan="1" valign="top">Keys</td><td colspan="1" valign="top">Keys required for fetching ui schema. These are passed as parameters to NEXT_PUBLIC_SCHEMA_URL endpoint</td></tr>
<tr><td colspan="1"><b>NEXT_PUBLIC_PRODUCT_ID, <br/>
NEXT_PUBLIC_SITE_ID</b></td><td colspan="1" valign="top">Keys</td><td colspan="1" valign="top">Keys passed as parameters to the SSO endpoint. NEXT_PUBLIC_SSO_URL</td></tr>
</table>

**Various .env used in ui applications are:**
- .env.local
- .env.base.test
- .env.base.uat
- .env.base.prod


- **Copy copyEnvFile.js**. **file from any existing application.**

All these .**env.base** file contents are copied into .**env.local** before build using **copyEnvFile** function defined inside **copyEnvFile.js**. This is necessary because NEXTJS supports only three environments: local, development, and production.

***Note: Custom envs can be created, but every env must be prefixed with NEXT\_PUBLIC. Refer this article for more information [Bundling Environment Variables for the Browser](https://nextjs.org/docs/pages/building-your-application/configuring/environment-variables#bundling-environment-variables-for-the-browser)***


### Configuration of .next.config.js 

- **Override your next.config.js with the following:**

```json
module.exports = {
  reactStrictMode: false, // prevents react from rendering twice
  trailingSlash: true, // it will automatically append ‘/’.
  basePath: process.env.NEXT_PUBLIC_BASE_PATH || '',  // base url
  assetPrefix: process.env.NEXT_PUBLIC_BASE_PATH || '/', // base url with prefix


// redirects when error occurs or when page not found.
  async redirects() {
    return [
        {
            source: '/',
            destination: process.env.NEXT_PUBLIC_BASE_PATH ,
            basePath: false,
            permanent: false
        },
        {
          source: '/500',
          destination: process.env.NEXT_PUBLIC_BASE_PATH + '/500',
          basePath: false,
          permanent: false
        },
        {
          source: '/400',
          destination: process.env.NEXT_PUBLIC_BASE_PATH + '/400',
          basePath: false,
          permanent: false
        }
    ]
  },
  images: {
    loader: 'akamai',
    path: "https://diep2.z13.web.core.windows.net/",
  },
}

```

## Blob SetUp on Azure Portal

**Steps to setup blob in azure container**

1. Open [Azure](https://portal.azure.com/)
2. Get the appropriate credentials and developer access to it from the Infrastructure Team (drop a mail to **Helpdesk Cogitate <helpdesk@cogitate.us>**).
3. On Azure Portal, open **Storage Accounts > ctsdiep2devstorage>Data Storage >Containers>diep2**
4. Here create a blob named **<CLIENT\_NAME>. E.g ROTHERT**
5. You cannot create a blob on the portal,instead download **Azure Storage Explorer** from [here.](https://azure.microsoft.com/en-us/products/storage/storage-explorer)
   - **Follow the steps to setUp storage locally:**
       1. Open **Azure Storage Explorer** and click on ![](../../static/img/docs/baseprojectsetup/bps-6.png) from the side menu.
       2. Select
        >![](../../static/img/docs/baseprojectsetup/bps-7.png)
       3. On Azure Portal,open **Storage Accounts > ctsdiep2devstorage> Data Storage >Containers>diep2>Security and Networking>Access Keys,** copy connection string.
        >![](../../static/img/docs/baseprojectsetup/bps-8.png)
        4. Paste it in the connection string section of **Azure Storage Explorer.** Once setUp is done,you will be able to view the storage account.
        5. Right Click on any existing blob E.g Rothert,click on Clone and name it.
        6. This will be the folder structure after clone:
        >![](../../static/img/docs/baseprojectsetup/bps-9.png)
        7. Update the flow inside each of this folders accordingly.
    - **Folder Structure**
        1. **Schema:-**
        - Contains all the schema used throughout the application.
        - **UISchemaList.js** contains an array of flows,with each flow containing an array of pages with **PageName(route in ui) and path(path to .json file)** property. This is used by ui fetcher api. **Note:All the pages in ui that use schema rendering must have entry in this file.**
        - Update your .env variables according to the path of the schema.
        E.g: if blob path is ![](../../static/img/docs/baseprojectsetup/bps-11.png) then
        >![](../../static/img/docs/baseprojectsetup/bps-10.png)
        2. **model:-**
            Contains policy model(../diep2/PolicyModelSchema).
        3. **Template:-**
            Contains email and other template files.
        4. **Configs:-**
            Contains **hook schema, uw rules, graphql type defs and otherconfig files**.


## DIEP2-Service(GraphQL) SetUp

### Setting Pipeline for diep2-service

**Note:**This setup can only be done by a user with **Admin** access.
1. Open [Jenkins.](https://jenkins.cogitate.us/)
2. Click on the DIEP tab.
3. Click on ![](../../static/img/docs/baseprojectsetup/bps-12.png) from the side menu.
4. Give name to the Pipeline and select **Pipeline** from the list below and click **OK**.
5. Keep all the configurations default and click **Pipeline Tab.**
6. Copy the following code inside script:
>![](../../static/img/docs/baseprojectsetup/bps-13.png)
7. Update the jenkins json path according to your project and click **Save**.
8. Jenkins will pull code from gitProjectURL [here.](https://git.cogitate.us/diep2/services/diep2-service.git)

### Setting Azure Function App for diep2-service

1. Open [Azure Portal.](https://portal.azure.com/)
2. Search for a **Function App.**
3. Click ![](../../static/img/docs/baseprojectsetup/bps-14.png).
4. Select following configuration:
>![](../../static/img/docs/baseprojectsetup/bps-15.jpeg)
5. Provide an appropriate name to your function app.
6. Select following configuration for **Storage**:
>![](../../static//img/docs/baseprojectsetup/bps-16.png)
7. Default Networking Configuration.
8. Select following configuration for **Monitoring**:
>![](../../static//img/docs/baseprojectsetup/bps-17.png)
9. Rest all configurations are default.
10. Click on ``Create``.

Note: To automatically create a Function App follow [here](#how-to-automatically-create-azure-function-app-using-jenkins-pipeline)

### Setting jenkins.json for diep2-service

1. Copy the jenkins.json file from [here.](https://git.cogitate.us/diep2/services/configuration-services.git)
1. Update **deploymentPath, git\_project\_id, redmine\_project\_id, and develop, uat, test, and prod** objects accordingly.

### Additional Settings on Azure Function App

1. Update cors settings as follows:
    >![](../../static/img/docs/baseprojectsetup/bps-18.jpeg)

2. **Identity** settings for **Function App:**
    - Open the function app previously created.
    - Search for identity from the side menu and click on it.
        >![](../../static//img/docs/baseprojectsetup/bps-19.png)
    - Click on **UserAssigned** and click ![](../../static//img/docs/baseprojectsetup/bps-20.png).
    - Select necessary configuration and click **Add.**
    - This allows Function App to use other storage account resources.

### Configuring diep2-service on Local Machine (Imp)

1. Clone **diep2-service** from [here.](https://git.cogitate.us/diep2/services/diep2-service.git)
2. Before installation of node packages,following configuration need to be done:
    - Install **node 18.x .**
    - Install **python 3.7** (for some system **python 2.x** might need to be installed)
    - Install following packages in **Visual Studio Installer.**
      - **Desktop Development for C++**
      - **C#**
    - Add **nodejs** path to **system variables** if not already present.
    - Open cmd and run **npm i -g azure-functions-core-tools.**
3. After the above steps,run **npm install** in vs code terminal to install necessary packages defined in diep2-service.
4. Install azure cli from [here.](https://aka.ms/installazurecliwindows)
5. Upon successful installation of azure cli, run **az login** in the terminal.
6. Select your azure account on the popup window.
7. After the above steps,run **npm start,** your diep2-service will be running.
8. **Errors you might face:**
    - **Node-gyp error:**
       - Refer to this article: [Node-Gyp-Error.](https://stackoverflow.com/questions/33896511/npm-install-fails-with-node-gyp)
    - **func is not recognized:**
       - Use **npm i -g azure-functions-core-tools**
    - **cannot-be-loaded-because-running-scripts-is-disabled-on-this-system-for-more-in**
      - Open **powershell** as administrator and run following commands:
        - **Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted**
        - **Get-ExecutionPolicy**


## FAQs

### How to start with a project?

- Create Data Model [E.g Policy Model](diep2/PolicyModelSchema)
- Based on Data Model define Graphql Type Defs
- Store this typedefs file into blob storage.**(as this will not change frequently)**.
- Generate Queries and Mutation from this typedefs file.
- These queries and mutations are then stored in the application itself inside queries and fragments file as follows:
 > ![](../../static//img/docs/baseprojectsetup/bps-21.png)

### How to generate TypeDefs from a Data Model?

1. To generate typedefs from policy models use the [Typedef generator ](https://git.cogitate.us/diep2/modules/diep2-typedefgenerator.git)utility.
2. Clone the utility and run **node typeDefGenerator.js.**
3. **GraphQLSchema.graphql** will be generated.
4. Just replace **AutogeneratedMainType** with **Policy** in **GraphQLSchema.graphql.**
5. Copy the file in your blob (**storageaccount>ctsdevdiep2storage>diep2>YOUR\_APP\_NAME >configs**).

### How to get queries & mutations from typedef?

- Open this url <https://devtogagraphql.azurewebsites.net/api/policygraphql?>.<br/> 
**(This url is just for reference purpose, it is application specific)**
- Click on Query Server.
- You will see following interface:
  >![](../../static//img/docs/baseprojectsetup/bps-26.jpeg)
- For generating queries click on Query ![](../../static//img/docs/baseprojectsetup/bps-27.png)
- Select any endpoint inside query for example ![](../../static//img/docs/baseprojectsetup/bps-22.png)
- Inside ![](../../static//img/docs/baseprojectsetup/bps-22.png)  select various fields that you want to query for example: 
  >![](../../static//img/docs/baseprojectsetup/bps-23.png)
- This will create following query:
  >![](../../static//img/docs/baseprojectsetup/bps-24.png)
- **For automatic generation of queries select drop down beside Fields as shown in the figure:**
  >![](../../static//img/docs/baseprojectsetup/bps-25.png)

For more information about queries and fragment refer [Queries&Fragments](../diep2/apis)

### How to fetch Schema from blob and store it in Redux?

1. Follow above steps to setup ui and blob.
2. In ui,all the schemas stored on blob are fetched when a user successfully logs in.
3. Use **fetchUISchema** function to fetch schemas from blob.
  ```
  fetchUISchema(
    process.env.NEXT_PUBLIC_CLIENT,
    process.env.NEXT_PUBLIC_DEFAULT_LINE,
    process.env.NEXT_PUBLIC_LINE_OF_BUSINESS,
    process.env.NEXT_PUBLIC_DEFAULT_STATE.toLowerCase(),
    [flowKeys.Quote.toLowerCase(),flowKeys.Application.toLowerCase()],
    process.env.NEXT_PUBLIC_DEFAULT_VERSION.toLowerCase()
  )
  ```
4. Once schema is in redux,use loadSchemafromblob
  ```
    loadSchemaFromStorage(
      process.env.NEXT_PUBLIC_DEFAULT_LINE,
      process.env.NEXT_PUBLIC_LINE_OF_BUSINESS,
      process.env.NEXT_PUBLIC_DEFAULT_STATE.toLowerCase(),
      process.env.NEXT_PUBLIC_DEFAULT_VERSION.toLowerCase(),
      flowKeys.Endorsement.toLowerCase(),
      routeKeys.EndorsementLanding // page to load
    )
  ```
5. Store the result in react state and pass it into **dynamic form** imported from **diep2-components-core**.

### How to save data for each page?

1. Use save method
  ```
  save(MODEL, ACTION, REQUESTED_PAGE, CALLBACK_PAGE, PROGRESS_INDEX, NEED_PROXY);
  ```
2. **MODEL** is the policy model to save.
3. **ACTION** can be Rate,updatePolicyStatus,Bind,etc. **Default is UpdatePolicy**.


### How to automatically create Azure Function App using Jenkins Pipeline?

1. Open [Jenkins.](https://jenkins.cogitate.us/)
2. Click on the **Automation** tab.
3. Click on ![](../../static/img/docs/baseprojectsetup/bps-12.png) from the side menu.
4. Give name to the Pipeline and select **Pipeline** from the list below.
5. Below you will see Copy from input box, Enter the pipeline name from where you can copy configuration as shown in below image:
>![](../../static/img/docs/baseprojectsetup/bps-29.png)
6. Click **OK**.
7. Add following configuration if not already loaded.
>![](../../static/img/docs/baseprojectsetup/bps-28.png)
8. Update **jsonFileUrl** -> From here pipeline will load settings file that has configuration of Function App.
9. Update **jsonFilePath** -> Path in above repository where the settings fileis stored.

## Tutorial Links

1. [Tutorial 1 - UI Setup - Nexus SetUp, Folder Structure, How to Start with Project?](https://cogitatetech.sharepoint.com/:v:/r/sites/CogitateSharePoint2/Shared%20Documents/Technical%20Operations%20%26%20Delivery/KT%20Videos/DIEP%202.0%20Training/DIEP%202.0%20Base%20Project%20Setup%20-%20KT-20230405_170557-Meeting%20Recording.mp4?csf=1&web=1&e=w0icrX&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZyIsInJlZmVycmFsQXBwUGxhdGZvcm0iOiJXZWIiLCJyZWZlcnJhbE1vZGUiOiJ2aWV3In19)
2. [Tutorial 2 - Blob SetUp - Configuration, Blob Structure, Redux](https://cogitatetech.sharepoint.com/:v:/r/sites/CogitateSharePoint2/Shared%20Documents/Technical%20Operations%20%26%20Delivery/KT%20Videos/DIEP%202.0%20Training/DIEP%202.0%20Base%20Project%20Setup%20-%20KT-20230406_074140-Meeting%20Recording.mp4?csf=1&web=1&e=3LQLzt&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZyIsInJlZmVycmFsQXBwUGxhdGZvcm0iOiJXZWIiLCJyZWZlcnJhbE1vZGUiOiJ2aWV3In19)
3. [Tutorial 3 - General - TypeDef Generator and More](https://cogitatetech.sharepoint.com/:v:/s/CogitateSharePoint2/Ee6jnc34yENJpw2QiRw88YcB5tiRYXxNzubBKZEJmWVPog?e=cbqPwe&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZyIsInJlZmVycmFsQXBwUGxhdGZvcm0iOiJXZWIiLCJyZWZlcnJhbE1vZGUiOiJ2aWV3In19)
3. [Tutorial 4 - Service SetUp](https://cogitatetech.sharepoint.com/:v:/s/CogitateSharePoint2/EUWtEzMBt2hCiIu8x-jT_Q0BCfnxtwJTw181Wl7luO3TCQ?e=w0LjHT&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZyIsInJlZmVycmFsQXBwUGxhdGZvcm0iOiJXZWIiLCJyZWZlcnJhbE1vZGUiOiJ2aWV3In19)