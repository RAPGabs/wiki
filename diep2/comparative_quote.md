---
id: comparative quote
title: Comparative Quote
---

- **Create Comparative Quote configuration JSON**  
To get a comparative quote we need to create a JSON file with configuration for the all the available carriers and LOB that we are working with. The JSON file contains array of JSON elements one for each carriera and LOB combination.  
Each JSON element contains key value pair of attributes that are required to fetch quote. Basically, we read this json file and identify what all rating APIs we need to hit to get the comaparative rate.  
Some important attributes:  
  * **State** - This is comma separated field, and we need to pass the value of state codes in this for which state this Carrier and LOB is allowing us to give rate.
  * **LOB** - This is also a comma separated field to club together similar rating LOBs for particular carriers.
  * **APIUrl** - The URL we need to call for rating. This URL can be of adaptive api in case it is third party rater or it can be the application URL that points to the rater class GetQuote function. Use dependency injection through unity to call this method through API. 
  The name is the combination of carrier code, coverholder code and lob code. 
  * **SubscriptionKey** - If we are using adaptive API for transformation, we must provide the Subscription Key for the APM.
  * **InHouseRater** - Boolean value that tells us if the rater is third party or developed by Cogitate itself.  
  Sample of the complete json file is as follows: 
  ```jsx
    [
        {
            "Carrier": "Lloyd's 201",
            "CarrierCode": "VA",
            "LOB": "HO3,HO6",
            "CompanyCode": "VARS",
            "State": "FL,NJ,GA,SC",
            "InHouseRater": false,
            "APIUrl": "https://adaptiveapiapm.azure-api.net/api/invoke?inputkey=VaveQuote_PriceNewQuote_Request&outputkey=VaveQuote_PriceNewQuote_Response",
            "SubscriptionKey": "************",
            "FeeAndTaxOverrideURL": "http://localhost:55189/api/PolicyDetails/OverrideFee",
            "QuoteRedirectionURL": "http://localhost:55189/Status/ValidateRedirectionToken",
            "BaseUrl": "http://localhost:55189/",
            
        },
        {
            "Carrier": "Lloyd's 101",
            "CarrierCode": "LL",
            "LOB": "HO3",
            "CompanyCode": "LLRS",
            "State": "FL,NJ,GA,SC",
            "InHouseRater": true,
            "APIUrl": "http://localhost:55188/api/RaterAPI/GetQuote",
            "SubscriptionKey": "49ecd203b39d4243b0baf206db3a82e7",
            "FeeAndTaxOverrideURL": "http://localhost:55188/api/RaterAPI/GetOverrideFee",
        },
        {
            "Carrier": "Lloyd's 101",
            "CarrierCode": "LL",
            "LOB": "HO6",
            "CompanyCode": "LLRS",
            "State": "FL,NJ",
            "InHouseRater": true,
            "APIUrl": "http://localhost:55188/api/RaterAPI/GetQuote",
            "SubscriptionKey": "49ecd203b39d4243b0baf206db3a82e7",
            "FeeAndTaxOverrideURL": "http://localhost:55188/api/RaterAPI/GetOverrideFee",
        }
    ]
    ```

- **Clone the policy object**  
After parsing through the comparative JSON file we will identify what all different APIs we need to call to fetch the comparative rates. All these calls will be parallel. But before calling the actual API we will have to modify each policy object as different carrier or different lob may expect different values for hidden coverages or deductibles. As our policy object can be complex, we need to deep clone the object. We can do this using lodash.
```jsx
const lodashClonedeep = require('lodash.clonedeep');

const arrOfFunction = [
  () => 2,
  {
    test: () => 3,
  },
  Symbol('4'),
];

// deepClone copy by refence function and Symbol
console.log(lodashClonedeep(arrOfFunction));
```

- **Update policy object with default values**  
We need to update the policy object before each API call so that we can send different default values to different APIs according to the carrier and LOB. For this we would use the individual cloned object for our API call and update it values in that object using another json file i.e. MultipleDefaults JSON. This file stores the default values of coverages, deducticle and other attributes of policy that might change with LOB or Occupancy. Now, premium also can be split up into different types i.e. Selected(the values selected by the user), Basic(Lower end values) and Premium(High end values). To get these premiums as well we follow the same approach and clone the policy object based on the MultipleDefaults file which has bifurcation for the premium types as well.  

The Multiple Defaults JSON can be designed as below:  

