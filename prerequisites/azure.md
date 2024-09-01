---
id: azure
title: Azure
---
Azure's Cloud is one of the leading cloud services provider. In DIEP 2.0 we have built or moved all are resource using Azure Cloud Services, so that we will get scallable maximum throughput for all application, modules & utilitites.

## Blob Storage

Azure Blob storage is Microsoft's object storage solution for the cloud. Blob storage is optimized for storing massive amounts of unstructured data. Unstructured data is data that doesn't adhere to a particular data model or definition, such as text or binary data.

**Blob storage is designed for**:

- Serving images or documents directly to a browser.
- Storing files for distributed access.
- Streaming video and audio.
- Writing to log files.
- Storing data for backup and restore, disaster recovery, and archiving.
- Storing data for analysis by an on-premises or Azure-hosted service.
- Users or client applications can access objects in Blob storage via HTTP/HTTPS, from anywhere in the world. Objects in Blob storage are accessible via the Azure Storage REST API, Azure PowerShell, Azure CLI, or an Azure Storage client library. 

**Note:**We typically use Blob Storage for storing schemas,email templates,generated and uploaded documents.

Below is the reference :-

![UI_Folder_Structure](../../static/img/docs/azure/blobstorage.png)

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- [``https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-overview``](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-overview)

## Content Delivery Network (CDN)

A content delivery network (CDN) is a distributed network of servers that can efficiently deliver web content to users. CDNs store cached content on edge servers in point-of-presence (POP) locations that are close to end users, to minimize latency.

Azure Content Delivery Network (CDN) offers developers a global solution for rapidly delivering high-bandwidth content to users by caching their content at strategically placed physical nodes across the world. Azure CDN can also accelerate dynamic content, which cannot be cached, by leveraging various network optimizations using CDN POPs.

