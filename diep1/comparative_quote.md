---
id: comparative quote
title: Comparative Quote
---

- **Create Comparative Quote configuration JSON**  
To get a comparative quote we need to create a JSON file with configuration for the all the available carriers and LOB that we are working with. The JSON file contains array of JSON elements one for each carriera and LOB combination.  
Each JSON element contains key value pair of attributes that are required to fetch quote. Basically, we read this json file and identify what all rating APIs we need to hit to get the comaparative rate.  
Some important attributes:  
  * **State** - This is comma separated field, and we need to pass the value of state codes in this for which state this Carrier and LOB is allowing us to give rate.
  * **Area** - In our project we segregate our code in areas depending on the LOBs we have in our database. For some carrier, two LOBs can behave similarly, i.e. we can same API for rating, and for others it may be different. So this also a comma separated field to club together samilar rating LOBs for particular carriers.
  * **APIUrl** - The URL we need to call for rating. This URL can be of adaptive api in case it is third party rater or it can be the application URL that points to the rater class GetQuote function. Use dependency injection through unity to call this method through API. 
  ```xml
  <register name="LLRSHO3" type="RaterQuoteBusiness" mapTo="Cogitate.DIEP.Impl.RPS.HO3.Business.Rater,Cogitate.DIEP.Impl.RPS.HO3.Business"/>
  <register name="LLRSHO6" type="RaterQuoteBusiness" mapTo="Cogitate.DIEP.Impl.RPS.HO6.Business.Rater,Cogitate.DIEP.Impl.RPS.HO6.Business"/>
  ```
  The name is the combination of carrier code, coverholder code and lob code. 
  * **SubscriptionKey** - If we are using adaptive API for transformation, we must provide the Subscription Key for the APM.
  * **InHouseRater** - Boolean value that tells us if the rater is third party or developed by Cogitate itself.  
  Sample of the complete json file is as follows: 
  ```jsx
    [
        {
            "Carrier": "Lloyd's 201",
            "CarrierCode": "VA",
            "Area": "HO3,HO6",
            "CompanyCode": "VARS",
            "LOBCode": "HO3",
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
            "Area": "HO3",
            "CompanyCode": "LLRS",
            "LOBCode": "9",
            "State": "FL,NJ,GA,SC",
            "InHouseRater": true,
            "APIUrl": "http://localhost:55188/api/RaterAPI/GetQuote",
            "SubscriptionKey": "49ecd203b39d4243b0baf206db3a82e7",
            "FeeAndTaxOverrideURL": "http://localhost:55188/api/RaterAPI/GetOverrideFee",
        },
        {
            "Carrier": "Lloyd's 101",
            "CarrierCode": "LL",
            "Area": "HO6",
            "CompanyCode": "LLRS",
            "LOBCode": "8",
            "State": "FL,NJ",
            "InHouseRater": true,
            "APIUrl": "http://localhost:55188/api/RaterAPI/GetQuote",
            "SubscriptionKey": "49ecd203b39d4243b0baf206db3a82e7",
            "FeeAndTaxOverrideURL": "http://localhost:55188/api/RaterAPI/GetOverrideFee",
        }
    ]
    ```

- **Clone the policy object**  
After parsing through the comparative JSON file we will identify what all different APIs we need to call to fetch the comparative rates. All these calls will be parallel. But before calling the actual API we need to clone the policy object so as not to update any other policy object. Moreover we need to update certain parameters in the policy object according to which carrier and what LOB we are calling, so only that object needs to be updated and not impact any other API call.
        
    public static T CloneObject<T>(this T self)
    {
        var serialized = JsonConvert.SerializeObject(self);
        return JsonConvert.DeserializeObject<T>(serialized);
    }

