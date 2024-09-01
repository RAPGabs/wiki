---

id: hooks

title: Hooks

---

As mentioned in earlier section, that we can perform certain custom actions on request received.
Hooks are used to execute certain important application logic, like **PolicyNumber generation, AIM Call, Triggering Underwriting rules** etc. form the backend. A particular configuration file is used to execute all these hooks. A brief example of hook configuration is as below.

**Note**:- For every Hook to execute following things are needed:-
1. The request should contain "Mutation" keyword
2. The RequestName should match, 
3. The Action should exist in Actions arrays
4. The required parameters should be present in **StaticParams**

```bash
{
  "Client": "Cogitate",
  "Hooks": {
    "Pre": [
      {
        "RequestName": "/Commercial/Auto/Quote/BusinessInfo",
        "NeedCascading": true,
        "StaticParams": {
          "DatabaseId": "pos",
          "VeriskAdaptiveKey": "49ecd203b39d4243b0baf206db3a82e7",
          "VeriskAdaptiveUrl": "https://adaptiveapiapm.azure-api.net/commercialauto/api/call",
					"MastersContainerId": "masters"
        },
        "Actions": [
					"AddProductDetails",
          "GenerateQuoteNumber"
        ]
      }
    ],
    "Post": [
    ]
  }
}
```

## Types of Hooks
We have used two types of Hooks here: Pre Hook and Post Hook.
### 1. Pre Hooks
These are used to perform some operation on received request object prior to giving it to to requested resolver for any operation.
Like AddProductDetails, GenerateQuoteNumber, AddRaterDetails, ExecuteUnderWritingRules, GeneratePolicyNumber, HandleTransactionNumber etc.
### 2. Post Hooks
These are used to perform some operation on response object from the resolver, the value received in the actions defined in it is updated into Policy object along with the next request that is received. Some example of these are AIMCall, GeneratePolicyDocuments, TrigerNotifications. Basically all those tasks which does not need to be immediately updated in the policy object before next use can be kept in Post hooks.

### Hook Configuration Parameters
1. **RequestName**:- This is triggering condition which is used to start any hook block
2. **Actions**:- Array of Actions user want to execute when the particular RequestName is matched.
3. **StaticParams**:- List of Params which can be required by any of the actions mentioned in Actions array.
4. **NeedCascading**:- When set to true the actions are executed synchronously otherwise asynchronously.

## Different Hooks
### 1. AddProductDetails Hook :- 
This is used to add **Product code, update PolicyTerm, QuoteValidity and Renewal Configuration** which are fetched from the master container. Inside master container a document belonging to particular client is kept with all the details required. This hook is called on the submission of first page of Quote Flow.

### 2. GeneratePolicyNumber Hook :-
This is used generate **PolicyNumber** at policy bind transaction. The hook uses **Product code, LastSequenceNo and Policy Effective Year** for Policy Number Generation. The format used is :- `${productcode}${slicedYear}${.LastSequenceNo.padStart(4, 0)}`.

### 3. GenerateQuoteNumber Hook :-
This is used to generate the unique **QuoteNumber** used as reference for each policy object. It is also called at the very first page of Quote Flow. The hook uses **QuoteNumber Prefix, LastQuoteSequenceNo and Sliced Policy Effective Year** for Quote Number Generation. The format used is :- `${process.env.QUOTENUMBERPREFIX}${slicedYear}${LastQuoteSequenceNo.padStart(4, 0)}`.
- The **Quote Number Prefix** is fetched from Graph QL functions environment variable.
- The Sliced Year is fetched from Policy Effective Year obtained from policy model,
- LastQuoteSequenceNo is fetched from the master container document belonging to particular client.

### 4. AddRaterDetails Hook :-
Rater URL is formed using `${RaterVersionURL}?ProgramName=${ProgramName}`. Then a get Request is made to fetch the latest Rater version for that implementation. This fetched Rater version is stored in Attributes.RaterVersion node of Policy Model.
- **RaterVersionURL** is fetched from the static params when the hook is called.
- **ProgramName** is created using `LOB + "-" + ImplementationName + "-" + state`. Here ImplementationName represent client and all three are fetched from Policy Model.

### 5. HandleTransactionNumber Hook :-
Based on **Transaction.Type and Transaction.Status** this is used to increment the transaction number. The transaction number is a very important property which is used by rater to determine the previous binded property as some fields like Endorsed Premium, Effective Premium etc. values are filled using calculation which needs the last binded policy. This is kept as a hook as it is used across multiple flows {Endorsement, Cancellation, Reinstatement and Renewal}, on multiple pages like Updated Details page in endorsment , summary page in Application when Adjust Premium could be called etc.. Been a logic of prime importance and to prevent updatation of transaction number on user trying different permutations in application on UI it is kept as a backend hook.

### 6. AddBusinessDetails Hook :-
This is a custom hook used to fetch the details of different vehicle unit registered against a particular **BusinessName and Address**. This uses VeRisk API which return the list of vehicles, which are added into the Vehicles node of the Policy model and then saved into the DB. So on Application UI when the latest object in DB is fetched it contains the pre-filled list of Vehicles with all details fetched via VeRisk API.
- The **VeRisk API URL** is read from the static params of the hook configuration.
- The Address and Business name and few other params are read from policy object.

### 7. AddPropertyDetails Hook :-
This is also a custom hook used to fetch the details of property from its address. It returns YearBuiltear, NumberOfStories, ProtectionClasstion, TornadoScore, Area,ConstructionType, DistanceToCoast, DistanceToHydrant, DistanceToFireStation and CrimeScore.

### 8. ExecuteUnderWritingRules Hook :-
There are certain conditions in every risk which can increase the risk's vulnerability. While filling the details during Quote process, these details are captured and stored in data model. There is Underwriting rules json kept in **config blob storage** for every individual client. When the request for **ExecuteUnderWritingRules** comes this json file is read and all those conditions which are violated is pushed into policy models **Rules node** in form of array. Which is then used by Underwriter to evaluate the risk and maybe adjust the premium.
- RunRules function is passed with current and previous policy model, rules URL, type to determine the whether to call rules for NB forms, END forms or for Underwriter Rules and the credentials for blob, etc in extraparams parameter.

### 9. HazardHubCall Hook :-
This is also a custom hook used to fetch all the details required for Quote flow from a API and populate the policy model which is then used in the application. Currently it is used in BnB implementation.

### 10. PayPlanRules Hook :-
Like Underwriting rules there are certain rules which determine different payplan options to user based on selection made during application. These rules are called on the summary page to show user different payplan options, from which then they can choose and proceed with payment. The payplan rules schema is kept in **config blob storage** for that client just like Underwriting rule schema.

### 11. ClueMvrCall Hook :-
This is also a custom hook called to fetch drivers and vehicles violation records. These are two API's Clue API which is used to fetch drivers violation record and MVR(Motor Vehicle Report) which keeps the history of vehicle. The details from these API is used for evaluation of risk by Insurance Agency.

### 12. AIMCall Hook :-
AIM Ageny Management System is used for keeping track of policy. From our system on every successful bind transaction we push details into AIM system for keeping track of records. AIM API is used to push the data. As this is not so crucial to be implemented in near real time we make a Post Hook call for this API. That is we perform our saving operation in DB and then pass the policy object to the AIM API which saves the record in AIM system asynchronosly.

<!-- ### 13. QuickBook Hook :- -->
