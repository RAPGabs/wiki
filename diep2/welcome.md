---
id: welcome
title: Introduction
---

As part of DIEP (Digital Insurance Engagement Platform) we are trying to provide next generation solutions to <b>Insurance Providers</b> by targeting to built loosely coupled, easy to configure, speed to market, highly performant & scalable products.<br/>
We have achieved the same over the period of time with different major releases to the DIEP platform. With each major incremental release team had keep innovating the platform by introducing new functional features with technical advancements.

## History
DIEP as an platform had gone through different versions:-
1. <b>DIEP 1</b><br/>
    As part of release 1 team introduced cool features like Form Factory, Data Service, Base Project, DMS, Analytics, Workflows, LOB Agnostic DB. Also team was able to implement new implementation within 24-36 weeks.
2. <b>DIEP 1.1</b><br/>
    As part of release 1.1 team introduced Async Web job, Cloud based error logging and monitoring. Team drastically improved the performance of rater and overall platform as well. Implementation time reduced to 16 weeks for a new Implementation also for adding new state (1 – 2 weeks) and new lob (4 – 6 week ) for existing implementation.
3. <b>DIEP1.1 + LCNC</b><br/>
    Introduced and integrated with in-house LCNC tools which facilitates business to configure different rules, underwritting questions, new forms & modify existing, rules for optional forms, add and modify fees & taxes. After introduction of LCNC the new implementation time was same 16 weeks but there is no time to add new state and lob implementation.
4. <b>DIEP2</b><br/>
    As part of DIEP 2.0, we are targeting to build a system that will be highly decoupled in nature. Most of its layers will be configuration-driven so that those will be highly reusable across implementations with minimal efforts.<br/>
    Also for DIEP 2.0 we have changed the entire architecture of the current system which will be more robust and highly scalable so that we can reuse all our resources across clients as well without any downtime & performance issues.<br/>
    Also, we are opting for most trending technologies like REACT, NODE, GRAPHQL, COSMOS & AZURE (SERVERLESS) which also provides an edge in the competitive market.<br/>
    Most importantly we are targetting to reduce the implementation to 8 weeks or further.

## Objectives Of DIEP 2.0
As part of DIEP2 we are targetting below objectives:-
<ul>
    <li>
        For DIEP 2.0 we are targeting to change the entire architecture of the current system which will be more robust and highly scalable and reusable, so that we can reuse all our resources across clients as well without any downtime & performance issues.
    </li>
    <li>
        Through V1 implementation of DIEP 2.0 we scoped to build 3 layers from the scratch UI (React & JSON Driven Forms), APIs( Azure Functions, Node & GRAPHQL) & Cosmos DB.
    </li>
    <li>
        We have created mltiple reusable libraries and packages to achieve higher level of reusability.
    </li>
    <li>
        We are targetting configuration driven layers so that we can increase the speed to market across implementations with minimal efforts. 
    </li>
    <li>
        We are building serverless environment to have highly scalable applications.
    </li>
    <li>
        Using Azure Monitor & AppInsight to have OOB realtime monitoring and log analytics.
    </li>
    <li>
        In later half of the implementation will enable Azure Synapse & Chart js for analytics.
    </li>
    <li>
        Reusing existing CTS resources like Form Factory, LCNC, SSO, Rater & Notification API.
    </li>
</ul>

## Architecture DIEP 2.0
Below is the reference High Level Architecture:-
![DIEP2_Architecture](../../static/img/docs/diep2/DIEP2.0-HL.jpg)
A per new architecture we can devide the entire architecture into sub-parts:-
1. POS Core<br/>
    a). <b>UI Client</b>:- 
        It's Azure Storage based JSON configuration driven front-end which is built using React & Next JS. Which can be deployed to Azure App Service or Static Website and can also be served over CDN. <br/>
    b). <b>APIM</b>:- 
        Azure's API Management is a connector & authenticator between UI Client & GraphQL Server.<br/>
    c). <b>GraphQL Server</b>:- 
        Its an Apollo Server & GraphQL based application which exposed various end points which executes respective business logic and communicates with Cosmos DB.<br/>
    d). <b>Cosmos DB</b>:- 
        It's No SQL based backend which holds all the policy details within its user-defined multiple containers.<br/>
    e). <b>Event Grid</b>:- 
        GraphQL Server can emit events to Event Grid based on event type it will process the different business flows. Like notifying Users, generating FORMS etc.
2. Adaptive API<br/>
    Adaptive API is a kind of configuration driven Forwarding API Management tool which helps to connect to any third party system on fly by cloud configuration based request and response transformations.
3. CTS APIs<br/>
    CTS APIs are collection of existing APIs like Rate, Form Factory, Notifications & SSO. DIEP 2.0 consumes these APIs via APIM.
4. Logging & Monitoring<br/>
    For logging & monitory we are using Azure's Application Insight & Azure Monitor.
