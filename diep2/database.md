---

id: database

title: Database

---
## I. Containers and Use Cases

### 1. Agencies Container
This container consists document having object representing details of different agencies to be used in the application. Below is sample object for reference
>![Agency_Object](../../static/img/docs/azure/SampleAgencyObject.png)
>[Agency Object](../../static/img/docs/azure/SampleAgencyObject.png)

- The Client parameter represents the different Client the specificied Agency will be used in.
- The Code parameter represents the Agency code.
- The Products parameter represents different products of the specified client, the Agency will have access too.
- The References array stores the list of different Agents belonging to the specified Agency.

### 2. Agents Container
This container consists document having object representing detail of different agents to be used in the application. Below is sample object for reference
>![Agenct_Object](../../static/img/docs/azure/SampleAgentObject.png)
>[Agenct Object](../../static/img/docs/azure/SampleAgentObject.png)

- The Client parameter represents the different Client the specificied Agent has access to.
- The Code parameter represents the Agenct code as registered in SSO.
- The Products parameter represents different products of the specified client, the Agent will have access too.
- The References array stores the list of different Agency, the specified Agent belong to.

### 3. AMS Container
This container is created for storing the Policy Data Model given to us by different Client Platform like TurboRater, etc.
This policy is used by rater for calculation and the response send back to the Client Platform is also stored in this container.
Primary Nodes in this document are:-
- **AppSource**:- Representing the source of request for this policy object.
- **AMSReferenceId**:- Used as Partition key and also for fetching the Particular Object.
- **Request**:- This holds the request that came from the third party platform.
- **Response**:- This holds the rated response sent back to the third party platform, which can also be used by our application.

### 4. Comparative Rater Container
At the time of comparative rating there are multiple responses from the different rater used at the time of Quote. These responses from different Rater's are stored here and used to show comparitive rating data to user. When the user selects on the comparitive rate we update the selected index in this container object and Selected Carrier detail in Policy Conatiner document marking which one of the rater(Carrier) the user selected and from later on in Application we use that Carrier only.

### 5. Conflicts Container
This container is created for custom requirement of showing all the conflicts to the user at the time of OOS Endorsement.

### 6. LCNC Container
This container is used by LCNC for maintaing its record for different client/carrier. This is not directly modified or used by DIEP2 implemented application.

### 7. Masters Container
This is one of the most important container holding the master data used by different application. It holds multiple kind of data like:
1. **Product Details Master** :- This document contains core details of any client application. Below is an attached image.
>![Product Master Object](../../static/img/docs/azure/ProductMaster.png)
>[Product_Master_Object](../../static/img/docs/azure/ProductMaster.png)

- **Client** :- This parameter is used to distinguish that this master belong to which client
- **Table** :- This parameter is used to distinguish what content this master for of the particular client does the document holds.
- **Rows** :- This is an array holding data of the particular document.

**Note**:- The **productcode** and **LastSequenceNo** is used for generating Policy Number. Similarly all parameter in this Product Master document holds prime importance.

2. **Fees And Taxes Master** :- Every client provides a list of different fees and taxes applicable on its different products, which can vary on the basis of different state too. Below is an image of FeesAndTaxes master document.
>![Fees And Taxes Master](../../static/img/docs/azure/FeesAndTaxesMaster.png)
>[Fees_And_Taxes_Object](../../static/img/docs/azure/FeesAndTaxesMaster.png)

- **Client** :- This parameter is used to distinguish that this master belong to which client
- **Table** :- This parameter is used to distinguish what content this master for of the particular client does the document holds.
- **Rows** :- This is an array holding data of the particular document.
- **Code**:- Inside each object Code represents Fee/Tax Code.
- **Product**:- Represents for which product this Fee/Tax is applicable.
- **Transactions**:- Represent the transaction in which that Fee/Tax is applicable.

**Note**:- Code, Product, Transactions is used by rater for adding that particular Fee/Tax.

**Note**:- Apart from these there can be different master object as per requirement of client or product implementation. Basically any static data used throughout the application and/or can be used by other service too like rater can be kept in form of master data document in this container.

### 8. Notifications Container
This container is created for event triggering of notifications. Whenever there is a status change of Policy by some actions performed by Agent, UW or Insured. This container will have a new/modified object representing that action. On change of object or addition of new object and new notification will be triggered on the contact details in the new object.
This is yet to be implemented in project.

