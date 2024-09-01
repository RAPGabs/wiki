---
id: aim
title: AIM
---

It is a policy management system powered by Vertaforce. It is specifically designed for MGAs and MGUs.It has the following features-
- Centralized underwriting, accounting, and claims operations.Intuitive solution for unique processes and transactions.
- Eliminate duplicate entry.
- Real-time reporting.
- Integrations with industry partners.

Just like other third party api integrations, we have integrated AIM using GraphQl hooks in a plugin.One thing to note here as well as with every other third party API is that we need certain transformations from our policy data model to the one accepted by the respective third party API and also we need to tranform back the response into our policy model.
Hence, for the above steps , we typically use JSONATA transformation engine which we call using Cogitate Adaptive API.
In return, we store a Quote reference number provided by the AIM back into our policy model's External references property.

To utilise the GraphQl plugin for calling third party APIs, we maintain a hook schema on our Azure blob storage. In this , we have a hookSchema(json) file in which we have two main properties: Pre and Post.
These two properties are as per the API calling steps since we may need to call an API before sending it to GraphQL endpoint or after we get a response from the GraphQL endpoint.
Also, we have a property called extra parameters which stores all the static information like Authorization, API link, Header Info ,etc required to call that API.

```
{
  "Client": "Cogitate",
  "Hooks": {
    "Pre": [
      {
        "RequestName": "/Quote/BusinessInfo",
        "NeedCascading": true,
        "StaticParams": {
          "DatabaseId": "pos",
        	"VeriskAdaptiveKey":"49ecd203b39d4243b0baf206db3a82e7",
					"VeriskAdaptiveUrl":"https://adaptiveapiapm.azure-api.net/commercialauto/api/call"
        },
        "Actions": [
          "AddBusinessDetails"
         ]
      },
			{
        "RequestName": "/Quote/CoverageInfo",
        "NeedCascading": true,
        "StaticParams": {
          "UwRulesType":"Rating",
					"UwURL":"https://cogitatemockapi.azure-api.net/CA/RestricitionNew/Invoke"
        },
        "Actions": [
          "ExecuteUnderWritingRules"
         ]
      },
			{
        "RequestName": "/Application/DriverInfo",
        "NeedCascading": true,
        "StaticParams": {
          "UwRulesType":"Rating",
					"UwURL":"https://cogitatemockapi.azure-api.net/CA/RestricitionNew/Invoke"
        },
        "Actions": [
          "ExecuteUnderWritingRules"
         ]
      },
			{
        "RequestName": "/Quote/Summary",
        "NeedCascading": true,
        "StaticParams": {
          "RaterVersionURL": "https://dev.cogitate.us/newrater/api/ratereditor/GetCurrentRaterVersionBasedOnProgram",
          "DatabaseId": "pos",
          "MastersContainerId": "masters"
					
        },
        "Actions": [
          "AddProductDetails",
          "GeneratePolicyNumber",
          "AddRaterDetails"
					
         ]
      },
			{
        "RequestName": "/Commercial/Auto/Quote/BusinessInfo",
        "NeedCascading": true,
        "StaticParams": {
          "DatabaseId": "pos",
        	"VeriskAdaptiveKey":"49ecd203b39d4243b0baf206db3a82e7",
					"VeriskAdaptiveUrl":"https://adaptiveapiapm.azure-api.net/commercialauto/api/call"
        },
        "Actions": [
          "AddBusinessDetails"
         ]
      },
			{
        "RequestName": "/Commercial/Auto/Quote/CoverageInfo",
        "NeedCascading": true,
        "StaticParams": {
          "UwRulesType":"Rating",
					"UwURL":"https://cogitatemockapi.azure-api.net/CA/RestricitionNew/Invoke"
        },
        "Actions": [
          "ExecuteUnderWritingRules"
         ]
      },
			{
        "RequestName": "/Commercial/Auto/Application/DriverInfo",
        "NeedCascading": true,
        "StaticParams": {
          "UwRulesType":"Rating",
					"UwURL":"https://cogitatemockapi.azure-api.net/CA/RestricitionNew/Invoke"
        },
        "Actions": [
          "ExecuteUnderWritingRules"
         ]
      },
			{
        "RequestName": "/Commercial/Auto/Quote/Summary",
        "NeedCascading": true,
        "StaticParams": {
          "RaterVersionURL": "https://dev.cogitate.us/newrater/api/ratereditor/GetCurrentRaterVersionBasedOnProgram",
          "DatabaseId": "pos",
          "MastersContainerId": "masters"
					
        },
        "Actions": [
          "AddProductDetails",
          "GeneratePolicyNumber",
          "AddRaterDetails"
					
         ]
      }
    ],
   "Post": [
      {
        "RequestName": "/Commercial/Auto/Quote/Summary",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Application/Summary",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Endorsement/UpdatedDetails",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Renewal/DriverInfo",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Endorsement/Landing",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Cancel/Landing",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Reinstate/Landing",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      },
			{
        "RequestName": "/Commercial/Auto/Application/DriverInfo",
        "StaticParams": {},
        "NeedCascading": false,
        "Actions": [ 
					"AIMCall"
				]
      }
    ]
  }
}
```