```jsx
[{
	"Type": "Defaults",
	"Collection": [{
		"Group": "Primary",
		"Values": [{
				"Name": "Personal Liability",
				"Code": "LIAB",
				"Value": "300000",
				"ValueType":"V"
			},
			{
				"Name": "Medical Payment",
				"Code": "MEDPAY",
				"Value": "5000",
				"ValueType":"V"
			},
			{
				"Name": "Mold",
				"Code": "MOLD",
				"Value": "25000",
				"ValueType":"V"
			},
			{
				"Name": "Wind Deductible",
				"Code": "WINDED",
				"Value": "2",
				"ValueType":"V"
			},
			{
				"Name": "All Other Perils",
				"Code": "AOP",
				"Value": "2500",
				"ValueType":"V"
			},
			{
				"Name": "Maximum Coverage D",
				"Code": "MAXCOVD",
				"Value": "70",
				"ValueType":"P",
				"PercentOf":"DWELAMNT"
			}
		]
	},{
		"Group": "Secondary",
		"Values": [{
				"Name": "Personal Liability",
				"Code": "LIAB",
				"Value": "300000",
				"ValueType":"V"
			},
			{
				"Name": "Medical Payment",
				"Code": "MEDPAY",
				"Value": "5000",
				"ValueType":"V"
			},
			{
				"Name": "Mold",
				"Code": "MOLD",
				"Value": "25000",
				"ValueType":"V"
			},
			{
				"Name": "All Other Perils",
				"Code": "AOP",
				"Value": "2500",
				"ValueType":"V"
			},
			{
				"Name": "ID Fraud",
				"Code": "IDFRAUD",
				"Value": "0",
				"ValueType":"V"
			},
			{
				"Name": "Minimum Coverage D",
				"Code": "MINCOVD",
				"Value": "10",
				"ValueType":"P",
				"PercentOf":"DWELAMNT"
			},
			{
				"Name": "Maximum Coverage D",
				"Code": "MAXCOVD",
				"Value": "70",
				"ValueType":"P",
				"PercentOf":"DWELAMNT"
			}
		]
	}]
},{
	"Type": "Basic",
	"Collection": [{
		"Group": "Primary",
		"Values": [{
				"Name": "Personal Liability",
				"Code": "LIAB",
				"Value": "300000",
				"ValueType":"V"
			},
			{
				"Name": "Medical Payment",
				"Code": "MEDPAY",
				"Value": "5000",
				"ValueType":"V"
			},
			{
				"Name": "Personal Injury",
				"Code": "PERSONALINJ",
				"Value": "no",
				"ValueType":"V"
			},
			{
				"Name": "Mechanical Breakdown",
				"Code": "MECHBR",
				"Value": "Excluded",
				"ValueType":"V"
			}
		]
	},
	{
		"Group": "Secondary",
		"Values": [{
				"Name": "Personal Liability",
				"Code": "LIAB",
				"Value": "300000",
				"ValueType":"V"
			},
			{
				"Name": "Medical Payment",
				"Code": "MEDPAY",
				"Value": "5000",
				"ValueType":"V"
			},
			{
				"Name": "Personal Injury",
				"Code": "PERSONALINJ",
				"Value": "no",
				"ValueType":"V"
			},
			{
				"Name": "Mechanical Breakdown",
				"Code": "MECHBR",
				"Value": "Excluded",
				"ValueType":"V"
			}
		]
	}]
}]
```

- **Transformation of request and response and use of adaptive API**  
We have modified all the clone of policy objects and now we use these updated policy objects to call the different APIs. As mentioned, all the APIs will follow the adaptive API structure and thus, we would need to transform the request into the acceptable request form by the thrid party API.
[Third Party Integration Link](/docs/diep1/thirdpartyintegration)

- **Calling the APIs**  
All the APIs that we would be calling should invoked from Cogitate's adaptive API, so that we have control over the transformation of request and response. One more challenge that we can face is sometimes we would be required to call multiple APIs one after the other such as 1. to get the premium from third party 2. to calculate fees and taxes depending on that premium.  
So in this case, we need to modify our comparative quote json file and have comma separate URLs in APIUrl attribute.
  ```jsx
"APIUrl": "https://adaptiveapiapm.azure-api.net/api/invoke?inputkey=VaveQuote_PriceNewQuote_Request&outputkey=VaveQuote_PriceNewQuote_Response,http://localhost:55189/api/PolicyDetails/OverrideFee",
  ```   
  By this chaining of URLs we can actually configure the sequence of activities if required. So, we will pass these URLs to Rater function, and the rater function will split them using the delimeter i.e. comma, and then we will call the first url. We will have to keep in mind that the output of the first URL will become the input to the next URL in line and the last URL response will become the final response of the rater function.  

- **Response of Comparative Quote**  
The output of the Rater function will be in the form of our policy object itself with all the Premium and Fees and Taxes updated in it. Also, rater function will itself push this policy object into a separate container 'comparative quote'.  
Here the objects will be grouped by a quote number and we will have a 'selected resource' flag against each object which will initially be set to false. Once the user select any particular carrier to proceed with, we will mark the 'selected resource' as true for that object only and push that object into main container of policies.