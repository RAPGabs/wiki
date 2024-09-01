---
id: ui
title: UI Client
---
In DIEP 2 we have built UI Client using React & Next JS as a base. On top of those have used Apollo Client to interact with Apollo Server & GraphQL based APIs. We have used SAAS, Fontawesome & Bootstrap for styling.
Also have used Chart JS as a charting library for Analytics.<br/>
In this we will try to provide brief insight about the structure, components, utilities and features used while implementing User Interface.

## Folder Structure

The folders in UI are kept in structure as shown below.

>![UI_Folder_Structure](../../static/img/docs/diep2/ui_folder_structure.png)

The different folders, their ingredients and usage are as follows:-

1. **__tests__ Folder** :- This folder holds unit test for utilities, validators etc. in the similar folder structure as those components are present. It will also have end to end testing scripts and snapshot tests.
>![UI_Tests_Folder](../../static/img/docs/diep2/ui_folders_tests.png)

2. **.next Folder** :- ``next build`` generates an optimized version of your application for production. This standard output includes:
- HTML files for pages using getStaticProps or Automatic Static Optimization
- CSS files for global styles or for individually scoped styles
- JavaScript for pre-rendering dynamic content from the Next.js server
- JavaScript for interactivity on the client-side through React

This output is generated inside the .next folder:

- ``.next/static/chunks/pages`` – Each JavaScript file inside this folder relates to the route with the same name. For example, .next/static/chunks/pages/about.js would be the JavaScript file loaded when viewing the /about route in your application
- ``.next/static/media`` – Statically imported images from next/image are hashed and copied here
- ``.next/static/css`` – Global CSS files for all pages in your application
- ``.next/server/pages`` – The HTML and JavaScript entry points prerendered from the server. The .nft.json files are created when Output File Tracing is enabled and contain all the file paths that depend on a given page.
- ``.next/server/chunks`` – Shared JavaScript chunks used in multiple places throughout your application
- ``.next/cache`` – Output for the build cache and cached images, responses, and pages from the Next.js server. Using a cache helps decrease build times and improve performance of loading images

All JavaScript code inside .next has been compiled and browser bundles have been minified to help achieve the best performance and support all modern browsers.

3. **components Folder** :- This folder contains all the reusable components we are using, we have categorized them based on there usage. We will look them in details in upcoming sections.
>![UI_Components_Folder](../../static/img/docs/diep2/ui_components_folder.png)

4. **coverage Folder** :- This folder contains the coverage report for unit tests performed. The most relevant file in this folder is ``index.html`` which shows us the files for which we have written the unit tests, it also shows the coverage for each function, the lines we have covered or missed and also the branches we have visited or left.

5. **data Folder** :- This folder contains static unique data such as keys, status, and other configuration data used throughout the application for providing static configuration values and rendering UI components like menu, progressbar etc.. The image below shows different files we are using, we will cover each of them in brief here.

>![UI_Data_Folder](../../static/img/docs/diep2/ui_data_folder.png)

  - _datatable.js_ :- This file contains the configuration for datatable core component.
  - _keys.js_ :- This folder contains different keys used throught the application. Brief info about the are as follows:-
    * storeKeys :- These are used for accessing different nodes stored in the redux store to use the values against them.
    * apolloKeys :- These are used for referring different apollo operations like CRUD operations on DB, interaction with different APIs.
    * commonKeys :- These are used to refer different general purpose constants like Module type, Notification type, Action type etc.
    * axiosKeys :- These holds different axios actions like POST and GET.
    * routeKeys :- These represents different routes that exist in the application.
    * tabKeys :- These represents different tab names visible to user on summary or analytics screen.
    * pageKeys :- These represents specific keys used in different page for particular functionality.
    * layoutKeys :- These are the keys defining different structural layout we have defined. More information about them is provided Core Components section.
    * templateKeys :- These keys are used for different Notification service functions we are using.
    * chartKeys :- These stores keys for different varity of chart we are storing.
    * summaryActionButtonKeys :- These keys are used for binding different action buttons to the UI.
    * flowKeys :- These are used to represent different application flows.
  - _labels.js_ :- This file holds title and description for different pages in the different flows thorughout the application.
  - _menu.js_ :- This file is used to define configurable JSON driven left side navbar.
  - _messages.js :- We store different validation, alert and console messages to show in case of validation failure, function crash and for alerting user about incorrect input passed.
  - _progressbar.js_ :- This file is used for defining configurable JSON driven right side progress bar during each flow.
  - _static.js_ : This file is used for accessing different values stored in local storage which are dynamically fetched and stored there. It also holds fields which are required during bulk upload for checking them not to be null. Along with these, it also holds paramters and queries used in analytics.
  - _status.js_ :- This file is very crucial and is used to store different Policy Status, Transaction status, Transaction Type and other important keys.
  - _toast.js_ :- It holds configurable parameter for toasts used.
  - _vehiclemaster.js_ :- This is again a very important file which stores all possible permutation for different inputs required while filling vehicle details. These are used in validation of filled vehicle data too.