- **Update policy object with default values**  
We need to update the policy object before each API call so that we can send the default values to different APIs according to the carrier and LOB. For this we would use the individual cloned object for our API call and update it values in that object using another json file i.e. MultipleDefaults JSON. This file stores the default values of coverages, deducticle and other attributes of policy that might change with LOB or Occupancy. Now, premium also can be split up into different types i.e. Selected(the values selected by the user), Basic(Lower end values) and Premium(High end values). To get these premiums as well we follow the same approach and clone the policy object based on the MultipleDefaults file which has bifurcation for the premium types as well.  
Code to read data from the defaults files is as follows:  
  ```cs
private PolicyInfo SetClonePolicyByType(PolicyInfo policyInfo, string state, string lobCode, string companyCode, string type)
{
    PolicyInfo policyInfoClone;
    var unitAttr = policyInfo.PolicyUnits.FirstOrDefault(x => x.UnitNumber == 1).UnitAttributes;
    var occType = unitAttr.FirstOrDefault(y => y.LOBAttribute.Code == "OCCU").Value;
    var listOfDefaultAttrList = GetMultipleDefaultsJson(lobCode, state, companyCode, type, occType);
    policyInfoClone = policyInfo.CloneObject();
    policyInfoClone.PolicyLOBAttributes.FirstOrDefault(x => x.LOBAttribute.Code == "QUOTETYPE").Value = type == "Defaults" "Selected" : type
    var cloneUnitAttr = policyInfoClone.PolicyUnits.FirstOrDefault(x => x.UnitNumber == 1).UnitAttributes
    foreach (var jObj in listOfDefaultAttrList)
    {
        var attr = cloneUnitAttr.FirstOrDefault(x => x.LOBAttribute.Code == (string) ( ( (Newtonsoft.Json.Linq.JValue) jO["Code"] ).Value ));
        if (attr != null)
        {
            if ((string) ( ( (Newtonsoft.Json.Linq.JValue) jObj["ValueType"] ).Value ) == "V")
            {
                attr.Value = (string) ( ( (Newtonsoft.Json.Linq.JValue) jObj["Value"] ).Value );
            }
            else if ((string) ( ( (Newtonsoft.Json.Linq.JValue) jObj["ValueType"] ).Value ) == "P")
            {
                string codeToCompare = (string) ( ( (Newtonsoft.Json.Linq.JValue) jObj["PercentOf"] ).Value );
                string percentValue = (string) ( ( (Newtonsoft.Json.Linq.JValue) jObj["Value"] ).Value );
                var attrToCalc = cloneUnitAttr.FirstOrDefault(y => y.LOBAttribute.Code == codeToCompare);
                string valueToCalc = "0";
                if (attrToCalc != null)
                {
                    valueToCalc = attrToCalc.Value;
                }
                decimal.TryParse(valueToCalc, out decimal val);
                decimal.TryParse(percentValue, out decimal percentVal)
                attr.Value = ( decimal.Floor(percentVal / 100 * val) ).ToString();
            }
        }
    
    return policyInfoClone;
}
  ```

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
We have modified all the clone of policy objects and now we use these updated policy objects to call the different APIs. The InHouse Rater APIs accept the policy object as it is, but for the third party rater APIs we need to transform the request into the acceptable request form by the thrid party API. This is where the adaptive API of Cogitate comes in.  
[Third Party Integration Link](/docs/diep1/thirdpartyintegration)

