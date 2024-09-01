---
id: ssointegration
title: SSO Integration
---

Logging into a DIEP 2.0 application is done through SSO (Single Sign-On).  
After logging in, the application and its features are accessible as per the user role and features.  
## Initial Registrations
SSO would require registration for
- **Site** - A new site needs to be registered at SSO Admin portal, in order for the login requests to process at SSO.  
    ![Register New Site](../../static/img/docs/diep2/ssointegration_register_site.png)
- **Product** - A new product needs to be created under the site, for each specific product that the site will have.  
    ![Register New Product](../../static/img/docs/diep2/ssointegration_register_product.png)
- **Users** - Once a site is registered at SSO, new users can be created under that Site, under different roles.  
    ![Create New User](../../static/img/docs/diep2/ssointegration_register_user.png)

## Keys Required for Integration
The application requires below values for a successful SSO integration:-
<ul>
    <li>
        SSO URL - This will be the SSO API URL for Authentication.
        Example: <b><i>https://test.cogitate.us/SSO/api/Login/GenerateJwtToken</i></b>
    </li>
    <li>
        Site ID - This can be obtained through the SSO Admin Portal. The Site ID will be different around SSO environments.
    </li>
    <li>
        Product ID - This can be obtained through the SSO Admin Portal. The Product ID will be different around SSO environments, just like the Site ID differs around environments.
    </li>
</ul>

## Process
Once all the pre-requisites are done, the integration process can be started for SSO.
1. Create a payload for user validation through SSO.
```jsx
const payLoad = {
      username: 'username_for_user',
      password: 'p@ssW0rd',
      productId: 123
    };
```
The values for properties ***'username'*** and ***'password'*** are to be taken as a user input from the User Interface. The value for property ***'productId'*** can be read from the Configuration file itself.

2. Generate headers for the request.
```jsx
const headers = {
      siteId: 345,
      'Content-Type': 'application/json'
    };
```
The value for property ***'siteId'*** can be read from the Configuration file itself.

3. Now, using the ***payload*** and the ***headers*** generated in the steps above, you can hit the SSO API, in order to get the response data.
```jsx
const ssoResponse = await callAPI("POST", requestURL, payLoad, headers);
```
The value for parameter ***'requestURL'*** can be read from the Configuration file itself. This is the SSO API URL for authentication.

A 200 response status from SSO API means that the request was success, and the user information in the request payload was successfully validated by SSO. If a success status is not received, an error message can be shown to the user accordingly.  

4. The complete response can now be stored for further use in the application.
An example of parsing required response SSO data is shown below:
```jsx
let tokenExpiryDate = new Date();
      const result = {
        encodedJWT: ssoResponse.ResponseObject.Token,
        JWTValidTill: tokenExpiryDate.setSeconds(tokenExpiryDate.getSeconds() + parseInt(ssoResponse.ResponseObject.ValidForSeconds)),
        decodedJWT: jwt.decode(ssoResponse.ResponseObject.Token)
      };
```

***This marks the successful integration of SSO in a DIEP 2.0 implementation.***