**Note:**One use case of Azure CDN in DIEP is that we load all the static resources like favi icons,logos,styles,etc from a CDN.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- [``https://docs.microsoft.com/en-us/azure/cdn``](https://docs.microsoft.com/en-us/azure/cdn)

## Functions & Triggers

Azure Functions is a serverless solution that allows you to write less code, maintain less infrastructure, and save on costs. Instead of worrying about deploying and maintaining servers, the cloud infrastructure provides all the up-to-date resources needed to keep your applications running.

You focus on the pieces of code that matter most to you, and Azure Functions handles the rest.

To meet this need, Azure Functions provides "compute on-demand" in two significant ways.

First, Azure Functions allows you to implement your system's logic into readily available blocks of code. These code blocks are called "functions". Different functions can run anytime you need to respond to critical events.

Second, as requests increase, Azure Functions meets the demand with as many resources and function instances as necessary - but only while needed. As requests fall, any extra resources and application instances drop off automatically.

Triggers are what cause a function to run. A trigger defines how a function is invoked and a function must have exactly one trigger. Triggers have associated data, which is often provided as the payload of the function.

Binding to a function is a way of declaratively connecting another resource to the function; bindings may be connected as input bindings, output bindings, or both. Data from bindings is provided to the function as parameters.

You can mix and match different bindings to suit your needs. Bindings are optional and a function might have one or multiple input and/or output bindings.

Triggers and bindings let you avoid hardcoding access to other services. Your function receives data (for example, the content of a queue message) in function parameters. You send data (for example, to create a queue message) by using the return value of the function.

**Note:**We typically use Azure Functions to process the back-end functioning of DIEP.For example, Our GraphQL server is mounted on one such Azure Function, similarly we use Queue Triggers for processing varios jobs.

**Example:**
```bash
module.exports = async function (context, req) {

    try {
        context.log('JavaScript HTTP trigger function processed a request.');

        // Read incoming data
        const name = (req.query.name || (req.body && req.body.name));
        const sport = (req.query.sport || (req.body && req.body.sport));

        // fail if incoming data is required
        if (!name || !sport) {

            context.res = {
                status: 400
            };
            return;
        }

        // Add or change code here
        const message = `${name} likes ${sport}`;

        // Construct response
        const responseJSON = {
            "name": name,
            "sport": sport,
            "message": message,
            "success": true
        }

        context.res = {
            // status: 200, /* Defaults to 200 */
            body: responseJSON,
            contentType: 'application/json'
        };
    } catch(err) {
        context.res = {
            status: 500
        };
    }
}

```

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview``](https://docs.microsoft.com/en-us/azure/azure-functions)

[``https://docs.microsoft.com/en-us/azure/azure-functions/functions-triggers-bindings?tabs=csharp``](https://docs.microsoft.com/en-us/azure/azure-functions/functions-triggers-bindings?tabs=csharp)

## API Management (APIM) 

Azure API Management is a hybrid, multicloud management platform for APIs across all environments. This article provides an overview of common scenarios and key components of API Management.

APIs enable digital experiences, simplify application integration, underpin new digital products, and make data and services reusable and universally accessible. ​With the proliferation and increasing dependency on APIs, organizations need to manage them as first-class assets throughout their lifecycle.​

Azure API Management helps customers meet these challenges:

- Abstract backend architecture diversity and complexity from API consumers
- Securely expose services hosted on and outside of Azure as APIs
- Protect, accelerate, and observe APIs
- Enable API discovery and consumption by internal and external users

**Integration with Azure services:**API Management integrates with many complementary Azure services, including:

- Azure Key Vault for secure safekeeping and management of client certificates and secrets
- Azure Monitor for logging, reporting, and alerting on management operations, systems events, and API requests
- Application Insights for live metrics, end-to-end tracing, and troubleshooting
- Virtual networks and Application Gateway for network-level protection
- Azure Active Directory for developer authentication and request authorization
- Event Hub for streaming events
- Several Azure compute offerings commonly used to build and host APIs on Azure, including Functions, Logic Apps, Web Apps, Service Fabric, and others.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/api-management``](https://docs.microsoft.com/en-us/azure/api-management)

## CosmoDB
Azure Cosmos DB is a fully managed NoSQL database for modern app development. Single-digit millisecond response times, and automatic and instant scalability, guarantee speed at any scale. Business continuity is assured with SLA-backed availability and enterprise-grade security. App development is faster and more productive thanks to turnkey multi region data distribution anywhere in the world, open source APIs and SDKs for popular languages. As a fully managed service, Azure Cosmos DB takes database administration off your hands with automatic management, updates and patching. It also handles capacity management with cost-effective serverless and automatic scaling options that respond to application needs to match capacity with demand.
>![CosmosDB_Entities](../../static/img/docs/azure/cosmos-entities.png)

**Our DB Components and Layout:**
>![CosmosDB_Layouts_Components](../../static/img/docs/azure/CosmosComponentsLayout.png)
>[CosmosDB_Layouts_Components](../../static/img/docs/azure/CosmosComponentsLayout.png)

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/cosmos-db/``](https://docs.microsoft.com/en-us/azure/cosmos-db/)

## Service Bus

Azure Service Bus is a fully managed enterprise message broker with message queues and publish-subscribe topics (in a namespace). Service Bus is used to decouple applications and services from each other, providing the following benefits:

- Load-balancing work across competing workers
- Safely routing and transferring data and control across service and application boundaries
- Coordinating transactional work that requires a high-degree of reliability

Data is transferred between different applications and services using messages. A message is a container decorated with metadata, and contains data. The data can be any kind of information, including structured data encoded with the common formats such as the following ones: JSON, XML, Apache Avro, Plain Text.

### Some Basic Concepts

These Concepts Include:
- **Queue:**Messages are sent to and received from queues. Queues store messages until the receiving application is available to receive and process them.

- **Topic:**You can also use topics to send and receive messages. While a queue is often used for point-to-point communication, topics are useful in publish/subscribe scenarios.opics can have multiple, independent subscriptions, which attach to the topic and otherwise work exactly like queues from the receiver side. A subscriber to a topic can receive a copy of each message sent to that topic. Subscriptions are named entities. Subscriptions are durable by default, but can be configured to expire and then be automatically deleted. Via the Java Message Service (JMS) API, Service Bus Premium also allows you to create volatile subscriptions that exist for the duration of the connection.

- **Namespace:**A namespace is a container for all messaging components (queues and topics). Multiple queues and topics can be in a single namespace, and namespaces often serve as application containers.
A namespace can be compared to a server in the terminology of other brokers, but the concepts aren't directly equivalent.

And there many other such concepts , please refer to the official documentation mentioned below.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview``](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview)

## Topics & Subscription

A queue allows processing of a message by a single consumer. In contrast to queues, topics and subscriptions provide a one-to-many form of communication in a publish and subscribe pattern. It's useful for scaling to large numbers of recipients. Each published message is made available to each subscription registered with the topic. Publisher sends a message to a topic and one or more subscribers receive a copy of the message, depending on filter rules set on these subscriptions. The subscriptions can use additional filters to restrict the messages that they want to receive. Publishers send messages to a topic in the same way that they send messages to a queue. But, consumers don't receive messages directly from the topic. Instead, consumers receive messages from subscriptions of the topic. A topic subscription resembles a virtual queue that receives copies of the messages that are sent to the topic. Consumers receive messages from a subscription identically to the way they receive messages from a queue.

The message-sending functionality of a queue maps directly to a topic and its message-receiving functionality maps to a subscription. Among other things, this feature means that subscriptions support the same patterns described earlier in this section regarding queues: competing consumer, temporal decoupling, load leveling, and load balancing.

**Note:**We use Topics for publishing to Notification Event Grid which basically notifies users about recent status updates on their policies. Also they are used for email and sms notifications for the same purpose.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-queues-topics-subscriptions``](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)