### 9. OOS Container
This container is used for maintaining the Out Of Sequence Policies. When a out of sequence transaction is triggered. All the future policies are kept here. The current Policy container holds the latest previous policy object. The operation is performed on the Policy Container object then on its bind, all these policies are checked for conflicts and also these policies are updated if any required changes are made in back date OOS Endorsed Policy.

### 10. Policy Container
The most important container among all. This container holds the lates policy object. While Load of application the list of policies belonging to the particular Client is fetched and shown on Accounthub. On every page submission the details are updated into this container. This container is used by Form Factory for fetching its required data, versions for keeping the latest object, and for many important usage of the application.

The Partition Key for this container is Quote Number of the policy, which is created when the first Post Item call is made from the application. Using the last submitted page Generate Quote Number hook is called which creates the Quote Number and then the object is pushed into the Policy container.

The small id "id" field is field used by Cosmos for distinguishing every object.
The details about Policy Model is present in Data Model documentation section

**Sample Policy Object**
```bash
{
    "id": "97a330ae-9979-4a0a-9e88-52b952e2bf6b",
    "AccountId": "UW",
    "QuoteNumber": "QENGS1IL220127",
    "IsPolicyBind": "false",
    "PolicyNumber": "",
    "PolicyTerm": "365",
    "AgentCommission": "0",
    "EffectiveDate": "2022-09-30",
    "ExpirationDate": "2023-09-30",
    "IsRenewed": "false",
    "BindDate": "2022-09-30",
    "QuoteDate": "2022-09-30",
    "PolicyStatus": "Application",
    "CurrentVersion": "1.0",
    "CurrentVersionEffectiveFrom": "",
    "NoOfTimesRenewed": "0",
    "QuoteExpDate": "0",
    "RenewalTerm": "0",
    "PayMode": "",
    "Claims": [
        {
            "ClaimSequence": "",
            "DateofLoss": "",
            "Amount": "",
            "IncidentType": "",
            "Remark": ""
        }
    ],
    "Agent": {
        // Similar as Underwriter - Agent Container Object
    },
    "Agency": {
      // Similar as Underwriter - Agency Container Object
    },
    "UnderWriter": {
        "Client": "ENGS",
        "Code": "13530",
        "Name": "Roman Hunter",
        "Status": "Active",
        "Products": [
            "ENGS1IL"
        ],
        "Reference": [
            "202001"
        ],
        "Details": {
            "Contact": {
                "HomePhone": "0XX-XXX-XX",
                "BusinessPhone": "+919599400141",
                "Fax": "0XX-XXX-XX00",
                "MobilePhone": "0XX-XXX-XX",
                "SendSms": false,
                "EmailId": "msingh@cogitate.us",
                "SendQuoteEmail": false,
                "QuoteEmailId": "rXXX@XXXX.com",
                "SendPolicyEmail": false,
                "PolicyEmailId": "rXXX@XXXX.com",
                "FromEmailId": "rXXX@XXXX.com",
                "EmailCCId": "rXXX@XXXX.com",
                "PreferedContactType": "E",
                "SecondaryEmailId": "rXXX@XXXX.com"
            },
            "Address": {
                "AddressType": "M",
                "StreetName": "1904 Leland Dr,",
                "Zip": "3XX-XXX-XX",
                "City": "MXX-XXX-XXta",
                "County": "CXX-XXX-XXBB",
                "State": "CA",
                "Country": "US",
                "CountryCode": "US",
                "Addr2": "1XXXXXXXXS"
            }
        }
    },
    "Contracts": [
        {
            "Status": "",
            "Agreement": "",
            "UMR": "",
            "Syndicate": "",
            "Paper": "",
            "TermFrom": "",
            "TermTo": "",
            "ContarctType": "",
            "OccupancyType": "",
            "MaxValue": "",
            "MinValue": "",
            "Shares": [
                {
                    "ContractPercentage": "",
                    "ContractAmount": "",
                    "LiabilityPercentage": "",
                    "LiabilityAmount": "",
                    "Status": ""
                }
            ]
        }
    ],
    "ContractDetails": {
        "ContractNumber": "",
        "ContractSection": "",
        "ContractPeriod": "",
        "ContractPercentage": "",
        "LiabilityPercentage": "",
        "AppVersion": "",
        "RaterVersion": "",
        "QuoteDate": ""
    },
    "Rules": {
        "Action": "Allow",
        "MatchingRules": []
    },
    "Risks": {
        "Drivers": [
            {
                "UnitNumber": "11",
                "Name": "Singh Mayank",
                "UnitType": "",
                "Status": "Valid",
                "TempDriverIdentifier": "",
                "DriverName": "",
                "DriverDOB": "1995-03-10",
                "DriverAge": 27,
                "LicenseNumber": "B89758342105",
                "Violations": "1",
                "HireDate": "2017-09-15",
                "IsDOTNumber": "true",
                "DOTNumber": "7502601",
                "Experience": "1",
                "ExperienceMoreThanTwo": "true",
                "Turnover": "20",
                "IsDriverUploaded": "",
                "Coverages": [],
                "PremiumFactors": [],
                "Audit": {
                    "CreatedBy": "",
                    "CreatedOn": "",
                    "LastUpdatedBy": "",
                    "LastUpdatedOn": ""
                },
                "Premium": {
                    "BasicPremium": "",
                    "Surcharge": "0",
                    "Discount": "0",
                    "MinPremium": "0",
                    "PolicyPremium": "",
                    "TotalSalePrice": "",
                    "AnnualPremium": 0,
                    "EffectivePremium": 0,
                    "AnnualPremiumWithFeesAndTaxes": 0,
                    "EffectivePremiumWithFeesAndTaxes": 0
                }
            }
        ],
        "Vehicles": [
            {
                "Name": "V",
                "UnitId": null,
                "Status": "Valid",
                "UnitNumber": "1",
                "UnitType": "V",
                "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS",
                "SecondaryUse": "",
                "SecondaryUsePercent": "",
                "VehicleType": "PICK UP",
                "VIN": "3N1CB51D95L517252",
                "Year": "2003",
                "VehicleAge": "19",
                "Make": "Audi",
                "Model": "3N1CB51D95L517252",
                "OwnedOrLeased": "Owned",
                "HASBIC": "N",
                "BusinessUseClass": "Retail",
                "SizeClass": "Light Duty (Class 1-3)",
                "GROSSCOMBWEIGHT": "(Over 45,000 Lbs.G.C.W)",
                "PrimaryGaragingLocation": "611 ILLINOIS ROUTE 59, PLAINFIELD, IL, USA, 60585, 60585",
                "RADIUSCLASSTYPE": "REGIONAL 100-500 MI RADIUS",
                "VEHPRICE": "90000",
                "PASSIVERESTR": "true",
                "VEHYEAR": "",
                "ANTILOCKBRAKES": "true",
                "COSTTYPE": "Actual Cash Value",
                "FARTHESTLOCCITY": "",
                "FARTHESTLOCCOUNTY": "",
                "FARTHESTLOCSTATE": "",
                "FARTHESTLOC": "",
                "ISVEHICLEUPLOADED": true,
                "COMPDED": "0",
                "COLLDED": "0",
                "MPDED": "0",
                "HASPD": "Y",
                "HASMP": "N",
                "TEMPLATENAME": "Default Template",
                "UWREFMSG": "---",
                "GARAGELOC": "",
                "HASRENTAL": "N",
                "CSLLIMIT": "0",
                "LIABDED": "0",
                "UMTYPE": "R",
                "UMDED": "0",
                "UMLIMIT": "0"
                "Premium": {
                    "BasicPremium": "0",
                    "Surcharge": "0",
                    "Discount": "0",
                    "MinPremium": "0",
                    "PolicyPremium": null,
                    "TotalSalePrice": null,
                    "AnnualPremium": 4779.6,
                    "EffectivePremium": 4779.6,
                    "AnnualPremiumWithFeesAndTaxes": null,
                    "EffectivePremiumWithFeesAndTaxes": null
                },
                "AdditionalParties": [
                    {
                        "Status": "",
                        "PartyType": "",
                        "InterestType": "",
                        "Name": "",
                        "ReferenceNumber": "",
                        "IsPayee": "",
                        "Contact": {
                            "Contact": [
                                ""
                            ],
                            "Address": {
                                "Postalcode": "",
                                "PlaceId": "",
                                "Number": "",
                                "Name": "",
                                "Long": "",
                                "Locality": "",
                                "Lat": "",
                                "State": "",
                                "PoBox": "",
                                "AddressLine1": "",
                                "AddressLine2": "",
                                "AptSuite": "",
                                "Territory": "",
                                "Premise": "",
                                "Description": "",
                                "CountyCode": "",
                                "County": "",
                                "City": "",
                                "Business": "",
                                "AdministrationArea2": "",
                                "AdministrationArea1": "",
                                "Street": "",
                                "FormattedAddress": "",
                                "UnFormattedAddress": "",
                                "Status": ""
                            }
                        }
                    }
                ],
                "Coverages": [],
                "PremiumFactors": [
                  {
                      "Name": "EquipAnnualPremium",
                      "Status": "Active",
                      "Type": "",
                      "Description": "Equipment Annual Premium Calculation",
                      "IsApplicable": "true",
                      "IsSelected": "true",
                      "IsMandatory": "",
                      "Rate": 0,
                      "Limit": "90000",
                      "LimitAmount": "0",
                      "Deductible": "0",
                      "Premium": 0,
                      "EffectivePremium": 0
                  }
                ],
                "Audit": {
                  "CreatedBy": "",
                  "CreatedOn": "",
                  "LastUpdatedBy": "",
                  "LastUpdatedOn": ""
                },
            }
        ]
    },
    "Underwriting": {
      "HaveAutoInsurance": "",
      "HaveSR22Fillings": "",
      "DriverLicenseSuspended": "",
      "DriverHaveTicketViolation": "",
      "HowLongWithCurrentInsuranceCompany": "",
      "AnyFaultClaim": "",
      "IsCarOlder": ""
    },
    "Transaction": {
        "Number": 0,
        "Date": "2022-09-30",
        "EffectiveDate": "2022-09-30",
        "Type": "Policy",
        "Status": "Application",
        "RequestedBy": "",
        "RequestedById": "",
        "IsOutOfSequence": "false",
        "PremiumType": "",
        "PolicyVersion": "",
        "FileType": "",
        "FileName": "",
        "File": "",
        "Remarks": "",
        "Reason": "",
        "ReasonId": "",
        "RenewalOffers": {
            "RenewalOfferId": "",
            "CurrentPremium": "",
            "RenewalPremium": "",
            "IsUpdateRenewalPremium": "true",
            "RenewalOfferFlags": {
                "CreatedOn": "",
                "UpdatedOn": "",
                "CreatedBy": "",
                "UpdatedBy": "",
                "EmailSentFlag": "false"
            }
        },
        "TransactionStatusHistory": [
            {
                "OldStatus": "",
                "NewStatus": "",
                "ChangedBy": "",
                "ChangedDate": ""
            }
        ],
        "Verification": {
            "IsInsuredESignVerified": "false",
            "IsAgentESignVerified": "false",
            "IsEmailVerified": "false",
            "IsOTPVerified": "false"
        }
    },
    "Forms": [],
    "TotalPremium": {
        "BasicPremium": "0",
        "Surcharge": "0",
        "Discount": "0",
        "MinPremium": "0",
        "PolicyPremium": null,
        "TotalSalePrice": null,
        "AnnualPremium": 17325.48,
        "EffectivePremium": 17325.48,
        "AnnualPremiumWithFeesAndTaxes": 18991,
        "EffectivePremiumWithFeesAndTaxes": 18991
    },
    "Premium": {
        "BasicPremium": "0",
        "Surcharge": "0",
        "Discount": "0",
        "MinPremium": "0",
        "PolicyPremium": null,
        "TotalSalePrice": null,
        "AnnualPremium": 0,
        "EffectivePremium": 0,
        "AnnualPremiumWithFeesAndTaxes": null,
        "EffectivePremiumWithFeesAndTaxes": null
    },
    "FeesAndTaxes": [
        {
            "Code": "INSFEE",
            "Status": "Active",
            "Value": "43",
            "ValueType": "V",
            "Amount": 43,
            "AnnualAmount": 43,
            "ProductFeesAndTaxes": {
                "Product": "ENGS1IL",
                "Code": "INSFEE",
                "Description": "Inspection Fee",
                "Status": "Active",
                "EffectiveFrom": "2020-01-01",
                "RangeFrom": "0.0000",
                "RangeTo": "99999.0000",
                "RangeValueType": "V",
                "IsEarned": "0",
                "LicenseNo": null,
                "ValueType": "V",
                "Value": "43.0000",
                "DecimalPoints": "",
                "CalculateOn": "",
                "Transactions": "A,P,CF,IF,R,Quote,Policy,FlatCancellation,FlatReinstate,Renewal"
            }
        }
    ],
    "Payplan": [
        {
            "Date": "",
            "Amount": "",
            "IsPaid": "",
            "Status": ""
        }
    ],
    "PolicyCoverages": {
        "Coverages": [
            {
                "Name": "Combined Single Limit",
                "Status": "",
                "Type": "",
                "Description": "Combined Single Limit",
                "NoOfDays": "",
                "WaitingPeriod": "",
                "ExpenseType": "",
                "IsApplicable": "",
                "IsSelected": "true",
                "IsMandatory": "true",
                "Rate": 0,
                "OtherCoverageField": {
                    "AtFault": ""
                },
                "Limit": "1000000",
                "LimitAmount": "",
                "Deductible": "1000",
                "Premium": 0,
                "EffectivePremium": 0,
                "PremiumDifference": 0,
                "Factor": {
                    "Status": "",
                    "Type": "",
                    "Description": "",
                    "IsApplicable": "",
                    "IsSelected": "",
                    "IsMandatory": "",
                    "Rate": "",
                    "Limit": "",
                    "LimitAmount": "",
                    "Deductible": "",
                    "Premium": "",
                    "EffectivePremium": ""
                }
            }
        ]
    },
    "PremiumFactors": [
        {
            "Name": "RiskPrem",
            "Status": "Active",
            "Type": "",
            "Description": "Risk Premium",
            "IsApplicable": "true",
            "IsSelected": "true",
            "IsMandatory": "",
            "Rate": 0,
            "Limit": "0",
            "LimitAmount": "0",
            "Deductible": "0",
            "Premium": 0,
            "EffectivePremium": 0
        }
    ],
    "JointPolicyHolders": [],
    "Attributes": {
        "IsFromSalesForce": "false",
        "Carrier": "ENGS",
        "Lob": "CA",
        "State": "IL",
        "Product": "ENGS1IL",
        "RaterVersion": "1.0.0.0",
        "Coverholder": "MS",
        "QuoteValidity": "30",
        "RenewalConfigurations": {
            "BeforeForAgent": "30",
            "AfterForAgent": "30",
            "BeforeForUnderwriter": "60",
            "AfterForUnderwriter": "30"
        }
    },
    "Payments": [
        {
            "LastName": "",
            "FirstName": "",
            "OrderID": "",
            "TransactionType": "",
            "TransactionID": "",
            "TransactionDate": "",
            "TransactionStatus": "",
            "TransactionAmount": "",
            "CardDetails": {
                "Type": "",
                "CardNumber": "",
                "Expiry": "",
                "CVVCode": "",
                "LastFourDigits": ""
            },
            "BankDetails": {
                "AccountName": "",
                "BankName": "",
                "BranchName": "",
                "AccountType": "",
                "RoutingNo": ""
            }
        }
    ],
    "ExternalRefrences": [],
    "Audit": {
        "LastUpdatedBy": null,
        "LastUpdatedOn": null,
        "CreatedBy": null,
        "CreatedOn": "2022-09-30T13:09:50.522Z"
    },
    "InsuredAccount": {
        "Type": "Primary",
        "CreationDate": "",
        "UserName": "",
        "FirstName": "",
        "MiddleName": "",
        "LastName": "",
        "DisplayName": "",
        "BusinessInfo": {
            "BusinessType": "",
            "YearsInBusiness": "",
            "IncorporationAge": "2016",
            "BusinessAge": 6,
            "BusinessName": "Mayank Singh",
            "DisplayName": "",
            "RegistrationNumber": "",
            "BusinessStruct": "Individual",
            "SpecialRisk": "",
            "NoOfOwners": "1",
            "FullTimeEmployees": "1",
            "PartTimeEmployees": "1",
            "Website": "",
            "IndustryType": "",
            "BusinessDecsription": "",
            "AnnualRevenue": "",
            "NumberOFLocations": "",
            "Locations": [
                {
                    "NickName": "",
                    "LocationNumber": "",
                    "IsValid": false,
                    "Status": "",
                    "Type": ""
                    "Address": {
                        "Postalcode": "60585",
                        "PlaceId": "Eio2MTEgSWxsaW5vaXMgUm91dGUgNTksIFBsYWluZmllbGQsIElMLCBVU0EiMRIvChQKEgkHWyN01PUOiBGE8pXbKxdKxBDjBCoUChIJFWw1OfKpD4gRvImWgtf0JOA",
                        "Number": "",
                        "Name": "",
                        "Long": "",
                        "Locality": "",
                        "Lat": "",
                        "State": "IL",
                        "PoBox": "",
                        "AddressLine1": "",
                        "AddressLine2": "",
                        "AptSuite": "",
                        "Territory": "",
                        "Premise": "",
                        "Description": "Primary Garaging Address",
                        "CountyCode": "",
                        "County": "US",
                        "City": "Plainfield",
                        "Business": "",
                        "AdministrationArea2": "",
                        "AdministrationArea1": "",
                        "Street": "",
                        "FormattedAddress": "611 Illinois Route 59",
                        "UnFormattedAddress": "611 ILLINOIS ROUTE 59, PLAINFIELD, IL, USA, 60585",
                        "Status": ""
                    },
                }
            ]
        },
        "Communications": [
            {
                "Type": "PhNo",
                "SubType": "Primary",
                "Value": "",
                "Status": ""
            },
            {
                "Type": "Email",
                "SubType": "Primary",
                "Value": "",
                "Status": ""
            }
        ],
        "BankDetails": {
            "AccountName": null,
            "BankName": null,
            "BranchName": null,
            "AccountType": null,
            "RoutingNo": null
        }
    },
    "PriorInsurances": [],
    "DiscountAndSurcharges": {
        "Description": null
    },
    "PreviousPolicies": {
        "IsPreviousPolicy": "",
        "PreviousPolicyNumber": "",
        "OtherCoverages": "",
        "IsPreviousClaims": "",
        "NoOfClaims": "",
        "TotalAmountClaimed": ""
    },
    "NonFunctional": {
        "LastSubmittedPage": "/Commercial/Auto/Application/BusinessInfo",
        "Milestones": [
            0,
            1,
            2,
            3
        ],
        "InsuredOTP": ""
    },
    "PolicyStatusHistory": [
        {
            "OldStatus": "",
            "NewStatus": "Quote",
            "ChangedBy": "",
            "ChangedDate": ""
        },
        {
            "OldStatus": "Quote",
            "NewStatus": "Application",
            "ChangedBy": "13530",
            "ChangedDate": "2022-09-30"
        }
    ],
    "_rid": "3UVSALPITwtDAAAAAAAAAA==",
    "_self": "dbs/3UVSAA==/colls/3UVSALPITws=/docs/3UVSALPITwtDAAAAAAAAAA==/",
    "_etag": "\"00000be8-0000-0100-0000-6336eb090000\"",
    "_attachments": "attachments/",
    "_ts": 1664543497
}
```

