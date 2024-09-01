---
id: rules
title: Rules Engine
---

## Introduction
title: Integration on UI
---

## 1. Rules Engine
Rule engines allow you to say "What to do" not "How to do it". The key advantage is that using rules can make it easy to express solutions to difficult problems and consequently have those solutions verified. Also rules are much easier to read then code. Keeping the business logic in the rules is a good idea as it keeps the code and business logic separate. It also allows us to change them on the fly without the need of the deployment cycle.

We have used the json-rules-engine which is a powerful, lightweight rules engine. Rules are composed of simple json structures, making them human readable and easy to persist. It is secure as there is no eval() used. There is full support for ALL and ANY boolean operators, including recursive nesting as well.

## Implementation
>![POS_COMPONENTS_RULES_SETUP](../../static/img/docs/diep2/rules-setup.png)

We use this Engine to verify underwriting rules. We have allow, block actions as a result when the rules are validated. The engine would require the policy model and the type of rules which needs to be run. These things are added as a fact in the Engine. We have called using the Hook Schema where we have listed the action as Underwriting Rules.
### Implementation
>![POS_COMPONENTS_RULES_SETUP](../../static/img/docs/diep2/rules-setup.png)

We use this Engine to verify underwriting rules. We have allow, block actions as a result when the rules are validated. The engine would require the policy model and the type of rules which needs to be run. These things are added as a fact in the Engine. We have called using the Hook Schema where we have listed the action as Underwriting Rules.

## 2. Form Factory
LCNC platform is used to add, remove and modify all the forms related to any LOB, State, ProductCode. It holds all the forms we use across our different implementations. In this section, we'll discuss majorly about how we are using those forms on UI in DIEP2.0

### Types of Forms
1. **Mandatory Forms** :- These forms are marked as mandatory while uploading on LCNC platform. These response received from form factory has IsMandatory node set as "true" for these forms. These are forms which are mandatory for the policy.

2. **Conditional Mandatory Forms** :- These are forms which are mandatory if while filling the policy certain conditions are met. On UI these are present in Optional Form Category as Pre-selected. These have IsMandatory set as "false" and IsChecked set as "true".

3. **Optional Forms** :- These are forms which are set as not mandatory in LCNC. These forms has IsMandatory node and IsChecked node both set as "false". User can select these forms from the checkbox if he/she want that form.

### Fetching Forms List
For fetching forms list **getForms** query is called along with which a payload containing below mentioned details are sent.
```bash
const payload = {
  "userName": userName,
  "password": password,
  "grantType": grantType,
  "tokenUrl": tokenUrl,
  "productCode": productCode,
  "transactionType": transactionType,
  "formFactoryApiUrl": formFactoryApiUrl,
  "quoteNumber": quoteNumber
};
```
- Username, Password, GrantType, TokenURL - is used to validate user login to form factory (LCNC).
- ProductCode is used to determine the Product whose forms are to be fetched.
- TransactionType is used to fetch the forms related to the particular transaction type (New Business, Endorsement, etc.)
- FormFactoryAPIURL is the URL of particular environment of form factory.
- QuoteNumber is the reference no used to fetch the policy object.

### Listing Forms on UI
Flow for fetching forms with conditional forms checked is :-
1. Request is made to getForms Resolver with payload mentioned as above.
2. The request may contain a reference no or not.
3. A request to **formFetchMain function** with **(args - current payload, [policy - current policy object], [previousPolicy - previous policy object])** is made.
4. formFetchMain calls **fetchForms function** with **(args)**.
5. fetchForms calls **getAccessToken function** with **(args)**.
6. getAccessToken return **accessToken**
7. Returned Access Token to fetchForms is passed as **Authorization header to call form factory API**.
8. fetchForms return a list of all the forms for that ProductCode and TransactionType.
9. If the request in [1] does not contain any reference no as mentioned in [2], IsChecked parameter is added to every form object with value **true** for mandatory form and **false** for every non-mandatory form and added into Forms Node of the Policy Model.
10. If the request payload in [1] contains reference no, **executeRules function** is called with **(policy - current Policy object, transaction type, and previousPolicy)**.
11. Inside executeRules an extraParam object is made like below which holds flag for whether to run rules, path of rules file **(json file stored in respective environment's client's config folder)**.
```bash
let extraParams={
  pullRulesFromBlob:process.env.PULLRULESFROMBLOBFLAG,
  DIEP2_STORAGE_ACCOUNT_ID:process.env.ACCOUNT_ID,
  DIEP2_STORAGE_BLOB_SAAS:process.env.BLOB_SAS,
  DIEP2_STORAGE_BLOB_CONTAINER:process.env.BLOB,
  DIEP2_STORAGE_BLOB_PATH:process.env.RULESPATH
}
```
12. **RunRules function** is called inside execute rules with **(currentPolicy , previousPolicy, ruleURL {APIM - CogitateMock API wrapper}, type {New Business, Endorsement etc}, and extraParams formed above)**.
13. Collection of rules for particular instance (form, UW Rules etc.) is received from the API call is then used to check different conditions on policy object, for which Node Package **json-rules-engine** is used as mentioned in above Rules Engine Section.
14. Based on satisfied rules, all the forms whose condition is satisfied is set with **IsChecked as true**.
15. The final response with all the **Mandatory forms IsMandatory and IsChecked set as true**, all the **Conditional Mandatory forms** whose condition is fulfilled when check with mentioned rules, set with **IsMandatory as false and IsChecked as true** and rest form with both set as **false** is returned to the UI.

16. On UI this list of forms is used to render **ViewForms Modal, Approve Policy Modal** etc. based on implementation requirement. The Mandatory forms are shown separately and the condtional mandatory is show as checked along with other forms in a separate section. **A user cannot deselect a Mandatory form, but he/she can select/deselect a conditional mandatory or optional form**.


### Download Draft Functionality
On UI inside ViewForms Modal we have a functionality where user can download and view the different forms in Draft format. Here we use LCNC formFactory's **GenerateFormsNew** endpoint and pass payload as below to receive an octet-steam of PDF response which we use to directly download a PDF file in specified fileName format : { `${summary.QuoteNumber}_Draft`}
```bash
const payload = {
  Policy: policy,
  FormList: formlist,
  IsDraft: isDraft,
  IsAgent: isAgent
};
```
- **Policy** - This parameter represents our policy model - it is used by Handlerbar to fill the details inside of each dynamic form.
- **FormList** - This is an array of string, with each string representing the **FormName** property of the Forms object.
- **IsDraft** - This is used to mark the forms as Draft. With this set as **tru** the downloaded forms have **DRAFT as Watermark**.

**Note**:- URL for form factory is created inside the function using :-
```bash
const productCode = policy?.Attributes.Product;
const transactionType = staticItems.FormFactoryTransactionTypes[`${policy.Transaction.Type}`];
const url = `${process.env.NEXT_PUBLIC_FORM_FACTORY_API_URL}ProductForm/${productCode}/${transactionType}/GenerateFormsNew/`;
```