## Core Components

There some components which are pretty basic when it comes to project selection. We have categorized these components as core components.
The image below shows the core components we have created. We'll cover each of them in brief here.

![UI_Core_Components](../../static/img/docs/diep2/ui_core_components.png)


## Shared Components

These are those components which we have used across out whole project, across different application flows (like application, endorsement, renewal, cancellation etc.). We will cover each of them briefly here.

![UI_Shared_Components](../../static/img/docs/diep2/ui_shared_components.png)

Apart from these we have other reusable components too, which we have categories based on there usage.

1. Layout Components
> ![UI_Layout_Components](../../static/img/docs/diep2/ui_layout_components.png)

2. Modal Components
> ![UI_Modal_Components](../../static/img/docs/diep2/ui_modal_components.png)

3. Tabs Components
> ![UI_Tabs_Components](../../static/img/docs/diep2/ui_tabs_components.png)

4. Line LOB Based Components
> ![UI_LINE_LOB_REUSABE_Components](../../static/img/docs/diep2/ui_line_lob_based_components.png)

## Stores
In DIEP 2 with [``Redux``](https://www.npmjs.com/package/redux) we have used [``React Redux``](https://www.npmjs.com/package/react-redux),  [``Redux Persist``](https://www.npmjs.com/package/redux-persist) & [``Redux Persist Transform Encrypt``](https://www.npmjs.com/package/redux-persist-transform-encrypt) as well.<br/>
Confugured store using redux toolkit by passing list of reducers (Policy, Schema, LoggedInUser, Masters & Application) by wrapping them in a root reducer. And passed the root reducer to the <b>persistReducer</b> which is responsible for persisting the state across application restarts.
And while persisting passing the encryption mechanism with a secret key.<br/>
>![UI_Store_Configuration](../../static//img/docs/diep2/ui_store_configuration.png)

We have different type of reducers defined so far:-
<ul>
  <li><b>policy:-</b>This will hold the details of on going policy or quote.</li>
  <li><b>application:-</b>It holds application attributes like menu selected by user, progress made by the user etc. </li>
  <li><b>masters:-</b>On loggedin successfully we pulled all the required master via an API and dump them in masters reducer so those can be reused during user flow.</li>
  <li><b>user:-</b>It hold details of logged in user details like username, JWT, role etc.</li>
  <li><b>schema:-</b>We pulled required line, lob, state & flow based page wise UI schemas and dump them in schema reducer and same can be reused once user reached to a particular UI page.</li>
</ul>

>![UI_Store_Structure](../../static//img/docs/diep2/ui_store_structure.png)

And we have created utilities function to interact with store state like:-<br/>
getStoreState ((key)=> based on key this method will return the state of a particular reducer.)<br/>
setStoreState ((key, payload) => based on key replaces the entire state of a particular reducer with passed in payload.<br/>
setStoreInternalState ((key, subkey, payload) => based on key & subkey replaces the entire state of a particular reducer's attribute with passed in payload.) 


## Validations

Validators are used to validate the input for any particular field. These are passed into the validators variables array inside of ``Dynamicform`` component. The image below shows different validators we have created.

>![UI_Validators](../../static/img/docs/diep2/ui_validators.png)

These validators can contain the logic for verifying different input crucial to business using different third party services too, like different API can be used for VIN number and Driver License Number verification.
These validation trigger and shows a toast with specific message defined in the body of every validation object passed into the validators variable inside dynamicform component; on schema change or on submission of form.

[//]: # (END OF VALIDATORS SECTION -----------------------------------------------------------------------------)

## Schema

The Schema folder holds the JSON based configurable UI schema for defining the look of different page in the application. Below is the image showing the structure and files within a particular flow.

>![UI_Schema_Structure](../../static/img/docs/diep2/ui_schema_structure.png)

To illustrate the usage of this JSON driven schema approach, see the code snippet and explanation below.

```
// Sample Schema used in Quote Businessinfo page
const businessInfoModel = [
  {
    key: "UnderwriterDetails",
    type: "Card",
    title: "Underwriter Details",
    className: " clearfix",
    titleClassName: "commonHead commonHeadPadding",
    childsClassName: "boxWrapper border-0 px-3 commonShadow",
    conditionalDisplay: [{
      src: "AccountId",
      exp: "==",
      needRefComp: false,
      target: "Agent",
      connector: ""
    }],
    controls: [
      {
        key: "underwriterdetails",
        label: "UNDERWRITER*",
        type: "select",
        value: "select",
        props: { required: true, class: "inputText" },
        errorMessage: "Please select underwriter",
        labelClass: "inputLabel ddlUnderwriterList",
        positionClass: "col-md-6",
        isColummnDisplay: false,
        dataPath: "UnderWriter.Code",
        options: getUsersData('underwriter')
      }
    ]
  },
  {
    key: "BusinessDetails",
    type: "Card",
    title: "Name",
    className: " mt-4",
    titleClassName: "commonHead commonHeadPadding",
    childsClassName: "boxWrapper border-0 px-3 commonShadow",
    controls: [
      {
        key: "businessname",
        label: "BUSINESS NAME*",
        props: { required: true, class: "inputText", placeholder:'Please enter business name Min 2 - Max 50 alphabets', pattern: '[a-zA-Z ]*$', maxlength: '50', minlength: '2'},
        errorMessage: "Please enter valid Business Name",
        inputClass: "mb-3 flex-nowrap",
        positionClass: "col-md-6",
        isColummnDisplay: false,
        dataPath: "InsuredAccount.BusinessInfo.BusinessName"
      },
      {
        key: "yearofincorporation",
        label: "YEAR OF INCORPORATION*",
        type: "month",
        props: { required: true, class: "inputText",min:yearOfIncorporationMin ,max: yearOfIncorporationMax },
        errorMessage: "Please select year of incorporation",
        positionClass: "col-md-6",
        isColummnDisplay: false,
        dataPath: "InsuredAccount.BusinessInfo.IncorporationAge"
      }
    ]
  }
]

export default businessInfoModel;
```

### Dynamicform Component
We have defined a core component named ``dynamicform`` which uses this JSON based definition and renders html components based on parameters defined. Inside of "dynamicform" we have defined different html components with configurable properties. Those properties are filled inside of JSON schema and at the time of rendering the UI, dynamicform component converts this JSON schema into html components to be passed to DOM.

To give a brief glance of Dynamic form see the code snippet below.
```
<DynamicForm
  key={props.pageKey}
  title=""
  formId="pageChangeForm"
  onChangeValidateForm="true"
  positionClass="form"
  titlePositionClass="form-title"
  formPositionClass="dynamic-form"
  actionsPositionClass="form-actions"
  submitPositionClass="btn btn-primary m-3 float-right"
  defaultValues={businessInfo}
  validators={[
    {
      key: "InsuredAccount.BusinessInfo.FullTimeEmployees", 
      validations: [
        {
          "validator": Validator.FullTimeEmployees,
          "message": validationMsgs.BusinessName.FullTimeEmployees
        }
      ]
    },
    {
      key: "InsuredAccount.BusinessInfo.NoOfOwners", 
      validations: [
        {
          "validator": Validator.NoOfOwners,
          "message": validationMsgs.BusinessName.NoOfOwners
        }
      ]
    }
  ]}
  model={businessInfoModel}
  dataModel={businessInfo}
  onSubmit={async(model) => {
    NProgress.start();
    setStoreState(storeKeys.PolicyReducer, model);
    setUsersData();
    await save(getStoreState(storeKeys.PolicyReducer), commonKeys.EmptyString , props.currentPage, commonKeys.EmptyString, 0);
    NProgress.done();
    router.push(props.nextPage);
  }}
  onChange={(model, key) => {
    onSchemaChange(model, key);
  }}
/>
```

In the above component the JSON schema is passed in model variable. Once passed in the variable the dynamicform component uses this to lay out the UI. To know more about the Dynamicform Component refer to Core Component section.

### How does Dynamicform interprets JSON Schema

In the JSON schema code above ``businessInfoModel`` is an array which consists of different objects denoting different parent containers (like cards etc.) which contains an array of controls which are actually the components displayed on UI. There are different type of components used like "text" or "" for html text components, "select" for html dropdown components, "month" for html month components, etc. Based on these types dynamicform components renders this html components it also uses different classes defined along that control.
Different props can be passed to the control in props variable like max, min, minlength, pattern etc. which are basically offered by html. The key represents the unique key provided to that control inside that particular form and the label variable represents the optional label given to the attached input field.
Out of all these variables inside a control the most important one is ``dataPath`` variable. This variable represents the path inside of policy model where the value related to corresponding field is stored.
The options variables provides different options to choose from in case of dropdown or radio buttons.

> Note:- There is also a way to show a control on UI only when an another field has a particular value, for this we have conditionalDisplay property which takes the dataPath uses the expression to compare with the value passed. We can also provide contional display based on values in multiple fields by using connector variable and passing other conditions inside of conditionalDisplay array.

### Fetching from the Blob
We have kept the schema on the Azure Blob Storage. The Schema fetching activity is done at the same time when we load masters while the user is logging in. We keep the schema in the Redux store for usage across the lifecycle. Below is the screenshot of the code for fetching the UI Schema from the blob.

>![UI_Fetching_From_Blob](../../static/img/docs/diep2/ui-schema-fetching.png)

Let us go through the code. We are first loading the application and schema reducer. Then we are making an API call to the schema fetching API for fetching correct schema as per the payload shared. Now as per the condition we are populating the schema in a local object and later setting that object to the schema reducer. Then the store is updated with the latest schema.


### Rendering for Each Page
We have called schema on each page through the key of that page. As you can see the screenshot. loadSchemaFromStorage loads the schema for the required parameters. Also, the function AddDefaultValues is used to add dropdown values in the schema passed as parameter.
>![UI_Fetching_From_Blob_On_Page](../../static/img/docs/diep2/ui-schema-fetching-on-page.png)

[//]: # (END OF SCHEMA SECTION -------------------------------------------------------------------------------------)



## Pages

The Pages folder in Next JS provides the routing functionality out of box. In this folder we have kept all the different pages grouped by flows they are used in. Below image gives a overview of structure and pages we have used.

>![UI_Pages_Structure](../../static/img/docs/diep2/ui_pages_structure.png)

To make the application Line and LOB agnostic we have made the folder structure in particular manner. Like in above example, for commercial line's Automobile LOB we have different flows. Every flow in itself is a folder and files within are different pages in that flow. To illustrate, for Quick Quote flow we have quote folder and 'businessinfo.js' file is its page.
The pages contains the logic to be implemented on that page and different components and utilities used on there.
Keeping this folder structure provides the url route in similar pattern, like for visiting businessinfo page in Quick Quote the route would be ``https://your-domain-name.com/commercial/auto/quote/businessinfo``. 

For reading more about routing in Next JS you can refer to [NextJS_Routing](https://nextjs.org/docs/routing/introduction)

## Utilities Folder

There are many functions we have used across the whole application. We have categorized them into three groups based on the nature and usage. Below is the structure and files we have created.

>![UI_Utilities_Structure](../../static/img/docs/diep2/ui_utilities_structure.png)

We will try to give a glance of each in brief here.

1. Apollo Utilities :- These are basically those files which are used to perform different apollo operations like connection with apollo client for executing different queries and mutations, different custom condition based queries used in application, different fragments and different function to perform different operations required in the application.

2. Pages Utilities :- There are some utilities used in some specific flow only. Those utilities are kept inside pages folder. Here each file basically denotes a flow, consisting of utilities specific to those flows.

3. Shared Utilities :- Some utilities are required across more than one flow. Such utilities are kept inside this folder. These are basically required by application to function.

## Styling

For Styling we have used SAAS based styling. We have installed "sass" package as dev dependency, which compiles our .scss files and create .css file used by application. The watch mode feature in sass package allows to create a compiles .css files when you make modifications in .scss files.
We have stored all the configurables parameters (like color schemas, etc.) in variables.scss file. Also for keeping bunch of fonts options we have fonts.scss file, where we have different fonts which are used all over the project. This separation of files provides flexibilty to change theme based on demand with ease and quickly.

The folder structure and files we are using are as follows:
>![UI_Styles_Folder](../../static/img/docs/diep2/ui_styles_structure.png)

### SAAS and SCSS

Sass (short for syntactically awesome style sheets) is a preprocessor scripting language that is interpreted or compiled into Cascading Style Sheets (CSS). 

Sass consists of two syntaxes. The original syntax, called "the indented syntax," uses a syntax similar to Haml. It uses indentation to separate code blocks and newline characters to separate rules. The newer syntax, "SCSS" (Sassy CSS), uses block formatting like that of CSS. It uses braces to denote code blocks and semicolons to separate rules within a block. The indented syntax and SCSS files are traditionally given the extensions .sass and .scss, respectively.

CSS3 consists of a series of selectors and pseudo-selectors that group rules that apply to them. Sass (in the larger context of both syntaxes) extends CSS by providing several mechanisms available in more traditional programming languages, particularly object-oriented languages, but that are not available to CSS3 itself. When SassScript is interpreted, it creates blocks of CSS rules for various selectors as defined by the Sass file. The Sass interpreter translates SassScript into CSS. Alternatively, Sass can monitor the .sass or .scss file and translate it to an output .css file whenever the .sass or .scss file is saved.

The indented syntax is a metalanguage. SCSS is a nested metalanguage, as valid CSS is valid SCSS with the same semantics.

SassScript provides the following mechanisms: variables, nesting, mixins, and selector inheritance.[Wikipedia_SAAS](https://en.wikipedia.org/wiki/Sass_(stylesheet_language))

### Sass Support in Next JS

Next.js allows you to import Sass using both the .scss and .sass extensions. You can use component-level Sass via CSS Modules and the .module.scss or .module.sass extension.

Before you can use Next.js' built-in Sass support, be sure to install sass:

```
npm install --save-dev sass
```
> Note: Sass supports two different syntaxes, each with their own extension. The .scss extension requires you use the SCSS syntax, while the .sass extension requires you use the Indented Syntax ("Sass"). If you're not sure which to choose, start with the .scss extension which is a superset of CSS, and doesn't require you learn the Indented Syntax ("Sass").

For more customization and further info, you can checkout Next JS built in CSS Support Page. [Next_JS_CSS_Support](https://nextjs.org/docs/basic-features/built-in-css-support)

## Public Folder

As the name suggests public folder is the place where we keep those files which are globally accessible. Basically we keep our image files, and other documents which we want to allow to be used across whole application. As we mentioned earlier we are using Next JS as out model for building the UI. The public folder in Next is globally accessible so you can directly give the routes to your files by providing there relative path begining inside public folder.

The structure of public folder is as below.
>![UI_Public_Folder](../../static/img/docs/diep2/ui_public_folder.png)

To access your image files kept inside images folder inside public folder anywhere inside the project, you don't need to right there absolute or exact relative path. You can directly begin with '/images/your_image' and it will be linked to the required images, rather than specificing '../../../public/images/your_image' in some component lying deep in folders.