## App Service (WebApps)

Azure App Service is an HTTP-based service for hosting web applications, REST APIs, and mobile back ends. You can develop in your favorite language, be it .NET, .NET Core, Java, Ruby, Node.js, PHP, or Python. Applications run and scale with ease on both Windows and Linux-based environments.

App Service not only adds the power of Microsoft Azure to your application, such as security, load balancing, autoscaling, and automated management. You can also take advantage of its DevOps capabilities, such as continuous deployment from Azure DevOps, GitHub, Docker Hub, and other sources, package management, staging environments, custom domain, and TLS/SSL certificates.

App Service on Linux supports a number of language specific built-in images. Just deploy your code. Supported languages include: Node.js, Java (JRE 8 & JRE 11), PHP, Python, .NET Core, and Ruby. Run az webapp list-runtimes --os linux to view the latest languages and supported versions. If the runtime your application requires is not supported in the built-in images, you can deploy it with a custom container.

**Note:**We use Azure App Service to host our application for all the environments.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/app-service/overview``](https://docs.microsoft.com/en-us/azure/app-service/overview)

## Static Website Hosting

You can serve static content (HTML, CSS, JavaScript, and image files) directly from a storage container named $web. Hosting your content in Azure Storage enables you to use serverless architectures that include Azure Functions and other Platform as a service (PaaS) services. Azure Storage static website hosting is a great option in cases where you don't require a web server to render content.

Static websites have some limitations. For example, If you want to configure headers, you'll have to use Azure Content Delivery Network (Azure CDN). There's no way to configure headers as part of the static website feature itself. Also, AuthN and AuthZ are not supported.

If these features are important for your scenario, consider using Azure Static Web Apps. It's a great alternative to static websites and is also appropriate in cases where you don't require a web server to render content. You can configure headers and AuthN / AuthZ is fully supported. Azure Static Web Apps also provides a fully managed continuous integration and continuous delivery (CI/CD) workflow from GitHub source to global deployment.

If you need a web server to render content, you can use Azure App Service.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website``](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website)

## Notification Hub or SignalR

Azure Notification Hubs provide an easy-to-use and scaled-out push engine that enables you to send notifications to any platform (iOS, Android, Windows, etc.) from any back-end (cloud or on-premises). Notification Hubs works great for both enterprise and consumer scenarios. Here are a few example scenarios:

- Send breaking news notifications to millions with low latency.
- Send location-based coupons to interested user segments.
- Send event-related notifications to users or groups for media/sports/finance/gaming applications.
- Push promotional contents to applications to engage and market to customers.
- Notify users of enterprise events such as new messages and work items.
- Send codes for multi-factor authentication.

**Push Notifications**
Push notifications are a form of app-to-user communication where users of mobile apps are notified of certain desired information, usually in a pop-up or dialog box on a mobile device. Users generally choose to view or dismiss the message; choosing the former opens the mobile application that communicated the notification. Some notifications are silent - delivered behind the scenes for the app to process and decide what to do.

Push notifications are vital for consumer apps in increasing app engagement and usage, and for enterprise apps in communicating up-to-date business information. It's the best app-to-user communication because it is energy-efficient for mobile devices, flexible for the notifications senders, and available when corresponding applications are not active.

  **How do push notifications work?**
  At a high level, here is how push works:

  - An application wants to receive a notification, so it contacts the PNS for the target platform on which the app is running and requests a unique and temporary push handle. The handle type depends on the system (for example, WNS uses URIs while APNS uses tokens).
  - The client app stores this handle in the app backend or provider.
  - To send a push notification, the app backend contacts the PNS using the handle to target a specific client app.
  - The PNS forwards the notification to the device specified by the handle.

#### References
Please refer to the below references for more detail-

- **Microsoft MDN Documentation**- 

[``https://docs.microsoft.com/en-us/azure/notification-hubs/notification-hubs-push-notification-overview``](https://docs.microsoft.com/en-us/azure/notification-hubs/notification-hubs-push-notification-overview)
















