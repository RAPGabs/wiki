---
id: thirdpartyintegration
title: Third Party Integration Using Adaptive API
---
 
The adaptive API takes in the input as the policy object, use JSONata transformation to convert the policy object to required request, then hit the desired API, fetch the response and then trandform the response into the desired output as specified to the adaptivr API.

Steps to get your transformation working with adaptive API:  
- **Create your adaptive API endpoint in APM**  
Create your own end point in the APM as shownin the image below.  
![Adaptive API Endpoint](../../static/img/docs/thirdpartyapi_endpoint.png)
- **Add the policy to the newly created endpoint**  
Policy is basically the definition of what you want to achieve through that API endpoint. So you need to add the policy of the endpoint. A sample policy is as below:
```xml
<policies>
    <inbound>
        <set-variable name="api" value="@(context.Request.Url.Query.GetValueOrDefault("api", ""))" />
        <set-variable name="inputData" value="@(context.Request.Body.As<JObject>())" />
        <cache-lookup-value key="token_ho" default-value="novalue" variable-name="accessToken" />
        <choose>
            <when condition="@((string)context.Variables["accessToken"] == "novalue")">
                <send-request mode="new" response-variable-name="tokenResponse" ignore-error="true">
                    <set-url>@($"https://vave.canopius.com/insure-dev/api/login")</set-url>
                    <set-method>POST</set-method>
                    <set-header name="Content-Type" exists-action="override">
                        <value>application/json</value>
                    </set-header>
                    <set-body>{
                        "username":"**************************",	
                        "password":"**************************"
                        }</set-body>
                </send-request>
                <set-variable name="accesstokenResponse" value="@(((IResponse)context.Variables["tokenResponse"]).Body.As<JObject>())" />
                <set-variable name="accessToken" value="@((string)((JObject)context.Variables["accesstokenResponse"])["access_token"])" />
                <cache-store-value key="token_ho" value="@((string)context.Variables["accessToken"])" duration="2400" />
            </when>
        </choose>
        <choose>
            <when condition="@((string)context.Variables["api"] == "pricenewquote")">
                <send-request mode="new" response-variable-name="pricenewResponse" ignore-error="true">
                    <set-url>@($"https://vave.canopius.com/insure-dev/api/Quote/PriceNew")</set-url>
                    <set-method>POST</set-method>
                    <set-header name="Content-Type" exists-action="override">
                        <value>application/json</value>
                    </set-header>
                    <set-header name="Authorization" exists-action="override">
                        <value>@("Bearer " + (string)context.Variables["accessToken"])</value>
                    </set-header>
                    <set-body>@{JObject output = new JObject();
                output = ((JObject)((JObject)context.Variables["inputData"])["Vave"]);
                return output.ToString();
                }</set-body>
                </send-request>
                <return-response>
                    <set-status code="200" reason="OK" />
                    <set-header name="Content-Type" exists-action="override">
                        <value>application/json</value>
                    </set-header>
                    <set-body>@(new JObject(new JProperty("Output",(((IResponse)context.Variables["pricenewResponse"]).Body.As<JObject>())),
                  new JProperty("Input",((JObject)context.Variables["inputData"])["DIEP"])
                  ).ToString())</set-body>
                </return-response>
            </when>
            <otherwise>
                <return-response>
                    <set-status code="500" reason="Invalid API Input" />
                    <set-header name="Content-Type" exists-action="override">
                        <value>text/plain</value>
                    </set-header>
                </return-response>
            </otherwise>
        </choose>
        <base />
    </inbound>
    <backend>
        <base />
    </backend>
    <outbound>
        <base />
    </outbound>
    <on-error>
        <base />
        <set-header name="ErrorSource" exists-action="override">
            <value>@(context.LastError.Source)</value>
        </set-header>
        <set-header name="ErrorReason" exists-action="override">
            <value>@(context.LastError.Reason)</value>
        </set-header>
        <set-header name="ErrorMessage" exists-action="override">
            <value>@(context.LastError.Message)</value>
        </set-header>
        <set-header name="ErrorScope" exists-action="override">
            <value>@(context.LastError.Scope)</value>
        </set-header>
        <set-header name="ErrorSection" exists-action="override">
            <value>@(context.LastError.Section)</value>
        </set-header>
        <set-header name="ErrorPath" exists-action="override">
            <value>@(context.LastError.Path)</value>
        </set-header>
        <set-header name="ErrorPolicyId" exists-action="override">
            <value>@(context.LastError.PolicyId)</value>
        </set-header>
        <set-header name="ErrorStatusCode" exists-action="override">
            <value>@(context.Response.StatusCode.ToString())</value>
        </set-header>
    </on-error>
</policies>
```  
Once this is done, you are ready to create transformations and create input and output keys.

- **Transformation of request**  
First task is to identify what are the different type of requests we need to create. That is the number of json files we will have to create for transformation. Each json file contains the following 6 attributes:
  * transformationType - What type of transformation we are using e.g. JSONATA
  * transformationExpression - Optional
  * key - Identifier of this json file
  * description - Optional
  * forwardingUrl - Contains the URL of the API endpoint that you created earlier with the action. Basically, what URL to call once the transformation is complete.
  * file - Refers to the JS file that it uses for transformation  
  Sample request json is as follows:
  ```jsx
    {
        "transformationType": "JSONATA",
        "transformationExpression":"",
        "key": "VaveQuote_PriceNewQuote_Request",
        "description": "",
        "forwardingUrl": "https://adaptiveapiapm.azure-api.net/rpsvave/rpsvave/Invoke?api=pricenewquote",
        "file":"RPSVavePriceNewQuoteQuoteRequest.js"
    }
  ```
  Now, we have to create a JS transformation file which is to be written in JSONATA or any other transformation type approved in the project. For JSONATA practice, you can use the following links:  
  * [TRY JSONATA](https://try.jsonata.org/)
  * [JSONATA DOCUMENTATION](http://docs.jsonata.org/overview.html)

- **Transformation of response**  
In the similar manner of request, we will need to create json and transformation for response as well.  
Sample response json is as follows:
  ```jsx
    {
        "transformationType": "JSONATA",
        "transformationExpression":"",
        "key": "VaveApplication_PolicyModel_Response",
        "description": "",
        "forwardingUrl": "",
        "file":"RPSVavePolicyModelResponse.js"
    }
  ```
  Here we can see the forwardingUrl is empty as we do not have to call another API after transforming the response.  

**For more details you can read the following document**  
[Adaptive API Documentation](/docs/diep2/adaptiveapi) 