### 11. Templates Container
Below is a sample templates container object:
>![Templates Container Object](../../static/img/docs/azure/TemplatesContainerObj.png)
>[Templates Container Object](../../static/img/docs/azure/TemplatesContainerObj.png)

#### Important Nodes:-
- TemplateName :- It is unique name representing every template.
- IsDefault :- This parameter is used to distinguish default template from the other user defined templates.
- Carrier :- Most important parameter - used as partition key - Also used for fetching templates for a particular client.
- LOB :- This parameter is also used for fetching forms.
- agencyId :- This parameter was made to fetch forms only created by resource belonging to particular agency.


#### Two types of templates object
1. **Default Template** :- These are very important and used for prepopulating the coverages selection and values.
2. **User Created Templates** :- When a user creates a templates using the new coverage template option - It must have a unique name - It is saved in this container, with that template name and values as selected by user while creating the template. The advantage of these user templates is that they can be applied to a group of vehicles at a single time.

**Note:-** User defined template can also be used for showing particular group of templates belonging to the current user's logged in Agency.

### 12. Underwriter Container
This container consists document having object representing detail of different underwriter to be used in the application. Below is sample object for reference
>![Underwriter Object](../../static/img/docs/azure/SampleUnderwriterObject.png)
>[Underwriter Object](../../static/img/docs/azure/SampleUnderwriterObject.png)

