---
id: uicomponentslibrary
title: UI Components
---

DIEP2.0 User interface is built using ReactJs.Now in order to utilise the potential of ReactJs, we have used some reusable components
which is also a core advantage of using ReactJs.Since we have to implement our application for different implementation which may share the same Line of Businesses , hence we need such reusable components in order to save development efforts and thus maintain a speed to market capability for our product.Moreover,to make these components more robust and reusable we have a dynamicforms component which is a JSON-schema based approach to build a web page.One thing to note down here is that this functionality of dynamicforms is our own technique to make the UI highly configurable in na sense that we are soon going to implement it with our Low-Code-No-Code(LCNC 2.0) which is basically an another product of Cogitate to make the UI build faster with minimum technical intervention.

``NOTE:All our components are Functional Components i.e. these components are created as a function which are exported later and used by the respective web page.``



>![Components](../../static/img/docs/diep2/components.png)


## Types Of Components

### Core Components

Core components are those components which are common across all the implementations/LOBs.Some common core components are:

- #### Dynamic Forms
Dynamic forms component is our in-house component which we basically use to utilize a JSON schema for our page generation. Here, there are different properties in this JSON schema like key,type,title,controls,etc. If observe carefully , it is nothing but a metadata for any conventional HTML element but with a slight modifications with additional properties like conditionalDisplay, controls,etc.
In order to consume and render a Web page out of this schema, we need our dynamicform component which processes this and renders the relevant UI with all the stylings , conditional logics, field types and validations as well. For example, below is a JSON schema :
```
{
    "key": "deductiblesdetails",
    "type": "Card",
    "title": "Deductible Details",
		"subtitle": "Almost there … go ahead and adjust the coverage amounts and select from the Additional Coverage Options…",
    "className": "",
    "titleClassName": "commonHead commonHeadPadding",
    "childsClassName": "boxWrapper px-3 commonShadow",
    "controls": [
      {
        "key": "CoverageCPersonalProperty",
        "label": "Coverage C - Personal Property*",
        "type": "number2",
        "props": { "required": true, "class": "inputText" },
				"prefix": "$",
				"inputClass": "d-flex flex-nowrap",
        "labelClass": "inputLabel",
        "positionClass": "col-md-6 mt-4",
        "isColummnDisplay": false,
        "dataPath": "Risks.Properties.@index.Coverages.2.Value",
				"conditionalDisplay": [{
          "src":  "Risks.Properties.@index.OtherDetails.BuildersRisks.Type",
          "exp": "!=",
          "needRefComp": false,
          "target": "COC",
          "connector": "&&"
        }]
      }
    ]
  }
```


- #### Map Auto Complete
Map Auto Complete component basically uses a react based google maps component which is present as NPM package. The one advantage of using this component is that we can easily insert any custom code for address selection purpose and also we can select what all details we actually require.Like, maybe we require full state name or just an abbreviation for the same.

>![Components](../../static/img/docs/diep2/mapautocomplete.png)

- #### Data Tables
Data tables component is a highly used components which we use in our DIEP2 application.We use it to show accounthub,claims history,list of entities,etc.

### Layout Components

Layout components are those components which are common across all the web pages of our application. Like header,footer , progressbar,etc.

### Page Components

Page components are those components which are specific to a particular page only throughout all the implementations.Like, accounthub page or the dashboard page.Since the application in general has a Quote/Policy listing feature along with some visual dynamic reports dashboarding feature hence we need this component across all the implementations.
