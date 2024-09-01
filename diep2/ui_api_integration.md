---
id: ui_api_integration
title: UI API Integration with GraphQL
---
GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

We have used GraphQL for ui api integration to save/update the data of every page in our policy container. On every page submission, save method is called which is responsible for saving details of that page.

>![UI_Folder_Structure](../../static/img/docs/diep2/onsumit_method.png)

To illustrate save method, see the code snippet and explanation below.

```
const save = async (policy, action, requestedPage = "", callBackPage = "", progressIndex = 0) => {
  try {
    if (action != apolloKeys.SaveMultipleAction && action != apolloKeys.MultipleRateAction && !policy.NonFunctional.Milestones.includes(progressIndex)) {
      policy.NonFunctional.Milestones.push(progressIndex);
    }
    let resp = await SavePayload(policy, action, requestedPage);
    if (resp) {
      if (action != apolloKeys.SaveMultipleAction && action != apolloKeys.MultipleRateAction) {
        store.dispatch({
          type: PUT_POLICY,
          payload: resp
        });
      }
      sharedSetProgress(progressIndex);
      if (callBackPage?.length > 0)
        window.location.href = callBackPage;
    }
    return resp || null;
  } catch (error) {
    console.log(consoleLogs.Utilities.Pages.Quote.Save, error);
    throw error;
  }
}
```
* policy :- This is our data model.
* action :- This tells the type of action we need to perform like POST, PUT, RATE etc.
* requestedPage :- This is the page from which request is triggered.
* apolloKeys :- These are used for referring different apollo operations like CRUD operations on DB, interaction with different APIs.

##### Method to create and update data in cosmos

This method update and returns the updated payload/object.

```
const SavePayload = async (payload, actionname = '', submittedpagename = "") => {
  try {
    let _mutation = CREATE_POLICY;
    let _mutationType = apolloKeys.PostMutation;
    if (submittedpagename.length > 0) {
      payload.NonFunctional.LastSubmittedPage = submittedpagename;
    }
    switch (actionname) {
      case apolloKeys.RateAction:
        _mutation = RATE_POLICY;
        _mutationType = apolloKeys.RateMutation;
        break;
      case apolloKeys.MultipleRateAction:
        _mutation = MULTIPLE_RATE_POLICY;
        _mutationType = apolloKeys.MultipleRaterMutation;
        break;
      case apolloKeys.SaveMultipleAction:
        _mutation = SAVE_MULTIPLE_RATE_POLICY;
        _mutationType = apolloKeys.SaveSelectedIndex;
        break;
      case apolloKeys.BindAction:
        _mutation = BIND_POLICY;
        _mutationType = apolloKeys.BindMutation;
        let dformat = (d.getFullYear().toString().padStart(2, '0') + "-" + (d.getMonth() + 1).toString().padStart(2, '0') + "-" + d.getDate().toString().padStart(2, '0'));
        payload.BindDate = dformat;
        payload.IsPolicyBind = "true";
        payload = {
          "input": payload,
          "emailBody": "FormFactory says Hi!!!!",
          "emailSubject": "FormFactory",
          "attachments": null,
          "newStatus": "Policy"
        }
        break;
      default:
        if (payload.id.length > 0) {
          _mutation = UPDATE_POLICY;
          _mutationType = apolloKeys.PutMutation;
        }
        else {
          let d = new Date();
          let dformat = (d.getMonth() + 1).toString().padStart(2, '0') + d.getDate().toString().padStart(2, '0') + d.getFullYear().toString().padStart(2, '0') + d.getHours().toString().padStart(2, '0') + d.getMinutes().toString().padStart(2, '0') + d.getSeconds().toString().padStart(2, '0');
          payload.QuoteNumber = dformat;
        }
        break;
    }
    const resp = await ExecuteMutation(GetApolloClient(gqlEndPoint), _mutation, actionname == apolloKeys.BindAction ? payload : { "input": payload });
    return resp.data[_mutationType];
  } catch (error) {
    logAPIErrorData(error, { payload, actionname, submittedpagename }, consoleLogs.Utilities.Apollo.Operations.SavePayload)
  }
}
```
* payload :- This is the payload to be updated in cosmos.
* actionname :- This is the type of action need to perform.
* submittedpagename :- This is the page from which request is triggered.


##### Method for executing mutation

Mutations allow you to modify server-side data, and it also returns an object based on the operation performed. It can be used to insert, update, or delete data.

```
const ExecuteMutation = async (apolloClient, mutation, variables) => {
  try {
    return await apolloClient.mutate({
      mutation,
      variables
    });
  } catch (error) {
    throw error;
  }
};
```

##### Method for creating and returing Apollo Clients

```
const GetApolloClient = (url) => {
  try {
    const httpLink = new HttpLink({ uri: url });
    return new ApolloClient({
      cache: cache,
      link: from([customHeaderMiddleware, httpLink]),
      name: 'insurance-next-web-client',
      version: '1.3',
      ssrMode: false,
      queryDeduplication: false,
      defaultOptions: _defaultOptions,
    });
  }
  catch (error) {
    throw error;
  }
}
```