- The Client parameter represents the Client the specificied Underwriter has access to.
- The Code parameter represents the Underwriter code as registered in SSO.
- The Products parameter represents different products of the specified client, the Underwriter will have access too.
- The References array stores the list of different Agency, the specified Underwriter belong to.

### 13. Versions Container
This container is used for keeping the version of policy after every bind transaction. For instance after Policy is Binded a version is pushed in version container and a new replica of same is kept in policy container. A new version is pushed at the time of endorsement, cancellation, reinstatement and renewal success.

The replica that is kept in the policy container has transaction number incremented by 1. If it was Policy Bind transaction IsBind flag is turned to "true".


## II. User Defined Functions
The SQL API extends the SQL syntax to support custom application logic using UDFs. You can register UDFs with the SQL API, and reference them in SQL queries. Unlike stored procedures and triggers, **UDFs are read-only**.

Using UDFs, you can extend Azure Cosmos DB's query language. UDFs are a great way to express complex business logic in a query's projection.

### Example

1. daysAdder UDF
```bash
function daysAdder(date, daysToAdd) {
  if (date == undefined) return -1;
  else {
    let splitDate = date.split('-');
    let newDate = new Date(parseInt(splitDate[0]), parseInt(splitDate[1]), parseInt(splitDate[2]));
    newDate.setDate(newDate.getDate() + parseInt(daysToAdd));  
    return (
      newDate.getFullYear().toString() +
      "-" +
      newDate.getMonth().toString().padStart("2", "0") +
      "-" +
      newDate.getDate().toString().padStart(2, "0")
    );
  }
}
```
2. Usage Implementation
```bash
/**Method to pull list of applicable renewal policies
 * @param {string} userType - role for which we want to pull applicable renewals
 * @returns {[policies]} - list of renewable policies 
 */
const LoadRenewels = async (userType) => {
  try {
    let input = {
      "input": {
        "clause": [],
        "LIMIT": 100,
        "containerName": "policy"
      }
    };
    if (userType == "UW") {
      input.input.clause = [
        { "src": "r.IsRenewed", "def": "false", "exp": "=" },
        { "src": "r.ExpirationDate", "def": "udf.daysadder(udf.getcurrentdate(), (-1 * StringToNumber(r.Attributes.RenewalConfigurations.BeforeForUnderwriter)))", 
        "exp": ">=", "operator": "AND" },
        { "src": "r.ExpirationDate", "def": "udf.daysadder(udf.getcurrentdate(), (StringToNumber(r.Attributes.RenewalConfigurations.AfterForUnderwriter)))", 
        "exp": "<=", "operator": "AND" },
      ]
    } else {
      input.input.clause = [
        { "src": "r.IsRenewed", "def": "false", "exp": "=" },
        { "src": "r.ExpirationDate", "def": "udf.daysadder(udf.getcurrentdate(), (-1 * StringToNumber(r.Attributes.RenewalConfigurations.BeforeForAgent)))", 
        "exp": ">=", "operator": "AND" },
        { "src": "r.ExpirationDate", "def": "udf.daysadder(udf.getcurrentdate(), (StringToNumber(r.Attributes.RenewalConfigurations.AfterForAgent)))", 
        "exp": "<=", "operator": "AND" },
      ]
    }
    const resp = await ExecuteQuery(GetApolloClient(gqlEndPoint), GETACCOUNTHUB, input);
    let data = [];
    if (resp) {
      data = await ProcessAccountHubData(resp.data[apolloKeys.GetByFilter], true);
    }
    return (data != null || data != undefined) ? data : null;
  } catch (error) {
    console.log(error);
    logAPIErrorData(error, { userType }, consoleLogs.Utilities.Apollo.Operations.LoadRenewels)
  }
};
```


**Note** :- However, we recommending avoiding UDFs when:

1. An equivalent system function already exists in Azure Cosmos DB. **System functions will always use fewer RU's than the equivalent UDF**.
2. The UDF is the only filter in the WHERE clause of your query. UDF's do not utilize the index so evaluating the UDF will require loading documents. Combining additional filter predicates that use the index, in combination with a UDF, in the WHERE clause will reduce the number of documents processed by the UDF.

**Note**:- If you must use the same UDF multiple times in a query, you should reference the UDF in a subquery, allowing you to use a JOIN expression to evaluate the UDF once but reference it many times.