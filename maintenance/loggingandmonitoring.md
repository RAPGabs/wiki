---
id: loggingandmonitoring
title: Logging And Monitoring
---

### Logging
We all start with writing a bunch of console.log statements in our work-in-progress React components. But then, you find yourself tracking these guys down because it’s not great to have users see all the console logs in a production app. That is where Logging comes into picture. Logging activities in the application helps understand the application behaviour as well as the user behaviour as well. We have used AppInsights for logging and monitoring in our application.

### What is AppInsights
AppInsights (Application Insights in its long-form) is part of the Azure Monitor platform and is a performance monitoring platform that can be used in applications from web to mobile, across a number of languages. The most important feature of AppInsights is capturing information such as page views, errors (handled and unhandled) and AJAX calls (XML HTTP Request and Fetch). Combining this both client and server can make it useful to provide a full view of a user’s interactions on your site. 

We have used two react library which are the wrapper function the AppInsight SDK for JavaScript. The two libraries are @microsoft/applicationinsights-react-js and @microsoft/applicationinsights-web.

>![UI_AppInsights](../../static/img/docs/diep2/app_insights.png)

This file is responsible for two things, the first is to set up the AppInsights connection using the key provided (we’re using an environment variable to store this which allows us to use a different one on each environment) and the second job is to export a Higher Order Component (HOC) that provides our AppInsights instance to the HOC provided by the React extension (this is just a convenience approach, you don’t need to wrap the HOC if you’d prefer not to add additional components).


>![UI_Exception_Function](../../static/img/docs/diep2/exception_function.png)

As we see, there is whole lot of information logged when the page or API breaks down. The app signifies, what failed - page or API. Error message is the actual message which either comes from the component which breaks or the error coming from the API. The other variables are straight forward to understand.

### Monitoring
Every application needs to be monitored, and this need for customer facing applications is more critical, to understand its needs and improve it based on their usage patterns and feedback. To achieve that though, we need to collect data, technical and behavioural logs, to analyse and understand patterns. It's then that we can make meaningful and strategic changes to scale, improve and grow the software base.


We want to monitor the application on all the end. Firstly we are tracking the failure on the frontend. If anything breaks, the AppInsight API is called through the above wrapper function. Next we also track if any API fails to execute. This gives us more insights on how our application behaves. We also track what exactly is breaking down. On the backend we have done the same setup to call the AppInsight API Wrapper Function.

### Backend
In the backend as well, we have a similar wrapper library for the AppInsight SDK. We have similar function to be called for logging API request and their characteristics.