- **Response of Comparative Quote**  
Once all the API are called and they give the response, we make sure that all the api responses are in similar format just as we ensured all the request were in similar format. The response format is what we call Quote Version. So if we hit 6 different APIs at the time of quick  quote then we get 6 quote version responses.  
A sample quote version response is as follows:  
  ```jsx
  {
    "QuoteId": 0,
    "PolicyInfoId": 4127,
    "ProductCode": "VARSHO3NJ",
    "Version": "",
    "Quoted": "2022-10-18 17:52:00Z",
    "Expires": "",
    "PremiumWTaxAndFee": 0,
    "Premium": 2682.31,
    "TotalTaxAndFee": 0,
    "TaxJson": null,
    "QuoteType": "Selected",
    "PropertyJson": "{\"FirstName\":\"Maralyn\",\"MiddleName\":null,\"LastName\":\"Mason\",\"DOB\":null,\"LLCNAM\":null,\"OCCU\":\"Secondary\",\"YEARBUILT\":\"1990\",\"YEARUPD\":\"1990\",\"SQFEET\":\"1258\",\"STRENTAL\":\"no\",\"PPC\":\"1\",\"TermLength\":12,\"CONSTRTYPE\":\"FRAME\",\"PERILS\":\"All Risks\",\"DISTTOCOAST\":\"0.6585\",\"NOOFCLAIMS\":\"0\"}",
    "CoverageJson": "{\"Coverages\":[{\"Name\":\"Coverage A\",\"Code\":\"DWELAMNT\",\"Value\":\"241000\",\"DisplayValue\":\"$241,000\",\"Section\":\"Primary Coverages\"},{\"Name\":\"Coverage B\",\"Code\":\"COVB\",\"Value\":\"24100\",\"DisplayValue\":\"$24,100\",\"Section\":\"Primary Coverages\"},{\"Name\":\"Coverage C\",\"Code\":\"CPP\",\"Value\":\"120500\",\"DisplayValue\":\"$120,500\",\"Section\":\"Primary Coverages\"},{\"Name\":\"Coverage D\",\"Code\":\"DLOU\",\"Value\":\"48200\",\"DisplayValue\":\"$48,200\",\"Section\":\"Primary Coverages\"},{\"Name\":\"Coverage E\",\"Code\":\"LIAB\",\"Value\":\"300000\",\"DisplayValue\":\"$300,000\",\"Section\":\"Primary Coverages\"},{\"Name\":\"Coverage F\",\"Code\":\"MEDPAY\",\"Value\":\"5000\",\"DisplayValue\":\"$5,000\",\"Section\":\"Primary Coverages\"},{\"Name\":\"Perils\",\"Code\":\"PERILS\",\"Value\":\"All Risks\",\"DisplayValue\":\"With Wind\",\"Section\":\"Additional Coverages\"},{\"Name\":\"Mold\",\"Code\":\"MOLD\",\"Value\":\"0\",\"DisplayValue\":\"<img src=\\\"https://asyncdev1.blob.core.windows.net/rps-style/v1/images/closingIcon.svg\\\" alt=\\\"Excluded\\\">\",\"Section\":\"Additional Coverages\"},{\"Name\":\"Loss Assessment\",\"Code\":\"LA\",\"Value\":\"1000\",\"DisplayValue\":\"$1,000\",\"Section\":\"Additional Coverages\"},{\"Name\":\"Water Backup\",\"Code\":\"WATERBK\",\"Value\":\"10000\",\"DisplayValue\":\"$10,000\",\"Section\":\"Additional Coverages\"},{\"Name\":\"Personal Injury\",\"Code\":\"PERSONALINJ\",\"Value\":\"300000\",\"DisplayValue\":\"$300,000\",\"Section\":\"Additional Coverages\"},{\"Name\":\"ID Fraud\",\"Code\":\"IDFRAUD\",\"Value\":\"15000\",\"DisplayValue\":\"$15,000\",\"Section\":\"Additional Coverages\"},{\"Name\":\"AOP Deductible\",\"Code\":\"AOP\",\"Value\":\"1000\",\"DisplayValue\":\"$1,000\",\"Section\":\"Deductibles\"},{\"Name\":\"Wind & Hail Deductible\",\"Code\":\"WINDED\",\"Value\":\"2\",\"DisplayValue\":\"2%\",\"Section\":\"Deductibles\"},{\"Name\":\"Alerts\",\"Code\":\"RATERERROR\",\"DisplayValue\":\"\",\"Value\":\"\",\"Section\":\"Rating Alerts\"}]}",
    "CarrierInfo": "{\"PricingId\":4776085}",
    "IsSelected": false,
    "CreatedBy": 0,
    "UpdatedBy": null,
    "UpdatedOn": null,
    "Status": "",
    "CarrierName": "Lloyd's 201",
    "CreatedOn": "2022-10-18T17:52:08.941Z"
}
  ```
  Most of the nodes of this response are self explainatory, but the three important nodes are:  
  * **PropertyJson** - Contains the information about the property
  * **CoverageJson** - Contains the information about the coverage that we have updated and sent to the API
  * **CarrierInfo** - Contains any information that we want to store back from the actual API response into our database for further use. Like in case of Vave, we are storing Pricing ID.

- **Storing responses in database**  
We store all the Quote Version response that we get from the API into our database. We have added a table in our database that stores specifically this data into our database. And once the user selects one of the Quote Version, we mark the IsSelected flag as true and update the final policy object according to the Property Json and Coverage Json data of the selected quote version.
