---
id: PolicyModelSchema
title: Policy Model Schema
---
```json
{
  "$schema": "https://json-schema.org/draft/2019-09/schema",
  "$id": "http://example.com/example.json",
  "title": "Policy",
  "description": "The root schema is the schema that comprises the entire JSON document.",
  "type": "object",
  "default": {},
  "required": [
      "id",
      "AccountId",
      "QuoteNumber",
      "IsPolicyBind",
      "IsRenewed",
      "PolicyNumber",
      "PolicyTerm",
      "EffectiveDate",
      "ExpirationDate",
      "BindDate",
      "QuoteDate",
      "QuoteExpDate",
      "PolicyStatus",
      "CurrentVersion",
      "CurrentVersionEffectiveFrom",
      "RenewalTerm",
      "Attributes"
  ],
  "additionalProperties": true,
  "properties": {
      "id": {
          "title": "Id",
          "description": "guid, unique within policy container",
          "type": "string",
          "default": "",
          "examples": [
              "cd27210f-81c9-4d6e-a7d5-e0cd11431006"
          ]
      },
      "AccountId": {
          "title": "Account Id",
          "description": "Account Id specifies the role of the user eg. Agent/UW",
          "type": "string",
          "default": "Agent",
          "examples": [
              "Agent"
          ]
      },
      "QuoteNumber": {
          "title": "Quote Number",
          "description": "QuoteNumber is unique identifier to across the transactions of given policy, it will remain same in Version container",
          "type": "string",
          "default": "",
          "examples": [
              "ENGS1CA220009"
          ]
      },
      "IsPolicyBind": {
          "title": "Is Policy Bind",
          "description": "flag denotes the the submission is bound or not, set true when update status PolicyInForceBind",
          "type": "boolean",
          "default": null,
          "examples": [
              false
          ]
      },
      "IsRenewed": {
          "title": "IsRenewed",
          "description": "flag is used to identify the renewal policy set true when we update status Renewed",
          "type": "boolean",
          "default": false,
          "examples": [
              false
          ]
      },
      "PolicyNumber": {
          "title": "PolicyNumber",
          "description": "Policy number is also unique identifier of a Policy but it is generated when we bind the NB Policy and for renewal at the time of renewal offer generation ",
          "type": "string",
          "default": "",
          "examples": [
              "SGIH3GA223885"
          ]
      },
      "PolicyTerm": {
          "title": "PolicyTerm",
          "description": "denotes the term of the policy, value may contain number of days, month or years and value type will be [Days, Months, Year]",
          "type": "object",
          "default": {},
          "required": [
              "Value",
              "ValueType"
          ],
          "additionalProperties": true,
          "properties": {
              "Value": {
                  "title": "Value",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      12
                  ]
              },
              "ValueType": {
                  "title": "ValueType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Months"
                  ]
              }
          },
          "examples": [
              {
                  "Value": 12,
                  "ValueType": "Months"
              }
          ]
      },
      "EffectiveDate": {
          "title": "EffectiveDate",
          "description": "Date in which selected record is effective or proposed effective.",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "ExpirationDate": {
          "title": "ExpirationDate",
          "description": "Date in which selected record expires or is proposed to expire.",
          "type": "string",
          "default": "",
          "examples": [
              "2023-08-18"
          ]
      },
      "BindDate": {
          "title": "BindDate",
          "description": "Date in which submission was first bound.",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "QuoteDate": {
          "title": "QuoteDate",
          "description": "Date in which submission or version was quoted.",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "QuoteExpDate": {
          "title": "QuoteExpDate",
          "description": "Date in which offered quote will expire and will be re-rated the new version. ",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "PolicyStatus": {
          "title": "PolicyStatus",
          "description": "Indicates the status that the submission is in.  ",
          "type": "string",
          "default": "",
          "examples": [
            {
              "QuoteIndication": "Quote Indication",
              "Submission": "Submission",
              "SubmissionDeclinedbyUW": "Submission Declined by UW",
              "ReferralAwaitingUWReview": "Referral - Awaiting UW Review",
              "QuoteOffered": "Quote Offered",
              "UWQuoteDeclined": "UW - Quote Declined",
              "QuoteExpired": "Quote Expired",
              "RetailerQuoteDeclined": "Retailer - Quote Declined",
              "BindRequestAwaitingUWApproval": "Bind Request - Awaiting UW Approval",
              "BindRequestDeclinedbyUW": "Bind Request Declined by UW",
              "BindRequestonHold": "Bind Request on Hold",
              "PolicyInForceBind": "Policy In Force-Bind",
              "PolicyInForceEndorsementRequestAwaitingUWApproval": "Policy In Force - Endorsement Request Awaiting UW Approval",
              "PolicyInForceEndorsed": "Policy In Force-Endorsed",
              "PolicyInForceEndorsementRequestOnHold": "Policy In Force - Endorsement Request On Hold",
              "PolicyInForceCancellationRequestPendingApproval": "Policy In Force - Cancellation Request Pending Approval",
              "PolicyCancelled": "Policy Cancelled",
              "PolicyInForceCancellationRequestOnHold": "Policy In Force - Cancellation Request On Hold",
              "PolicyCancelledReinstatementRequestPendingUWApproval": "Policy Cancelled - Reinstatement Request Pending UW Approval",
              "PolicyCancelledReinstatementRequestOnHold": "Policy Cancelled - Reinstatement Request On Hold",
              "PolicyInForceReInstated": "Policy In Force-ReInstated",
              "WaitingForRevisedApproval": "Waiting For Revised Approval",
              "BindSignaturePending": "Bind Signature Pending",
              "BindSignatureCompleted": "Bind Signature Completed",
              "PolicyInForceEndorsementSignaturePending": "Policy In Force - Endorsement Signature Pending",
              "PolicyInForceEndorsementSignatureCompleted": "Policy In Force - Endorsement Signature Completed",
              "PolicyInForceCancellationSignaturePending": "Policy In Force - Cancellation Signature Pending",
              "PolicyInForceCancellationSignatureCompleted": "Policy In Force - Cancellation Signature Completed",
              "RenewalSubmission": "Renewal Submission",
              "RenewalOfferGenerated": "Renewal Offer Generated",
              "RetailerRenewalOfferDeclined": "Retailer - Renewal Offer Declined",
              "DeclineRenewalOffer": "Decline Renewal Offer",
              "RenewalRequestSignaturePending": "Renewal Request - Signature Pending",
              "RenewalRequestSignatureCompleted": "Renewal Request - Signature Completed",
              "RenewalQuoteOffered": "Renewal Quote Offered",
              "RenewalAwaitingUWReview": "Renewal Awaiting UW Review",
              "Policyexpired": "Policy expired",
              "Waitingforrenewal": "Waiting for renewal",
              "Renewed": "Renewed",
              "Renewalonhold": "Renewal on hold",
              "RenewalDeclined": "Renewal Declined",
              "Renewalcancelled": "Renewal cancelled",
              "RenewalBindRequestAwaitingUWApproval": "Renewal Bind Request - Awaiting UW Approval"
            }
          ]
      },
      "CurrentVersion": {
          "title": "CurrentVersion",
          "description": " ",
          "type": "string",
          "default": "",
          "examples": [
              "1.0"
          ]
      },
      "CurrentVersionEffectiveFrom": {
          "title": "CurrentVersionEffectiveFrom",
          "description": " ",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "RenewalTerm": {
          "title": "RenewalTerm",
          "description": "Number of times record renewed ",
          "type": "number",
          "default": 0,
          "examples": [
              0
          ]
      },
      "RenewalQuoteID": {
        "title": "RenewalQuoteID",
        "description": "If policy has been renewed, then the old policy will hold the quote id of the new policy. ",
        "type": "number",
        "default": 0,
        "examples": [
            0
        ]
    },
  
      "Attributes": {
          "title": "Attributes",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "AppSource",
              "Carrier",
              "Coverholder",
              "Lob",
              "State",
              "Product",
              "RaterVersion",
              "RenewalConfigurations",
              "QuoteValidity",
              "IsTestPolicy"
          ],
          "additionalProperties": true,
          "properties": {
              "AppSource": {
                  "title": "AppSource",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "SalesForce"
                  ]
              },
              "Carrier": {
                  "title": "Carrier",
                  "description": "Holds the carrier code, refences to carrier ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "ENGS"
                  ]
              },
              "Coverholder": {
                  "title": "Coverholder",
                  "description": "Holds the Coverholder code, refences to Coverholder ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "IH"
                  ]
              },
              "Lob": {
                  "title": "Lob",
                  "description": "Indicates the Line of business ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "CA", "HO","PA"
                  ]
              },
              "State": {
                  "title": "State",
                  "description": " ",
                  "type": "string",
                  "default": "State abbreviation of the filing tax state.",
                  "examples": [
                      "GA"
                  ]
              },
              "Product": {
                  "title": "Product",
                  "description": "Code of the product -- a combination of the carrier, coverholder, lob and risk state",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "ENGS1CA"
                  ]
              },
              "RaterVersion": {
                  "title": "RaterVersion",
                  "description": " ",
                  "type": "string",
                  "default": "Indicates the rater version, rater version is freezed quote is offered",
                  "examples": [
                      "2.0.0.0"
                  ]
              },
              "RenewalConfigurations": {
                  "title": "RenewalConfigurations",
                  "description": "Hold the information about renewal process ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "BeforeForAgent",
                      "AfterForAgent",
                      "BeforeForUnderwriter",
                      "AfterForUnderwriter"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "BeforeForAgent": {
                          "title": "BeforeForAgent",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      30
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 30,
                                  "ValueType": "Days"
                              }
                          ]
                      },
                      "AfterForAgent": {
                          "title": "AfterForAgent",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      30
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 30,
                                  "ValueType": "Days"
                              }
                          ]
                      },
                      "BeforeForUnderwriter": {
                          "title": "BeforeForUnderwriter",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      60
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 60,
                                  "ValueType": "Days"
                              }
                          ]
                      },
                      "AfterForUnderwriter": {
                          "title": "AfterForUnderwriter",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      60
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 60,
                                  "ValueType": "Days"
                              }
                          ]
                      }
                  },
                  "examples": [
                      {
                          "BeforeForAgent": {
                              "Value": 30,
                              "ValueType": "Days"
                          },
                          "AfterForAgent": {
                              "Value": 30,
                              "ValueType": "Days"
                          },
                          "BeforeForUnderwriter": {
                              "Value": 60,
                              "ValueType": "Days"
                          },
                          "AfterForUnderwriter": {
                              "Value": 60,
                              "ValueType": "Days"
                          }
                      }
                  ]
              },
              "QuoteValidity": {
                  "title": "QuoteValidity",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Value",
                      "ValueType"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Value": {
                          "title": "Value",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              60
                          ]
                      },
                      "ValueType": {
                          "title": "ValueType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Days"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "Value": 60,
                          "ValueType": "Days"
                      }
                  ]
              },
              "IsTestPolicy": {
                  "title": "IsTestPolicy",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              }
          },
          "examples": [
              {
                  "AppSource": "SalesForce",
                  "Carrier": "ENGS",
                  "Coverholder": "IH",
                  "Lob": "CA",
                  "State": "GA",
                  "Product": "ENGS1CA",
                  "RaterVersion": "2.0.0.0",
                  "RenewalConfigurations": {
                      "BeforeForAgent": {
                          "Value": 30,
                          "ValueType": "Days"
                      },
                      "AfterForAgent": {
                          "Value": 30,
                          "ValueType": "Days"
                      },
                      "BeforeForUnderwriter": {
                          "Value": 60,
                          "ValueType": "Days"
                      },
                      "AfterForUnderwriter": {
                          "Value": 60,
                          "ValueType": "Days"
                      }
                  },
                  "QuoteValidity": {
                      "Value": 60,
                      "ValueType": "Days"
                  },
                  "IsTestPolicy": true
              }
          ]
      },
      "PolicyStatusHistory": {
          "title": "PolicyStatusHistory",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "OldStatus",
                  "NewStatus",
                  "ChangedBy",
                  "ChangedDate"
              ],
              "additionalProperties": true,
              "properties": {
                  "OldStatus": {
                      "title": "OldStatus",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Quote"
                      ]
                  },
                  "NewStatus": {
                      "title": "NewStatus",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Application"
                      ]
                  },
                  "ChangedBy": {
                      "title": "ChangedBy",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "nkadam"
                      ]
                  },
                  "ChangedDate": {
                      "title": "ChangedDate",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2022-08-18"
                      ]
                  }
              },
              "examples": [
                  {
                      "OldStatus": "Quote",
                      "NewStatus": "Application",
                      "ChangedBy": "nkadam",
                      "ChangedDate": "2022-08-18"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "OldStatus": "Quote",
                      "NewStatus": "Application",
                      "ChangedBy": "nkadam",
                      "ChangedDate": "2022-08-18"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Transaction": {
          "title": "Transaction",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Date",
              "EffectiveDate",
              "Type",
              "Status",
              "Number",
              "IsOutOfSequence",
              "RequestedBy",
              "RequestedById",
              "PremiumType",
              "PolicyVersion",
              "FileType",
              "FileName",
              "File",
              "Remarks",
              "ReasonId",
              "Reason",
              "Verification",
              "TransactionStatusHistory",
              "RenewalOffers"
          ],
          "additionalProperties": true,
          "properties": {
              "Date": {
                  "title": "Date",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-10-19"
                  ]
              },
              "EffectiveDate": {
                  "title": "EffectiveDate",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-10-19"
                  ]
              },
              "Type": {
                  "title": "Type",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Application"
                  ]
              },
              "Status": {
                  "title": "Status",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "In-Progress"
                  ]
              },
              "Number": {
                  "title": "Number",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "IsOutOfSequence": {
                  "title": "IsOutOfSequence",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "RequestedBy": {
                  "title": "RequestedBy",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Agent"
                  ]
              },
              "RequestedById": {
                  "title": "RequestedById",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "123"
                  ]
              },
              "PremiumType": {
                  "title": "PremiumType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "PRO_RATE"
                  ]
              },
              "PolicyVersion": {
                  "title": "PolicyVersion",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "1.0.0"
                  ]
              },
              "FileType": {
                  "title": "FileType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      ""
                  ]
              },
              "FileName": {
                  "title": "FileName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      ""
                  ]
              },
              "File": {
                  "title": "File",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      ""
                  ]
              },
              "Remarks": {
                  "title": "Remarks",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "test policy"
                  ]
              },
              "ReasonId": {
                  "title": "ReasonId",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "AI16"
                  ]
              },
              "Reason": {
                  "title": "Reason",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Policy Rewrite"
                  ]
              },
              "Verification": {
                  "title": "Verification",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "IsInsuredESignVerified",
                      "IsAgentESignVerified",
                      "IsEmailVerified",
                      "IsOTPVerified",
                      "InsuredOTP"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "IsInsuredESignVerified": {
                          "title": "IsInsuredESignVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "IsAgentESignVerified": {
                          "title": "IsAgentESignVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "IsEmailVerified": {
                          "title": "IsEmailVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "IsOTPVerified": {
                          "title": "IsOTPVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "InsuredOTP": {
                          "title": "InsuredOTP",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      }
                  },
                  "examples": [
                      {
                          "IsInsuredESignVerified": false,
                          "IsAgentESignVerified": false,
                          "IsEmailVerified": false,
                          "IsOTPVerified": false,
                          "InsuredOTP": ""
                      }
                  ]
              },
              "TransactionStatusHistory": {
                  "title": "TransactionStatusHistory",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "OldStatus",
                          "NewStatus",
                          "ChangedBy",
                          "ChangedDate"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "OldStatus": {
                              "title": "OldStatus",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Quote"
                              ]
                          },
                          "NewStatus": {
                              "title": "NewStatus",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Application"
                              ]
                          },
                          "ChangedBy": {
                              "title": "ChangedBy",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "nkadam"
                              ]
                          },
                          "ChangedDate": {
                              "title": "ChangedDate",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2022-10-19"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "OldStatus": "Quote",
                              "NewStatus": "Application",
                              "ChangedBy": "nkadam",
                              "ChangedDate": "2022-10-19"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "OldStatus": "Quote",
                              "NewStatus": "Application",
                              "ChangedBy": "nkadam",
                              "ChangedDate": "2022-10-19"
                          }
                      ]
                  ],
                  "uniqueItems": false
              },
              "RenewalOffers": {
                  "title": "RenewalOffers",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "RenewalOfferId",
                      "CurrentPremium",
                      "RenewalPremium",
                      "IsUpdateRenewalPremium",
                      "RenewalOfferFlags"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "RenewalOfferId": {
                          "title": "RenewalOfferId",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "A123"
                          ]
                      },
                      "CurrentPremium": {
                          "title": "CurrentPremium",
                          "description": " ",
                          "type": "number",
                          "default": 0.0,
                          "examples": [
                              1365.12
                          ]
                      },
                      "RenewalPremium": {
                          "title": "RenewalPremium",
                          "description": " ",
                          "type": "number",
                          "default": 0.0,
                          "examples": [
                              1465.12
                          ]
                      },
                      "IsUpdateRenewalPremium": {
                          "title": "IsUpdateRenewalPremium",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              true
                          ]
                      },
                      "RenewalOfferFlags": {
                          "title": "RenewalOfferFlags",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "CreatedOn",
                              "UpdatedOn",
                              "CreatedBy",
                              "UpdatedBy",
                              "EmailSentFlag"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "CreatedOn": {
                                  "title": "CreatedOn",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "2022-10-19"
                                  ]
                              },
                              "UpdatedOn": {
                                  "title": "UpdatedOn",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "2022-10-19"
                                  ]
                              },
                              "CreatedBy": {
                                  "title": "CreatedBy",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "nkadam"
                                  ]
                              },
                              "UpdatedBy": {
                                  "title": "UpdatedBy",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "nkadam"
                                  ]
                              },
                              "EmailSentFlag": {
                                  "title": "EmailSentFlag",
                                  "description": " ",
                                  "type": "boolean",
                                  "default": false,
                                  "examples": [
                                      false
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "CreatedOn": "2022-10-19",
                                  "UpdatedOn": "2022-10-19",
                                  "CreatedBy": "nkadam",
                                  "UpdatedBy": "nkadam",
                                  "EmailSentFlag": false
                              }
                          ]
                      }
                  },
                  "examples": [
                      {
                          "RenewalOfferId": "A123",
                          "CurrentPremium": 1365.12,
                          "RenewalPremium": 1465.12,
                          "IsUpdateRenewalPremium": true,
                          "RenewalOfferFlags": {
                              "CreatedOn": "2022-10-19",
                              "UpdatedOn": "2022-10-19",
                              "CreatedBy": "nkadam",
                              "UpdatedBy": "nkadam",
                              "EmailSentFlag": false
                          }
                      }
                  ]
              }
          },
          "examples": [
              {
                  "Date": "2022-10-19",
                  "EffectiveDate": "2022-10-19",
                  "Type": "Application",
                  "Status": "In-Progress",
                  "Number": 0,
                  "IsOutOfSequence": false,
                  "RequestedBy": "Agent",
                  "RequestedById": "123",
                  "PremiumType": "PRO_RATE",
                  "PolicyVersion": "1.0.0",
                  "FileType": "",
                  "FileName": "",
                  "File": "",
                  "Remarks": "test policy",
                  "ReasonId": "AI16",
                  "Reason": "Policy Rewrite",
                  "Verification": {
                      "IsInsuredESignVerified": false,
                      "IsAgentESignVerified": false,
                      "IsEmailVerified": false,
                      "IsOTPVerified": false,
                      "InsuredOTP": ""
                  },
                  "TransactionStatusHistory": [
                      {
                          "OldStatus": "Quote",
                          "NewStatus": "Application",
                          "ChangedBy": "nkadam",
                          "ChangedDate": "2022-10-19"
                      }
                  ],
                  "RenewalOffers": {
                      "RenewalOfferId": "A123",
                      "CurrentPremium": 1365.12,
                      "RenewalPremium": 1465.12,
                      "IsUpdateRenewalPremium": true,
                      "RenewalOfferFlags": {
                          "CreatedOn": "2022-10-19",
                          "UpdatedOn": "2022-10-19",
                          "CreatedBy": "nkadam",
                          "UpdatedBy": "nkadam",
                          "EmailSentFlag": false
                      }
                  }
              }
          ]
      },
      "AgentCommission": {
          "title": "AgentCommission",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Value",
              "ValueType"
          ],
          "additionalProperties": true,
          "properties": {
              "Value": {
                  "title": "Value",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "10"
                  ]
              },
              "ValueType": {
                  "title": "ValueType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Percent"
                  ]
              }
          },
          "examples": [
              {
                  "Value": "10",
                  "ValueType": "Percent"
              }
          ]
      },
      "Agency": {
          "title": "Agency",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Client",
              "Code",
              "Name",
              "Status",
              "Products",
              "Reference",
              "Address",
              "Communications"
          ],
          "additionalProperties": true,
          "properties": {
              "Client": {
                  "title": "Client",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "SGIH"
                  ]
              },
              "Code": {
                  "title": "Code",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "108999"
                  ]
              },
              "Name": {
                  "title": "Name",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "test agency"
                  ]
              },
              "Status": {
                  "title": "Status",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Active"
                  ]
              },
              "Products": {
                  "title": "Products",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "1",
                          "2",
                          "3"
                      ]
                  },
                  "examples": [
                      [
                          "1",
                          "2",
                          "3"
                      ]
                  ],
                  "uniqueItems": false
              },
              "Reference": {
                  "title": "Reference",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "12907",
                          "12911"
                      ]
                  },
                  "examples": [
                      [
                          "12907",
                          "12911"
                      ]
                  ],
                  "uniqueItems": false
              },
              "Address": {
                  "title": "Address",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Number",
                      "AddressType",
                      "Description",
                      "AddressLine1",
                      "AddressLine2",
                      "AptSuite",
                      "City",
                      "County",
                      "CountyCode",
                      "State",
                      "PoBox",
                      "Postalcode",
                      "FormattedAddress",
                      "UnFormattedAddress",
                      "AdministrationArea1",
                      "AdministrationArea2",
                      "Locality",
                      "Lat",
                      "Long",
                      "Name",
                      "Premise",
                      "Status",
                      "Territory",
                      "Business",
                      "PlaceId"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Number": {
                          "title": "Number",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              1
                          ]
                      },
                      "AddressType": {
                          "title": "AddressType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Primary"
                          ]
                      },
                      "Description": {
                          "title": "Description",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Mailing Address"
                          ]
                      },
                      "AddressLine1": {
                          "title": "AddressLine1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE"
                          ]
                      },
                      "AddressLine2": {
                          "title": "AddressLine2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Apt I"
                          ]
                      },
                      "AptSuite": {
                          "title": "AptSuite",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "1000"
                          ]
                      },
                      "City": {
                          "title": "City",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Forest Park"
                          ]
                      },
                      "County": {
                          "title": "County",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "US"
                          ]
                      },
                      "CountyCode": {
                          "title": "CountyCode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "COBB"
                          ]
                      },
                      "State": {
                          "title": "State",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "GA"
                          ]
                      },
                      "PoBox": {
                          "title": "PoBox",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "Postalcode": {
                          "title": "Postalcode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "FormattedAddress": {
                          "title": "FormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE, Smyrna GA 30080"
                          ]
                      },
                      "UnFormattedAddress": {
                          "title": "UnFormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141LakeParkDRSESmyrnaGA30080"
                          ]
                      },
                      "AdministrationArea1": {
                          "title": "AdministrationArea1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "AdministrationArea2": {
                          "title": "AdministrationArea2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Locality": {
                          "title": "Locality",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Atlanta"
                          ]
                      },
                      "Lat": {
                          "title": "Lat",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.6654"
                          ]
                      },
                      "Long": {
                          "title": "Long",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.65646"
                          ]
                      },
                      "Name": {
                          "title": "Name",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cobb Galleria Pkwy"
                          ]
                      },
                      "Premise": {
                          "title": "Premise",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Fron"
                          ]
                      },
                      "Status": {
                          "title": "Status",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Active"
                          ]
                      },
                      "Territory": {
                          "title": "Territory",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Business": {
                          "title": "Business",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cogitate Technology Solution"
                          ]
                      },
                      "PlaceId": {
                          "title": "PlaceId",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      }
                  ]
              },
              "Communications": {
                  "title": "Communications",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Type",
                          "SubType",
                          "Value",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "PhNo",
                                  "Email"
                              ]
                          },
                          "SubType": {
                              "title": "SubType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "4707070096",
                                  "nkadam@cogitate.us"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Client": "SGIH",
                  "Code": "108999",
                  "Name": "test agency",
                  "Status": "Active",
                  "Products": [
                      "1",
                      "2",
                      "3"
                  ],
                  "Reference": [
                      "12907",
                      "12911"
                  ],
                  "Address": {
                      "Number": 1,
                      "AddressType": "Primary",
                      "Description": "Mailing Address",
                      "AddressLine1": "2141 Lake Park DR SE",
                      "AddressLine2": "Apt I",
                      "AptSuite": "1000",
                      "City": "Forest Park",
                      "County": "US",
                      "CountyCode": "COBB",
                      "State": "GA",
                      "PoBox": "30080",
                      "Postalcode": "30080",
                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                      "AdministrationArea1": "",
                      "AdministrationArea2": "",
                      "Locality": "Atlanta",
                      "Lat": "45.6654",
                      "Long": "45.65646",
                      "Name": "Cobb Galleria Pkwy",
                      "Premise": "Fron",
                      "Status": "Active",
                      "Territory": "",
                      "Business": "Cogitate Technology Solution",
                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                  },
                  "Communications": [
                      {
                          "Type": "PhNo",
                          "SubType": "Primary",
                          "Value": "4707070096",
                          "Status": "Active"
                      },
                      {
                          "Type": "Email",
                          "SubType": "Primary",
                          "Value": "nkadam@cogitate.us",
                          "Status": "Active"
                      }
                  ]
              }
          ]
      },
      "UnderWriter": {
          "title": "UnderWriter",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Client",
              "Code",
              "Name",
              "Status",
              "Products",
              "Reference",
              "UWAttributes",
              "Address",
              "Communications"
          ],
          "additionalProperties": true,
          "properties": {
              "Client": {
                  "title": "Client",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "SGIH"
                  ]
              },
              "Code": {
                  "title": "Code",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "001"
                  ]
              },
              "Name": {
                  "title": "Name",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "test UW"
                  ]
              },
              "Status": {
                  "title": "Status",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Active"
                  ]
              },
              "Products": {
                  "title": "Products",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "1",
                          "2",
                          "3"
                      ]
                  },
                  "examples": [
                      [
                          "1",
                          "2",
                          "3"
                      ]
                  ],
                  "uniqueItems": false
              },
              "Reference": {
                  "title": "Reference",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "108999"
                      ]
                  },
                  "examples": [
                      [
                          "108999"
                      ]
                  ],
                  "uniqueItems": false
              },
              "UWAttributes": {
                  "title": "UWAttributes",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "UWOffice",
                      "ContractNumber",
                      "AccountExecCode"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "UWOffice": {
                          "title": "UWOffice",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Rosewell"
                          ]
                      },
                      "ContractNumber": {
                          "title": "ContractNumber",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "ACV124"
                          ]
                      },
                      "AccountExecCode": {
                          "title": "AccountExecCode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "bclark"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "UWOffice": "Rosewell",
                          "ContractNumber": "ACV124",
                          "AccountExecCode": "bclark"
                      }
                  ]
              },
              "Address": {
                  "title": "Address",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Number",
                      "AddressType",
                      "Description",
                      "AddressLine1",
                      "AddressLine2",
                      "AptSuite",
                      "City",
                      "County",
                      "CountyCode",
                      "State",
                      "PoBox",
                      "Postalcode",
                      "FormattedAddress",
                      "UnFormattedAddress",
                      "AdministrationArea1",
                      "AdministrationArea2",
                      "Locality",
                      "Lat",
                      "Long",
                      "Name",
                      "Premise",
                      "Status",
                      "Territory",
                      "Business",
                      "PlaceId"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Number": {
                          "title": "Number",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              1
                          ]
                      },
                      "AddressType": {
                          "title": "AddressType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Primary"
                          ]
                      },
                      "Description": {
                          "title": "Description",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Mailing Address"
                          ]
                      },
                      "AddressLine1": {
                          "title": "AddressLine1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE"
                          ]
                      },
                      "AddressLine2": {
                          "title": "AddressLine2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Apt I"
                          ]
                      },
                      "AptSuite": {
                          "title": "AptSuite",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "1000"
                          ]
                      },
                      "City": {
                          "title": "City",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Forest Park"
                          ]
                      },
                      "County": {
                          "title": "County",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "US"
                          ]
                      },
                      "CountyCode": {
                          "title": "CountyCode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "COBB"
                          ]
                      },
                      "State": {
                          "title": "State",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "GA"
                          ]
                      },
                      "PoBox": {
                          "title": "PoBox",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "Postalcode": {
                          "title": "Postalcode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "FormattedAddress": {
                          "title": "FormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE, Smyrna GA 30080"
                          ]
                      },
                      "UnFormattedAddress": {
                          "title": "UnFormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141LakeParkDRSESmyrnaGA30080"
                          ]
                      },
                      "AdministrationArea1": {
                          "title": "AdministrationArea1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "AdministrationArea2": {
                          "title": "AdministrationArea2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Locality": {
                          "title": "Locality",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Atlanta"
                          ]
                      },
                      "Lat": {
                          "title": "Lat",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.6654"
                          ]
                      },
                      "Long": {
                          "title": "Long",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.65646"
                          ]
                      },
                      "Name": {
                          "title": "Name",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cobb Galleria Pkwy"
                          ]
                      },
                      "Premise": {
                          "title": "Premise",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Fron"
                          ]
                      },
                      "Status": {
                          "title": "Status",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Active"
                          ]
                      },
                      "Territory": {
                          "title": "Territory",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Business": {
                          "title": "Business",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cogitate Technology Solution"
                          ]
                      },
                      "PlaceId": {
                          "title": "PlaceId",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      }
                  ]
              },
              "Communications": {
                  "title": "Communications",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Type",
                          "SubType",
                          "Value",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "PhNo",
                                  "Email"
                              ]
                          },
                          "SubType": {
                              "title": "SubType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "4707070096",
                                  "nkadam@cogitate.us"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Client": "SGIH",
                  "Code": "001",
                  "Name": "test UW",
                  "Status": "Active",
                  "Products": [
                      "1",
                      "2",
                      "3"
                  ],
                  "Reference": [
                      "108999"
                  ],
                  "UWAttributes": {
                      "UWOffice": "Rosewell",
                      "ContractNumber": "ACV124",
                      "AccountExecCode": "bclark"
                  },
                  "Address": {
                      "Number": 1,
                      "AddressType": "Primary",
                      "Description": "Mailing Address",
                      "AddressLine1": "2141 Lake Park DR SE",
                      "AddressLine2": "Apt I",
                      "AptSuite": "1000",
                      "City": "Forest Park",
                      "County": "US",
                      "CountyCode": "COBB",
                      "State": "GA",
                      "PoBox": "30080",
                      "Postalcode": "30080",
                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                      "AdministrationArea1": "",
                      "AdministrationArea2": "",
                      "Locality": "Atlanta",
                      "Lat": "45.6654",
                      "Long": "45.65646",
                      "Name": "Cobb Galleria Pkwy",
                      "Premise": "Fron",
                      "Status": "Active",
                      "Territory": "",
                      "Business": "Cogitate Technology Solution",
                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                  },
                  "Communications": [
                      {
                          "Type": "PhNo",
                          "SubType": "Primary",
                          "Value": "4707070096",
                          "Status": "Active"
                      },
                      {
                          "Type": "Email",
                          "SubType": "Primary",
                          "Value": "nkadam@cogitate.us",
                          "Status": "Active"
                      }
                  ]
              }
          ]
      },
      "PriorInsurances": {
          "title": "PriorInsurances",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "IsCurrentlyInsured",
                  "CompanyName",
                  "OtherCompanyName",
                  "EffectiveDate",
                  "ExpirationDate",
                  "Premium",
                  "Status"
              ],
              "additionalProperties": true,
              "properties": {
                  "IsCurrentlyInsured": {
                      "title": "IsCurrentlyInsured",
                      "description": " ",
                      "type": "boolean",
                      "default": false,
                      "examples": [
                          false
                      ]
                  },
                  "CompanyName": {
                      "title": "CompanyName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Other"
                      ]
                  },
                  "OtherCompanyName": {
                      "title": "OtherCompanyName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "xyz insurance"
                      ]
                  },
                  "EffectiveDate": {
                      "title": "EffectiveDate",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2022-08-18"
                      ]
                  },
                  "ExpirationDate": {
                      "title": "ExpirationDate",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2023-08-18"
                      ]
                  },
                  "Premium": {
                      "title": "Premium",
                      "description": " ",
                      "type": "number",
                      "default": 0,
                      "examples": [
                          6545
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Active"
                      ]
                  }
              },
              "examples": [
                  {
                      "IsCurrentlyInsured": false,
                      "CompanyName": "Other",
                      "OtherCompanyName": "xyz insurance",
                      "EffectiveDate": "2022-08-18",
                      "ExpirationDate": "2023-08-18",
                      "Premium": 6545,
                      "Status": "Active"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "IsCurrentlyInsured": false,
                      "CompanyName": "Other",
                      "OtherCompanyName": "xyz insurance",
                      "EffectiveDate": "2022-08-18",
                      "ExpirationDate": "2023-08-18",
                      "Premium": 6545,
                      "Status": "Active"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "InsuredAccount": {
          "title": "InsuredAccount",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Type",
              "CreationDate",
              "UserName",
              "FirstName",
              "MiddleName",
              "LastName",
              "DisplayName",
              "BankDetails",
              "Communications",
              "BusinessInfo"
          ],
          "additionalProperties": true,
          "properties": {
              "Type": {
                  "title": "Type",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Primary"
                  ]
              },
              "CreationDate": {
                  "title": "CreationDate",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-08-18"
                  ]
              },
              "UserName": {
                  "title": "UserName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "nkadam"
                  ]
              },
              "FirstName": {
                  "title": "FirstName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Nitin"
                  ]
              },
              "MiddleName": {
                  "title": "MiddleName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "B"
                  ]
              },
              "LastName": {
                  "title": "LastName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Kadam"
                  ]
              },
              "DisplayName": {
                  "title": "DisplayName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Nitin Kadam"
                  ]
              },
              "BankDetails": {
                  "title": "BankDetails",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "AccountName",
                      "BankName",
                      "BranchName",
                      "AccountType",
                      "RoutingNo"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "AccountName": {
                          "title": "AccountName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Nitin Kadam"
                          ]
                      },
                      "BankName": {
                          "title": "BankName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Bank of America"
                          ]
                      },
                      "BranchName": {
                          "title": "BranchName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Smyrna"
                          ]
                      },
                      "AccountType": {
                          "title": "AccountType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Saving"
                          ]
                      },
                      "RoutingNo": {
                          "title": "RoutingNo",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "123456789"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "AccountName": "Nitin Kadam",
                          "BankName": "Bank of America",
                          "BranchName": "Smyrna",
                          "AccountType": "Saving",
                          "RoutingNo": "123456789"
                      }
                  ]
              },
              "Communications": {
                  "title": "Communications",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Type",
                          "SubType",
                          "Value",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "PhNo",
                                  "Email"
                              ]
                          },
                          "SubType": {
                              "title": "SubType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "4707070096",
                                  "nkadam@cogitate.us"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              },
              "BusinessInfo": {
                  "title": "BusinessInfo",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "BusinessType",
                      "YearsInBusiness",
                      "IncorporationAge",
                      "BusinessName",
                      "DisplayName",
                      "RegistrationNumber",
                      "BusinessStruct",
                      "SpecialRisk",
                      "NoOfOwners",
                      "FullTimeEmployees",
                      "PartTimeEmployees",
                      "Website",
                      "IndustryType",
                      "BusinessDecsription",
                      "AnnualRevenue",
                      "NumberOFLocations",
                      "Locations"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "BusinessType": {
                          "title": "BusinessType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Inc"
                          ]
                      },
                      "YearsInBusiness": {
                          "title": "YearsInBusiness",
                          "description": " ",
                          "type": "number",
                          "default": 0.0,
                          "examples": [
                              4.5
                          ]
                      },
                      "IncorporationAge": {
                          "title": "IncorporationAge",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2018-11-30"
                          ]
                      },
                      "BusinessName": {
                          "title": "BusinessName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "segitech"
                          ]
                      },
                      "DisplayName": {
                          "title": "DisplayName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cogitate"
                          ]
                      },
                      "RegistrationNumber": {
                          "title": "RegistrationNumber",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "123A64DF"
                          ]
                      },
                      "BusinessStruct": {
                          "title": "BusinessStruct",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Individual"
                          ]
                      },
                      "SpecialRisk": {
                          "title": "SpecialRisk",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Manager"
                          ]
                      },
                      "NoOfOwners": {
                          "title": "NoOfOwners",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              1
                          ]
                      },
                      "FullTimeEmployees": {
                          "title": "FullTimeEmployees",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              22
                          ]
                      },
                      "PartTimeEmployees": {
                          "title": "PartTimeEmployees",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              12
                          ]
                      },
                      "Website": {
                          "title": "Website",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "http://cogitate.us"
                          ]
                      },
                      "IndustryType": {
                          "title": "IndustryType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Information Technology"
                          ]
                      },
                      "BusinessDecsription": {
                          "title": "BusinessDecsription",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Insurnace Technology"
                          ]
                      },
                      "AnnualRevenue": {
                          "title": "AnnualRevenue",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              9456456
                          ]
                      },
                      "NumberOFLocations": {
                          "title": "NumberOFLocations",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              2
                          ]
                      },
                      "Locations": {
                          "title": "Locations",
                          "description": " ",
                          "type": "array",
                          "default": [],
                          "additionalItems": true,
                          "items": {
                              "title": "A",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "NickName",
                                  "LocationNumber",
                                  "IsValid",
                                  "Status",
                                  "Address",
                                  "Type"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "NickName": {
                                      "title": "NickName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Atlanta"
                                      ]
                                  },
                                  "LocationNumber": {
                                      "title": "LocationNumber",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          1
                                      ]
                                  },
                                  "IsValid": {
                                      "title": "IsValid",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          true
                                      ]
                                  },
                                  "Status": {
                                      "title": "Status",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Active"
                                      ]
                                  },
                                  "Address": {
                                      "title": "Address",
                                      "description": " ",
                                      "type": "object",
                                      "default": {},
                                      "required": [
                                          "Number",
                                          "AddressType",
                                          "Description",
                                          "AddressLine1",
                                          "AddressLine2",
                                          "AptSuite",
                                          "City",
                                          "County",
                                          "CountyCode",
                                          "State",
                                          "PoBox",
                                          "Postalcode",
                                          "FormattedAddress",
                                          "UnFormattedAddress",
                                          "AdministrationArea1",
                                          "AdministrationArea2",
                                          "Locality",
                                          "Lat",
                                          "Long",
                                          "Name",
                                          "Premise",
                                          "Status",
                                          "Territory",
                                          "Business",
                                          "PlaceId"
                                      ],
                                      "additionalProperties": true,
                                      "properties": {
                                          "Number": {
                                              "title": "Number",
                                              "description": " ",
                                              "type": "number",
                                              "default": 0,
                                              "examples": [
                                                  1
                                              ]
                                          },
                                          "AddressType": {
                                              "title": "AddressType",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Primary"
                                              ]
                                          },
                                          "Description": {
                                              "title": "Description",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Mailing Address"
                                              ]
                                          },
                                          "AddressLine1": {
                                              "title": "AddressLine1",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "2141 Lake Park DR SE"
                                              ]
                                          },
                                          "AddressLine2": {
                                              "title": "AddressLine2",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Apt I"
                                              ]
                                          },
                                          "AptSuite": {
                                              "title": "AptSuite",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "1000"
                                              ]
                                          },
                                          "City": {
                                              "title": "City",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Forest Park"
                                              ]
                                          },
                                          "County": {
                                              "title": "County",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "US"
                                              ]
                                          },
                                          "CountyCode": {
                                              "title": "CountyCode",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "COBB"
                                              ]
                                          },
                                          "State": {
                                              "title": "State",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "GA"
                                              ]
                                          },
                                          "PoBox": {
                                              "title": "PoBox",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "30080"
                                              ]
                                          },
                                          "Postalcode": {
                                              "title": "Postalcode",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "30080"
                                              ]
                                          },
                                          "FormattedAddress": {
                                              "title": "FormattedAddress",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "2141 Lake Park DR SE, Smyrna GA 30080"
                                              ]
                                          },
                                          "UnFormattedAddress": {
                                              "title": "UnFormattedAddress",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "2141LakeParkDRSESmyrnaGA30080"
                                              ]
                                          },
                                          "AdministrationArea1": {
                                              "title": "AdministrationArea1",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "AdministrationArea2": {
                                              "title": "AdministrationArea2",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "Locality": {
                                              "title": "Locality",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Atlanta"
                                              ]
                                          },
                                          "Lat": {
                                              "title": "Lat",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "45.6654"
                                              ]
                                          },
                                          "Long": {
                                              "title": "Long",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "45.65646"
                                              ]
                                          },
                                          "Name": {
                                              "title": "Name",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Cobb Galleria Pkwy"
                                              ]
                                          },
                                          "Premise": {
                                              "title": "Premise",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Fron"
                                              ]
                                          },
                                          "Status": {
                                              "title": "Status",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Active"
                                              ]
                                          },
                                          "Territory": {
                                              "title": "Territory",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "Business": {
                                              "title": "Business",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Cogitate Technology Solution"
                                              ]
                                          },
                                          "PlaceId": {
                                              "title": "PlaceId",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                              ]
                                          }
                                      },
                                      "examples": [
                                          {
                                              "Number": 1,
                                              "AddressType": "Primary",
                                              "Description": "Mailing Address",
                                              "AddressLine1": "2141 Lake Park DR SE",
                                              "AddressLine2": "Apt I",
                                              "AptSuite": "1000",
                                              "City": "Forest Park",
                                              "County": "US",
                                              "CountyCode": "COBB",
                                              "State": "GA",
                                              "PoBox": "30080",
                                              "Postalcode": "30080",
                                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                              "AdministrationArea1": "",
                                              "AdministrationArea2": "",
                                              "Locality": "Atlanta",
                                              "Lat": "45.6654",
                                              "Long": "45.65646",
                                              "Name": "Cobb Galleria Pkwy",
                                              "Premise": "Fron",
                                              "Status": "Active",
                                              "Territory": "",
                                              "Business": "Cogitate Technology Solution",
                                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                          }
                                      ]
                                  },
                                  "Type": {
                                      "title": "Type",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Primary"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "NickName": "Atlanta",
                                      "LocationNumber": 1,
                                      "IsValid": true,
                                      "Status": "Active",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Type": "Primary"
                                  }
                              ]
                          },
                          "examples": [
                              [
                                  {
                                      "NickName": "Atlanta",
                                      "LocationNumber": 1,
                                      "IsValid": true,
                                      "Status": "Active",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Type": "Primary"
                                  }
                              ]
                          ],
                          "uniqueItems": false
                      }
                  },
                  "examples": [
                      {
                          "BusinessType": "Inc",
                          "YearsInBusiness": 4.5,
                          "IncorporationAge": "2018-11-30",
                          "BusinessName": "segitech",
                          "DisplayName": "Cogitate",
                          "RegistrationNumber": "123A64DF",
                          "BusinessStruct": "Individual",
                          "SpecialRisk": "Manager",
                          "NoOfOwners": 1,
                          "FullTimeEmployees": 22,
                          "PartTimeEmployees": 12,
                          "Website": "http://cogitate.us",
                          "IndustryType": "Information Technology",
                          "BusinessDecsription": "Insurnace Technology",
                          "AnnualRevenue": 9456456,
                          "NumberOFLocations": 2,
                          "Locations": [
                              {
                                  "NickName": "Atlanta",
                                  "LocationNumber": 1,
                                  "IsValid": true,
                                  "Status": "Active",
                                  "Address": {
                                      "Number": 1,
                                      "AddressType": "Primary",
                                      "Description": "Mailing Address",
                                      "AddressLine1": "2141 Lake Park DR SE",
                                      "AddressLine2": "Apt I",
                                      "AptSuite": "1000",
                                      "City": "Forest Park",
                                      "County": "US",
                                      "CountyCode": "COBB",
                                      "State": "GA",
                                      "PoBox": "30080",
                                      "Postalcode": "30080",
                                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                      "AdministrationArea1": "",
                                      "AdministrationArea2": "",
                                      "Locality": "Atlanta",
                                      "Lat": "45.6654",
                                      "Long": "45.65646",
                                      "Name": "Cobb Galleria Pkwy",
                                      "Premise": "Fron",
                                      "Status": "Active",
                                      "Territory": "",
                                      "Business": "Cogitate Technology Solution",
                                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                  },
                                  "Type": "Primary"
                              }
                          ]
                      }
                  ]
              }
          },
          "examples": [
              {
                  "Type": "Primary",
                  "CreationDate": "2022-08-18",
                  "UserName": "nkadam",
                  "FirstName": "Nitin",
                  "MiddleName": "B",
                  "LastName": "Kadam",
                  "DisplayName": "Nitin Kadam",
                  "BankDetails": {
                      "AccountName": "Nitin Kadam",
                      "BankName": "Bank of America",
                      "BranchName": "Smyrna",
                      "AccountType": "Saving",
                      "RoutingNo": "123456789"
                  },
                  "Communications": [
                      {
                          "Type": "PhNo",
                          "SubType": "Primary",
                          "Value": "4707070096",
                          "Status": "Active"
                      },
                      {
                          "Type": "Email",
                          "SubType": "Primary",
                          "Value": "nkadam@cogitate.us",
                          "Status": "Active"
                      }
                  ],
                  "BusinessInfo": {
                      "BusinessType": "Inc",
                      "YearsInBusiness": 4.5,
                      "IncorporationAge": "2018-11-30",
                      "BusinessName": "segitech",
                      "DisplayName": "Cogitate",
                      "RegistrationNumber": "123A64DF",
                      "BusinessStruct": "Individual",
                      "SpecialRisk": "Manager",
                      "NoOfOwners": 1,
                      "FullTimeEmployees": 22,
                      "PartTimeEmployees": 12,
                      "Website": "http://cogitate.us",
                      "IndustryType": "Information Technology",
                      "BusinessDecsription": "Insurnace Technology",
                      "AnnualRevenue": 9456456,
                      "NumberOFLocations": 2,
                      "Locations": [
                          {
                              "NickName": "Atlanta",
                              "LocationNumber": 1,
                              "IsValid": true,
                              "Status": "Active",
                              "Address": {
                                  "Number": 1,
                                  "AddressType": "Primary",
                                  "Description": "Mailing Address",
                                  "AddressLine1": "2141 Lake Park DR SE",
                                  "AddressLine2": "Apt I",
                                  "AptSuite": "1000",
                                  "City": "Forest Park",
                                  "County": "US",
                                  "CountyCode": "COBB",
                                  "State": "GA",
                                  "PoBox": "30080",
                                  "Postalcode": "30080",
                                  "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                  "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                  "AdministrationArea1": "",
                                  "AdministrationArea2": "",
                                  "Locality": "Atlanta",
                                  "Lat": "45.6654",
                                  "Long": "45.65646",
                                  "Name": "Cobb Galleria Pkwy",
                                  "Premise": "Fron",
                                  "Status": "Active",
                                  "Territory": "",
                                  "Business": "Cogitate Technology Solution",
                                  "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                              },
                              "Type": "Primary"
                          }
                      ]
                  }
              }
          ]
      },
      "JointPolicyHolders": {
          "title": "JointPolicyHolders",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "FirstName",
                  "MiddleName",
                  "LastName",
                  "DateOfBirth",
                  "InsuredType",
                  "Age",
                  "Occupation",
                  "IsHighProfile",
                  "IsAddressSameAsRisk",
                  "Address",
                  "Communications"
              ],
              "additionalProperties": true,
              "properties": {
                  "FirstName": {
                      "title": "FirstName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Nitin"
                      ]
                  },
                  "MiddleName": {
                      "title": "MiddleName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "B"
                      ]
                  },
                  "LastName": {
                      "title": "LastName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Kadam"
                      ]
                  },
                  "DateOfBirth": {
                      "title": "DateOfBirth",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2022-08-18"
                      ]
                  },
                  "InsuredType": {
                      "title": "InsuredType",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "SecondaryInsured"
                      ]
                  },
                  "Age": {
                      "title": "Age",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Value",
                          "ValueType"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "54"
                              ]
                          },
                          "ValueType": {
                              "title": "ValueType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Years"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Value": "54",
                              "ValueType": "Years"
                          }
                      ]
                  },
                  "Occupation": {
                      "title": "Occupation",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Software engineer"
                      ]
                  },
                  "IsHighProfile": {
                      "title": "IsHighProfile",
                      "description": " ",
                      "type": "boolean",
                      "default": false,
                      "examples": [
                          false
                      ]
                  },
                  "IsAddressSameAsRisk": {
                      "title": "IsAddressSameAsRisk",
                      "description": " ",
                      "type": "boolean",
                      "default": false,
                      "examples": [
                          true
                      ]
                  },
                  "Address": {
                      "title": "Address",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Number",
                          "AddressType",
                          "Description",
                          "AddressLine1",
                          "AddressLine2",
                          "AptSuite",
                          "City",
                          "County",
                          "CountyCode",
                          "State",
                          "PoBox",
                          "Postalcode",
                          "FormattedAddress",
                          "UnFormattedAddress",
                          "AdministrationArea1",
                          "AdministrationArea2",
                          "Locality",
                          "Lat",
                          "Long",
                          "Name",
                          "Premise",
                          "Status",
                          "Territory",
                          "Business",
                          "PlaceId"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Number": {
                              "title": "Number",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  1
                              ]
                          },
                          "AddressType": {
                              "title": "AddressType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Mailing Address"
                              ]
                          },
                          "AddressLine1": {
                              "title": "AddressLine1",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2141 Lake Park DR SE"
                              ]
                          },
                          "AddressLine2": {
                              "title": "AddressLine2",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Apt I"
                              ]
                          },
                          "AptSuite": {
                              "title": "AptSuite",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "1000"
                              ]
                          },
                          "City": {
                              "title": "City",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Forest Park"
                              ]
                          },
                          "County": {
                              "title": "County",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "US"
                              ]
                          },
                          "CountyCode": {
                              "title": "CountyCode",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "COBB"
                              ]
                          },
                          "State": {
                              "title": "State",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "GA"
                              ]
                          },
                          "PoBox": {
                              "title": "PoBox",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "30080"
                              ]
                          },
                          "Postalcode": {
                              "title": "Postalcode",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "30080"
                              ]
                          },
                          "FormattedAddress": {
                              "title": "FormattedAddress",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2141 Lake Park DR SE, Smyrna GA 30080"
                              ]
                          },
                          "UnFormattedAddress": {
                              "title": "UnFormattedAddress",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2141LakeParkDRSESmyrnaGA30080"
                              ]
                          },
                          "AdministrationArea1": {
                              "title": "AdministrationArea1",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "AdministrationArea2": {
                              "title": "AdministrationArea2",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "Locality": {
                              "title": "Locality",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Atlanta"
                              ]
                          },
                          "Lat": {
                              "title": "Lat",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "45.6654"
                              ]
                          },
                          "Long": {
                              "title": "Long",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "45.65646"
                              ]
                          },
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Cobb Galleria Pkwy"
                              ]
                          },
                          "Premise": {
                              "title": "Premise",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Fron"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Territory": {
                              "title": "Territory",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "Business": {
                              "title": "Business",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Cogitate Technology Solution"
                              ]
                          },
                          "PlaceId": {
                              "title": "PlaceId",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Number": 1,
                              "AddressType": "Primary",
                              "Description": "Mailing Address",
                              "AddressLine1": "2141 Lake Park DR SE",
                              "AddressLine2": "Apt I",
                              "AptSuite": "1000",
                              "City": "Forest Park",
                              "County": "US",
                              "CountyCode": "COBB",
                              "State": "GA",
                              "PoBox": "30080",
                              "Postalcode": "30080",
                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                              "AdministrationArea1": "",
                              "AdministrationArea2": "",
                              "Locality": "Atlanta",
                              "Lat": "45.6654",
                              "Long": "45.65646",
                              "Name": "Cobb Galleria Pkwy",
                              "Premise": "Fron",
                              "Status": "Active",
                              "Territory": "",
                              "Business": "Cogitate Technology Solution",
                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                          }
                      ]
                  },
                  "Communications": {
                      "title": "Communications",
                      "description": " ",
                      "type": "array",
                      "default": [],
                      "additionalItems": true,
                      "items": {
                          "title": "A",
                          "description": " ",
                          "type": "object",
                          "required": [
                              "Type",
                              "SubType",
                              "Value",
                              "Status"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Type": {
                                  "title": "Type",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "PhNo",
                                      "Email"
                                  ]
                              },
                              "SubType": {
                                  "title": "SubType",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "Primary"
                                  ]
                              },
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "4707070096",
                                      "nkadam@cogitate.us"
                                  ]
                              },
                              "Status": {
                                  "title": "Status",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "Active"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Type": "PhNo",
                                  "SubType": "Primary",
                                  "Value": "4707070096",
                                  "Status": "Active"
                              },
                              {
                                  "Type": "Email",
                                  "SubType": "Primary",
                                  "Value": "nkadam@cogitate.us",
                                  "Status": "Active"
                              }
                          ]
                      },
                      "examples": [
                          [
                              {
                                  "Type": "PhNo",
                                  "SubType": "Primary",
                                  "Value": "4707070096",
                                  "Status": "Active"
                              },
                              {
                                  "Type": "Email",
                                  "SubType": "Primary",
                                  "Value": "nkadam@cogitate.us",
                                  "Status": "Active"
                              }
                          ]
                      ],
                      "uniqueItems": false
                  }
              },
              "examples": [
                  {
                      "FirstName": "Nitin",
                      "MiddleName": "B",
                      "LastName": "Kadam",
                      "DateOfBirth": "2022-08-18",
                      "InsuredType": "SecondaryInsured",
                      "Age": {
                          "Value": "54",
                          "ValueType": "Years"
                      },
                      "Occupation": "Software engineer",
                      "IsHighProfile": false,
                      "IsAddressSameAsRisk": true,
                      "Address": {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      },
                      "Communications": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  }
              ]
          },
          "examples": [
              [
                  {
                      "FirstName": "Nitin",
                      "MiddleName": "B",
                      "LastName": "Kadam",
                      "DateOfBirth": "2022-08-18",
                      "InsuredType": "SecondaryInsured",
                      "Age": {
                          "Value": "54",
                          "ValueType": "Years"
                      },
                      "Occupation": "Software engineer",
                      "IsHighProfile": false,
                      "IsAddressSameAsRisk": true,
                      "Address": {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      },
                      "Communications": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Audit": {
          "title": "Audit",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "CreatedBy",
              "CreatedOn",
              "LastUpdatedBy",
              "LastUpdatedOn"
          ],
          "additionalProperties": true,
          "properties": {
              "CreatedBy": {
                  "title": "CreatedBy",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "nkadam"
                  ]
              },
              "CreatedOn": {
                  "title": "CreatedOn",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-08-18"
                  ]
              },
              "LastUpdatedBy": {
                  "title": "LastUpdatedBy",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "nkadam"
                  ]
              },
              "LastUpdatedOn": {
                  "title": "LastUpdatedOn",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-08-18"
                  ]
              }
          },
          "examples": [
              {
                  "CreatedBy": "nkadam",
                  "CreatedOn": "2022-08-18",
                  "LastUpdatedBy": "nkadam",
                  "LastUpdatedOn": "2022-08-18"
              }
          ]
      },
      "ExternalRefrences": {
          "title": "ExternalRefrences",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "ReferenceNumber",
                  "ReferenceTarget",
                  "Status"
              ],
              "additionalProperties": true,
              "properties": {
                  "ReferenceNumber": {
                      "title": "ReferenceNumber",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "0246879"
                      ]
                  },
                  "ReferenceTarget": {
                      "title": "ReferenceTarget",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "AIM"
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Active"
                      ]
                  }
              },
              "examples": [
                  {
                      "ReferenceNumber": "0246879",
                      "ReferenceTarget": "AIM",
                      "Status": "Active"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "ReferenceNumber": "0246879",
                      "ReferenceTarget": "AIM",
                      "Status": "Active"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Claims": {
          "title": "Claims",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Status",
                  "ClaimSequence",
                  "IsUnrepairedDamage",
                  "DateofLoss",
                  "PaidAmount",
                  "ReserveAmount",
                  "IncidentType",
                  "CoverageType",
                  "ClaimantName",
                  "UnitId",
                  "Remark"
              ],
              "additionalProperties": true,
              "properties": {
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active",
                          "InActive"
                      ]
                  },
                  "ClaimSequence": {
                      "title": "ClaimSequence",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          1.0,
                          2.0
                      ]
                  },
                  "IsUnrepairedDamage": {
                      "title": "IsUnrepairedDamage",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "DateofLoss": {
                      "title": "DateofLoss",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "2022-09-07"
                      ]
                  },
                  "PaidAmount": {
                      "title": "PaidAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          5000,
                          8000
                      ]
                  },
                  "ReserveAmount": {
                      "title": "ReserveAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          5000
                      ]
                  },
                  "IncidentType": {
                      "title": "IncidentType",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Flood",
                          "Hail"
                      ]
                  },
                  "CoverageType": {
                      "title": "CoverageType",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "HO"
                      ]
                  },
                  "ClaimantName": {
                      "title": "ClaimantName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Ben Johns"
                      ]
                  },
                  "UnitId": {
                      "title": "UnitId",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          1,
                          2
                      ]
                  },
                  "Remark": {
                      "title": "Remark",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Flood Claim ",
                          "Hail Damage"
                      ]
                  }
              },
              "examples": [
                  {
                      "Status": "Active",
                      "ClaimSequence": 1.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 5000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Flood",
                      "CoverageType": "HO",
                      "ClaimantName": "Ben Johns",
                      "UnitId": 1,
                      "Remark": "Flood Claim "
                  },
                  {
                      "Status": "InActive",
                      "ClaimSequence": 2.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 8000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Hail",
                      "UnitId": 2,
                      "Remark": "Hail Damage"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Status": "Active",
                      "ClaimSequence": 1.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 5000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Flood",
                      "CoverageType": "HO",
                      "ClaimantName": "Ben Johns",
                      "UnitId": 1,
                      "Remark": "Flood Claim "
                  },
                  {
                      "Status": "InActive",
                      "ClaimSequence": 2.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 8000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Hail",
                      "UnitId": 2,
                      "Remark": "Hail Damage"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Forms": {
          "title": "Forms",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Status",
                  "FormName",
                  "FormDesc",
                  "Sequence",
                  "FormType",
                  "Template",
                  "IsMandatory",
                  "IsChecked",
                  "AcordCode",
                  "File",
                  "Dmspath"
              ],
              "additionalProperties": true,
              "properties": {
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active"
                      ]
                  },
                  "FormName": {
                      "title": "FormName",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "SG1004",
                          "SG1025"
                      ]
                  },
                  "FormDesc": {
                      "title": "FormDesc",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Binder",
                          "Statement of No Other Drivers Form"
                      ]
                  },
                  "Sequence": {
                      "title": "Sequence",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          1.0,
                          2.0
                      ]
                  },
                  "FormType": {
                      "title": "FormType",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Dynamic",
                          "Static"
                      ]
                  },
                  "Template": {
                      "title": "Template",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "l4pb03ugrcr",
                          "slhmuehfzyv"
                      ]
                  },
                  "IsMandatory": {
                      "title": "IsMandatory",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "IsChecked": {
                      "title": "IsChecked",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "AcordCode": {
                      "title": "AcordCode",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "IH005",
                          "IH034"
                      ]
                  },
                  "File": {
                      "title": "File",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          ""
                      ]
                  },
                  "Dmspath": {
                      "title": "Dmspath",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          ""
                      ]
                  }
              },
              "examples": [
                  {
                      "Status": "Active",
                      "FormName": "SG1004",
                      "FormDesc": "Binder",
                      "Sequence": 1.0,
                      "FormType": "Dynamic",
                      "Template": "l4pb03ugrcr",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH005",
                      "File": "",
                      "Dmspath": ""
                  },
                  {
                      "Status": "Active",
                      "FormName": "SG1025",
                      "FormDesc": "Statement of No Other Drivers Form",
                      "Sequence": 2.0,
                      "FormType": "Static",
                      "Template": "slhmuehfzyv",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH034",
                      "File": "",
                      "Dmspath": ""
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Status": "Active",
                      "FormName": "SG1004",
                      "FormDesc": "Binder",
                      "Sequence": 1.0,
                      "FormType": "Dynamic",
                      "Template": "l4pb03ugrcr",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH005",
                      "File": "",
                      "Dmspath": ""
                  },
                  {
                      "Status": "Active",
                      "FormName": "SG1025",
                      "FormDesc": "Statement of No Other Drivers Form",
                      "Sequence": 2.0,
                      "FormType": "Static",
                      "Template": "slhmuehfzyv",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH034",
                      "File": "",
                      "Dmspath": ""
                  }
              ]
          ],
          "uniqueItems": false
      },
      "PolicyCoverages": {
          "title": "PolicyCoverages",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Coverages"
          ],
          "additionalProperties": true,
          "properties": {
              "Coverages": {
                  "title": "Coverages",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Name",
                          "Description",
                          "Type",
                          "SettlementType",
                          "Value",
                          "Limit",
                          "LimitAmount",
                          "Deductible",
                          "IsApplicable",
                          "IsSelected",
                          "IsMandatory",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Combined Single Limit"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Combined Single Limit"
                              ]
                          },
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Coverage"
                              ]
                          },
                          "SettlementType": {
                              "title": "SettlementType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "ACV"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "5"
                              ]
                          },
                          "Limit": {
                              "title": "Limit",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  10000
                              ]
                          },
                          "LimitAmount": {
                              "title": "LimitAmount",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  10000
                              ]
                          },
                          "Deductible": {
                              "title": "Deductible",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  500
                              ]
                          },
                          "IsApplicable": {
                              "title": "IsApplicable",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "IsSelected": {
                              "title": "IsSelected",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "IsMandatory": {
                              "title": "IsMandatory",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Name": "Combined Single Limit",
                              "Description": "Combined Single Limit",
                              "Type": "Coverage",
                              "SettlementType": "ACV",
                              "Value": "5",
                              "Limit": 10000,
                              "LimitAmount": 10000,
                              "Deductible": 500,
                              "IsApplicable": true,
                              "IsSelected": true,
                              "IsMandatory": true,
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Name": "Combined Single Limit",
                              "Description": "Combined Single Limit",
                              "Type": "Coverage",
                              "SettlementType": "ACV",
                              "Value": "5",
                              "Limit": 10000,
                              "LimitAmount": 10000,
                              "Deductible": 500,
                              "IsApplicable": true,
                              "IsSelected": true,
                              "IsMandatory": true,
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Coverages": [
                      {
                          "Name": "Combined Single Limit",
                          "Description": "Combined Single Limit",
                          "Type": "Coverage",
                          "SettlementType": "ACV",
                          "Value": "5",
                          "Limit": 10000,
                          "LimitAmount": 10000,
                          "Deductible": 500,
                          "IsApplicable": true,
                          "IsSelected": true,
                          "IsMandatory": true,
                          "Status": "Active"
                      }
                  ]
              }
          ]
      },
      "PremiumFactors": {
          "title": "PremiumFactors",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Name",
                  "Status",
                  "Type",
                  "Description",
                  "IsApplicable",
                  "IsSelected",
                  "IsMandatory",
                  "Rate",
                  "Limit",
                  "LimitAmount",
                  "Deductible",
                  "Premium",
                  "EffectivePremium",
                  "PremiumDifference",
                  "Factor"
              ],
              "additionalProperties": true,
              "properties": {
                  "Name": {
                      "title": "Name",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "RP",
                          "MinPre"
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active"
                      ]
                  },
                  "Type": {
                      "title": "Type",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "SUR"
                      ]
                  },
                  "Description": {
                      "title": "Description",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Risk Premium",
                          "Minimum Premium"
                      ]
                  },
                  "IsApplicable": {
                      "title": "IsApplicable",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "IsSelected": {
                      "title": "IsSelected",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "IsMandatory": {
                      "title": "IsMandatory",
                      "description": " ",
                      "type": [
                          "boolean",
                          "string"
                      ],
                      "examples": [
                          true,
                          ""
                      ]
                  },
                  "Rate": {
                      "title": "Rate",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Limit": {
                      "title": "Limit",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "LimitAmount": {
                      "title": "LimitAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Deductible": {
                      "title": "Deductible",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Premium": {
                      "title": "Premium",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "EffectivePremium": {
                      "title": "EffectivePremium",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "PremiumDifference": {
                      "title": "PremiumDifference",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Factor": {
                      "title": "Factor",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Name",
                          "Type",
                          "Description",
                          "Rate",
                          "Limit",
                          "LimitAmount",
                          "Premium",
                          "Status",
                          "IsApplicable",
                          "IsSelected",
                          "IsMandatory",
                          "Deductible",
                          "EffectivePremium"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "RP",
                                  "MinPre"
                              ]
                          },
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "SUR"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Risk Premium",
                                  "Minimum Premium"
                              ]
                          },
                          "Rate": {
                              "title": "Rate",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "Limit": {
                              "title": "Limit",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "LimitAmount": {
                              "title": "LimitAmount",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "Premium": {
                              "title": "Premium",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "IsApplicable": {
                              "title": "IsApplicable",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "IsSelected": {
                              "title": "IsSelected",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "IsMandatory": {
                              "title": "IsMandatory",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "Deductible": {
                              "title": "Deductible",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "EffectivePremium": {
                              "title": "EffectivePremium",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Name": "RP",
                              "Type": "SUR",
                              "Description": "Risk Premium",
                              "Rate": 0,
                              "Limit": 0,
                              "LimitAmount": 0,
                              "Premium": 0,
                              "Status": "Active",
                              "IsApplicable": "",
                              "IsSelected": "",
                              "IsMandatory": "",
                              "Deductible": 0,
                              "EffectivePremium": 0
                          },
                          {
                              "Name": "MinPre",
                              "Type": "SUR",
                              "Description": "Minimum Premium",
                              "Rate": 0,
                              "Limit": 0,
                              "LimitAmount": 0,
                              "Premium": 0,
                              "Status": "Active",
                              "IsApplicable": "",
                              "IsSelected": "",
                              "IsMandatory": "",
                              "Deductible": 0,
                              "EffectivePremium": 0
                          }
                      ]
                  }
              },
              "examples": [
                  {
                      "Name": "RP",
                      "Status": "Active",
                      "Type": "SUR",
                      "Description": "Risk Premium",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": true,
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Deductible": 0,
                      "Premium": 0,
                      "EffectivePremium": 0,
                      "PremiumDifference": 0,
                      "Factor": {
                          "Name": "RP",
                          "Type": "SUR",
                          "Description": "Risk Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      }
                  },
                  {
                      "Name": "MinPre",
                      "Type": "SUR",
                      "Description": "Minimum Premium",
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Premium": 0,
                      "Status": "Active",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": "",
                      "Deductible": 0,
                      "EffectivePremium": 0,
                      "Factor": {
                          "Name": "MinPre",
                          "Type": "SUR",
                          "Description": "Minimum Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      },
                      "PremiumDifference": 0
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Name": "RP",
                      "Status": "Active",
                      "Type": "SUR",
                      "Description": "Risk Premium",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": true,
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Deductible": 0,
                      "Premium": 0,
                      "EffectivePremium": 0,
                      "PremiumDifference": 0,
                      "Factor": {
                          "Name": "RP",
                          "Type": "SUR",
                          "Description": "Risk Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      }
                  },
                  {
                      "Name": "MinPre",
                      "Type": "SUR",
                      "Description": "Minimum Premium",
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Premium": 0,
                      "Status": "Active",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": "",
                      "Deductible": 0,
                      "EffectivePremium": 0,
                      "Factor": {
                          "Name": "MinPre",
                          "Type": "SUR",
                          "Description": "Minimum Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      },
                      "PremiumDifference": 0
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Premium": {
          "title": "Premium",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "BasicPremium",
              "Surcharge",
              "Discount",
              "MinPremium",
              "EffectivePremium",
              "AnnualPremium"
          ],
          "additionalProperties": true,
          "properties": {
              "BasicPremium": {
                  "title": "BasicPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      153
                  ]
              },
              "Surcharge": {
                  "title": "Surcharge",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "Discount": {
                  "title": "Discount",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "MinPremium": {
                  "title": "MinPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "EffectivePremium": {
                  "title": "EffectivePremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "AnnualPremium": {
                  "title": "AnnualPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              }
          },
          "examples": [
              {
                  "BasicPremium": 153,
                  "Surcharge": 0,
                  "Discount": 0,
                  "MinPremium": 0,
                  "EffectivePremium": 0,
                  "AnnualPremium": 0
              }
          ]
      },
      "TotalPremium": {
          "title": "TotalPremium",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "BasicPremium",
              "Surcharge",
              "Discount",
              "MinPremium",
              "EffectivePremium",
              "AnnualPremium",
              "PriorAnnualPremium",
              "EffectivePremiumWithFeesAndTaxes",
              "AnnualPremiumWithFeesAndTaxes"
          ],
          "additionalProperties": true,
          "properties": {
              "BasicPremium": {
                  "title": "BasicPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      4500
                  ]
              },
              "Surcharge": {
                  "title": "Surcharge",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "Discount": {
                  "title": "Discount",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "MinPremium": {
                  "title": "MinPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      750
                  ]
              },
              "EffectivePremium": {
                  "title": "EffectivePremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      4500
                  ]
              },
              "AnnualPremium": {
                  "title": "AnnualPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      4500
                  ]
              },
              "PriorAnnualPremium": {
                  "title": "PriorAnnualPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "EffectivePremiumWithFeesAndTaxes": {
                  "title": "EffectivePremiumWithFeesAndTaxes",
                  "description": " ",
                  "type": "number",
                  "default": 0.0,
                  "examples": [
                      4938.16
                  ]
              },
              "AnnualPremiumWithFeesAndTaxes": {
                  "title": "AnnualPremiumWithFeesAndTaxes",
                  "description": " ",
                  "type": "number",
                  "default": 0.0,
                  "examples": [
                      4938.16
                  ]
              }
          },
          "examples": [
              {
                  "BasicPremium": 4500,
                  "Surcharge": 0,
                  "Discount": 0,
                  "MinPremium": 750,
                  "EffectivePremium": 4500,
                  "AnnualPremium": 4500,
                  "PriorAnnualPremium": 0,
                  "EffectivePremiumWithFeesAndTaxes": 4938.16,
                  "AnnualPremiumWithFeesAndTaxes": 4938.16
              }
          ]
      },
      "FeesAndTaxes": {
          "title": "FeesAndTaxes",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Code",
                  "IsOverride",
                  "Status",
                  "Value",
                  "ValueType",
                  "Amount",
                  "AnnualAmount",
                  "ProductFeesAndTaxes"
              ],
              "additionalProperties": true,
              "properties": {
                  "Code": {
                      "title": "Code",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "INSFEE",
                          "PFEE"
                      ]
                  },
                  "IsOverride": {
                      "title": "IsOverride",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          false
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active"
                      ]
                  },
                  "Value": {
                      "title": "Value",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          25
                      ]
                  },
                  "ValueType": {
                      "title": "ValueType",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "V"
                      ]
                  },
                  "Amount": {
                      "title": "Amount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          25
                      ]
                  },
                  "AnnualAmount": {
                      "title": "AnnualAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          25
                      ]
                  },
                  "ProductFeesAndTaxes": {
                      "title": "ProductFeesAndTaxes",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Code",
                          "Description",
                          "EffectiveFrom",
                          "Status",
                          "Product",
                          "IsEarned",
                          "Value",
                          "ValueType",
                          "DecimalPoints",
                          "RangeFrom",
                          "RangeTo",
                          "RangeValueType",
                          "Transactions",
                          "CalculateOn",
                          "Term"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Code": {
                              "title": "Code",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "INSFEE",
                                  "PFEE"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Installment Fee",
                                  "Policy Fee"
                              ]
                          },
                          "EffectiveFrom": {
                              "title": "EffectiveFrom",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "2020-01-01"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Product": {
                              "title": "Product",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "GAPA"
                              ]
                          },
                          "IsEarned": {
                              "title": "IsEarned",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "0"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "0.0000",
                                  "25.0000"
                              ]
                          },
                          "ValueType": {
                              "title": "ValueType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "V"
                              ]
                          },
                          "DecimalPoints": {
                              "title": "DecimalPoints",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "RangeFrom": {
                              "title": "RangeFrom",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "0.0000"
                              ]
                          },
                          "RangeTo": {
                              "title": "RangeTo",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "99999.0000"
                              ]
                          },
                          "RangeValueType": {
                              "title": "RangeValueType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "V"
                              ]
                          },
                          "Transactions": {
                              "title": "Transactions",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "A,P,CF,IF,R"
                              ]
                          },
                          "CalculateOn": {
                              "title": "CalculateOn",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "Term": {
                              "title": "Term",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "12"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Code": "INSFEE",
                              "Description": "Installment Fee",
                              "EffectiveFrom": "2020-01-01",
                              "Status": "Active",
                              "Product": "GAPA",
                              "IsEarned": "0",
                              "Value": "0.0000",
                              "ValueType": "V",
                              "DecimalPoints": "",
                              "RangeFrom": "0.0000",
                              "RangeTo": "99999.0000",
                              "RangeValueType": "V",
                              "Transactions": "A,P,CF,IF,R",
                              "CalculateOn": "",
                              "Term": "12"
                          },
                          {
                              "Code": "PFEE",
                              "Description": "Policy Fee",
                              "EffectiveFrom": "2020-01-01",
                              "Status": "Active",
                              "Product": "GAPA",
                              "IsEarned": "0",
                              "Value": "25.0000",
                              "ValueType": "V",
                              "DecimalPoints": "",
                              "RangeFrom": "0.0000",
                              "RangeTo": "99999.0000",
                              "RangeValueType": "V",
                              "Transactions": "A,P,CF,IF,R",
                              "CalculateOn": "",
                              "Term": "12"
                          }
                      ]
                  }
              },
              "examples": [
                  {
                      "Code": "INSFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 0,
                      "ValueType": "V",
                      "Amount": 0,
                      "AnnualAmount": 0,
                      "ProductFeesAndTaxes": {
                          "Code": "INSFEE",
                          "Description": "Installment Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "0.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  },
                  {
                      "Code": "PFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 25,
                      "ValueType": "V",
                      "Amount": 25,
                      "AnnualAmount": 25,
                      "ProductFeesAndTaxes": {
                          "Code": "PFEE",
                          "Description": "Policy Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "25.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Code": "INSFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 0,
                      "ValueType": "V",
                      "Amount": 0,
                      "AnnualAmount": 0,
                      "ProductFeesAndTaxes": {
                          "Code": "INSFEE",
                          "Description": "Installment Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "0.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  },
                  {
                      "Code": "PFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 25,
                      "ValueType": "V",
                      "Amount": 25,
                      "AnnualAmount": 25,
                      "ProductFeesAndTaxes": {
                          "Code": "PFEE",
                          "Description": "Policy Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "25.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Risks": {
          "title": "Risks",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Vehicles",
              "Drivers"
          ],
          "additionalProperties": true,
          "properties": {
              "Vehicles": {
                  "title": "Vehicles",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "UnitId",
                          "UnitNumber",
                          "Name",
                          "UnitType",
                          "Status",
                          "Coverages",
                          "PremiumFactors",
                          "Premium",
                          "AdditionalParties",
                          "Audit",
                          "RiskAttributes"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "UnitId": {
                              "title": "UnitId",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  1
                              ]
                          },
                          "UnitNumber": {
                              "title": "UnitNumber",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "1"
                              ]
                          },
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Vehicle"
                              ]
                          },
                          "UnitType": {
                              "title": "UnitType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Vehicle"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Coverages": {
                              "title": "Coverages",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Description",
                                      "Type",
                                      "SettlementType",
                                      "Value",
                                      "Limit",
                                      "LimitAmount",
                                      "Deductible",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Status"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Coverage"
                                          ]
                                      },
                                      "SettlementType": {
                                          "title": "SettlementType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "ACV"
                                          ]
                                      },
                                      "Value": {
                                          "title": "Value",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "5"
                                          ]
                                      },
                                      "Limit": {
                                          "title": "Limit",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "LimitAmount": {
                                          "title": "LimitAmount",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "PremiumFactors": {
                              "title": "PremiumFactors",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Type",
                                      "Description",
                                      "Rate",
                                      "Premium",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Deductible",
                                      "EffectivePremium",
                                      "PremiumDifference",
                                      "Status",
                                      "Factor"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "CSL"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "SUR"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Rate": {
                                          "title": "Rate",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "Premium": {
                                          "title": "Premium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "EffectivePremium": {
                                          "title": "EffectivePremium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "PremiumDifference": {
                                          "title": "PremiumDifference",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      },
                                      "Factor": {
                                          "title": "Factor",
                                          "description": " ",
                                          "type": "object",
                                          "default": {},
                                          "required": [
                                              "Name",
                                              "Type",
                                              "Description",
                                              "Rate",
                                              "Limit",
                                              "LimitAmount",
                                              "Deductible",
                                              "Premium",
                                              "EffectivePremium",
                                              "IsApplicable",
                                              "IsSelected",
                                              "IsMandatory"
                                          ],
                                          "additionalProperties": true,
                                          "properties": {
                                              "Name": {
                                                  "title": "Name",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "PDCollNZ"
                                                  ]
                                              },
                                              "Type": {
                                                  "title": "Type",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "SUR"
                                                  ]
                                              },
                                              "Description": {
                                                  "title": "Description",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Physical Damage Rating - Collision(Non-Zone)"
                                                  ]
                                              },
                                              "Rate": {
                                                  "title": "Rate",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      0
                                                  ]
                                              },
                                              "Limit": {
                                                  "title": "Limit",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "LimitAmount": {
                                                  "title": "LimitAmount",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "Deductible": {
                                                  "title": "Deductible",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      500
                                                  ]
                                              },
                                              "Premium": {
                                                  "title": "Premium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "EffectivePremium": {
                                                  "title": "EffectivePremium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "IsApplicable": {
                                                  "title": "IsApplicable",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsSelected": {
                                                  "title": "IsSelected",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsMandatory": {
                                                  "title": "IsMandatory",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              }
                                          },
                                          "examples": [
                                              {
                                                  "Name": "PDCollNZ",
                                                  "Type": "SUR",
                                                  "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                                  "Rate": 0,
                                                  "Limit": 10000,
                                                  "LimitAmount": 10000,
                                                  "Deductible": 500,
                                                  "Premium": 119,
                                                  "EffectivePremium": 119,
                                                  "IsApplicable": true,
                                                  "IsSelected": true,
                                                  "IsMandatory": true
                                              }
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "CSL",
                                          "Type": "SUR",
                                          "Description": "Combined Single Limit",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "CSL",
                                          "Type": "SUR",
                                          "Description": "Combined Single Limit",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "Premium": {
                              "title": "Premium",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "BasicPremium",
                                  "Surcharge",
                                  "Discount",
                                  "MinPremium",
                                  "EffectivePremium",
                                  "AnnualPremium",
                                  "EffectivePremiumWithFeesAndTaxes",
                                  "AnnualPremiumWithFeesAndTaxes"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "BasicPremium": {
                                      "title": "BasicPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "Surcharge": {
                                      "title": "Surcharge",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "Discount": {
                                      "title": "Discount",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "MinPremium": {
                                      "title": "MinPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "EffectivePremium": {
                                      "title": "EffectivePremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "AnnualPremium": {
                                      "title": "AnnualPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "EffectivePremiumWithFeesAndTaxes": {
                                      "title": "EffectivePremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  },
                                  "AnnualPremiumWithFeesAndTaxes": {
                                      "title": "AnnualPremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "BasicPremium": 12005,
                                      "Surcharge": 0,
                                      "Discount": 0,
                                      "MinPremium": 0,
                                      "EffectivePremium": 12005,
                                      "AnnualPremium": 12005,
                                      "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                      "AnnualPremiumWithFeesAndTaxes": 12405.16
                                  }
                              ]
                          },
                          "AdditionalParties": {
                              "title": "AdditionalParties",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Status",
                                      "Name",
                                      "ReferenceNumber",
                                      "IsPayee",
                                      "PartyType",
                                      "InterestType",
                                      "CreatedOn",
                                      "DeletedOn",
                                      "Address",
                                      "Communications"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      },
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "bank of america"
                                          ]
                                      },
                                      "ReferenceNumber": {
                                          "title": "ReferenceNumber",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "132456"
                                          ]
                                      },
                                      "IsPayee": {
                                          "title": "IsPayee",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "PartyType": {
                                          "title": "PartyType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Mortgagee"
                                          ]
                                      },
                                      "InterestType": {
                                          "title": "InterestType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Mortgagee"
                                          ]
                                      },
                                      "CreatedOn": {
                                          "title": "CreatedOn",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "2018-08-18"
                                          ]
                                      },
                                      "DeletedOn": {
                                          "title": "DeletedOn",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "2022-11-30"
                                          ]
                                      },
                                      "Address": {
                                          "title": "Address",
                                          "description": " ",
                                          "type": "object",
                                          "default": {},
                                          "required": [
                                              "Number",
                                              "AddressType",
                                              "Description",
                                              "AddressLine1",
                                              "AddressLine2",
                                              "AptSuite",
                                              "City",
                                              "County",
                                              "CountyCode",
                                              "State",
                                              "PoBox",
                                              "Postalcode",
                                              "FormattedAddress",
                                              "UnFormattedAddress",
                                              "AdministrationArea1",
                                              "AdministrationArea2",
                                              "Locality",
                                              "Lat",
                                              "Long",
                                              "Name",
                                              "Premise",
                                              "Status",
                                              "Territory",
                                              "Business",
                                              "PlaceId"
                                          ],
                                          "additionalProperties": true,
                                          "properties": {
                                              "Number": {
                                                  "title": "Number",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      1
                                                  ]
                                              },
                                              "AddressType": {
                                                  "title": "AddressType",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Primary"
                                                  ]
                                              },
                                              "Description": {
                                                  "title": "Description",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Mailing Address"
                                                  ]
                                              },
                                              "AddressLine1": {
                                                  "title": "AddressLine1",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "2141 Lake Park DR SE"
                                                  ]
                                              },
                                              "AddressLine2": {
                                                  "title": "AddressLine2",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Apt I"
                                                  ]
                                              },
                                              "AptSuite": {
                                                  "title": "AptSuite",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "1000"
                                                  ]
                                              },
                                              "City": {
                                                  "title": "City",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Forest Park"
                                                  ]
                                              },
                                              "County": {
                                                  "title": "County",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "US"
                                                  ]
                                              },
                                              "CountyCode": {
                                                  "title": "CountyCode",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "COBB"
                                                  ]
                                              },
                                              "State": {
                                                  "title": "State",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "GA"
                                                  ]
                                              },
                                              "PoBox": {
                                                  "title": "PoBox",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "30080"
                                                  ]
                                              },
                                              "Postalcode": {
                                                  "title": "Postalcode",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "30080"
                                                  ]
                                              },
                                              "FormattedAddress": {
                                                  "title": "FormattedAddress",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "2141 Lake Park DR SE, Smyrna GA 30080"
                                                  ]
                                              },
                                              "UnFormattedAddress": {
                                                  "title": "UnFormattedAddress",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "2141LakeParkDRSESmyrnaGA30080"
                                                  ]
                                              },
                                              "AdministrationArea1": {
                                                  "title": "AdministrationArea1",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      ""
                                                  ]
                                              },
                                              "AdministrationArea2": {
                                                  "title": "AdministrationArea2",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      ""
                                                  ]
                                              },
                                              "Locality": {
                                                  "title": "Locality",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Atlanta"
                                                  ]
                                              },
                                              "Lat": {
                                                  "title": "Lat",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "45.6654"
                                                  ]
                                              },
                                              "Long": {
                                                  "title": "Long",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "45.65646"
                                                  ]
                                              },
                                              "Name": {
                                                  "title": "Name",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Cobb Galleria Pkwy"
                                                  ]
                                              },
                                              "Premise": {
                                                  "title": "Premise",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Fron"
                                                  ]
                                              },
                                              "Status": {
                                                  "title": "Status",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Active"
                                                  ]
                                              },
                                              "Territory": {
                                                  "title": "Territory",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      ""
                                                  ]
                                              },
                                              "Business": {
                                                  "title": "Business",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Cogitate Technology Solution"
                                                  ]
                                              },
                                              "PlaceId": {
                                                  "title": "PlaceId",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                                  ]
                                              }
                                          },
                                          "examples": [
                                              {
                                                  "Number": 1,
                                                  "AddressType": "Primary",
                                                  "Description": "Mailing Address",
                                                  "AddressLine1": "2141 Lake Park DR SE",
                                                  "AddressLine2": "Apt I",
                                                  "AptSuite": "1000",
                                                  "City": "Forest Park",
                                                  "County": "US",
                                                  "CountyCode": "COBB",
                                                  "State": "GA",
                                                  "PoBox": "30080",
                                                  "Postalcode": "30080",
                                                  "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                                  "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                                  "AdministrationArea1": "",
                                                  "AdministrationArea2": "",
                                                  "Locality": "Atlanta",
                                                  "Lat": "45.6654",
                                                  "Long": "45.65646",
                                                  "Name": "Cobb Galleria Pkwy",
                                                  "Premise": "Fron",
                                                  "Status": "Active",
                                                  "Territory": "",
                                                  "Business": "Cogitate Technology Solution",
                                                  "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                              }
                                          ]
                                      },
                                      "Communications": {
                                          "title": "Communications",
                                          "description": " ",
                                          "type": "array",
                                          "default": [],
                                          "additionalItems": true,
                                          "items": {
                                              "title": "A",
                                              "description": " ",
                                              "type": "object",
                                              "required": [
                                                  "Type",
                                                  "SubType",
                                                  "Value",
                                                  "Status"
                                              ],
                                              "additionalProperties": true,
                                              "properties": {
                                                  "Type": {
                                                      "title": "Type",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "PhNo",
                                                          "Email"
                                                      ]
                                                  },
                                                  "SubType": {
                                                      "title": "SubType",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "Primary"
                                                      ]
                                                  },
                                                  "Value": {
                                                      "title": "Value",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "4707070096",
                                                          "nkadam@cogitate.us"
                                                      ]
                                                  },
                                                  "Status": {
                                                      "title": "Status",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "Active"
                                                      ]
                                                  }
                                              },
                                              "examples": [
                                                  {
                                                      "Type": "PhNo",
                                                      "SubType": "Primary",
                                                      "Value": "4707070096",
                                                      "Status": "Active"
                                                  },
                                                  {
                                                      "Type": "Email",
                                                      "SubType": "Primary",
                                                      "Value": "nkadam@cogitate.us",
                                                      "Status": "Active"
                                                  }
                                              ]
                                          },
                                          "examples": [
                                              [
                                                  {
                                                      "Type": "PhNo",
                                                      "SubType": "Primary",
                                                      "Value": "4707070096",
                                                      "Status": "Active"
                                                  },
                                                  {
                                                      "Type": "Email",
                                                      "SubType": "Primary",
                                                      "Value": "nkadam@cogitate.us",
                                                      "Status": "Active"
                                                  }
                                              ]
                                          ],
                                          "uniqueItems": false
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Status": "Active",
                                          "Name": "bank of america",
                                          "ReferenceNumber": "132456",
                                          "IsPayee": true,
                                          "PartyType": "Mortgagee",
                                          "InterestType": "Mortgagee",
                                          "CreatedOn": "2018-08-18",
                                          "DeletedOn": "2022-11-30",
                                          "Address": {
                                              "Number": 1,
                                              "AddressType": "Primary",
                                              "Description": "Mailing Address",
                                              "AddressLine1": "2141 Lake Park DR SE",
                                              "AddressLine2": "Apt I",
                                              "AptSuite": "1000",
                                              "City": "Forest Park",
                                              "County": "US",
                                              "CountyCode": "COBB",
                                              "State": "GA",
                                              "PoBox": "30080",
                                              "Postalcode": "30080",
                                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                              "AdministrationArea1": "",
                                              "AdministrationArea2": "",
                                              "Locality": "Atlanta",
                                              "Lat": "45.6654",
                                              "Long": "45.65646",
                                              "Name": "Cobb Galleria Pkwy",
                                              "Premise": "Fron",
                                              "Status": "Active",
                                              "Territory": "",
                                              "Business": "Cogitate Technology Solution",
                                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                          },
                                          "Communications": [
                                              {
                                                  "Type": "PhNo",
                                                  "SubType": "Primary",
                                                  "Value": "4707070096",
                                                  "Status": "Active"
                                              },
                                              {
                                                  "Type": "Email",
                                                  "SubType": "Primary",
                                                  "Value": "nkadam@cogitate.us",
                                                  "Status": "Active"
                                              }
                                          ]
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Status": "Active",
                                          "Name": "bank of america",
                                          "ReferenceNumber": "132456",
                                          "IsPayee": true,
                                          "PartyType": "Mortgagee",
                                          "InterestType": "Mortgagee",
                                          "CreatedOn": "2018-08-18",
                                          "DeletedOn": "2022-11-30",
                                          "Address": {
                                              "Number": 1,
                                              "AddressType": "Primary",
                                              "Description": "Mailing Address",
                                              "AddressLine1": "2141 Lake Park DR SE",
                                              "AddressLine2": "Apt I",
                                              "AptSuite": "1000",
                                              "City": "Forest Park",
                                              "County": "US",
                                              "CountyCode": "COBB",
                                              "State": "GA",
                                              "PoBox": "30080",
                                              "Postalcode": "30080",
                                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                              "AdministrationArea1": "",
                                              "AdministrationArea2": "",
                                              "Locality": "Atlanta",
                                              "Lat": "45.6654",
                                              "Long": "45.65646",
                                              "Name": "Cobb Galleria Pkwy",
                                              "Premise": "Fron",
                                              "Status": "Active",
                                              "Territory": "",
                                              "Business": "Cogitate Technology Solution",
                                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                          },
                                          "Communications": [
                                              {
                                                  "Type": "PhNo",
                                                  "SubType": "Primary",
                                                  "Value": "4707070096",
                                                  "Status": "Active"
                                              },
                                              {
                                                  "Type": "Email",
                                                  "SubType": "Primary",
                                                  "Value": "nkadam@cogitate.us",
                                                  "Status": "Active"
                                              }
                                          ]
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "Audit": {
                              "title": "Audit",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "CreatedBy",
                                  "CreatedOn",
                                  "DeletedOn",
                                  "LastUpdatedBy",
                                  "LastUpdatedOn"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "CreatedBy": {
                                      "title": "CreatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "CreatedOn": {
                                      "title": "CreatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  },
                                  "DeletedOn": {
                                      "title": "DeletedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-11-30"
                                      ]
                                  },
                                  "LastUpdatedBy": {
                                      "title": "LastUpdatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "LastUpdatedOn": {
                                      "title": "LastUpdatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "CreatedBy": "nkadam",
                                      "CreatedOn": "2022-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "LastUpdatedBy": "nkadam",
                                      "LastUpdatedOn": "2022-08-18"
                                  }
                              ]
                          },
                          "RiskAttributes": {
                              "title": "RiskAttributes",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "ClassificationType",
                                  "SecondaryUse",
                                  "SecondaryUsePercent",
                                  "VehicleType",
                                  "VIN",
                                  "Year",
                                  "VehicleAge",
                                  "Make",
                                  "Model",
                                  "OwnedOrLeased",
                                  "BusinessUseClass",
                                  "SizeClass",
                                  "GROSSCOMBWEIGHT",
                                  "PrimaryGaragingLocation",
                                  "RADIUSCLASSTYPE",
                                  "VEHPRICE",
                                  "PASSIVERESTR",
                                  "VEHYEAR",
                                  "ANTILOCKBRAKES",
                                  "COSTTYPE",
                                  "FARTHESTLOCCITY",
                                  "FARTHESTLOCCOUNTY",
                                  "FARTHESTLOCSTATE",
                                  "FARTHESTLOC",
                                  "ISVEHICLEUPLOADED",
                                  "COMPDED",
                                  "COLLDED",
                                  "MPDED",
                                  "HASPD",
                                  "HASMP",
                                  "TEMPLATENAME",
                                  "UWREFMSG",
                                  "GARAGELOC",
                                  "HASRENTAL",
                                  "CSLLIMIT",
                                  "LIABDED",
                                  "UMTYPE",
                                  "UMDED",
                                  "UMLIMIT"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "ClassificationType": {
                                      "title": "ClassificationType",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS"
                                      ]
                                  },
                                  "SecondaryUse": {
                                      "title": "SecondaryUse",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "SecondaryUsePercent": {
                                      "title": "SecondaryUsePercent",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "VehicleType": {
                                      "title": "VehicleType",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "CargoVan"
                                      ]
                                  },
                                  "VIN": {
                                      "title": "VIN",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2A4RR8DG6BR760259"
                                      ]
                                  },
                                  "Year": {
                                      "title": "Year",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2000"
                                      ]
                                  },
                                  "VehicleAge": {
                                      "title": "VehicleAge",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "15"
                                      ]
                                  },
                                  "Make": {
                                      "title": "Make",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "AlfaRomeo"
                                      ]
                                  },
                                  "Model": {
                                      "title": "Model",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Ecoride"
                                      ]
                                  },
                                  "OwnedOrLeased": {
                                      "title": "OwnedOrLeased",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Owned"
                                      ]
                                  },
                                  "BusinessUseClass": {
                                      "title": "BusinessUseClass",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "retail"
                                      ]
                                  },
                                  "SizeClass": {
                                      "title": "SizeClass",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "lighttrucks"
                                      ]
                                  },
                                  "GROSSCOMBWEIGHT": {
                                      "title": "GROSSCOMBWEIGHT",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "MoreThan45000"
                                      ]
                                  },
                                  "PrimaryGaragingLocation": {
                                      "title": "PrimaryGaragingLocation",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "RADIUSCLASSTYPE": {
                                      "title": "RADIUSCLASSTYPE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "local"
                                      ]
                                  },
                                  "VEHPRICE": {
                                      "title": "VEHPRICE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "20000"
                                      ]
                                  },
                                  "PASSIVERESTR": {
                                      "title": "PASSIVERESTR",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "VEHYEAR": {
                                      "title": "VEHYEAR",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "15"
                                      ]
                                  },
                                  "ANTILOCKBRAKES": {
                                      "title": "ANTILOCKBRAKES",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "COSTTYPE": {
                                      "title": "COSTTYPE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "ACV"
                                      ]
                                  },
                                  "FARTHESTLOCCITY": {
                                      "title": "FARTHESTLOCCITY",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "FARTHESTLOCCOUNTY": {
                                      "title": "FARTHESTLOCCOUNTY",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "FARTHESTLOCSTATE": {
                                      "title": "FARTHESTLOCSTATE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "FARTHESTLOC": {
                                      "title": "FARTHESTLOC",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "ISVEHICLEUPLOADED": {
                                      "title": "ISVEHICLEUPLOADED",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          true
                                      ]
                                  },
                                  "COMPDED": {
                                      "title": "COMPDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "COLLDED": {
                                      "title": "COLLDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "MPDED": {
                                      "title": "MPDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "HASPD": {
                                      "title": "HASPD",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Y"
                                      ]
                                  },
                                  "HASMP": {
                                      "title": "HASMP",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Y"
                                      ]
                                  },
                                  "TEMPLATENAME": {
                                      "title": "TEMPLATENAME",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Default Template"
                                      ]
                                  },
                                  "UWREFMSG": {
                                      "title": "UWREFMSG",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "962"
                                      ]
                                  },
                                  "GARAGELOC": {
                                      "title": "GARAGELOC",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "30084"
                                      ]
                                  },
                                  "HASRENTAL": {
                                      "title": "HASRENTAL",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "N"
                                      ]
                                  },
                                  "CSLLIMIT": {
                                      "title": "CSLLIMIT",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "1000"
                                      ]
                                  },
                                  "LIABDED": {
                                      "title": "LIABDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "UMTYPE": {
                                      "title": "UMTYPE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "R"
                                      ]
                                  },
                                  "UMDED": {
                                      "title": "UMDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "UMLIMIT": {
                                      "title": "UMLIMIT",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "75000"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                                      "SecondaryUse": "",
                                      "SecondaryUsePercent": "",
                                      "VehicleType": "CargoVan",
                                      "VIN": "2A4RR8DG6BR760259",
                                      "Year": "2000",
                                      "VehicleAge": "15",
                                      "Make": "AlfaRomeo",
                                      "Model": "Ecoride",
                                      "OwnedOrLeased": "Owned",
                                      "BusinessUseClass": "retail",
                                      "SizeClass": "lighttrucks",
                                      "GROSSCOMBWEIGHT": "MoreThan45000",
                                      "PrimaryGaragingLocation": "",
                                      "RADIUSCLASSTYPE": "local",
                                      "VEHPRICE": "20000",
                                      "PASSIVERESTR": false,
                                      "VEHYEAR": "15",
                                      "ANTILOCKBRAKES": false,
                                      "COSTTYPE": "ACV",
                                      "FARTHESTLOCCITY": "",
                                      "FARTHESTLOCCOUNTY": "",
                                      "FARTHESTLOCSTATE": "",
                                      "FARTHESTLOC": "",
                                      "ISVEHICLEUPLOADED": true,
                                      "COMPDED": "500",
                                      "COLLDED": "500",
                                      "MPDED": "500",
                                      "HASPD": "Y",
                                      "HASMP": "Y",
                                      "TEMPLATENAME": "Default Template",
                                      "UWREFMSG": "962",
                                      "GARAGELOC": "30084",
                                      "HASRENTAL": "N",
                                      "CSLLIMIT": "1000",
                                      "LIABDED": "500",
                                      "UMTYPE": "R",
                                      "UMDED": "500",
                                      "UMLIMIT": "75000"
                                  }
                              ]
                          }
                      },
                      "examples": [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Vehicle",
                              "UnitType": "Vehicle",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "CSL",
                                      "Type": "SUR",
                                      "Description": "Combined Single Limit",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "AdditionalParties": [
                                  {
                                      "Status": "Active",
                                      "Name": "bank of america",
                                      "ReferenceNumber": "132456",
                                      "IsPayee": true,
                                      "PartyType": "Mortgagee",
                                      "InterestType": "Mortgagee",
                                      "CreatedOn": "2018-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Communications": [
                                          {
                                              "Type": "PhNo",
                                              "SubType": "Primary",
                                              "Value": "4707070096",
                                              "Status": "Active"
                                          },
                                          {
                                              "Type": "Email",
                                              "SubType": "Primary",
                                              "Value": "nkadam@cogitate.us",
                                              "Status": "Active"
                                          }
                                      ]
                                  }
                              ],
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                                  "SecondaryUse": "",
                                  "SecondaryUsePercent": "",
                                  "VehicleType": "CargoVan",
                                  "VIN": "2A4RR8DG6BR760259",
                                  "Year": "2000",
                                  "VehicleAge": "15",
                                  "Make": "AlfaRomeo",
                                  "Model": "Ecoride",
                                  "OwnedOrLeased": "Owned",
                                  "BusinessUseClass": "retail",
                                  "SizeClass": "lighttrucks",
                                  "GROSSCOMBWEIGHT": "MoreThan45000",
                                  "PrimaryGaragingLocation": "",
                                  "RADIUSCLASSTYPE": "local",
                                  "VEHPRICE": "20000",
                                  "PASSIVERESTR": false,
                                  "VEHYEAR": "15",
                                  "ANTILOCKBRAKES": false,
                                  "COSTTYPE": "ACV",
                                  "FARTHESTLOCCITY": "",
                                  "FARTHESTLOCCOUNTY": "",
                                  "FARTHESTLOCSTATE": "",
                                  "FARTHESTLOC": "",
                                  "ISVEHICLEUPLOADED": true,
                                  "COMPDED": "500",
                                  "COLLDED": "500",
                                  "MPDED": "500",
                                  "HASPD": "Y",
                                  "HASMP": "Y",
                                  "TEMPLATENAME": "Default Template",
                                  "UWREFMSG": "962",
                                  "GARAGELOC": "30084",
                                  "HASRENTAL": "N",
                                  "CSLLIMIT": "1000",
                                  "LIABDED": "500",
                                  "UMTYPE": "R",
                                  "UMDED": "500",
                                  "UMLIMIT": "75000"
                              }
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Vehicle",
                              "UnitType": "Vehicle",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "CSL",
                                      "Type": "SUR",
                                      "Description": "Combined Single Limit",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "AdditionalParties": [
                                  {
                                      "Status": "Active",
                                      "Name": "bank of america",
                                      "ReferenceNumber": "132456",
                                      "IsPayee": true,
                                      "PartyType": "Mortgagee",
                                      "InterestType": "Mortgagee",
                                      "CreatedOn": "2018-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Communications": [
                                          {
                                              "Type": "PhNo",
                                              "SubType": "Primary",
                                              "Value": "4707070096",
                                              "Status": "Active"
                                          },
                                          {
                                              "Type": "Email",
                                              "SubType": "Primary",
                                              "Value": "nkadam@cogitate.us",
                                              "Status": "Active"
                                          }
                                      ]
                                  }
                              ],
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                                  "SecondaryUse": "",
                                  "SecondaryUsePercent": "",
                                  "VehicleType": "CargoVan",
                                  "VIN": "2A4RR8DG6BR760259",
                                  "Year": "2000",
                                  "VehicleAge": "15",
                                  "Make": "AlfaRomeo",
                                  "Model": "Ecoride",
                                  "OwnedOrLeased": "Owned",
                                  "BusinessUseClass": "retail",
                                  "SizeClass": "lighttrucks",
                                  "GROSSCOMBWEIGHT": "MoreThan45000",
                                  "PrimaryGaragingLocation": "",
                                  "RADIUSCLASSTYPE": "local",
                                  "VEHPRICE": "20000",
                                  "PASSIVERESTR": false,
                                  "VEHYEAR": "15",
                                  "ANTILOCKBRAKES": false,
                                  "COSTTYPE": "ACV",
                                  "FARTHESTLOCCITY": "",
                                  "FARTHESTLOCCOUNTY": "",
                                  "FARTHESTLOCSTATE": "",
                                  "FARTHESTLOC": "",
                                  "ISVEHICLEUPLOADED": true,
                                  "COMPDED": "500",
                                  "COLLDED": "500",
                                  "MPDED": "500",
                                  "HASPD": "Y",
                                  "HASMP": "Y",
                                  "TEMPLATENAME": "Default Template",
                                  "UWREFMSG": "962",
                                  "GARAGELOC": "30084",
                                  "HASRENTAL": "N",
                                  "CSLLIMIT": "1000",
                                  "LIABDED": "500",
                                  "UMTYPE": "R",
                                  "UMDED": "500",
                                  "UMLIMIT": "75000"
                              }
                          }
                      ]
                  ],
                  "uniqueItems": false
              },
              "Drivers": {
                  "title": "Drivers",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "UnitId",
                          "UnitNumber",
                          "Name",
                          "UnitType",
                          "Status",
                          "Coverages",
                          "PremiumFactors",
                          "Premium",
                          "Audit",
                          "RiskAttributes"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "UnitId": {
                              "title": "UnitId",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  1
                              ]
                          },
                          "UnitNumber": {
                              "title": "UnitNumber",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "1"
                              ]
                          },
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Driver"
                              ]
                          },
                          "UnitType": {
                              "title": "UnitType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Driver"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Coverages": {
                              "title": "Coverages",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Description",
                                      "Type",
                                      "SettlementType",
                                      "Value",
                                      "Limit",
                                      "LimitAmount",
                                      "Deductible",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Status"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Coverage"
                                          ]
                                      },
                                      "SettlementType": {
                                          "title": "SettlementType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "ACV"
                                          ]
                                      },
                                      "Value": {
                                          "title": "Value",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "5"
                                          ]
                                      },
                                      "Limit": {
                                          "title": "Limit",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "LimitAmount": {
                                          "title": "LimitAmount",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "PremiumFactors": {
                              "title": "PremiumFactors",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Type",
                                      "Description",
                                      "Rate",
                                      "Premium",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Deductible",
                                      "EffectivePremium",
                                      "PremiumDifference",
                                      "Status",
                                      "Factor"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "PDCollNZ"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "SUR"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Physical Damage Rating - Collision(Non-Zone)"
                                          ]
                                      },
                                      "Rate": {
                                          "title": "Rate",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "Premium": {
                                          "title": "Premium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "EffectivePremium": {
                                          "title": "EffectivePremium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "PremiumDifference": {
                                          "title": "PremiumDifference",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      },
                                      "Factor": {
                                          "title": "Factor",
                                          "description": " ",
                                          "type": "object",
                                          "default": {},
                                          "required": [
                                              "Name",
                                              "Type",
                                              "Description",
                                              "Rate",
                                              "Limit",
                                              "LimitAmount",
                                              "Deductible",
                                              "Premium",
                                              "EffectivePremium",
                                              "IsApplicable",
                                              "IsSelected",
                                              "IsMandatory"
                                          ],
                                          "additionalProperties": true,
                                          "properties": {
                                              "Name": {
                                                  "title": "Name",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "PDCollNZ"
                                                  ]
                                              },
                                              "Type": {
                                                  "title": "Type",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "SUR"
                                                  ]
                                              },
                                              "Description": {
                                                  "title": "Description",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Physical Damage Rating - Collision(Non-Zone)"
                                                  ]
                                              },
                                              "Rate": {
                                                  "title": "Rate",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      0
                                                  ]
                                              },
                                              "Limit": {
                                                  "title": "Limit",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "LimitAmount": {
                                                  "title": "LimitAmount",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "Deductible": {
                                                  "title": "Deductible",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      500
                                                  ]
                                              },
                                              "Premium": {
                                                  "title": "Premium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "EffectivePremium": {
                                                  "title": "EffectivePremium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "IsApplicable": {
                                                  "title": "IsApplicable",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsSelected": {
                                                  "title": "IsSelected",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsMandatory": {
                                                  "title": "IsMandatory",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              }
                                          },
                                          "examples": [
                                              {
                                                  "Name": "PDCollNZ",
                                                  "Type": "SUR",
                                                  "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                                  "Rate": 0,
                                                  "Limit": 10000,
                                                  "LimitAmount": 10000,
                                                  "Deductible": 500,
                                                  "Premium": 119,
                                                  "EffectivePremium": 119,
                                                  "IsApplicable": true,
                                                  "IsSelected": true,
                                                  "IsMandatory": true
                                              }
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "Premium": {
                              "title": "Premium",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "BasicPremium",
                                  "Surcharge",
                                  "Discount",
                                  "MinPremium",
                                  "EffectivePremium",
                                  "AnnualPremium",
                                  "EffectivePremiumWithFeesAndTaxes",
                                  "AnnualPremiumWithFeesAndTaxes"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "BasicPremium": {
                                      "title": "BasicPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "Surcharge": {
                                      "title": "Surcharge",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "Discount": {
                                      "title": "Discount",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "MinPremium": {
                                      "title": "MinPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "EffectivePremium": {
                                      "title": "EffectivePremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "AnnualPremium": {
                                      "title": "AnnualPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "EffectivePremiumWithFeesAndTaxes": {
                                      "title": "EffectivePremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  },
                                  "AnnualPremiumWithFeesAndTaxes": {
                                      "title": "AnnualPremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "BasicPremium": 12005,
                                      "Surcharge": 0,
                                      "Discount": 0,
                                      "MinPremium": 0,
                                      "EffectivePremium": 12005,
                                      "AnnualPremium": 12005,
                                      "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                      "AnnualPremiumWithFeesAndTaxes": 12405.16
                                  }
                              ]
                          },
                          "Audit": {
                              "title": "Audit",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "CreatedBy",
                                  "CreatedOn",
                                  "DeletedOn",
                                  "LastUpdatedBy",
                                  "LastUpdatedOn"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "CreatedBy": {
                                      "title": "CreatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "CreatedOn": {
                                      "title": "CreatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  },
                                  "DeletedOn": {
                                      "title": "DeletedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-11-30"
                                      ]
                                  },
                                  "LastUpdatedBy": {
                                      "title": "LastUpdatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "LastUpdatedOn": {
                                      "title": "LastUpdatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "CreatedBy": "nkadam",
                                      "CreatedOn": "2022-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "LastUpdatedBy": "nkadam",
                                      "LastUpdatedOn": "2022-08-18"
                                  }
                              ]
                          },
                          "RiskAttributes": {
                              "title": "RiskAttributes",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "Type",
                                  "FirstName",
                                  "MiddleName",
                                  "LastName",
                                  "Suffix",
                                  "DOB",
                                  "Age",
                                  "LicenseNumber",
                                  "Violations",
                                  "IsUSCitizen",
                                  "Occupation",
                                  "FilingStatusCode",
                                  "Fillings",
                                  "FilingCode",
                                  "LicenseDate",
                                  "State",
                                  "HadTrainingCourse",
                                  "IsMilitary",
                                  "MilitaryRank",
                                  "HadDUIDWI",
                                  "DriverCourseCompletedDate",
                                  "CanInsureOperate",
                                  "LicenseStatus",
                                  "IsGoodStudentDiscountApplicable",
                                  "MaritalStatus",
                                  "Gender",
                                  "Violation",
                                  "RelationToApplicant"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "Type": {
                                      "title": "Type",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Principal"
                                      ]
                                  },
                                  "FirstName": {
                                      "title": "FirstName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Diane"
                                      ]
                                  },
                                  "MiddleName": {
                                      "title": "MiddleName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "LastName": {
                                      "title": "LastName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Boyer"
                                      ]
                                  },
                                  "Suffix": {
                                      "title": "Suffix",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "DOB": {
                                      "title": "DOB",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "1962-10-24"
                                      ]
                                  },
                                  "Age": {
                                      "title": "Age",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          59
                                      ]
                                  },
                                  "LicenseNumber": {
                                      "title": "LicenseNumber",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "Violations": {
                                      "title": "Violations",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "IsUSCitizen": {
                                      "title": "IsUSCitizen",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          true
                                      ]
                                  },
                                  "Occupation": {
                                      "title": "Occupation",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "UN"
                                      ]
                                  },
                                  "FilingStatusCode": {
                                      "title": "FilingStatusCode",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "Fillings": {
                                      "title": "Fillings",
                                      "description": " ",
                                      "type": "object",
                                      "default": {},
                                      "required": [
                                          "Fillings",
                                          "Date",
                                          "Reason",
                                          "FilingCd",
                                          "FilingStatusCd"
                                      ],
                                      "additionalProperties": true,
                                      "properties": {
                                          "Fillings": {
                                              "title": "Fillings",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "No"
                                              ]
                                          },
                                          "Date": {
                                              "title": "Date",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "Reason": {
                                              "title": "Reason",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "FilingCd": {
                                              "title": "FilingCd",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "FilingStatusCd": {
                                              "title": "FilingStatusCd",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          }
                                      },
                                      "examples": [
                                          {
                                              "Fillings": "No",
                                              "Date": "",
                                              "Reason": "",
                                              "FilingCd": "",
                                              "FilingStatusCd": ""
                                          }
                                      ]
                                  },
                                  "FilingCode": {
                                      "title": "FilingCode",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "LicenseDate": {
                                      "title": "LicenseDate",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "1978-11-20"
                                      ]
                                  },
                                  "State": {
                                      "title": "State",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "GA"
                                      ]
                                  },
                                  "HadTrainingCourse": {
                                      "title": "HadTrainingCourse",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "IsMilitary": {
                                      "title": "IsMilitary",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "MilitaryRank": {
                                      "title": "MilitaryRank",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "HadDUIDWI": {
                                      "title": "HadDUIDWI",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "DriverCourseCompletedDate": {
                                      "title": "DriverCourseCompletedDate",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "CanInsureOperate": {
                                      "title": "CanInsureOperate",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "LicenseStatus": {
                                      "title": "LicenseStatus",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Valid"
                                      ]
                                  },
                                  "IsGoodStudentDiscountApplicable": {
                                      "title": "IsGoodStudentDiscountApplicable",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "MaritalStatus": {
                                      "title": "MaritalStatus",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "S"
                                      ]
                                  },
                                  "Gender": {
                                      "title": "Gender",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "F"
                                      ]
                                  },
                                  "Violation": {
                                      "title": "Violation",
                                      "description": " ",
                                      "type": "array",
                                      "default": [],
                                      "additionalItems": true,
                                      "items": {},
                                      "examples": [
                                          []
                                      ],
                                      "uniqueItems": false
                                  },
                                  "RelationToApplicant": {
                                      "title": "RelationToApplicant",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Insured"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "Type": "Principal",
                                      "FirstName": "Diane",
                                      "MiddleName": "",
                                      "LastName": "Boyer",
                                      "Suffix": "",
                                      "DOB": "1962-10-24",
                                      "Age": 59,
                                      "LicenseNumber": "",
                                      "Violations": 0,
                                      "IsUSCitizen": true,
                                      "Occupation": "UN",
                                      "FilingStatusCode": "",
                                      "Fillings": {
                                          "Fillings": "No",
                                          "Date": "",
                                          "Reason": "",
                                          "FilingCd": "",
                                          "FilingStatusCd": ""
                                      },
                                      "FilingCode": "",
                                      "LicenseDate": "1978-11-20",
                                      "State": "GA",
                                      "HadTrainingCourse": false,
                                      "IsMilitary": false,
                                      "MilitaryRank": "",
                                      "HadDUIDWI": false,
                                      "DriverCourseCompletedDate": "",
                                      "CanInsureOperate": "",
                                      "LicenseStatus": "Valid",
                                      "IsGoodStudentDiscountApplicable": false,
                                      "MaritalStatus": "S",
                                      "Gender": "F",
                                      "Violation": [],
                                      "RelationToApplicant": "Insured"
                                  }
                              ]
                          }
                      },
                      "examples": [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Driver",
                              "UnitType": "Driver",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "Type": "Principal",
                                  "FirstName": "Diane",
                                  "MiddleName": "",
                                  "LastName": "Boyer",
                                  "Suffix": "",
                                  "DOB": "1962-10-24",
                                  "Age": 59,
                                  "LicenseNumber": "",
                                  "Violations": 0,
                                  "IsUSCitizen": true,
                                  "Occupation": "UN",
                                  "FilingStatusCode": "",
                                  "Fillings": {
                                      "Fillings": "No",
                                      "Date": "",
                                      "Reason": "",
                                      "FilingCd": "",
                                      "FilingStatusCd": ""
                                  },
                                  "FilingCode": "",
                                  "LicenseDate": "1978-11-20",
                                  "State": "GA",
                                  "HadTrainingCourse": false,
                                  "IsMilitary": false,
                                  "MilitaryRank": "",
                                  "HadDUIDWI": false,
                                  "DriverCourseCompletedDate": "",
                                  "CanInsureOperate": "",
                                  "LicenseStatus": "Valid",
                                  "IsGoodStudentDiscountApplicable": false,
                                  "MaritalStatus": "S",
                                  "Gender": "F",
                                  "Violation": [],
                                  "RelationToApplicant": "Insured"
                              }
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Driver",
                              "UnitType": "Driver",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "Type": "Principal",
                                  "FirstName": "Diane",
                                  "MiddleName": "",
                                  "LastName": "Boyer",
                                  "Suffix": "",
                                  "DOB": "1962-10-24",
                                  "Age": 59,
                                  "LicenseNumber": "",
                                  "Violations": 0,
                                  "IsUSCitizen": true,
                                  "Occupation": "UN",
                                  "FilingStatusCode": "",
                                  "Fillings": {
                                      "Fillings": "No",
                                      "Date": "",
                                      "Reason": "",
                                      "FilingCd": "",
                                      "FilingStatusCd": ""
                                  },
                                  "FilingCode": "",
                                  "LicenseDate": "1978-11-20",
                                  "State": "GA",
                                  "HadTrainingCourse": false,
                                  "IsMilitary": false,
                                  "MilitaryRank": "",
                                  "HadDUIDWI": false,
                                  "DriverCourseCompletedDate": "",
                                  "CanInsureOperate": "",
                                  "LicenseStatus": "Valid",
                                  "IsGoodStudentDiscountApplicable": false,
                                  "MaritalStatus": "S",
                                  "Gender": "F",
                                  "Violation": [],
                                  "RelationToApplicant": "Insured"
                              }
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Vehicles": [
                      {
                          "UnitId": 1,
                          "UnitNumber": "1",
                          "Name": "Vehicle",
                          "UnitType": "Vehicle",
                          "Status": "Active",
                          "Coverages": [
                              {
                                  "Name": "Combined Single Limit",
                                  "Description": "Combined Single Limit",
                                  "Type": "Coverage",
                                  "SettlementType": "ACV",
                                  "Value": "5",
                                  "Limit": 10000,
                                  "LimitAmount": 10000,
                                  "Deductible": 500,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Status": "Active"
                              }
                          ],
                          "PremiumFactors": [
                              {
                                  "Name": "CSL",
                                  "Type": "SUR",
                                  "Description": "Combined Single Limit",
                                  "Rate": 0,
                                  "Premium": 0,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Deductible": 500,
                                  "EffectivePremium": 119,
                                  "PremiumDifference": 119,
                                  "Status": "Active",
                                  "Factor": {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "Premium": 119,
                                      "EffectivePremium": 119,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true
                                  }
                              }
                          ],
                          "Premium": {
                              "BasicPremium": 12005,
                              "Surcharge": 0,
                              "Discount": 0,
                              "MinPremium": 0,
                              "EffectivePremium": 12005,
                              "AnnualPremium": 12005,
                              "EffectivePremiumWithFeesAndTaxes": 12405.16,
                              "AnnualPremiumWithFeesAndTaxes": 12405.16
                          },
                          "AdditionalParties": [
                              {
                                  "Status": "Active",
                                  "Name": "bank of america",
                                  "ReferenceNumber": "132456",
                                  "IsPayee": true,
                                  "PartyType": "Mortgagee",
                                  "InterestType": "Mortgagee",
                                  "CreatedOn": "2018-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "Address": {
                                      "Number": 1,
                                      "AddressType": "Primary",
                                      "Description": "Mailing Address",
                                      "AddressLine1": "2141 Lake Park DR SE",
                                      "AddressLine2": "Apt I",
                                      "AptSuite": "1000",
                                      "City": "Forest Park",
                                      "County": "US",
                                      "CountyCode": "COBB",
                                      "State": "GA",
                                      "PoBox": "30080",
                                      "Postalcode": "30080",
                                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                      "AdministrationArea1": "",
                                      "AdministrationArea2": "",
                                      "Locality": "Atlanta",
                                      "Lat": "45.6654",
                                      "Long": "45.65646",
                                      "Name": "Cobb Galleria Pkwy",
                                      "Premise": "Fron",
                                      "Status": "Active",
                                      "Territory": "",
                                      "Business": "Cogitate Technology Solution",
                                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                  },
                                  "Communications": [
                                      {
                                          "Type": "PhNo",
                                          "SubType": "Primary",
                                          "Value": "4707070096",
                                          "Status": "Active"
                                      },
                                      {
                                          "Type": "Email",
                                          "SubType": "Primary",
                                          "Value": "nkadam@cogitate.us",
                                          "Status": "Active"
                                      }
                                  ]
                              }
                          ],
                          "Audit": {
                              "CreatedBy": "nkadam",
                              "CreatedOn": "2022-08-18",
                              "DeletedOn": "2022-11-30",
                              "LastUpdatedBy": "nkadam",
                              "LastUpdatedOn": "2022-08-18"
                          },
                          "RiskAttributes": {
                              "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                              "SecondaryUse": "",
                              "SecondaryUsePercent": "",
                              "VehicleType": "CargoVan",
                              "VIN": "2A4RR8DG6BR760259",
                              "Year": "2000",
                              "VehicleAge": "15",
                              "Make": "AlfaRomeo",
                              "Model": "Ecoride",
                              "OwnedOrLeased": "Owned",
                              "BusinessUseClass": "retail",
                              "SizeClass": "lighttrucks",
                              "GROSSCOMBWEIGHT": "MoreThan45000",
                              "PrimaryGaragingLocation": "",
                              "RADIUSCLASSTYPE": "local",
                              "VEHPRICE": "20000",
                              "PASSIVERESTR": false,
                              "VEHYEAR": "15",
                              "ANTILOCKBRAKES": false,
                              "COSTTYPE": "ACV",
                              "FARTHESTLOCCITY": "",
                              "FARTHESTLOCCOUNTY": "",
                              "FARTHESTLOCSTATE": "",
                              "FARTHESTLOC": "",
                              "ISVEHICLEUPLOADED": true,
                              "COMPDED": "500",
                              "COLLDED": "500",
                              "MPDED": "500",
                              "HASPD": "Y",
                              "HASMP": "Y",
                              "TEMPLATENAME": "Default Template",
                              "UWREFMSG": "962",
                              "GARAGELOC": "30084",
                              "HASRENTAL": "N",
                              "CSLLIMIT": "1000",
                              "LIABDED": "500",
                              "UMTYPE": "R",
                              "UMDED": "500",
                              "UMLIMIT": "75000"
                          }
                      }
                  ],
                  "Drivers": [
                      {
                          "UnitId": 1,
                          "UnitNumber": "1",
                          "Name": "Driver",
                          "UnitType": "Driver",
                          "Status": "Active",
                          "Coverages": [
                              {
                                  "Name": "Combined Single Limit",
                                  "Description": "Combined Single Limit",
                                  "Type": "Coverage",
                                  "SettlementType": "ACV",
                                  "Value": "5",
                                  "Limit": 10000,
                                  "LimitAmount": 10000,
                                  "Deductible": 500,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Status": "Active"
                              }
                          ],
                          "PremiumFactors": [
                              {
                                  "Name": "PDCollNZ",
                                  "Type": "SUR",
                                  "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                  "Rate": 0,
                                  "Premium": 0,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Deductible": 500,
                                  "EffectivePremium": 119,
                                  "PremiumDifference": 119,
                                  "Status": "Active",
                                  "Factor": {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "Premium": 119,
                                      "EffectivePremium": 119,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true
                                  }
                              }
                          ],
                          "Premium": {
                              "BasicPremium": 12005,
                              "Surcharge": 0,
                              "Discount": 0,
                              "MinPremium": 0,
                              "EffectivePremium": 12005,
                              "AnnualPremium": 12005,
                              "EffectivePremiumWithFeesAndTaxes": 12405.16,
                              "AnnualPremiumWithFeesAndTaxes": 12405.16
                          },
                          "Audit": {
                              "CreatedBy": "nkadam",
                              "CreatedOn": "2022-08-18",
                              "DeletedOn": "2022-11-30",
                              "LastUpdatedBy": "nkadam",
                              "LastUpdatedOn": "2022-08-18"
                          },
                          "RiskAttributes": {
                              "Type": "Principal",
                              "FirstName": "Diane",
                              "MiddleName": "",
                              "LastName": "Boyer",
                              "Suffix": "",
                              "DOB": "1962-10-24",
                              "Age": 59,
                              "LicenseNumber": "",
                              "Violations": 0,
                              "IsUSCitizen": true,
                              "Occupation": "UN",
                              "FilingStatusCode": "",
                              "Fillings": {
                                  "Fillings": "No",
                                  "Date": "",
                                  "Reason": "",
                                  "FilingCd": "",
                                  "FilingStatusCd": ""
                              },
                              "FilingCode": "",
                              "LicenseDate": "1978-11-20",
                              "State": "GA",
                              "HadTrainingCourse": false,
                              "IsMilitary": false,
                              "MilitaryRank": "",
                              "HadDUIDWI": false,
                              "DriverCourseCompletedDate": "",
                              "CanInsureOperate": "",
                              "LicenseStatus": "Valid",
                              "IsGoodStudentDiscountApplicable": false,
                              "MaritalStatus": "S",
                              "Gender": "F",
                              "Violation": [],
                              "RelationToApplicant": "Insured"
                          }
                      }
                  ]
              }
          ]
      },
      "Rules": {
          "title": "Rules",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Action",
              "MatchingRules"
          ],
          "additionalProperties": true,
          "properties": {
              "Action": {
                  "title": "Action",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "ReferToUW"
                  ]
              },
              "MatchingRules": {
                  "title": "MatchingRules",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Type",
                          "Description",
                          "Isfulfilled",
                          "Status",
                          "Remark",
                          "Reason"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "ReferToUW"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Business structure is a Trust"
                              ]
                          },
                          "Isfulfilled": {
                              "title": "Isfulfilled",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Remark": {
                              "title": "Remark",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "Reason": {
                              "title": "Reason",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          }
                      },
                      "examples": [{
                          "Type": "ReferToUW",
                          "Description": "Business structure is a Trust",
                          "Isfulfilled": true,
                          "Status": "Active",
                          "Remark": "",
                          "Reason": ""
                      }]
                  },
                  "examples": [
                      [{
                          "Type": "ReferToUW",
                          "Description": "Business structure is a Trust",
                          "Isfulfilled": true,
                          "Status": "Active",
                          "Remark": "",
                          "Reason": ""
                      }]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [{
              "Action": "ReferToUW",
              "MatchingRules": [{
                  "Type": "ReferToUW",
                  "Description": "Business structure is a Trust",
                  "Isfulfilled": true,
                  "Status": "Active",
                  "Remark": "",
                  "Reason": ""
              }]
          }]
      },
      "PreviousPolicies": {
          "title": "PreviousPolicies",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "IsPreviousPolicy",
              "PreviousPolicyNumber",
              "OtherCoverages",
              "IsPreviousClaims",
              "NoOfClaims",
              "TotalAmountClaimed"
          ],
          "additionalProperties": true,
          "properties": {
              "IsPreviousPolicy": {
                  "title": "IsPreviousPolicy",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              },
              "PreviousPolicyNumber": {
                  "title": "PreviousPolicyNumber",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "BCIH221023"
                  ]
              },
              "OtherCoverages": {
                  "title": "OtherCoverages",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "NA"
                  ]
              },
              "IsPreviousClaims": {
                  "title": "IsPreviousClaims",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              },
              "NoOfClaims": {
                  "title": "NoOfClaims",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "TotalAmountClaimed": {
                  "title": "TotalAmountClaimed",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              }
          },
          "examples": [{
              "IsPreviousPolicy": true,
              "PreviousPolicyNumber": "BCIH221023",
              "OtherCoverages": "NA",
              "IsPreviousClaims": true,
              "NoOfClaims": 0,
              "TotalAmountClaimed": 0
          }]
      },
      "Underwriting": {
          "title": "Underwriting",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "HaveAutoInsurance",
              "HaveSR22Fillings",
              "DriverLicenseSuspended",
              "DriverHaveTicketViolation",
              "HowLongWithCurrentInsuranceCompany",
              "AnyFaultClaim",
              "IsCarOlder"
          ],
          "additionalProperties": true,
          "properties": {
              "HaveAutoInsurance": {
                  "title": "HaveAutoInsurance",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              },
              "HaveSR22Fillings": {
                  "title": "HaveSR22Fillings",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "DriverLicenseSuspended": {
                  "title": "DriverLicenseSuspended",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "DriverHaveTicketViolation": {
                  "title": "DriverHaveTicketViolation",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "HowLongWithCurrentInsuranceCompany": {
                  "title": "HowLongWithCurrentInsuranceCompany",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Value",
                      "ValueType"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Value": {
                          "title": "Value",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2"
                          ]
                      },
                      "ValueType": {
                          "title": "ValueType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "years"
                          ]
                      }
                  },
                  "examples": [{
                      "Value": "2",
                      "ValueType": "years"
                  }]
              },
              "AnyFaultClaim": {
                  "title": "AnyFaultClaim",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "No"
                  ]
              },
              "IsCarOlder": {
                  "title": "IsCarOlder",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              }
          },
          "examples": [{
              "HaveAutoInsurance": true,
              "HaveSR22Fillings": false,
              "DriverLicenseSuspended": false,
              "DriverHaveTicketViolation": false,
              "HowLongWithCurrentInsuranceCompany": {
                  "Value": "2",
                  "ValueType": "years"
              },
              "AnyFaultClaim": "No",
              "IsCarOlder": false
          }]
      },
      "NonFunctional": {
          "title": "NonFunctional",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "LastSubmittedPage",
              "Milestones"
          ],
          "additionalProperties": true,
          "properties": {
              "LastSubmittedPage": {
                  "title": "LastSubmittedPage",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "/Commercial/Auto/Quote/BusinessInfo"
                  ]
              },
              "Milestones": {
                  "title": "Milestones",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          1,
                          2,
                          4
                      ]
                  },
                  "examples": [
                      [0, 1,
                          2,
                          4
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [{
              "LastSubmittedPage": "/Commercial/Auto/Quote/BusinessInfo",
              "Milestones": [
                  0,
                  1,
                  2,
                  4
              ]
          }]
      }
  },
  "examples": [
      {
          "id": "cd27210f-81c9-4d6e-a7d5-e0cd11431006",
          "AccountId": "Agent",
          "QuoteNumber": "ENGS1CA220009",
          "IsPolicyBind": false,
          "IsRenewed": false,
          "PolicyNumber": "SGIH3GA223885",
          "PolicyTerm": {
              "Value": 12,
              "ValueType": "Months"
          },
          "EffectiveDate": "2022-08-18",
          "ExpirationDate": "2023-08-18",
          "BindDate": "2022-08-18",
          "QuoteDate": "2022-08-18",
          "QuoteExpDate": "2022-08-18",
          "PolicyStatus": "Quote",
          "CurrentVersion": "1.0",
          "CurrentVersionEffectiveFrom": "2022-08-18",
          "RenewalTerm": 0,
          "Attributes": {
              "AppSource": "SalesForce",
              "Carrier": "ENGS",
              "Coverholder": "IH",
              "Lob": "CA",
              "State": "GA",
              "Product": "ENGS1CA",
              "RaterVersion": "2.0.0.0",
              "RenewalConfigurations": {
                  "BeforeForAgent": {
                      "Value": 30,
                      "ValueType": "Days"
                  },
                  "AfterForAgent": {
                      "Value": 30,
                      "ValueType": "Days"
                  },
                  "BeforeForUnderwriter": {
                      "Value": 60,
                      "ValueType": "Days"
                  },
                  "AfterForUnderwriter": {
                      "Value": 60,
                      "ValueType": "Days"
                  }
              },
              "QuoteValidity": {
                  "Value": 60,
                  "ValueType": "Days"
              },
              "IsTestPolicy": true
          }
      }
  ]
}
```


---
id: PolicyModelSchema
title: Policy Model Schema
---
```json
{
  "$schema": "https://json-schema.org/draft/2019-09/schema",
  "$id": "http://example.com/example.json",
  "title": "Policy",
  "description": "The root schema is the schema that comprises the entire JSON document.",
  "type": "object",
  "default": {},
  "required": [
      "id",
      "AccountId",
      "QuoteNumber",
      "IsPolicyBind",
      "IsRenewed",
      "PolicyNumber",
      "PolicyTerm",
      "EffectiveDate",
      "ExpirationDate",
      "BindDate",
      "QuoteDate",
      "QuoteExpDate",
      "PolicyStatus",
      "CurrentVersion",
      "CurrentVersionEffectiveFrom",
      "RenewalTerm",
      "Attributes"
  ],
  "additionalProperties": true,
  "properties": {
      "id": {
          "title": "Id",
          "description": "guid, unique within policy container",
          "type": "string",
          "default": "",
          "examples": [
              "cd27210f-81c9-4d6e-a7d5-e0cd11431006"
          ]
      },
      "AccountId": {
          "title": "Account Id",
          "description": "Account Id specifies the role of the user eg. Agent/UW",
          "type": "string",
          "default": "Agent",
          "examples": [
              "Agent"
          ]
      },
      "QuoteNumber": {
          "title": "Quote Number",
          "description": "QuoteNumber is unique identifier to across the transactions of given policy, it will remain same in Version container",
          "type": "string",
          "default": "",
          "examples": [
              "ENGS1CA220009"
          ]
      },
      "IsPolicyBind": {
          "title": "Is Policy Bind",
          "description": "flag denotes the the submission is bound or not, set true when update status PolicyInForceBind",
          "type": "boolean",
          "default": null,
          "examples": [
              false
          ]
      },
      "IsRenewed": {
          "title": "IsRenewed",
          "description": "flag is used to identify the renewal policy set true when we update status Renewed",
          "type": "boolean",
          "default": false,
          "examples": [
              false
          ]
      },
      "PolicyNumber": {
          "title": "PolicyNumber",
          "description": "Policy number is also unique identifier of a Policy but it is generated when we bind the NB Policy and for renewal at the time of renewal offer generation ",
          "type": "string",
          "default": "",
          "examples": [
              "SGIH3GA223885"
          ]
      },
      "PolicyTerm": {
          "title": "PolicyTerm",
          "description": "denotes the term of the policy, value may contain number of days, month or years and value type will be [Days, Months, Year]",
          "type": "object",
          "default": {},
          "required": [
              "Value",
              "ValueType"
          ],
          "additionalProperties": true,
          "properties": {
              "Value": {
                  "title": "Value",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      12
                  ]
              },
              "ValueType": {
                  "title": "ValueType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Months"
                  ]
              }
          },
          "examples": [
              {
                  "Value": 12,
                  "ValueType": "Months"
              }
          ]
      },
      "EffectiveDate": {
          "title": "EffectiveDate",
          "description": "Date in which selected record is effective or proposed effective.",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "ExpirationDate": {
          "title": "ExpirationDate",
          "description": "Date in which selected record expires or is proposed to expire.",
          "type": "string",
          "default": "",
          "examples": [
              "2023-08-18"
          ]
      },
      "BindDate": {
          "title": "BindDate",
          "description": "Date in which submission was first bound.",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "QuoteDate": {
          "title": "QuoteDate",
          "description": "Date in which submission or version was quoted.",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "QuoteExpDate": {
          "title": "QuoteExpDate",
          "description": "Date in which offered quote will expire and will be re-rated the new version. ",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "PolicyStatus": {
          "title": "PolicyStatus",
          "description": "Indicates the status that the submission is in.  ",
          "type": "string",
          "default": "",
          "examples": [
            {
              "QuoteIndication": "Quote Indication",
              "Submission": "Submission",
              "SubmissionDeclinedbyUW": "Submission Declined by UW",
              "ReferralAwaitingUWReview": "Referral - Awaiting UW Review",
              "QuoteOffered": "Quote Offered",
              "UWQuoteDeclined": "UW - Quote Declined",
              "QuoteExpired": "Quote Expired",
              "RetailerQuoteDeclined": "Retailer - Quote Declined",
              "BindRequestAwaitingUWApproval": "Bind Request - Awaiting UW Approval",
              "BindRequestDeclinedbyUW": "Bind Request Declined by UW",
              "BindRequestonHold": "Bind Request on Hold",
              "PolicyInForceBind": "Policy In Force-Bind",
              "PolicyInForceEndorsementRequestAwaitingUWApproval": "Policy In Force - Endorsement Request Awaiting UW Approval",
              "PolicyInForceEndorsed": "Policy In Force-Endorsed",
              "PolicyInForceEndorsementRequestOnHold": "Policy In Force - Endorsement Request On Hold",
              "PolicyInForceCancellationRequestPendingApproval": "Policy In Force - Cancellation Request Pending Approval",
              "PolicyCancelled": "Policy Cancelled",
              "PolicyInForceCancellationRequestOnHold": "Policy In Force - Cancellation Request On Hold",
              "PolicyCancelledReinstatementRequestPendingUWApproval": "Policy Cancelled - Reinstatement Request Pending UW Approval",
              "PolicyCancelledReinstatementRequestOnHold": "Policy Cancelled - Reinstatement Request On Hold",
              "PolicyInForceReInstated": "Policy In Force-ReInstated",
              "WaitingForRevisedApproval": "Waiting For Revised Approval",
              "BindSignaturePending": "Bind Signature Pending",
              "BindSignatureCompleted": "Bind Signature Completed",
              "PolicyInForceEndorsementSignaturePending": "Policy In Force - Endorsement Signature Pending",
              "PolicyInForceEndorsementSignatureCompleted": "Policy In Force - Endorsement Signature Completed",
              "PolicyInForceCancellationSignaturePending": "Policy In Force - Cancellation Signature Pending",
              "PolicyInForceCancellationSignatureCompleted": "Policy In Force - Cancellation Signature Completed",
              "RenewalSubmission": "Renewal Submission",
              "RenewalOfferGenerated": "Renewal Offer Generated",
              "RetailerRenewalOfferDeclined": "Retailer - Renewal Offer Declined",
              "DeclineRenewalOffer": "Decline Renewal Offer",
              "RenewalRequestSignaturePending": "Renewal Request - Signature Pending",
              "RenewalRequestSignatureCompleted": "Renewal Request - Signature Completed",
              "RenewalQuoteOffered": "Renewal Quote Offered",
              "RenewalAwaitingUWReview": "Renewal Awaiting UW Review",
              "Policyexpired": "Policy expired",
              "Waitingforrenewal": "Waiting for renewal",
              "Renewed": "Renewed",
              "Renewalonhold": "Renewal on hold",
              "RenewalDeclined": "Renewal Declined",
              "Renewalcancelled": "Renewal cancelled",
              "RenewalBindRequestAwaitingUWApproval": "Renewal Bind Request - Awaiting UW Approval"
            }
          ]
      },
      "CurrentVersion": {
          "title": "CurrentVersion",
          "description": " ",
          "type": "string",
          "default": "",
          "examples": [
              "1.0"
          ]
      },
      "CurrentVersionEffectiveFrom": {
          "title": "CurrentVersionEffectiveFrom",
          "description": " ",
          "type": "string",
          "default": "",
          "examples": [
              "2022-08-18"
          ]
      },
      "RenewalTerm": {
          "title": "RenewalTerm",
          "description": "Number of times record renewed ",
          "type": "number",
          "default": 0,
          "examples": [
              0
          ]
      },
      "RenewalQuoteID": {
        "title": "RenewalQuoteID",
        "description": "If policy has been renewed, then the old policy will hold the quote id of the new policy. ",
        "type": "number",
        "default": 0,
        "examples": [
            0
        ]
    },
  
      "Attributes": {
          "title": "Attributes",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "AppSource",
              "Carrier",
              "Coverholder",
              "Lob",
              "State",
              "Product",
              "RaterVersion",
              "RenewalConfigurations",
              "QuoteValidity",
              "IsTestPolicy"
          ],
          "additionalProperties": true,
          "properties": {
              "AppSource": {
                  "title": "AppSource",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "SalesForce"
                  ]
              },
              "Carrier": {
                  "title": "Carrier",
                  "description": "Holds the carrier code, refences to carrier ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "ENGS"
                  ]
              },
              "Coverholder": {
                  "title": "Coverholder",
                  "description": "Holds the Coverholder code, refences to Coverholder ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "IH"
                  ]
              },
              "Lob": {
                  "title": "Lob",
                  "description": "Indicates the Line of business ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "CA", "HO","PA"
                  ]
              },
              "State": {
                  "title": "State",
                  "description": " ",
                  "type": "string",
                  "default": "State abbreviation of the filing tax state.",
                  "examples": [
                      "GA"
                  ]
              },
              "Product": {
                  "title": "Product",
                  "description": "Code of the product -- a combination of the carrier, coverholder, lob and risk state",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "ENGS1CA"
                  ]
              },
              "RaterVersion": {
                  "title": "RaterVersion",
                  "description": " ",
                  "type": "string",
                  "default": "Indicates the rater version, rater version is freezed quote is offered",
                  "examples": [
                      "2.0.0.0"
                  ]
              },
              "RenewalConfigurations": {
                  "title": "RenewalConfigurations",
                  "description": "Hold the information about renewal process ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "BeforeForAgent",
                      "AfterForAgent",
                      "BeforeForUnderwriter",
                      "AfterForUnderwriter"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "BeforeForAgent": {
                          "title": "BeforeForAgent",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      30
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 30,
                                  "ValueType": "Days"
                              }
                          ]
                      },
                      "AfterForAgent": {
                          "title": "AfterForAgent",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      30
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 30,
                                  "ValueType": "Days"
                              }
                          ]
                      },
                      "BeforeForUnderwriter": {
                          "title": "BeforeForUnderwriter",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      60
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 60,
                                  "ValueType": "Days"
                              }
                          ]
                      },
                      "AfterForUnderwriter": {
                          "title": "AfterForUnderwriter",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "Value",
                              "ValueType"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "number",
                                  "default": 0,
                                  "examples": [
                                      60
                                  ]
                              },
                              "ValueType": {
                                  "title": "ValueType",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "Days"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Value": 60,
                                  "ValueType": "Days"
                              }
                          ]
                      }
                  },
                  "examples": [
                      {
                          "BeforeForAgent": {
                              "Value": 30,
                              "ValueType": "Days"
                          },
                          "AfterForAgent": {
                              "Value": 30,
                              "ValueType": "Days"
                          },
                          "BeforeForUnderwriter": {
                              "Value": 60,
                              "ValueType": "Days"
                          },
                          "AfterForUnderwriter": {
                              "Value": 60,
                              "ValueType": "Days"
                          }
                      }
                  ]
              },
              "QuoteValidity": {
                  "title": "QuoteValidity",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Value",
                      "ValueType"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Value": {
                          "title": "Value",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              60
                          ]
                      },
                      "ValueType": {
                          "title": "ValueType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Days"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "Value": 60,
                          "ValueType": "Days"
                      }
                  ]
              },
              "IsTestPolicy": {
                  "title": "IsTestPolicy",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              }
          },
          "examples": [
              {
                  "AppSource": "SalesForce",
                  "Carrier": "ENGS",
                  "Coverholder": "IH",
                  "Lob": "CA",
                  "State": "GA",
                  "Product": "ENGS1CA",
                  "RaterVersion": "2.0.0.0",
                  "RenewalConfigurations": {
                      "BeforeForAgent": {
                          "Value": 30,
                          "ValueType": "Days"
                      },
                      "AfterForAgent": {
                          "Value": 30,
                          "ValueType": "Days"
                      },
                      "BeforeForUnderwriter": {
                          "Value": 60,
                          "ValueType": "Days"
                      },
                      "AfterForUnderwriter": {
                          "Value": 60,
                          "ValueType": "Days"
                      }
                  },
                  "QuoteValidity": {
                      "Value": 60,
                      "ValueType": "Days"
                  },
                  "IsTestPolicy": true
              }
          ]
      },
      "PolicyStatusHistory": {
          "title": "PolicyStatusHistory",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "OldStatus",
                  "NewStatus",
                  "ChangedBy",
                  "ChangedDate"
              ],
              "additionalProperties": true,
              "properties": {
                  "OldStatus": {
                      "title": "OldStatus",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Quote"
                      ]
                  },
                  "NewStatus": {
                      "title": "NewStatus",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Application"
                      ]
                  },
                  "ChangedBy": {
                      "title": "ChangedBy",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "nkadam"
                      ]
                  },
                  "ChangedDate": {
                      "title": "ChangedDate",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2022-08-18"
                      ]
                  }
              },
              "examples": [
                  {
                      "OldStatus": "Quote",
                      "NewStatus": "Application",
                      "ChangedBy": "nkadam",
                      "ChangedDate": "2022-08-18"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "OldStatus": "Quote",
                      "NewStatus": "Application",
                      "ChangedBy": "nkadam",
                      "ChangedDate": "2022-08-18"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Transaction": {
          "title": "Transaction",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Date",
              "EffectiveDate",
              "Type",
              "Status",
              "Number",
              "IsOutOfSequence",
              "RequestedBy",
              "RequestedById",
              "PremiumType",
              "PolicyVersion",
              "FileType",
              "FileName",
              "File",
              "Remarks",
              "ReasonId",
              "Reason",
              "Verification",
              "TransactionStatusHistory",
              "RenewalOffers"
          ],
          "additionalProperties": true,
          "properties": {
              "Date": {
                  "title": "Date",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-10-19"
                  ]
              },
              "EffectiveDate": {
                  "title": "EffectiveDate",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-10-19"
                  ]
              },
              "Type": {
                  "title": "Type",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Application"
                  ]
              },
              "Status": {
                  "title": "Status",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "In-Progress"
                  ]
              },
              "Number": {
                  "title": "Number",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "IsOutOfSequence": {
                  "title": "IsOutOfSequence",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "RequestedBy": {
                  "title": "RequestedBy",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Agent"
                  ]
              },
              "RequestedById": {
                  "title": "RequestedById",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "123"
                  ]
              },
              "PremiumType": {
                  "title": "PremiumType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "PRO_RATE"
                  ]
              },
              "PolicyVersion": {
                  "title": "PolicyVersion",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "1.0.0"
                  ]
              },
              "FileType": {
                  "title": "FileType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      ""
                  ]
              },
              "FileName": {
                  "title": "FileName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      ""
                  ]
              },
              "File": {
                  "title": "File",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      ""
                  ]
              },
              "Remarks": {
                  "title": "Remarks",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "test policy"
                  ]
              },
              "ReasonId": {
                  "title": "ReasonId",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "AI16"
                  ]
              },
              "Reason": {
                  "title": "Reason",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Policy Rewrite"
                  ]
              },
              "Verification": {
                  "title": "Verification",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "IsInsuredESignVerified",
                      "IsAgentESignVerified",
                      "IsEmailVerified",
                      "IsOTPVerified",
                      "InsuredOTP"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "IsInsuredESignVerified": {
                          "title": "IsInsuredESignVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "IsAgentESignVerified": {
                          "title": "IsAgentESignVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "IsEmailVerified": {
                          "title": "IsEmailVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "IsOTPVerified": {
                          "title": "IsOTPVerified",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              false
                          ]
                      },
                      "InsuredOTP": {
                          "title": "InsuredOTP",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      }
                  },
                  "examples": [
                      {
                          "IsInsuredESignVerified": false,
                          "IsAgentESignVerified": false,
                          "IsEmailVerified": false,
                          "IsOTPVerified": false,
                          "InsuredOTP": ""
                      }
                  ]
              },
              "TransactionStatusHistory": {
                  "title": "TransactionStatusHistory",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "OldStatus",
                          "NewStatus",
                          "ChangedBy",
                          "ChangedDate"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "OldStatus": {
                              "title": "OldStatus",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Quote"
                              ]
                          },
                          "NewStatus": {
                              "title": "NewStatus",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Application"
                              ]
                          },
                          "ChangedBy": {
                              "title": "ChangedBy",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "nkadam"
                              ]
                          },
                          "ChangedDate": {
                              "title": "ChangedDate",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2022-10-19"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "OldStatus": "Quote",
                              "NewStatus": "Application",
                              "ChangedBy": "nkadam",
                              "ChangedDate": "2022-10-19"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "OldStatus": "Quote",
                              "NewStatus": "Application",
                              "ChangedBy": "nkadam",
                              "ChangedDate": "2022-10-19"
                          }
                      ]
                  ],
                  "uniqueItems": false
              },
              "RenewalOffers": {
                  "title": "RenewalOffers",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "RenewalOfferId",
                      "CurrentPremium",
                      "RenewalPremium",
                      "IsUpdateRenewalPremium",
                      "RenewalOfferFlags"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "RenewalOfferId": {
                          "title": "RenewalOfferId",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "A123"
                          ]
                      },
                      "CurrentPremium": {
                          "title": "CurrentPremium",
                          "description": " ",
                          "type": "number",
                          "default": 0.0,
                          "examples": [
                              1365.12
                          ]
                      },
                      "RenewalPremium": {
                          "title": "RenewalPremium",
                          "description": " ",
                          "type": "number",
                          "default": 0.0,
                          "examples": [
                              1465.12
                          ]
                      },
                      "IsUpdateRenewalPremium": {
                          "title": "IsUpdateRenewalPremium",
                          "description": " ",
                          "type": "boolean",
                          "default": false,
                          "examples": [
                              true
                          ]
                      },
                      "RenewalOfferFlags": {
                          "title": "RenewalOfferFlags",
                          "description": " ",
                          "type": "object",
                          "default": {},
                          "required": [
                              "CreatedOn",
                              "UpdatedOn",
                              "CreatedBy",
                              "UpdatedBy",
                              "EmailSentFlag"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "CreatedOn": {
                                  "title": "CreatedOn",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "2022-10-19"
                                  ]
                              },
                              "UpdatedOn": {
                                  "title": "UpdatedOn",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "2022-10-19"
                                  ]
                              },
                              "CreatedBy": {
                                  "title": "CreatedBy",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "nkadam"
                                  ]
                              },
                              "UpdatedBy": {
                                  "title": "UpdatedBy",
                                  "description": " ",
                                  "type": "string",
                                  "default": "",
                                  "examples": [
                                      "nkadam"
                                  ]
                              },
                              "EmailSentFlag": {
                                  "title": "EmailSentFlag",
                                  "description": " ",
                                  "type": "boolean",
                                  "default": false,
                                  "examples": [
                                      false
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "CreatedOn": "2022-10-19",
                                  "UpdatedOn": "2022-10-19",
                                  "CreatedBy": "nkadam",
                                  "UpdatedBy": "nkadam",
                                  "EmailSentFlag": false
                              }
                          ]
                      }
                  },
                  "examples": [
                      {
                          "RenewalOfferId": "A123",
                          "CurrentPremium": 1365.12,
                          "RenewalPremium": 1465.12,
                          "IsUpdateRenewalPremium": true,
                          "RenewalOfferFlags": {
                              "CreatedOn": "2022-10-19",
                              "UpdatedOn": "2022-10-19",
                              "CreatedBy": "nkadam",
                              "UpdatedBy": "nkadam",
                              "EmailSentFlag": false
                          }
                      }
                  ]
              }
          },
          "examples": [
              {
                  "Date": "2022-10-19",
                  "EffectiveDate": "2022-10-19",
                  "Type": "Application",
                  "Status": "In-Progress",
                  "Number": 0,
                  "IsOutOfSequence": false,
                  "RequestedBy": "Agent",
                  "RequestedById": "123",
                  "PremiumType": "PRO_RATE",
                  "PolicyVersion": "1.0.0",
                  "FileType": "",
                  "FileName": "",
                  "File": "",
                  "Remarks": "test policy",
                  "ReasonId": "AI16",
                  "Reason": "Policy Rewrite",
                  "Verification": {
                      "IsInsuredESignVerified": false,
                      "IsAgentESignVerified": false,
                      "IsEmailVerified": false,
                      "IsOTPVerified": false,
                      "InsuredOTP": ""
                  },
                  "TransactionStatusHistory": [
                      {
                          "OldStatus": "Quote",
                          "NewStatus": "Application",
                          "ChangedBy": "nkadam",
                          "ChangedDate": "2022-10-19"
                      }
                  ],
                  "RenewalOffers": {
                      "RenewalOfferId": "A123",
                      "CurrentPremium": 1365.12,
                      "RenewalPremium": 1465.12,
                      "IsUpdateRenewalPremium": true,
                      "RenewalOfferFlags": {
                          "CreatedOn": "2022-10-19",
                          "UpdatedOn": "2022-10-19",
                          "CreatedBy": "nkadam",
                          "UpdatedBy": "nkadam",
                          "EmailSentFlag": false
                      }
                  }
              }
          ]
      },
      "AgentCommission": {
          "title": "AgentCommission",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Value",
              "ValueType"
          ],
          "additionalProperties": true,
          "properties": {
              "Value": {
                  "title": "Value",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "10"
                  ]
              },
              "ValueType": {
                  "title": "ValueType",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Percent"
                  ]
              }
          },
          "examples": [
              {
                  "Value": "10",
                  "ValueType": "Percent"
              }
          ]
      },
      "Agency": {
          "title": "Agency",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Client",
              "Code",
              "Name",
              "Status",
              "Products",
              "Reference",
              "Address",
              "Communications"
          ],
          "additionalProperties": true,
          "properties": {
              "Client": {
                  "title": "Client",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "SGIH"
                  ]
              },
              "Code": {
                  "title": "Code",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "108999"
                  ]
              },
              "Name": {
                  "title": "Name",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "test agency"
                  ]
              },
              "Status": {
                  "title": "Status",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Active"
                  ]
              },
              "Products": {
                  "title": "Products",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "1",
                          "2",
                          "3"
                      ]
                  },
                  "examples": [
                      [
                          "1",
                          "2",
                          "3"
                      ]
                  ],
                  "uniqueItems": false
              },
              "Reference": {
                  "title": "Reference",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "12907",
                          "12911"
                      ]
                  },
                  "examples": [
                      [
                          "12907",
                          "12911"
                      ]
                  ],
                  "uniqueItems": false
              },
              "Address": {
                  "title": "Address",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Number",
                      "AddressType",
                      "Description",
                      "AddressLine1",
                      "AddressLine2",
                      "AptSuite",
                      "City",
                      "County",
                      "CountyCode",
                      "State",
                      "PoBox",
                      "Postalcode",
                      "FormattedAddress",
                      "UnFormattedAddress",
                      "AdministrationArea1",
                      "AdministrationArea2",
                      "Locality",
                      "Lat",
                      "Long",
                      "Name",
                      "Premise",
                      "Status",
                      "Territory",
                      "Business",
                      "PlaceId"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Number": {
                          "title": "Number",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              1
                          ]
                      },
                      "AddressType": {
                          "title": "AddressType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Primary"
                          ]
                      },
                      "Description": {
                          "title": "Description",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Mailing Address"
                          ]
                      },
                      "AddressLine1": {
                          "title": "AddressLine1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE"
                          ]
                      },
                      "AddressLine2": {
                          "title": "AddressLine2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Apt I"
                          ]
                      },
                      "AptSuite": {
                          "title": "AptSuite",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "1000"
                          ]
                      },
                      "City": {
                          "title": "City",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Forest Park"
                          ]
                      },
                      "County": {
                          "title": "County",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "US"
                          ]
                      },
                      "CountyCode": {
                          "title": "CountyCode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "COBB"
                          ]
                      },
                      "State": {
                          "title": "State",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "GA"
                          ]
                      },
                      "PoBox": {
                          "title": "PoBox",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "Postalcode": {
                          "title": "Postalcode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "FormattedAddress": {
                          "title": "FormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE, Smyrna GA 30080"
                          ]
                      },
                      "UnFormattedAddress": {
                          "title": "UnFormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141LakeParkDRSESmyrnaGA30080"
                          ]
                      },
                      "AdministrationArea1": {
                          "title": "AdministrationArea1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "AdministrationArea2": {
                          "title": "AdministrationArea2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Locality": {
                          "title": "Locality",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Atlanta"
                          ]
                      },
                      "Lat": {
                          "title": "Lat",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.6654"
                          ]
                      },
                      "Long": {
                          "title": "Long",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.65646"
                          ]
                      },
                      "Name": {
                          "title": "Name",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cobb Galleria Pkwy"
                          ]
                      },
                      "Premise": {
                          "title": "Premise",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Fron"
                          ]
                      },
                      "Status": {
                          "title": "Status",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Active"
                          ]
                      },
                      "Territory": {
                          "title": "Territory",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Business": {
                          "title": "Business",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cogitate Technology Solution"
                          ]
                      },
                      "PlaceId": {
                          "title": "PlaceId",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      }
                  ]
              },
              "Communications": {
                  "title": "Communications",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Type",
                          "SubType",
                          "Value",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "PhNo",
                                  "Email"
                              ]
                          },
                          "SubType": {
                              "title": "SubType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "4707070096",
                                  "nkadam@cogitate.us"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Client": "SGIH",
                  "Code": "108999",
                  "Name": "test agency",
                  "Status": "Active",
                  "Products": [
                      "1",
                      "2",
                      "3"
                  ],
                  "Reference": [
                      "12907",
                      "12911"
                  ],
                  "Address": {
                      "Number": 1,
                      "AddressType": "Primary",
                      "Description": "Mailing Address",
                      "AddressLine1": "2141 Lake Park DR SE",
                      "AddressLine2": "Apt I",
                      "AptSuite": "1000",
                      "City": "Forest Park",
                      "County": "US",
                      "CountyCode": "COBB",
                      "State": "GA",
                      "PoBox": "30080",
                      "Postalcode": "30080",
                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                      "AdministrationArea1": "",
                      "AdministrationArea2": "",
                      "Locality": "Atlanta",
                      "Lat": "45.6654",
                      "Long": "45.65646",
                      "Name": "Cobb Galleria Pkwy",
                      "Premise": "Fron",
                      "Status": "Active",
                      "Territory": "",
                      "Business": "Cogitate Technology Solution",
                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                  },
                  "Communications": [
                      {
                          "Type": "PhNo",
                          "SubType": "Primary",
                          "Value": "4707070096",
                          "Status": "Active"
                      },
                      {
                          "Type": "Email",
                          "SubType": "Primary",
                          "Value": "nkadam@cogitate.us",
                          "Status": "Active"
                      }
                  ]
              }
          ]
      },
      "UnderWriter": {
          "title": "UnderWriter",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Client",
              "Code",
              "Name",
              "Status",
              "Products",
              "Reference",
              "UWAttributes",
              "Address",
              "Communications"
          ],
          "additionalProperties": true,
          "properties": {
              "Client": {
                  "title": "Client",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "SGIH"
                  ]
              },
              "Code": {
                  "title": "Code",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "001"
                  ]
              },
              "Name": {
                  "title": "Name",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "test UW"
                  ]
              },
              "Status": {
                  "title": "Status",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Active"
                  ]
              },
              "Products": {
                  "title": "Products",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "1",
                          "2",
                          "3"
                      ]
                  },
                  "examples": [
                      [
                          "1",
                          "2",
                          "3"
                      ]
                  ],
                  "uniqueItems": false
              },
              "Reference": {
                  "title": "Reference",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "108999"
                      ]
                  },
                  "examples": [
                      [
                          "108999"
                      ]
                  ],
                  "uniqueItems": false
              },
              "UWAttributes": {
                  "title": "UWAttributes",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "UWOffice",
                      "ContractNumber",
                      "AccountExecCode"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "UWOffice": {
                          "title": "UWOffice",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Rosewell"
                          ]
                      },
                      "ContractNumber": {
                          "title": "ContractNumber",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "ACV124"
                          ]
                      },
                      "AccountExecCode": {
                          "title": "AccountExecCode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "bclark"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "UWOffice": "Rosewell",
                          "ContractNumber": "ACV124",
                          "AccountExecCode": "bclark"
                      }
                  ]
              },
              "Address": {
                  "title": "Address",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Number",
                      "AddressType",
                      "Description",
                      "AddressLine1",
                      "AddressLine2",
                      "AptSuite",
                      "City",
                      "County",
                      "CountyCode",
                      "State",
                      "PoBox",
                      "Postalcode",
                      "FormattedAddress",
                      "UnFormattedAddress",
                      "AdministrationArea1",
                      "AdministrationArea2",
                      "Locality",
                      "Lat",
                      "Long",
                      "Name",
                      "Premise",
                      "Status",
                      "Territory",
                      "Business",
                      "PlaceId"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Number": {
                          "title": "Number",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              1
                          ]
                      },
                      "AddressType": {
                          "title": "AddressType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Primary"
                          ]
                      },
                      "Description": {
                          "title": "Description",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Mailing Address"
                          ]
                      },
                      "AddressLine1": {
                          "title": "AddressLine1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE"
                          ]
                      },
                      "AddressLine2": {
                          "title": "AddressLine2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Apt I"
                          ]
                      },
                      "AptSuite": {
                          "title": "AptSuite",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "1000"
                          ]
                      },
                      "City": {
                          "title": "City",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Forest Park"
                          ]
                      },
                      "County": {
                          "title": "County",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "US"
                          ]
                      },
                      "CountyCode": {
                          "title": "CountyCode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "COBB"
                          ]
                      },
                      "State": {
                          "title": "State",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "GA"
                          ]
                      },
                      "PoBox": {
                          "title": "PoBox",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "Postalcode": {
                          "title": "Postalcode",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "30080"
                          ]
                      },
                      "FormattedAddress": {
                          "title": "FormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141 Lake Park DR SE, Smyrna GA 30080"
                          ]
                      },
                      "UnFormattedAddress": {
                          "title": "UnFormattedAddress",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2141LakeParkDRSESmyrnaGA30080"
                          ]
                      },
                      "AdministrationArea1": {
                          "title": "AdministrationArea1",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "AdministrationArea2": {
                          "title": "AdministrationArea2",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Locality": {
                          "title": "Locality",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Atlanta"
                          ]
                      },
                      "Lat": {
                          "title": "Lat",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.6654"
                          ]
                      },
                      "Long": {
                          "title": "Long",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "45.65646"
                          ]
                      },
                      "Name": {
                          "title": "Name",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cobb Galleria Pkwy"
                          ]
                      },
                      "Premise": {
                          "title": "Premise",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Fron"
                          ]
                      },
                      "Status": {
                          "title": "Status",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Active"
                          ]
                      },
                      "Territory": {
                          "title": "Territory",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              ""
                          ]
                      },
                      "Business": {
                          "title": "Business",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cogitate Technology Solution"
                          ]
                      },
                      "PlaceId": {
                          "title": "PlaceId",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      }
                  ]
              },
              "Communications": {
                  "title": "Communications",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Type",
                          "SubType",
                          "Value",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "PhNo",
                                  "Email"
                              ]
                          },
                          "SubType": {
                              "title": "SubType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "4707070096",
                                  "nkadam@cogitate.us"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Client": "SGIH",
                  "Code": "001",
                  "Name": "test UW",
                  "Status": "Active",
                  "Products": [
                      "1",
                      "2",
                      "3"
                  ],
                  "Reference": [
                      "108999"
                  ],
                  "UWAttributes": {
                      "UWOffice": "Rosewell",
                      "ContractNumber": "ACV124",
                      "AccountExecCode": "bclark"
                  },
                  "Address": {
                      "Number": 1,
                      "AddressType": "Primary",
                      "Description": "Mailing Address",
                      "AddressLine1": "2141 Lake Park DR SE",
                      "AddressLine2": "Apt I",
                      "AptSuite": "1000",
                      "City": "Forest Park",
                      "County": "US",
                      "CountyCode": "COBB",
                      "State": "GA",
                      "PoBox": "30080",
                      "Postalcode": "30080",
                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                      "AdministrationArea1": "",
                      "AdministrationArea2": "",
                      "Locality": "Atlanta",
                      "Lat": "45.6654",
                      "Long": "45.65646",
                      "Name": "Cobb Galleria Pkwy",
                      "Premise": "Fron",
                      "Status": "Active",
                      "Territory": "",
                      "Business": "Cogitate Technology Solution",
                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                  },
                  "Communications": [
                      {
                          "Type": "PhNo",
                          "SubType": "Primary",
                          "Value": "4707070096",
                          "Status": "Active"
                      },
                      {
                          "Type": "Email",
                          "SubType": "Primary",
                          "Value": "nkadam@cogitate.us",
                          "Status": "Active"
                      }
                  ]
              }
          ]
      },
      "PriorInsurances": {
          "title": "PriorInsurances",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "IsCurrentlyInsured",
                  "CompanyName",
                  "OtherCompanyName",
                  "EffectiveDate",
                  "ExpirationDate",
                  "Premium",
                  "Status"
              ],
              "additionalProperties": true,
              "properties": {
                  "IsCurrentlyInsured": {
                      "title": "IsCurrentlyInsured",
                      "description": " ",
                      "type": "boolean",
                      "default": false,
                      "examples": [
                          false
                      ]
                  },
                  "CompanyName": {
                      "title": "CompanyName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Other"
                      ]
                  },
                  "OtherCompanyName": {
                      "title": "OtherCompanyName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "xyz insurance"
                      ]
                  },
                  "EffectiveDate": {
                      "title": "EffectiveDate",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2022-08-18"
                      ]
                  },
                  "ExpirationDate": {
                      "title": "ExpirationDate",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2023-08-18"
                      ]
                  },
                  "Premium": {
                      "title": "Premium",
                      "description": " ",
                      "type": "number",
                      "default": 0,
                      "examples": [
                          6545
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Active"
                      ]
                  }
              },
              "examples": [
                  {
                      "IsCurrentlyInsured": false,
                      "CompanyName": "Other",
                      "OtherCompanyName": "xyz insurance",
                      "EffectiveDate": "2022-08-18",
                      "ExpirationDate": "2023-08-18",
                      "Premium": 6545,
                      "Status": "Active"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "IsCurrentlyInsured": false,
                      "CompanyName": "Other",
                      "OtherCompanyName": "xyz insurance",
                      "EffectiveDate": "2022-08-18",
                      "ExpirationDate": "2023-08-18",
                      "Premium": 6545,
                      "Status": "Active"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "InsuredAccount": {
          "title": "InsuredAccount",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Type",
              "CreationDate",
              "UserName",
              "FirstName",
              "MiddleName",
              "LastName",
              "DisplayName",
              "BankDetails",
              "Communications",
              "BusinessInfo"
          ],
          "additionalProperties": true,
          "properties": {
              "Type": {
                  "title": "Type",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Primary"
                  ]
              },
              "CreationDate": {
                  "title": "CreationDate",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-08-18"
                  ]
              },
              "UserName": {
                  "title": "UserName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "nkadam"
                  ]
              },
              "FirstName": {
                  "title": "FirstName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Nitin"
                  ]
              },
              "MiddleName": {
                  "title": "MiddleName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "B"
                  ]
              },
              "LastName": {
                  "title": "LastName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Kadam"
                  ]
              },
              "DisplayName": {
                  "title": "DisplayName",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "Nitin Kadam"
                  ]
              },
              "BankDetails": {
                  "title": "BankDetails",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "AccountName",
                      "BankName",
                      "BranchName",
                      "AccountType",
                      "RoutingNo"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "AccountName": {
                          "title": "AccountName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Nitin Kadam"
                          ]
                      },
                      "BankName": {
                          "title": "BankName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Bank of America"
                          ]
                      },
                      "BranchName": {
                          "title": "BranchName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Smyrna"
                          ]
                      },
                      "AccountType": {
                          "title": "AccountType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Saving"
                          ]
                      },
                      "RoutingNo": {
                          "title": "RoutingNo",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "123456789"
                          ]
                      }
                  },
                  "examples": [
                      {
                          "AccountName": "Nitin Kadam",
                          "BankName": "Bank of America",
                          "BranchName": "Smyrna",
                          "AccountType": "Saving",
                          "RoutingNo": "123456789"
                      }
                  ]
              },
              "Communications": {
                  "title": "Communications",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Type",
                          "SubType",
                          "Value",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "PhNo",
                                  "Email"
                              ]
                          },
                          "SubType": {
                              "title": "SubType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "4707070096",
                                  "nkadam@cogitate.us"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              },
              "BusinessInfo": {
                  "title": "BusinessInfo",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "BusinessType",
                      "YearsInBusiness",
                      "IncorporationAge",
                      "BusinessName",
                      "DisplayName",
                      "RegistrationNumber",
                      "BusinessStruct",
                      "SpecialRisk",
                      "NoOfOwners",
                      "FullTimeEmployees",
                      "PartTimeEmployees",
                      "Website",
                      "IndustryType",
                      "BusinessDecsription",
                      "AnnualRevenue",
                      "NumberOFLocations",
                      "Locations"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "BusinessType": {
                          "title": "BusinessType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Inc"
                          ]
                      },
                      "YearsInBusiness": {
                          "title": "YearsInBusiness",
                          "description": " ",
                          "type": "number",
                          "default": 0.0,
                          "examples": [
                              4.5
                          ]
                      },
                      "IncorporationAge": {
                          "title": "IncorporationAge",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2018-11-30"
                          ]
                      },
                      "BusinessName": {
                          "title": "BusinessName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "segitech"
                          ]
                      },
                      "DisplayName": {
                          "title": "DisplayName",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Cogitate"
                          ]
                      },
                      "RegistrationNumber": {
                          "title": "RegistrationNumber",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "123A64DF"
                          ]
                      },
                      "BusinessStruct": {
                          "title": "BusinessStruct",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Individual"
                          ]
                      },
                      "SpecialRisk": {
                          "title": "SpecialRisk",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Manager"
                          ]
                      },
                      "NoOfOwners": {
                          "title": "NoOfOwners",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              1
                          ]
                      },
                      "FullTimeEmployees": {
                          "title": "FullTimeEmployees",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              22
                          ]
                      },
                      "PartTimeEmployees": {
                          "title": "PartTimeEmployees",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              12
                          ]
                      },
                      "Website": {
                          "title": "Website",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "http://cogitate.us"
                          ]
                      },
                      "IndustryType": {
                          "title": "IndustryType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Information Technology"
                          ]
                      },
                      "BusinessDecsription": {
                          "title": "BusinessDecsription",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "Insurnace Technology"
                          ]
                      },
                      "AnnualRevenue": {
                          "title": "AnnualRevenue",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              9456456
                          ]
                      },
                      "NumberOFLocations": {
                          "title": "NumberOFLocations",
                          "description": " ",
                          "type": "number",
                          "default": 0,
                          "examples": [
                              2
                          ]
                      },
                      "Locations": {
                          "title": "Locations",
                          "description": " ",
                          "type": "array",
                          "default": [],
                          "additionalItems": true,
                          "items": {
                              "title": "A",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "NickName",
                                  "LocationNumber",
                                  "IsValid",
                                  "Status",
                                  "Address",
                                  "Type"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "NickName": {
                                      "title": "NickName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Atlanta"
                                      ]
                                  },
                                  "LocationNumber": {
                                      "title": "LocationNumber",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          1
                                      ]
                                  },
                                  "IsValid": {
                                      "title": "IsValid",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          true
                                      ]
                                  },
                                  "Status": {
                                      "title": "Status",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Active"
                                      ]
                                  },
                                  "Address": {
                                      "title": "Address",
                                      "description": " ",
                                      "type": "object",
                                      "default": {},
                                      "required": [
                                          "Number",
                                          "AddressType",
                                          "Description",
                                          "AddressLine1",
                                          "AddressLine2",
                                          "AptSuite",
                                          "City",
                                          "County",
                                          "CountyCode",
                                          "State",
                                          "PoBox",
                                          "Postalcode",
                                          "FormattedAddress",
                                          "UnFormattedAddress",
                                          "AdministrationArea1",
                                          "AdministrationArea2",
                                          "Locality",
                                          "Lat",
                                          "Long",
                                          "Name",
                                          "Premise",
                                          "Status",
                                          "Territory",
                                          "Business",
                                          "PlaceId"
                                      ],
                                      "additionalProperties": true,
                                      "properties": {
                                          "Number": {
                                              "title": "Number",
                                              "description": " ",
                                              "type": "number",
                                              "default": 0,
                                              "examples": [
                                                  1
                                              ]
                                          },
                                          "AddressType": {
                                              "title": "AddressType",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Primary"
                                              ]
                                          },
                                          "Description": {
                                              "title": "Description",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Mailing Address"
                                              ]
                                          },
                                          "AddressLine1": {
                                              "title": "AddressLine1",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "2141 Lake Park DR SE"
                                              ]
                                          },
                                          "AddressLine2": {
                                              "title": "AddressLine2",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Apt I"
                                              ]
                                          },
                                          "AptSuite": {
                                              "title": "AptSuite",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "1000"
                                              ]
                                          },
                                          "City": {
                                              "title": "City",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Forest Park"
                                              ]
                                          },
                                          "County": {
                                              "title": "County",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "US"
                                              ]
                                          },
                                          "CountyCode": {
                                              "title": "CountyCode",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "COBB"
                                              ]
                                          },
                                          "State": {
                                              "title": "State",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "GA"
                                              ]
                                          },
                                          "PoBox": {
                                              "title": "PoBox",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "30080"
                                              ]
                                          },
                                          "Postalcode": {
                                              "title": "Postalcode",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "30080"
                                              ]
                                          },
                                          "FormattedAddress": {
                                              "title": "FormattedAddress",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "2141 Lake Park DR SE, Smyrna GA 30080"
                                              ]
                                          },
                                          "UnFormattedAddress": {
                                              "title": "UnFormattedAddress",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "2141LakeParkDRSESmyrnaGA30080"
                                              ]
                                          },
                                          "AdministrationArea1": {
                                              "title": "AdministrationArea1",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "AdministrationArea2": {
                                              "title": "AdministrationArea2",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "Locality": {
                                              "title": "Locality",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Atlanta"
                                              ]
                                          },
                                          "Lat": {
                                              "title": "Lat",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "45.6654"
                                              ]
                                          },
                                          "Long": {
                                              "title": "Long",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "45.65646"
                                              ]
                                          },
                                          "Name": {
                                              "title": "Name",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Cobb Galleria Pkwy"
                                              ]
                                          },
                                          "Premise": {
                                              "title": "Premise",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Fron"
                                              ]
                                          },
                                          "Status": {
                                              "title": "Status",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Active"
                                              ]
                                          },
                                          "Territory": {
                                              "title": "Territory",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "Business": {
                                              "title": "Business",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "Cogitate Technology Solution"
                                              ]
                                          },
                                          "PlaceId": {
                                              "title": "PlaceId",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                              ]
                                          }
                                      },
                                      "examples": [
                                          {
                                              "Number": 1,
                                              "AddressType": "Primary",
                                              "Description": "Mailing Address",
                                              "AddressLine1": "2141 Lake Park DR SE",
                                              "AddressLine2": "Apt I",
                                              "AptSuite": "1000",
                                              "City": "Forest Park",
                                              "County": "US",
                                              "CountyCode": "COBB",
                                              "State": "GA",
                                              "PoBox": "30080",
                                              "Postalcode": "30080",
                                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                              "AdministrationArea1": "",
                                              "AdministrationArea2": "",
                                              "Locality": "Atlanta",
                                              "Lat": "45.6654",
                                              "Long": "45.65646",
                                              "Name": "Cobb Galleria Pkwy",
                                              "Premise": "Fron",
                                              "Status": "Active",
                                              "Territory": "",
                                              "Business": "Cogitate Technology Solution",
                                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                          }
                                      ]
                                  },
                                  "Type": {
                                      "title": "Type",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Primary"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "NickName": "Atlanta",
                                      "LocationNumber": 1,
                                      "IsValid": true,
                                      "Status": "Active",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Type": "Primary"
                                  }
                              ]
                          },
                          "examples": [
                              [
                                  {
                                      "NickName": "Atlanta",
                                      "LocationNumber": 1,
                                      "IsValid": true,
                                      "Status": "Active",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Type": "Primary"
                                  }
                              ]
                          ],
                          "uniqueItems": false
                      }
                  },
                  "examples": [
                      {
                          "BusinessType": "Inc",
                          "YearsInBusiness": 4.5,
                          "IncorporationAge": "2018-11-30",
                          "BusinessName": "segitech",
                          "DisplayName": "Cogitate",
                          "RegistrationNumber": "123A64DF",
                          "BusinessStruct": "Individual",
                          "SpecialRisk": "Manager",
                          "NoOfOwners": 1,
                          "FullTimeEmployees": 22,
                          "PartTimeEmployees": 12,
                          "Website": "http://cogitate.us",
                          "IndustryType": "Information Technology",
                          "BusinessDecsription": "Insurnace Technology",
                          "AnnualRevenue": 9456456,
                          "NumberOFLocations": 2,
                          "Locations": [
                              {
                                  "NickName": "Atlanta",
                                  "LocationNumber": 1,
                                  "IsValid": true,
                                  "Status": "Active",
                                  "Address": {
                                      "Number": 1,
                                      "AddressType": "Primary",
                                      "Description": "Mailing Address",
                                      "AddressLine1": "2141 Lake Park DR SE",
                                      "AddressLine2": "Apt I",
                                      "AptSuite": "1000",
                                      "City": "Forest Park",
                                      "County": "US",
                                      "CountyCode": "COBB",
                                      "State": "GA",
                                      "PoBox": "30080",
                                      "Postalcode": "30080",
                                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                      "AdministrationArea1": "",
                                      "AdministrationArea2": "",
                                      "Locality": "Atlanta",
                                      "Lat": "45.6654",
                                      "Long": "45.65646",
                                      "Name": "Cobb Galleria Pkwy",
                                      "Premise": "Fron",
                                      "Status": "Active",
                                      "Territory": "",
                                      "Business": "Cogitate Technology Solution",
                                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                  },
                                  "Type": "Primary"
                              }
                          ]
                      }
                  ]
              }
          },
          "examples": [
              {
                  "Type": "Primary",
                  "CreationDate": "2022-08-18",
                  "UserName": "nkadam",
                  "FirstName": "Nitin",
                  "MiddleName": "B",
                  "LastName": "Kadam",
                  "DisplayName": "Nitin Kadam",
                  "BankDetails": {
                      "AccountName": "Nitin Kadam",
                      "BankName": "Bank of America",
                      "BranchName": "Smyrna",
                      "AccountType": "Saving",
                      "RoutingNo": "123456789"
                  },
                  "Communications": [
                      {
                          "Type": "PhNo",
                          "SubType": "Primary",
                          "Value": "4707070096",
                          "Status": "Active"
                      },
                      {
                          "Type": "Email",
                          "SubType": "Primary",
                          "Value": "nkadam@cogitate.us",
                          "Status": "Active"
                      }
                  ],
                  "BusinessInfo": {
                      "BusinessType": "Inc",
                      "YearsInBusiness": 4.5,
                      "IncorporationAge": "2018-11-30",
                      "BusinessName": "segitech",
                      "DisplayName": "Cogitate",
                      "RegistrationNumber": "123A64DF",
                      "BusinessStruct": "Individual",
                      "SpecialRisk": "Manager",
                      "NoOfOwners": 1,
                      "FullTimeEmployees": 22,
                      "PartTimeEmployees": 12,
                      "Website": "http://cogitate.us",
                      "IndustryType": "Information Technology",
                      "BusinessDecsription": "Insurnace Technology",
                      "AnnualRevenue": 9456456,
                      "NumberOFLocations": 2,
                      "Locations": [
                          {
                              "NickName": "Atlanta",
                              "LocationNumber": 1,
                              "IsValid": true,
                              "Status": "Active",
                              "Address": {
                                  "Number": 1,
                                  "AddressType": "Primary",
                                  "Description": "Mailing Address",
                                  "AddressLine1": "2141 Lake Park DR SE",
                                  "AddressLine2": "Apt I",
                                  "AptSuite": "1000",
                                  "City": "Forest Park",
                                  "County": "US",
                                  "CountyCode": "COBB",
                                  "State": "GA",
                                  "PoBox": "30080",
                                  "Postalcode": "30080",
                                  "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                  "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                  "AdministrationArea1": "",
                                  "AdministrationArea2": "",
                                  "Locality": "Atlanta",
                                  "Lat": "45.6654",
                                  "Long": "45.65646",
                                  "Name": "Cobb Galleria Pkwy",
                                  "Premise": "Fron",
                                  "Status": "Active",
                                  "Territory": "",
                                  "Business": "Cogitate Technology Solution",
                                  "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                              },
                              "Type": "Primary"
                          }
                      ]
                  }
              }
          ]
      },
      "JointPolicyHolders": {
          "title": "JointPolicyHolders",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "FirstName",
                  "MiddleName",
                  "LastName",
                  "DateOfBirth",
                  "InsuredType",
                  "Age",
                  "Occupation",
                  "IsHighProfile",
                  "IsAddressSameAsRisk",
                  "Address",
                  "Communications"
              ],
              "additionalProperties": true,
              "properties": {
                  "FirstName": {
                      "title": "FirstName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Nitin"
                      ]
                  },
                  "MiddleName": {
                      "title": "MiddleName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "B"
                      ]
                  },
                  "LastName": {
                      "title": "LastName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Kadam"
                      ]
                  },
                  "DateOfBirth": {
                      "title": "DateOfBirth",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "2022-08-18"
                      ]
                  },
                  "InsuredType": {
                      "title": "InsuredType",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "SecondaryInsured"
                      ]
                  },
                  "Age": {
                      "title": "Age",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Value",
                          "ValueType"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "54"
                              ]
                          },
                          "ValueType": {
                              "title": "ValueType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Years"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Value": "54",
                              "ValueType": "Years"
                          }
                      ]
                  },
                  "Occupation": {
                      "title": "Occupation",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Software engineer"
                      ]
                  },
                  "IsHighProfile": {
                      "title": "IsHighProfile",
                      "description": " ",
                      "type": "boolean",
                      "default": false,
                      "examples": [
                          false
                      ]
                  },
                  "IsAddressSameAsRisk": {
                      "title": "IsAddressSameAsRisk",
                      "description": " ",
                      "type": "boolean",
                      "default": false,
                      "examples": [
                          true
                      ]
                  },
                  "Address": {
                      "title": "Address",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Number",
                          "AddressType",
                          "Description",
                          "AddressLine1",
                          "AddressLine2",
                          "AptSuite",
                          "City",
                          "County",
                          "CountyCode",
                          "State",
                          "PoBox",
                          "Postalcode",
                          "FormattedAddress",
                          "UnFormattedAddress",
                          "AdministrationArea1",
                          "AdministrationArea2",
                          "Locality",
                          "Lat",
                          "Long",
                          "Name",
                          "Premise",
                          "Status",
                          "Territory",
                          "Business",
                          "PlaceId"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Number": {
                              "title": "Number",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  1
                              ]
                          },
                          "AddressType": {
                              "title": "AddressType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Primary"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Mailing Address"
                              ]
                          },
                          "AddressLine1": {
                              "title": "AddressLine1",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2141 Lake Park DR SE"
                              ]
                          },
                          "AddressLine2": {
                              "title": "AddressLine2",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Apt I"
                              ]
                          },
                          "AptSuite": {
                              "title": "AptSuite",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "1000"
                              ]
                          },
                          "City": {
                              "title": "City",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Forest Park"
                              ]
                          },
                          "County": {
                              "title": "County",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "US"
                              ]
                          },
                          "CountyCode": {
                              "title": "CountyCode",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "COBB"
                              ]
                          },
                          "State": {
                              "title": "State",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "GA"
                              ]
                          },
                          "PoBox": {
                              "title": "PoBox",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "30080"
                              ]
                          },
                          "Postalcode": {
                              "title": "Postalcode",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "30080"
                              ]
                          },
                          "FormattedAddress": {
                              "title": "FormattedAddress",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2141 Lake Park DR SE, Smyrna GA 30080"
                              ]
                          },
                          "UnFormattedAddress": {
                              "title": "UnFormattedAddress",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "2141LakeParkDRSESmyrnaGA30080"
                              ]
                          },
                          "AdministrationArea1": {
                              "title": "AdministrationArea1",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "AdministrationArea2": {
                              "title": "AdministrationArea2",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "Locality": {
                              "title": "Locality",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Atlanta"
                              ]
                          },
                          "Lat": {
                              "title": "Lat",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "45.6654"
                              ]
                          },
                          "Long": {
                              "title": "Long",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "45.65646"
                              ]
                          },
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Cobb Galleria Pkwy"
                              ]
                          },
                          "Premise": {
                              "title": "Premise",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Fron"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Territory": {
                              "title": "Territory",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "Business": {
                              "title": "Business",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Cogitate Technology Solution"
                              ]
                          },
                          "PlaceId": {
                              "title": "PlaceId",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Number": 1,
                              "AddressType": "Primary",
                              "Description": "Mailing Address",
                              "AddressLine1": "2141 Lake Park DR SE",
                              "AddressLine2": "Apt I",
                              "AptSuite": "1000",
                              "City": "Forest Park",
                              "County": "US",
                              "CountyCode": "COBB",
                              "State": "GA",
                              "PoBox": "30080",
                              "Postalcode": "30080",
                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                              "AdministrationArea1": "",
                              "AdministrationArea2": "",
                              "Locality": "Atlanta",
                              "Lat": "45.6654",
                              "Long": "45.65646",
                              "Name": "Cobb Galleria Pkwy",
                              "Premise": "Fron",
                              "Status": "Active",
                              "Territory": "",
                              "Business": "Cogitate Technology Solution",
                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                          }
                      ]
                  },
                  "Communications": {
                      "title": "Communications",
                      "description": " ",
                      "type": "array",
                      "default": [],
                      "additionalItems": true,
                      "items": {
                          "title": "A",
                          "description": " ",
                          "type": "object",
                          "required": [
                              "Type",
                              "SubType",
                              "Value",
                              "Status"
                          ],
                          "additionalProperties": true,
                          "properties": {
                              "Type": {
                                  "title": "Type",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "PhNo",
                                      "Email"
                                  ]
                              },
                              "SubType": {
                                  "title": "SubType",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "Primary"
                                  ]
                              },
                              "Value": {
                                  "title": "Value",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "4707070096",
                                      "nkadam@cogitate.us"
                                  ]
                              },
                              "Status": {
                                  "title": "Status",
                                  "description": " ",
                                  "type": "string",
                                  "examples": [
                                      "Active"
                                  ]
                              }
                          },
                          "examples": [
                              {
                                  "Type": "PhNo",
                                  "SubType": "Primary",
                                  "Value": "4707070096",
                                  "Status": "Active"
                              },
                              {
                                  "Type": "Email",
                                  "SubType": "Primary",
                                  "Value": "nkadam@cogitate.us",
                                  "Status": "Active"
                              }
                          ]
                      },
                      "examples": [
                          [
                              {
                                  "Type": "PhNo",
                                  "SubType": "Primary",
                                  "Value": "4707070096",
                                  "Status": "Active"
                              },
                              {
                                  "Type": "Email",
                                  "SubType": "Primary",
                                  "Value": "nkadam@cogitate.us",
                                  "Status": "Active"
                              }
                          ]
                      ],
                      "uniqueItems": false
                  }
              },
              "examples": [
                  {
                      "FirstName": "Nitin",
                      "MiddleName": "B",
                      "LastName": "Kadam",
                      "DateOfBirth": "2022-08-18",
                      "InsuredType": "SecondaryInsured",
                      "Age": {
                          "Value": "54",
                          "ValueType": "Years"
                      },
                      "Occupation": "Software engineer",
                      "IsHighProfile": false,
                      "IsAddressSameAsRisk": true,
                      "Address": {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      },
                      "Communications": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  }
              ]
          },
          "examples": [
              [
                  {
                      "FirstName": "Nitin",
                      "MiddleName": "B",
                      "LastName": "Kadam",
                      "DateOfBirth": "2022-08-18",
                      "InsuredType": "SecondaryInsured",
                      "Age": {
                          "Value": "54",
                          "ValueType": "Years"
                      },
                      "Occupation": "Software engineer",
                      "IsHighProfile": false,
                      "IsAddressSameAsRisk": true,
                      "Address": {
                          "Number": 1,
                          "AddressType": "Primary",
                          "Description": "Mailing Address",
                          "AddressLine1": "2141 Lake Park DR SE",
                          "AddressLine2": "Apt I",
                          "AptSuite": "1000",
                          "City": "Forest Park",
                          "County": "US",
                          "CountyCode": "COBB",
                          "State": "GA",
                          "PoBox": "30080",
                          "Postalcode": "30080",
                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                          "AdministrationArea1": "",
                          "AdministrationArea2": "",
                          "Locality": "Atlanta",
                          "Lat": "45.6654",
                          "Long": "45.65646",
                          "Name": "Cobb Galleria Pkwy",
                          "Premise": "Fron",
                          "Status": "Active",
                          "Territory": "",
                          "Business": "Cogitate Technology Solution",
                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                      },
                      "Communications": [
                          {
                              "Type": "PhNo",
                              "SubType": "Primary",
                              "Value": "4707070096",
                              "Status": "Active"
                          },
                          {
                              "Type": "Email",
                              "SubType": "Primary",
                              "Value": "nkadam@cogitate.us",
                              "Status": "Active"
                          }
                      ]
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Audit": {
          "title": "Audit",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "CreatedBy",
              "CreatedOn",
              "LastUpdatedBy",
              "LastUpdatedOn"
          ],
          "additionalProperties": true,
          "properties": {
              "CreatedBy": {
                  "title": "CreatedBy",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "nkadam"
                  ]
              },
              "CreatedOn": {
                  "title": "CreatedOn",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-08-18"
                  ]
              },
              "LastUpdatedBy": {
                  "title": "LastUpdatedBy",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "nkadam"
                  ]
              },
              "LastUpdatedOn": {
                  "title": "LastUpdatedOn",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "2022-08-18"
                  ]
              }
          },
          "examples": [
              {
                  "CreatedBy": "nkadam",
                  "CreatedOn": "2022-08-18",
                  "LastUpdatedBy": "nkadam",
                  "LastUpdatedOn": "2022-08-18"
              }
          ]
      },
      "ExternalRefrences": {
          "title": "ExternalRefrences",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "default": {},
              "required": [
                  "ReferenceNumber",
                  "ReferenceTarget",
                  "Status"
              ],
              "additionalProperties": true,
              "properties": {
                  "ReferenceNumber": {
                      "title": "ReferenceNumber",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "0246879"
                      ]
                  },
                  "ReferenceTarget": {
                      "title": "ReferenceTarget",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "AIM"
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Active"
                      ]
                  }
              },
              "examples": [
                  {
                      "ReferenceNumber": "0246879",
                      "ReferenceTarget": "AIM",
                      "Status": "Active"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "ReferenceNumber": "0246879",
                      "ReferenceTarget": "AIM",
                      "Status": "Active"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Claims": {
          "title": "Claims",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Status",
                  "ClaimSequence",
                  "IsUnrepairedDamage",
                  "DateofLoss",
                  "PaidAmount",
                  "ReserveAmount",
                  "IncidentType",
                  "CoverageType",
                  "ClaimantName",
                  "UnitId",
                  "Remark"
              ],
              "additionalProperties": true,
              "properties": {
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active",
                          "InActive"
                      ]
                  },
                  "ClaimSequence": {
                      "title": "ClaimSequence",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          1.0,
                          2.0
                      ]
                  },
                  "IsUnrepairedDamage": {
                      "title": "IsUnrepairedDamage",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "DateofLoss": {
                      "title": "DateofLoss",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "2022-09-07"
                      ]
                  },
                  "PaidAmount": {
                      "title": "PaidAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          5000,
                          8000
                      ]
                  },
                  "ReserveAmount": {
                      "title": "ReserveAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          5000
                      ]
                  },
                  "IncidentType": {
                      "title": "IncidentType",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Flood",
                          "Hail"
                      ]
                  },
                  "CoverageType": {
                      "title": "CoverageType",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "HO"
                      ]
                  },
                  "ClaimantName": {
                      "title": "ClaimantName",
                      "description": " ",
                      "type": "string",
                      "default": "",
                      "examples": [
                          "Ben Johns"
                      ]
                  },
                  "UnitId": {
                      "title": "UnitId",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          1,
                          2
                      ]
                  },
                  "Remark": {
                      "title": "Remark",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Flood Claim ",
                          "Hail Damage"
                      ]
                  }
              },
              "examples": [
                  {
                      "Status": "Active",
                      "ClaimSequence": 1.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 5000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Flood",
                      "CoverageType": "HO",
                      "ClaimantName": "Ben Johns",
                      "UnitId": 1,
                      "Remark": "Flood Claim "
                  },
                  {
                      "Status": "InActive",
                      "ClaimSequence": 2.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 8000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Hail",
                      "UnitId": 2,
                      "Remark": "Hail Damage"
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Status": "Active",
                      "ClaimSequence": 1.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 5000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Flood",
                      "CoverageType": "HO",
                      "ClaimantName": "Ben Johns",
                      "UnitId": 1,
                      "Remark": "Flood Claim "
                  },
                  {
                      "Status": "InActive",
                      "ClaimSequence": 2.0,
                      "IsUnrepairedDamage": true,
                      "DateofLoss": "2022-09-07",
                      "PaidAmount": 8000,
                      "ReserveAmount": 5000,
                      "IncidentType": "Hail",
                      "UnitId": 2,
                      "Remark": "Hail Damage"
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Forms": {
          "title": "Forms",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Status",
                  "FormName",
                  "FormDesc",
                  "Sequence",
                  "FormType",
                  "Template",
                  "IsMandatory",
                  "IsChecked",
                  "AcordCode",
                  "File",
                  "Dmspath"
              ],
              "additionalProperties": true,
              "properties": {
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active"
                      ]
                  },
                  "FormName": {
                      "title": "FormName",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "SG1004",
                          "SG1025"
                      ]
                  },
                  "FormDesc": {
                      "title": "FormDesc",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Binder",
                          "Statement of No Other Drivers Form"
                      ]
                  },
                  "Sequence": {
                      "title": "Sequence",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          1.0,
                          2.0
                      ]
                  },
                  "FormType": {
                      "title": "FormType",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Dynamic",
                          "Static"
                      ]
                  },
                  "Template": {
                      "title": "Template",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "l4pb03ugrcr",
                          "slhmuehfzyv"
                      ]
                  },
                  "IsMandatory": {
                      "title": "IsMandatory",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "IsChecked": {
                      "title": "IsChecked",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "AcordCode": {
                      "title": "AcordCode",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "IH005",
                          "IH034"
                      ]
                  },
                  "File": {
                      "title": "File",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          ""
                      ]
                  },
                  "Dmspath": {
                      "title": "Dmspath",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          ""
                      ]
                  }
              },
              "examples": [
                  {
                      "Status": "Active",
                      "FormName": "SG1004",
                      "FormDesc": "Binder",
                      "Sequence": 1.0,
                      "FormType": "Dynamic",
                      "Template": "l4pb03ugrcr",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH005",
                      "File": "",
                      "Dmspath": ""
                  },
                  {
                      "Status": "Active",
                      "FormName": "SG1025",
                      "FormDesc": "Statement of No Other Drivers Form",
                      "Sequence": 2.0,
                      "FormType": "Static",
                      "Template": "slhmuehfzyv",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH034",
                      "File": "",
                      "Dmspath": ""
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Status": "Active",
                      "FormName": "SG1004",
                      "FormDesc": "Binder",
                      "Sequence": 1.0,
                      "FormType": "Dynamic",
                      "Template": "l4pb03ugrcr",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH005",
                      "File": "",
                      "Dmspath": ""
                  },
                  {
                      "Status": "Active",
                      "FormName": "SG1025",
                      "FormDesc": "Statement of No Other Drivers Form",
                      "Sequence": 2.0,
                      "FormType": "Static",
                      "Template": "slhmuehfzyv",
                      "IsMandatory": true,
                      "IsChecked": true,
                      "AcordCode": "IH034",
                      "File": "",
                      "Dmspath": ""
                  }
              ]
          ],
          "uniqueItems": false
      },
      "PolicyCoverages": {
          "title": "PolicyCoverages",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Coverages"
          ],
          "additionalProperties": true,
          "properties": {
              "Coverages": {
                  "title": "Coverages",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Name",
                          "Description",
                          "Type",
                          "SettlementType",
                          "Value",
                          "Limit",
                          "LimitAmount",
                          "Deductible",
                          "IsApplicable",
                          "IsSelected",
                          "IsMandatory",
                          "Status"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Combined Single Limit"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Combined Single Limit"
                              ]
                          },
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Coverage"
                              ]
                          },
                          "SettlementType": {
                              "title": "SettlementType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "ACV"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "5"
                              ]
                          },
                          "Limit": {
                              "title": "Limit",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  10000
                              ]
                          },
                          "LimitAmount": {
                              "title": "LimitAmount",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  10000
                              ]
                          },
                          "Deductible": {
                              "title": "Deductible",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  500
                              ]
                          },
                          "IsApplicable": {
                              "title": "IsApplicable",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "IsSelected": {
                              "title": "IsSelected",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "IsMandatory": {
                              "title": "IsMandatory",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Name": "Combined Single Limit",
                              "Description": "Combined Single Limit",
                              "Type": "Coverage",
                              "SettlementType": "ACV",
                              "Value": "5",
                              "Limit": 10000,
                              "LimitAmount": 10000,
                              "Deductible": 500,
                              "IsApplicable": true,
                              "IsSelected": true,
                              "IsMandatory": true,
                              "Status": "Active"
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "Name": "Combined Single Limit",
                              "Description": "Combined Single Limit",
                              "Type": "Coverage",
                              "SettlementType": "ACV",
                              "Value": "5",
                              "Limit": 10000,
                              "LimitAmount": 10000,
                              "Deductible": 500,
                              "IsApplicable": true,
                              "IsSelected": true,
                              "IsMandatory": true,
                              "Status": "Active"
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Coverages": [
                      {
                          "Name": "Combined Single Limit",
                          "Description": "Combined Single Limit",
                          "Type": "Coverage",
                          "SettlementType": "ACV",
                          "Value": "5",
                          "Limit": 10000,
                          "LimitAmount": 10000,
                          "Deductible": 500,
                          "IsApplicable": true,
                          "IsSelected": true,
                          "IsMandatory": true,
                          "Status": "Active"
                      }
                  ]
              }
          ]
      },
      "PremiumFactors": {
          "title": "PremiumFactors",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Name",
                  "Status",
                  "Type",
                  "Description",
                  "IsApplicable",
                  "IsSelected",
                  "IsMandatory",
                  "Rate",
                  "Limit",
                  "LimitAmount",
                  "Deductible",
                  "Premium",
                  "EffectivePremium",
                  "PremiumDifference",
                  "Factor"
              ],
              "additionalProperties": true,
              "properties": {
                  "Name": {
                      "title": "Name",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "RP",
                          "MinPre"
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active"
                      ]
                  },
                  "Type": {
                      "title": "Type",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "SUR"
                      ]
                  },
                  "Description": {
                      "title": "Description",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Risk Premium",
                          "Minimum Premium"
                      ]
                  },
                  "IsApplicable": {
                      "title": "IsApplicable",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "IsSelected": {
                      "title": "IsSelected",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          true
                      ]
                  },
                  "IsMandatory": {
                      "title": "IsMandatory",
                      "description": " ",
                      "type": [
                          "boolean",
                          "string"
                      ],
                      "examples": [
                          true,
                          ""
                      ]
                  },
                  "Rate": {
                      "title": "Rate",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Limit": {
                      "title": "Limit",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "LimitAmount": {
                      "title": "LimitAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Deductible": {
                      "title": "Deductible",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Premium": {
                      "title": "Premium",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "EffectivePremium": {
                      "title": "EffectivePremium",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "PremiumDifference": {
                      "title": "PremiumDifference",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0
                      ]
                  },
                  "Factor": {
                      "title": "Factor",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Name",
                          "Type",
                          "Description",
                          "Rate",
                          "Limit",
                          "LimitAmount",
                          "Premium",
                          "Status",
                          "IsApplicable",
                          "IsSelected",
                          "IsMandatory",
                          "Deductible",
                          "EffectivePremium"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "RP",
                                  "MinPre"
                              ]
                          },
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "SUR"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Risk Premium",
                                  "Minimum Premium"
                              ]
                          },
                          "Rate": {
                              "title": "Rate",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "Limit": {
                              "title": "Limit",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "LimitAmount": {
                              "title": "LimitAmount",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "Premium": {
                              "title": "Premium",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "IsApplicable": {
                              "title": "IsApplicable",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "IsSelected": {
                              "title": "IsSelected",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "IsMandatory": {
                              "title": "IsMandatory",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "Deductible": {
                              "title": "Deductible",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          },
                          "EffectivePremium": {
                              "title": "EffectivePremium",
                              "description": " ",
                              "type": "number",
                              "examples": [
                                  0
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Name": "RP",
                              "Type": "SUR",
                              "Description": "Risk Premium",
                              "Rate": 0,
                              "Limit": 0,
                              "LimitAmount": 0,
                              "Premium": 0,
                              "Status": "Active",
                              "IsApplicable": "",
                              "IsSelected": "",
                              "IsMandatory": "",
                              "Deductible": 0,
                              "EffectivePremium": 0
                          },
                          {
                              "Name": "MinPre",
                              "Type": "SUR",
                              "Description": "Minimum Premium",
                              "Rate": 0,
                              "Limit": 0,
                              "LimitAmount": 0,
                              "Premium": 0,
                              "Status": "Active",
                              "IsApplicable": "",
                              "IsSelected": "",
                              "IsMandatory": "",
                              "Deductible": 0,
                              "EffectivePremium": 0
                          }
                      ]
                  }
              },
              "examples": [
                  {
                      "Name": "RP",
                      "Status": "Active",
                      "Type": "SUR",
                      "Description": "Risk Premium",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": true,
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Deductible": 0,
                      "Premium": 0,
                      "EffectivePremium": 0,
                      "PremiumDifference": 0,
                      "Factor": {
                          "Name": "RP",
                          "Type": "SUR",
                          "Description": "Risk Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      }
                  },
                  {
                      "Name": "MinPre",
                      "Type": "SUR",
                      "Description": "Minimum Premium",
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Premium": 0,
                      "Status": "Active",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": "",
                      "Deductible": 0,
                      "EffectivePremium": 0,
                      "Factor": {
                          "Name": "MinPre",
                          "Type": "SUR",
                          "Description": "Minimum Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      },
                      "PremiumDifference": 0
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Name": "RP",
                      "Status": "Active",
                      "Type": "SUR",
                      "Description": "Risk Premium",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": true,
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Deductible": 0,
                      "Premium": 0,
                      "EffectivePremium": 0,
                      "PremiumDifference": 0,
                      "Factor": {
                          "Name": "RP",
                          "Type": "SUR",
                          "Description": "Risk Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      }
                  },
                  {
                      "Name": "MinPre",
                      "Type": "SUR",
                      "Description": "Minimum Premium",
                      "Rate": 0,
                      "Limit": 0,
                      "LimitAmount": 0,
                      "Premium": 0,
                      "Status": "Active",
                      "IsApplicable": true,
                      "IsSelected": true,
                      "IsMandatory": "",
                      "Deductible": 0,
                      "EffectivePremium": 0,
                      "Factor": {
                          "Name": "MinPre",
                          "Type": "SUR",
                          "Description": "Minimum Premium",
                          "Rate": 0,
                          "Limit": 0,
                          "LimitAmount": 0,
                          "Premium": 0,
                          "Status": "Active",
                          "IsApplicable": "",
                          "IsSelected": "",
                          "IsMandatory": "",
                          "Deductible": 0,
                          "EffectivePremium": 0
                      },
                      "PremiumDifference": 0
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Premium": {
          "title": "Premium",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "BasicPremium",
              "Surcharge",
              "Discount",
              "MinPremium",
              "EffectivePremium",
              "AnnualPremium"
          ],
          "additionalProperties": true,
          "properties": {
              "BasicPremium": {
                  "title": "BasicPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      153
                  ]
              },
              "Surcharge": {
                  "title": "Surcharge",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "Discount": {
                  "title": "Discount",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "MinPremium": {
                  "title": "MinPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "EffectivePremium": {
                  "title": "EffectivePremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "AnnualPremium": {
                  "title": "AnnualPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              }
          },
          "examples": [
              {
                  "BasicPremium": 153,
                  "Surcharge": 0,
                  "Discount": 0,
                  "MinPremium": 0,
                  "EffectivePremium": 0,
                  "AnnualPremium": 0
              }
          ]
      },
      "TotalPremium": {
          "title": "TotalPremium",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "BasicPremium",
              "Surcharge",
              "Discount",
              "MinPremium",
              "EffectivePremium",
              "AnnualPremium",
              "PriorAnnualPremium",
              "EffectivePremiumWithFeesAndTaxes",
              "AnnualPremiumWithFeesAndTaxes"
          ],
          "additionalProperties": true,
          "properties": {
              "BasicPremium": {
                  "title": "BasicPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      4500
                  ]
              },
              "Surcharge": {
                  "title": "Surcharge",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "Discount": {
                  "title": "Discount",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "MinPremium": {
                  "title": "MinPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      750
                  ]
              },
              "EffectivePremium": {
                  "title": "EffectivePremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      4500
                  ]
              },
              "AnnualPremium": {
                  "title": "AnnualPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      4500
                  ]
              },
              "PriorAnnualPremium": {
                  "title": "PriorAnnualPremium",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "EffectivePremiumWithFeesAndTaxes": {
                  "title": "EffectivePremiumWithFeesAndTaxes",
                  "description": " ",
                  "type": "number",
                  "default": 0.0,
                  "examples": [
                      4938.16
                  ]
              },
              "AnnualPremiumWithFeesAndTaxes": {
                  "title": "AnnualPremiumWithFeesAndTaxes",
                  "description": " ",
                  "type": "number",
                  "default": 0.0,
                  "examples": [
                      4938.16
                  ]
              }
          },
          "examples": [
              {
                  "BasicPremium": 4500,
                  "Surcharge": 0,
                  "Discount": 0,
                  "MinPremium": 750,
                  "EffectivePremium": 4500,
                  "AnnualPremium": 4500,
                  "PriorAnnualPremium": 0,
                  "EffectivePremiumWithFeesAndTaxes": 4938.16,
                  "AnnualPremiumWithFeesAndTaxes": 4938.16
              }
          ]
      },
      "FeesAndTaxes": {
          "title": "FeesAndTaxes",
          "description": " ",
          "type": "array",
          "default": [],
          "additionalItems": true,
          "items": {
              "title": "A",
              "description": " ",
              "type": "object",
              "required": [
                  "Code",
                  "IsOverride",
                  "Status",
                  "Value",
                  "ValueType",
                  "Amount",
                  "AnnualAmount",
                  "ProductFeesAndTaxes"
              ],
              "additionalProperties": true,
              "properties": {
                  "Code": {
                      "title": "Code",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "INSFEE",
                          "PFEE"
                      ]
                  },
                  "IsOverride": {
                      "title": "IsOverride",
                      "description": " ",
                      "type": "boolean",
                      "examples": [
                          false
                      ]
                  },
                  "Status": {
                      "title": "Status",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "Active"
                      ]
                  },
                  "Value": {
                      "title": "Value",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          25
                      ]
                  },
                  "ValueType": {
                      "title": "ValueType",
                      "description": " ",
                      "type": "string",
                      "examples": [
                          "V"
                      ]
                  },
                  "Amount": {
                      "title": "Amount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          25
                      ]
                  },
                  "AnnualAmount": {
                      "title": "AnnualAmount",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          25
                      ]
                  },
                  "ProductFeesAndTaxes": {
                      "title": "ProductFeesAndTaxes",
                      "description": " ",
                      "type": "object",
                      "required": [
                          "Code",
                          "Description",
                          "EffectiveFrom",
                          "Status",
                          "Product",
                          "IsEarned",
                          "Value",
                          "ValueType",
                          "DecimalPoints",
                          "RangeFrom",
                          "RangeTo",
                          "RangeValueType",
                          "Transactions",
                          "CalculateOn",
                          "Term"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Code": {
                              "title": "Code",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "INSFEE",
                                  "PFEE"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Installment Fee",
                                  "Policy Fee"
                              ]
                          },
                          "EffectiveFrom": {
                              "title": "EffectiveFrom",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "2020-01-01"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Product": {
                              "title": "Product",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "GAPA"
                              ]
                          },
                          "IsEarned": {
                              "title": "IsEarned",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "0"
                              ]
                          },
                          "Value": {
                              "title": "Value",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "0.0000",
                                  "25.0000"
                              ]
                          },
                          "ValueType": {
                              "title": "ValueType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "V"
                              ]
                          },
                          "DecimalPoints": {
                              "title": "DecimalPoints",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "RangeFrom": {
                              "title": "RangeFrom",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "0.0000"
                              ]
                          },
                          "RangeTo": {
                              "title": "RangeTo",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "99999.0000"
                              ]
                          },
                          "RangeValueType": {
                              "title": "RangeValueType",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "V"
                              ]
                          },
                          "Transactions": {
                              "title": "Transactions",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "A,P,CF,IF,R"
                              ]
                          },
                          "CalculateOn": {
                              "title": "CalculateOn",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  ""
                              ]
                          },
                          "Term": {
                              "title": "Term",
                              "description": " ",
                              "type": "string",
                              "examples": [
                                  "12"
                              ]
                          }
                      },
                      "examples": [
                          {
                              "Code": "INSFEE",
                              "Description": "Installment Fee",
                              "EffectiveFrom": "2020-01-01",
                              "Status": "Active",
                              "Product": "GAPA",
                              "IsEarned": "0",
                              "Value": "0.0000",
                              "ValueType": "V",
                              "DecimalPoints": "",
                              "RangeFrom": "0.0000",
                              "RangeTo": "99999.0000",
                              "RangeValueType": "V",
                              "Transactions": "A,P,CF,IF,R",
                              "CalculateOn": "",
                              "Term": "12"
                          },
                          {
                              "Code": "PFEE",
                              "Description": "Policy Fee",
                              "EffectiveFrom": "2020-01-01",
                              "Status": "Active",
                              "Product": "GAPA",
                              "IsEarned": "0",
                              "Value": "25.0000",
                              "ValueType": "V",
                              "DecimalPoints": "",
                              "RangeFrom": "0.0000",
                              "RangeTo": "99999.0000",
                              "RangeValueType": "V",
                              "Transactions": "A,P,CF,IF,R",
                              "CalculateOn": "",
                              "Term": "12"
                          }
                      ]
                  }
              },
              "examples": [
                  {
                      "Code": "INSFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 0,
                      "ValueType": "V",
                      "Amount": 0,
                      "AnnualAmount": 0,
                      "ProductFeesAndTaxes": {
                          "Code": "INSFEE",
                          "Description": "Installment Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "0.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  },
                  {
                      "Code": "PFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 25,
                      "ValueType": "V",
                      "Amount": 25,
                      "AnnualAmount": 25,
                      "ProductFeesAndTaxes": {
                          "Code": "PFEE",
                          "Description": "Policy Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "25.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  }
              ]
          },
          "examples": [
              [
                  {
                      "Code": "INSFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 0,
                      "ValueType": "V",
                      "Amount": 0,
                      "AnnualAmount": 0,
                      "ProductFeesAndTaxes": {
                          "Code": "INSFEE",
                          "Description": "Installment Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "0.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  },
                  {
                      "Code": "PFEE",
                      "IsOverride": false,
                      "Status": "Active",
                      "Value": 25,
                      "ValueType": "V",
                      "Amount": 25,
                      "AnnualAmount": 25,
                      "ProductFeesAndTaxes": {
                          "Code": "PFEE",
                          "Description": "Policy Fee",
                          "EffectiveFrom": "2020-01-01",
                          "Status": "Active",
                          "Product": "GAPA",
                          "IsEarned": "0",
                          "Value": "25.0000",
                          "ValueType": "V",
                          "DecimalPoints": "",
                          "RangeFrom": "0.0000",
                          "RangeTo": "99999.0000",
                          "RangeValueType": "V",
                          "Transactions": "A,P,CF,IF,R",
                          "CalculateOn": "",
                          "Term": "12"
                      }
                  }
              ]
          ],
          "uniqueItems": false
      },
      "Risks": {
          "title": "Risks",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Vehicles",
              "Drivers"
          ],
          "additionalProperties": true,
          "properties": {
              "Vehicles": {
                  "title": "Vehicles",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "UnitId",
                          "UnitNumber",
                          "Name",
                          "UnitType",
                          "Status",
                          "Coverages",
                          "PremiumFactors",
                          "Premium",
                          "AdditionalParties",
                          "Audit",
                          "RiskAttributes"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "UnitId": {
                              "title": "UnitId",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  1
                              ]
                          },
                          "UnitNumber": {
                              "title": "UnitNumber",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "1"
                              ]
                          },
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Vehicle"
                              ]
                          },
                          "UnitType": {
                              "title": "UnitType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Vehicle"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Coverages": {
                              "title": "Coverages",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Description",
                                      "Type",
                                      "SettlementType",
                                      "Value",
                                      "Limit",
                                      "LimitAmount",
                                      "Deductible",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Status"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Coverage"
                                          ]
                                      },
                                      "SettlementType": {
                                          "title": "SettlementType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "ACV"
                                          ]
                                      },
                                      "Value": {
                                          "title": "Value",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "5"
                                          ]
                                      },
                                      "Limit": {
                                          "title": "Limit",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "LimitAmount": {
                                          "title": "LimitAmount",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "PremiumFactors": {
                              "title": "PremiumFactors",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Type",
                                      "Description",
                                      "Rate",
                                      "Premium",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Deductible",
                                      "EffectivePremium",
                                      "PremiumDifference",
                                      "Status",
                                      "Factor"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "CSL"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "SUR"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Rate": {
                                          "title": "Rate",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "Premium": {
                                          "title": "Premium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "EffectivePremium": {
                                          "title": "EffectivePremium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "PremiumDifference": {
                                          "title": "PremiumDifference",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      },
                                      "Factor": {
                                          "title": "Factor",
                                          "description": " ",
                                          "type": "object",
                                          "default": {},
                                          "required": [
                                              "Name",
                                              "Type",
                                              "Description",
                                              "Rate",
                                              "Limit",
                                              "LimitAmount",
                                              "Deductible",
                                              "Premium",
                                              "EffectivePremium",
                                              "IsApplicable",
                                              "IsSelected",
                                              "IsMandatory"
                                          ],
                                          "additionalProperties": true,
                                          "properties": {
                                              "Name": {
                                                  "title": "Name",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "PDCollNZ"
                                                  ]
                                              },
                                              "Type": {
                                                  "title": "Type",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "SUR"
                                                  ]
                                              },
                                              "Description": {
                                                  "title": "Description",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Physical Damage Rating - Collision(Non-Zone)"
                                                  ]
                                              },
                                              "Rate": {
                                                  "title": "Rate",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      0
                                                  ]
                                              },
                                              "Limit": {
                                                  "title": "Limit",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "LimitAmount": {
                                                  "title": "LimitAmount",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "Deductible": {
                                                  "title": "Deductible",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      500
                                                  ]
                                              },
                                              "Premium": {
                                                  "title": "Premium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "EffectivePremium": {
                                                  "title": "EffectivePremium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "IsApplicable": {
                                                  "title": "IsApplicable",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsSelected": {
                                                  "title": "IsSelected",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsMandatory": {
                                                  "title": "IsMandatory",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              }
                                          },
                                          "examples": [
                                              {
                                                  "Name": "PDCollNZ",
                                                  "Type": "SUR",
                                                  "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                                  "Rate": 0,
                                                  "Limit": 10000,
                                                  "LimitAmount": 10000,
                                                  "Deductible": 500,
                                                  "Premium": 119,
                                                  "EffectivePremium": 119,
                                                  "IsApplicable": true,
                                                  "IsSelected": true,
                                                  "IsMandatory": true
                                              }
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "CSL",
                                          "Type": "SUR",
                                          "Description": "Combined Single Limit",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "CSL",
                                          "Type": "SUR",
                                          "Description": "Combined Single Limit",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "Premium": {
                              "title": "Premium",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "BasicPremium",
                                  "Surcharge",
                                  "Discount",
                                  "MinPremium",
                                  "EffectivePremium",
                                  "AnnualPremium",
                                  "EffectivePremiumWithFeesAndTaxes",
                                  "AnnualPremiumWithFeesAndTaxes"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "BasicPremium": {
                                      "title": "BasicPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "Surcharge": {
                                      "title": "Surcharge",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "Discount": {
                                      "title": "Discount",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "MinPremium": {
                                      "title": "MinPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "EffectivePremium": {
                                      "title": "EffectivePremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "AnnualPremium": {
                                      "title": "AnnualPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "EffectivePremiumWithFeesAndTaxes": {
                                      "title": "EffectivePremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  },
                                  "AnnualPremiumWithFeesAndTaxes": {
                                      "title": "AnnualPremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "BasicPremium": 12005,
                                      "Surcharge": 0,
                                      "Discount": 0,
                                      "MinPremium": 0,
                                      "EffectivePremium": 12005,
                                      "AnnualPremium": 12005,
                                      "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                      "AnnualPremiumWithFeesAndTaxes": 12405.16
                                  }
                              ]
                          },
                          "AdditionalParties": {
                              "title": "AdditionalParties",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Status",
                                      "Name",
                                      "ReferenceNumber",
                                      "IsPayee",
                                      "PartyType",
                                      "InterestType",
                                      "CreatedOn",
                                      "DeletedOn",
                                      "Address",
                                      "Communications"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      },
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "bank of america"
                                          ]
                                      },
                                      "ReferenceNumber": {
                                          "title": "ReferenceNumber",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "132456"
                                          ]
                                      },
                                      "IsPayee": {
                                          "title": "IsPayee",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "PartyType": {
                                          "title": "PartyType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Mortgagee"
                                          ]
                                      },
                                      "InterestType": {
                                          "title": "InterestType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Mortgagee"
                                          ]
                                      },
                                      "CreatedOn": {
                                          "title": "CreatedOn",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "2018-08-18"
                                          ]
                                      },
                                      "DeletedOn": {
                                          "title": "DeletedOn",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "2022-11-30"
                                          ]
                                      },
                                      "Address": {
                                          "title": "Address",
                                          "description": " ",
                                          "type": "object",
                                          "default": {},
                                          "required": [
                                              "Number",
                                              "AddressType",
                                              "Description",
                                              "AddressLine1",
                                              "AddressLine2",
                                              "AptSuite",
                                              "City",
                                              "County",
                                              "CountyCode",
                                              "State",
                                              "PoBox",
                                              "Postalcode",
                                              "FormattedAddress",
                                              "UnFormattedAddress",
                                              "AdministrationArea1",
                                              "AdministrationArea2",
                                              "Locality",
                                              "Lat",
                                              "Long",
                                              "Name",
                                              "Premise",
                                              "Status",
                                              "Territory",
                                              "Business",
                                              "PlaceId"
                                          ],
                                          "additionalProperties": true,
                                          "properties": {
                                              "Number": {
                                                  "title": "Number",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      1
                                                  ]
                                              },
                                              "AddressType": {
                                                  "title": "AddressType",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Primary"
                                                  ]
                                              },
                                              "Description": {
                                                  "title": "Description",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Mailing Address"
                                                  ]
                                              },
                                              "AddressLine1": {
                                                  "title": "AddressLine1",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "2141 Lake Park DR SE"
                                                  ]
                                              },
                                              "AddressLine2": {
                                                  "title": "AddressLine2",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Apt I"
                                                  ]
                                              },
                                              "AptSuite": {
                                                  "title": "AptSuite",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "1000"
                                                  ]
                                              },
                                              "City": {
                                                  "title": "City",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Forest Park"
                                                  ]
                                              },
                                              "County": {
                                                  "title": "County",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "US"
                                                  ]
                                              },
                                              "CountyCode": {
                                                  "title": "CountyCode",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "COBB"
                                                  ]
                                              },
                                              "State": {
                                                  "title": "State",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "GA"
                                                  ]
                                              },
                                              "PoBox": {
                                                  "title": "PoBox",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "30080"
                                                  ]
                                              },
                                              "Postalcode": {
                                                  "title": "Postalcode",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "30080"
                                                  ]
                                              },
                                              "FormattedAddress": {
                                                  "title": "FormattedAddress",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "2141 Lake Park DR SE, Smyrna GA 30080"
                                                  ]
                                              },
                                              "UnFormattedAddress": {
                                                  "title": "UnFormattedAddress",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "2141LakeParkDRSESmyrnaGA30080"
                                                  ]
                                              },
                                              "AdministrationArea1": {
                                                  "title": "AdministrationArea1",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      ""
                                                  ]
                                              },
                                              "AdministrationArea2": {
                                                  "title": "AdministrationArea2",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      ""
                                                  ]
                                              },
                                              "Locality": {
                                                  "title": "Locality",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Atlanta"
                                                  ]
                                              },
                                              "Lat": {
                                                  "title": "Lat",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "45.6654"
                                                  ]
                                              },
                                              "Long": {
                                                  "title": "Long",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "45.65646"
                                                  ]
                                              },
                                              "Name": {
                                                  "title": "Name",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Cobb Galleria Pkwy"
                                                  ]
                                              },
                                              "Premise": {
                                                  "title": "Premise",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Fron"
                                                  ]
                                              },
                                              "Status": {
                                                  "title": "Status",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Active"
                                                  ]
                                              },
                                              "Territory": {
                                                  "title": "Territory",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      ""
                                                  ]
                                              },
                                              "Business": {
                                                  "title": "Business",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Cogitate Technology Solution"
                                                  ]
                                              },
                                              "PlaceId": {
                                                  "title": "PlaceId",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                                  ]
                                              }
                                          },
                                          "examples": [
                                              {
                                                  "Number": 1,
                                                  "AddressType": "Primary",
                                                  "Description": "Mailing Address",
                                                  "AddressLine1": "2141 Lake Park DR SE",
                                                  "AddressLine2": "Apt I",
                                                  "AptSuite": "1000",
                                                  "City": "Forest Park",
                                                  "County": "US",
                                                  "CountyCode": "COBB",
                                                  "State": "GA",
                                                  "PoBox": "30080",
                                                  "Postalcode": "30080",
                                                  "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                                  "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                                  "AdministrationArea1": "",
                                                  "AdministrationArea2": "",
                                                  "Locality": "Atlanta",
                                                  "Lat": "45.6654",
                                                  "Long": "45.65646",
                                                  "Name": "Cobb Galleria Pkwy",
                                                  "Premise": "Fron",
                                                  "Status": "Active",
                                                  "Territory": "",
                                                  "Business": "Cogitate Technology Solution",
                                                  "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                              }
                                          ]
                                      },
                                      "Communications": {
                                          "title": "Communications",
                                          "description": " ",
                                          "type": "array",
                                          "default": [],
                                          "additionalItems": true,
                                          "items": {
                                              "title": "A",
                                              "description": " ",
                                              "type": "object",
                                              "required": [
                                                  "Type",
                                                  "SubType",
                                                  "Value",
                                                  "Status"
                                              ],
                                              "additionalProperties": true,
                                              "properties": {
                                                  "Type": {
                                                      "title": "Type",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "PhNo",
                                                          "Email"
                                                      ]
                                                  },
                                                  "SubType": {
                                                      "title": "SubType",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "Primary"
                                                      ]
                                                  },
                                                  "Value": {
                                                      "title": "Value",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "4707070096",
                                                          "nkadam@cogitate.us"
                                                      ]
                                                  },
                                                  "Status": {
                                                      "title": "Status",
                                                      "description": " ",
                                                      "type": "string",
                                                      "examples": [
                                                          "Active"
                                                      ]
                                                  }
                                              },
                                              "examples": [
                                                  {
                                                      "Type": "PhNo",
                                                      "SubType": "Primary",
                                                      "Value": "4707070096",
                                                      "Status": "Active"
                                                  },
                                                  {
                                                      "Type": "Email",
                                                      "SubType": "Primary",
                                                      "Value": "nkadam@cogitate.us",
                                                      "Status": "Active"
                                                  }
                                              ]
                                          },
                                          "examples": [
                                              [
                                                  {
                                                      "Type": "PhNo",
                                                      "SubType": "Primary",
                                                      "Value": "4707070096",
                                                      "Status": "Active"
                                                  },
                                                  {
                                                      "Type": "Email",
                                                      "SubType": "Primary",
                                                      "Value": "nkadam@cogitate.us",
                                                      "Status": "Active"
                                                  }
                                              ]
                                          ],
                                          "uniqueItems": false
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Status": "Active",
                                          "Name": "bank of america",
                                          "ReferenceNumber": "132456",
                                          "IsPayee": true,
                                          "PartyType": "Mortgagee",
                                          "InterestType": "Mortgagee",
                                          "CreatedOn": "2018-08-18",
                                          "DeletedOn": "2022-11-30",
                                          "Address": {
                                              "Number": 1,
                                              "AddressType": "Primary",
                                              "Description": "Mailing Address",
                                              "AddressLine1": "2141 Lake Park DR SE",
                                              "AddressLine2": "Apt I",
                                              "AptSuite": "1000",
                                              "City": "Forest Park",
                                              "County": "US",
                                              "CountyCode": "COBB",
                                              "State": "GA",
                                              "PoBox": "30080",
                                              "Postalcode": "30080",
                                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                              "AdministrationArea1": "",
                                              "AdministrationArea2": "",
                                              "Locality": "Atlanta",
                                              "Lat": "45.6654",
                                              "Long": "45.65646",
                                              "Name": "Cobb Galleria Pkwy",
                                              "Premise": "Fron",
                                              "Status": "Active",
                                              "Territory": "",
                                              "Business": "Cogitate Technology Solution",
                                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                          },
                                          "Communications": [
                                              {
                                                  "Type": "PhNo",
                                                  "SubType": "Primary",
                                                  "Value": "4707070096",
                                                  "Status": "Active"
                                              },
                                              {
                                                  "Type": "Email",
                                                  "SubType": "Primary",
                                                  "Value": "nkadam@cogitate.us",
                                                  "Status": "Active"
                                              }
                                          ]
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Status": "Active",
                                          "Name": "bank of america",
                                          "ReferenceNumber": "132456",
                                          "IsPayee": true,
                                          "PartyType": "Mortgagee",
                                          "InterestType": "Mortgagee",
                                          "CreatedOn": "2018-08-18",
                                          "DeletedOn": "2022-11-30",
                                          "Address": {
                                              "Number": 1,
                                              "AddressType": "Primary",
                                              "Description": "Mailing Address",
                                              "AddressLine1": "2141 Lake Park DR SE",
                                              "AddressLine2": "Apt I",
                                              "AptSuite": "1000",
                                              "City": "Forest Park",
                                              "County": "US",
                                              "CountyCode": "COBB",
                                              "State": "GA",
                                              "PoBox": "30080",
                                              "Postalcode": "30080",
                                              "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                              "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                              "AdministrationArea1": "",
                                              "AdministrationArea2": "",
                                              "Locality": "Atlanta",
                                              "Lat": "45.6654",
                                              "Long": "45.65646",
                                              "Name": "Cobb Galleria Pkwy",
                                              "Premise": "Fron",
                                              "Status": "Active",
                                              "Territory": "",
                                              "Business": "Cogitate Technology Solution",
                                              "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                          },
                                          "Communications": [
                                              {
                                                  "Type": "PhNo",
                                                  "SubType": "Primary",
                                                  "Value": "4707070096",
                                                  "Status": "Active"
                                              },
                                              {
                                                  "Type": "Email",
                                                  "SubType": "Primary",
                                                  "Value": "nkadam@cogitate.us",
                                                  "Status": "Active"
                                              }
                                          ]
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "Audit": {
                              "title": "Audit",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "CreatedBy",
                                  "CreatedOn",
                                  "DeletedOn",
                                  "LastUpdatedBy",
                                  "LastUpdatedOn"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "CreatedBy": {
                                      "title": "CreatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "CreatedOn": {
                                      "title": "CreatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  },
                                  "DeletedOn": {
                                      "title": "DeletedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-11-30"
                                      ]
                                  },
                                  "LastUpdatedBy": {
                                      "title": "LastUpdatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "LastUpdatedOn": {
                                      "title": "LastUpdatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "CreatedBy": "nkadam",
                                      "CreatedOn": "2022-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "LastUpdatedBy": "nkadam",
                                      "LastUpdatedOn": "2022-08-18"
                                  }
                              ]
                          },
                          "RiskAttributes": {
                              "title": "RiskAttributes",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "ClassificationType",
                                  "SecondaryUse",
                                  "SecondaryUsePercent",
                                  "VehicleType",
                                  "VIN",
                                  "Year",
                                  "VehicleAge",
                                  "Make",
                                  "Model",
                                  "OwnedOrLeased",
                                  "BusinessUseClass",
                                  "SizeClass",
                                  "GROSSCOMBWEIGHT",
                                  "PrimaryGaragingLocation",
                                  "RADIUSCLASSTYPE",
                                  "VEHPRICE",
                                  "PASSIVERESTR",
                                  "VEHYEAR",
                                  "ANTILOCKBRAKES",
                                  "COSTTYPE",
                                  "FARTHESTLOCCITY",
                                  "FARTHESTLOCCOUNTY",
                                  "FARTHESTLOCSTATE",
                                  "FARTHESTLOC",
                                  "ISVEHICLEUPLOADED",
                                  "COMPDED",
                                  "COLLDED",
                                  "MPDED",
                                  "HASPD",
                                  "HASMP",
                                  "TEMPLATENAME",
                                  "UWREFMSG",
                                  "GARAGELOC",
                                  "HASRENTAL",
                                  "CSLLIMIT",
                                  "LIABDED",
                                  "UMTYPE",
                                  "UMDED",
                                  "UMLIMIT"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "ClassificationType": {
                                      "title": "ClassificationType",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS"
                                      ]
                                  },
                                  "SecondaryUse": {
                                      "title": "SecondaryUse",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "SecondaryUsePercent": {
                                      "title": "SecondaryUsePercent",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "VehicleType": {
                                      "title": "VehicleType",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "CargoVan"
                                      ]
                                  },
                                  "VIN": {
                                      "title": "VIN",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2A4RR8DG6BR760259"
                                      ]
                                  },
                                  "Year": {
                                      "title": "Year",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2000"
                                      ]
                                  },
                                  "VehicleAge": {
                                      "title": "VehicleAge",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "15"
                                      ]
                                  },
                                  "Make": {
                                      "title": "Make",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "AlfaRomeo"
                                      ]
                                  },
                                  "Model": {
                                      "title": "Model",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Ecoride"
                                      ]
                                  },
                                  "OwnedOrLeased": {
                                      "title": "OwnedOrLeased",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Owned"
                                      ]
                                  },
                                  "BusinessUseClass": {
                                      "title": "BusinessUseClass",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "retail"
                                      ]
                                  },
                                  "SizeClass": {
                                      "title": "SizeClass",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "lighttrucks"
                                      ]
                                  },
                                  "GROSSCOMBWEIGHT": {
                                      "title": "GROSSCOMBWEIGHT",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "MoreThan45000"
                                      ]
                                  },
                                  "PrimaryGaragingLocation": {
                                      "title": "PrimaryGaragingLocation",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "RADIUSCLASSTYPE": {
                                      "title": "RADIUSCLASSTYPE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "local"
                                      ]
                                  },
                                  "VEHPRICE": {
                                      "title": "VEHPRICE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "20000"
                                      ]
                                  },
                                  "PASSIVERESTR": {
                                      "title": "PASSIVERESTR",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "VEHYEAR": {
                                      "title": "VEHYEAR",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "15"
                                      ]
                                  },
                                  "ANTILOCKBRAKES": {
                                      "title": "ANTILOCKBRAKES",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "COSTTYPE": {
                                      "title": "COSTTYPE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "ACV"
                                      ]
                                  },
                                  "FARTHESTLOCCITY": {
                                      "title": "FARTHESTLOCCITY",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "FARTHESTLOCCOUNTY": {
                                      "title": "FARTHESTLOCCOUNTY",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "FARTHESTLOCSTATE": {
                                      "title": "FARTHESTLOCSTATE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "FARTHESTLOC": {
                                      "title": "FARTHESTLOC",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "ISVEHICLEUPLOADED": {
                                      "title": "ISVEHICLEUPLOADED",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          true
                                      ]
                                  },
                                  "COMPDED": {
                                      "title": "COMPDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "COLLDED": {
                                      "title": "COLLDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "MPDED": {
                                      "title": "MPDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "HASPD": {
                                      "title": "HASPD",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Y"
                                      ]
                                  },
                                  "HASMP": {
                                      "title": "HASMP",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Y"
                                      ]
                                  },
                                  "TEMPLATENAME": {
                                      "title": "TEMPLATENAME",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Default Template"
                                      ]
                                  },
                                  "UWREFMSG": {
                                      "title": "UWREFMSG",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "962"
                                      ]
                                  },
                                  "GARAGELOC": {
                                      "title": "GARAGELOC",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "30084"
                                      ]
                                  },
                                  "HASRENTAL": {
                                      "title": "HASRENTAL",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "N"
                                      ]
                                  },
                                  "CSLLIMIT": {
                                      "title": "CSLLIMIT",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "1000"
                                      ]
                                  },
                                  "LIABDED": {
                                      "title": "LIABDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "UMTYPE": {
                                      "title": "UMTYPE",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "R"
                                      ]
                                  },
                                  "UMDED": {
                                      "title": "UMDED",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "500"
                                      ]
                                  },
                                  "UMLIMIT": {
                                      "title": "UMLIMIT",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "75000"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                                      "SecondaryUse": "",
                                      "SecondaryUsePercent": "",
                                      "VehicleType": "CargoVan",
                                      "VIN": "2A4RR8DG6BR760259",
                                      "Year": "2000",
                                      "VehicleAge": "15",
                                      "Make": "AlfaRomeo",
                                      "Model": "Ecoride",
                                      "OwnedOrLeased": "Owned",
                                      "BusinessUseClass": "retail",
                                      "SizeClass": "lighttrucks",
                                      "GROSSCOMBWEIGHT": "MoreThan45000",
                                      "PrimaryGaragingLocation": "",
                                      "RADIUSCLASSTYPE": "local",
                                      "VEHPRICE": "20000",
                                      "PASSIVERESTR": false,
                                      "VEHYEAR": "15",
                                      "ANTILOCKBRAKES": false,
                                      "COSTTYPE": "ACV",
                                      "FARTHESTLOCCITY": "",
                                      "FARTHESTLOCCOUNTY": "",
                                      "FARTHESTLOCSTATE": "",
                                      "FARTHESTLOC": "",
                                      "ISVEHICLEUPLOADED": true,
                                      "COMPDED": "500",
                                      "COLLDED": "500",
                                      "MPDED": "500",
                                      "HASPD": "Y",
                                      "HASMP": "Y",
                                      "TEMPLATENAME": "Default Template",
                                      "UWREFMSG": "962",
                                      "GARAGELOC": "30084",
                                      "HASRENTAL": "N",
                                      "CSLLIMIT": "1000",
                                      "LIABDED": "500",
                                      "UMTYPE": "R",
                                      "UMDED": "500",
                                      "UMLIMIT": "75000"
                                  }
                              ]
                          }
                      },
                      "examples": [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Vehicle",
                              "UnitType": "Vehicle",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "CSL",
                                      "Type": "SUR",
                                      "Description": "Combined Single Limit",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "AdditionalParties": [
                                  {
                                      "Status": "Active",
                                      "Name": "bank of america",
                                      "ReferenceNumber": "132456",
                                      "IsPayee": true,
                                      "PartyType": "Mortgagee",
                                      "InterestType": "Mortgagee",
                                      "CreatedOn": "2018-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Communications": [
                                          {
                                              "Type": "PhNo",
                                              "SubType": "Primary",
                                              "Value": "4707070096",
                                              "Status": "Active"
                                          },
                                          {
                                              "Type": "Email",
                                              "SubType": "Primary",
                                              "Value": "nkadam@cogitate.us",
                                              "Status": "Active"
                                          }
                                      ]
                                  }
                              ],
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                                  "SecondaryUse": "",
                                  "SecondaryUsePercent": "",
                                  "VehicleType": "CargoVan",
                                  "VIN": "2A4RR8DG6BR760259",
                                  "Year": "2000",
                                  "VehicleAge": "15",
                                  "Make": "AlfaRomeo",
                                  "Model": "Ecoride",
                                  "OwnedOrLeased": "Owned",
                                  "BusinessUseClass": "retail",
                                  "SizeClass": "lighttrucks",
                                  "GROSSCOMBWEIGHT": "MoreThan45000",
                                  "PrimaryGaragingLocation": "",
                                  "RADIUSCLASSTYPE": "local",
                                  "VEHPRICE": "20000",
                                  "PASSIVERESTR": false,
                                  "VEHYEAR": "15",
                                  "ANTILOCKBRAKES": false,
                                  "COSTTYPE": "ACV",
                                  "FARTHESTLOCCITY": "",
                                  "FARTHESTLOCCOUNTY": "",
                                  "FARTHESTLOCSTATE": "",
                                  "FARTHESTLOC": "",
                                  "ISVEHICLEUPLOADED": true,
                                  "COMPDED": "500",
                                  "COLLDED": "500",
                                  "MPDED": "500",
                                  "HASPD": "Y",
                                  "HASMP": "Y",
                                  "TEMPLATENAME": "Default Template",
                                  "UWREFMSG": "962",
                                  "GARAGELOC": "30084",
                                  "HASRENTAL": "N",
                                  "CSLLIMIT": "1000",
                                  "LIABDED": "500",
                                  "UMTYPE": "R",
                                  "UMDED": "500",
                                  "UMLIMIT": "75000"
                              }
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Vehicle",
                              "UnitType": "Vehicle",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "CSL",
                                      "Type": "SUR",
                                      "Description": "Combined Single Limit",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "AdditionalParties": [
                                  {
                                      "Status": "Active",
                                      "Name": "bank of america",
                                      "ReferenceNumber": "132456",
                                      "IsPayee": true,
                                      "PartyType": "Mortgagee",
                                      "InterestType": "Mortgagee",
                                      "CreatedOn": "2018-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "Address": {
                                          "Number": 1,
                                          "AddressType": "Primary",
                                          "Description": "Mailing Address",
                                          "AddressLine1": "2141 Lake Park DR SE",
                                          "AddressLine2": "Apt I",
                                          "AptSuite": "1000",
                                          "City": "Forest Park",
                                          "County": "US",
                                          "CountyCode": "COBB",
                                          "State": "GA",
                                          "PoBox": "30080",
                                          "Postalcode": "30080",
                                          "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                          "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                          "AdministrationArea1": "",
                                          "AdministrationArea2": "",
                                          "Locality": "Atlanta",
                                          "Lat": "45.6654",
                                          "Long": "45.65646",
                                          "Name": "Cobb Galleria Pkwy",
                                          "Premise": "Fron",
                                          "Status": "Active",
                                          "Territory": "",
                                          "Business": "Cogitate Technology Solution",
                                          "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                      },
                                      "Communications": [
                                          {
                                              "Type": "PhNo",
                                              "SubType": "Primary",
                                              "Value": "4707070096",
                                              "Status": "Active"
                                          },
                                          {
                                              "Type": "Email",
                                              "SubType": "Primary",
                                              "Value": "nkadam@cogitate.us",
                                              "Status": "Active"
                                          }
                                      ]
                                  }
                              ],
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                                  "SecondaryUse": "",
                                  "SecondaryUsePercent": "",
                                  "VehicleType": "CargoVan",
                                  "VIN": "2A4RR8DG6BR760259",
                                  "Year": "2000",
                                  "VehicleAge": "15",
                                  "Make": "AlfaRomeo",
                                  "Model": "Ecoride",
                                  "OwnedOrLeased": "Owned",
                                  "BusinessUseClass": "retail",
                                  "SizeClass": "lighttrucks",
                                  "GROSSCOMBWEIGHT": "MoreThan45000",
                                  "PrimaryGaragingLocation": "",
                                  "RADIUSCLASSTYPE": "local",
                                  "VEHPRICE": "20000",
                                  "PASSIVERESTR": false,
                                  "VEHYEAR": "15",
                                  "ANTILOCKBRAKES": false,
                                  "COSTTYPE": "ACV",
                                  "FARTHESTLOCCITY": "",
                                  "FARTHESTLOCCOUNTY": "",
                                  "FARTHESTLOCSTATE": "",
                                  "FARTHESTLOC": "",
                                  "ISVEHICLEUPLOADED": true,
                                  "COMPDED": "500",
                                  "COLLDED": "500",
                                  "MPDED": "500",
                                  "HASPD": "Y",
                                  "HASMP": "Y",
                                  "TEMPLATENAME": "Default Template",
                                  "UWREFMSG": "962",
                                  "GARAGELOC": "30084",
                                  "HASRENTAL": "N",
                                  "CSLLIMIT": "1000",
                                  "LIABDED": "500",
                                  "UMTYPE": "R",
                                  "UMDED": "500",
                                  "UMLIMIT": "75000"
                              }
                          }
                      ]
                  ],
                  "uniqueItems": false
              },
              "Drivers": {
                  "title": "Drivers",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "UnitId",
                          "UnitNumber",
                          "Name",
                          "UnitType",
                          "Status",
                          "Coverages",
                          "PremiumFactors",
                          "Premium",
                          "Audit",
                          "RiskAttributes"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "UnitId": {
                              "title": "UnitId",
                              "description": " ",
                              "type": "number",
                              "default": 0,
                              "examples": [
                                  1
                              ]
                          },
                          "UnitNumber": {
                              "title": "UnitNumber",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "1"
                              ]
                          },
                          "Name": {
                              "title": "Name",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Driver"
                              ]
                          },
                          "UnitType": {
                              "title": "UnitType",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Driver"
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Coverages": {
                              "title": "Coverages",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Description",
                                      "Type",
                                      "SettlementType",
                                      "Value",
                                      "Limit",
                                      "LimitAmount",
                                      "Deductible",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Status"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Combined Single Limit"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Coverage"
                                          ]
                                      },
                                      "SettlementType": {
                                          "title": "SettlementType",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "ACV"
                                          ]
                                      },
                                      "Value": {
                                          "title": "Value",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "5"
                                          ]
                                      },
                                      "Limit": {
                                          "title": "Limit",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "LimitAmount": {
                                          "title": "LimitAmount",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              10000
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "Combined Single Limit",
                                          "Description": "Combined Single Limit",
                                          "Type": "Coverage",
                                          "SettlementType": "ACV",
                                          "Value": "5",
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Status": "Active"
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "PremiumFactors": {
                              "title": "PremiumFactors",
                              "description": " ",
                              "type": "array",
                              "default": [],
                              "additionalItems": true,
                              "items": {
                                  "title": "A",
                                  "description": " ",
                                  "type": "object",
                                  "default": {},
                                  "required": [
                                      "Name",
                                      "Type",
                                      "Description",
                                      "Rate",
                                      "Premium",
                                      "IsApplicable",
                                      "IsSelected",
                                      "IsMandatory",
                                      "Deductible",
                                      "EffectivePremium",
                                      "PremiumDifference",
                                      "Status",
                                      "Factor"
                                  ],
                                  "additionalProperties": true,
                                  "properties": {
                                      "Name": {
                                          "title": "Name",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "PDCollNZ"
                                          ]
                                      },
                                      "Type": {
                                          "title": "Type",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "SUR"
                                          ]
                                      },
                                      "Description": {
                                          "title": "Description",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Physical Damage Rating - Collision(Non-Zone)"
                                          ]
                                      },
                                      "Rate": {
                                          "title": "Rate",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "Premium": {
                                          "title": "Premium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              0
                                          ]
                                      },
                                      "IsApplicable": {
                                          "title": "IsApplicable",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsSelected": {
                                          "title": "IsSelected",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "IsMandatory": {
                                          "title": "IsMandatory",
                                          "description": " ",
                                          "type": "boolean",
                                          "default": false,
                                          "examples": [
                                              true
                                          ]
                                      },
                                      "Deductible": {
                                          "title": "Deductible",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              500
                                          ]
                                      },
                                      "EffectivePremium": {
                                          "title": "EffectivePremium",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "PremiumDifference": {
                                          "title": "PremiumDifference",
                                          "description": " ",
                                          "type": "number",
                                          "default": 0,
                                          "examples": [
                                              119
                                          ]
                                      },
                                      "Status": {
                                          "title": "Status",
                                          "description": " ",
                                          "type": "string",
                                          "default": "",
                                          "examples": [
                                              "Active"
                                          ]
                                      },
                                      "Factor": {
                                          "title": "Factor",
                                          "description": " ",
                                          "type": "object",
                                          "default": {},
                                          "required": [
                                              "Name",
                                              "Type",
                                              "Description",
                                              "Rate",
                                              "Limit",
                                              "LimitAmount",
                                              "Deductible",
                                              "Premium",
                                              "EffectivePremium",
                                              "IsApplicable",
                                              "IsSelected",
                                              "IsMandatory"
                                          ],
                                          "additionalProperties": true,
                                          "properties": {
                                              "Name": {
                                                  "title": "Name",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "PDCollNZ"
                                                  ]
                                              },
                                              "Type": {
                                                  "title": "Type",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "SUR"
                                                  ]
                                              },
                                              "Description": {
                                                  "title": "Description",
                                                  "description": " ",
                                                  "type": "string",
                                                  "default": "",
                                                  "examples": [
                                                      "Physical Damage Rating - Collision(Non-Zone)"
                                                  ]
                                              },
                                              "Rate": {
                                                  "title": "Rate",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      0
                                                  ]
                                              },
                                              "Limit": {
                                                  "title": "Limit",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "LimitAmount": {
                                                  "title": "LimitAmount",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      10000
                                                  ]
                                              },
                                              "Deductible": {
                                                  "title": "Deductible",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      500
                                                  ]
                                              },
                                              "Premium": {
                                                  "title": "Premium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "EffectivePremium": {
                                                  "title": "EffectivePremium",
                                                  "description": " ",
                                                  "type": "number",
                                                  "default": 0,
                                                  "examples": [
                                                      119
                                                  ]
                                              },
                                              "IsApplicable": {
                                                  "title": "IsApplicable",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsSelected": {
                                                  "title": "IsSelected",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              },
                                              "IsMandatory": {
                                                  "title": "IsMandatory",
                                                  "description": " ",
                                                  "type": "boolean",
                                                  "default": false,
                                                  "examples": [
                                                      true
                                                  ]
                                              }
                                          },
                                          "examples": [
                                              {
                                                  "Name": "PDCollNZ",
                                                  "Type": "SUR",
                                                  "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                                  "Rate": 0,
                                                  "Limit": 10000,
                                                  "LimitAmount": 10000,
                                                  "Deductible": 500,
                                                  "Premium": 119,
                                                  "EffectivePremium": 119,
                                                  "IsApplicable": true,
                                                  "IsSelected": true,
                                                  "IsMandatory": true
                                              }
                                          ]
                                      }
                                  },
                                  "examples": [
                                      {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              },
                              "examples": [
                                  [
                                      {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Premium": 0,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true,
                                          "Deductible": 500,
                                          "EffectivePremium": 119,
                                          "PremiumDifference": 119,
                                          "Status": "Active",
                                          "Factor": {
                                              "Name": "PDCollNZ",
                                              "Type": "SUR",
                                              "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                              "Rate": 0,
                                              "Limit": 10000,
                                              "LimitAmount": 10000,
                                              "Deductible": 500,
                                              "Premium": 119,
                                              "EffectivePremium": 119,
                                              "IsApplicable": true,
                                              "IsSelected": true,
                                              "IsMandatory": true
                                          }
                                      }
                                  ]
                              ],
                              "uniqueItems": false
                          },
                          "Premium": {
                              "title": "Premium",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "BasicPremium",
                                  "Surcharge",
                                  "Discount",
                                  "MinPremium",
                                  "EffectivePremium",
                                  "AnnualPremium",
                                  "EffectivePremiumWithFeesAndTaxes",
                                  "AnnualPremiumWithFeesAndTaxes"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "BasicPremium": {
                                      "title": "BasicPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "Surcharge": {
                                      "title": "Surcharge",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "Discount": {
                                      "title": "Discount",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "MinPremium": {
                                      "title": "MinPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "EffectivePremium": {
                                      "title": "EffectivePremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "AnnualPremium": {
                                      "title": "AnnualPremium",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          12005
                                      ]
                                  },
                                  "EffectivePremiumWithFeesAndTaxes": {
                                      "title": "EffectivePremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  },
                                  "AnnualPremiumWithFeesAndTaxes": {
                                      "title": "AnnualPremiumWithFeesAndTaxes",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0.0,
                                      "examples": [
                                          12405.16
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "BasicPremium": 12005,
                                      "Surcharge": 0,
                                      "Discount": 0,
                                      "MinPremium": 0,
                                      "EffectivePremium": 12005,
                                      "AnnualPremium": 12005,
                                      "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                      "AnnualPremiumWithFeesAndTaxes": 12405.16
                                  }
                              ]
                          },
                          "Audit": {
                              "title": "Audit",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "CreatedBy",
                                  "CreatedOn",
                                  "DeletedOn",
                                  "LastUpdatedBy",
                                  "LastUpdatedOn"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "CreatedBy": {
                                      "title": "CreatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "CreatedOn": {
                                      "title": "CreatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  },
                                  "DeletedOn": {
                                      "title": "DeletedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-11-30"
                                      ]
                                  },
                                  "LastUpdatedBy": {
                                      "title": "LastUpdatedBy",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "nkadam"
                                      ]
                                  },
                                  "LastUpdatedOn": {
                                      "title": "LastUpdatedOn",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "2022-08-18"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "CreatedBy": "nkadam",
                                      "CreatedOn": "2022-08-18",
                                      "DeletedOn": "2022-11-30",
                                      "LastUpdatedBy": "nkadam",
                                      "LastUpdatedOn": "2022-08-18"
                                  }
                              ]
                          },
                          "RiskAttributes": {
                              "title": "RiskAttributes",
                              "description": " ",
                              "type": "object",
                              "default": {},
                              "required": [
                                  "Type",
                                  "FirstName",
                                  "MiddleName",
                                  "LastName",
                                  "Suffix",
                                  "DOB",
                                  "Age",
                                  "LicenseNumber",
                                  "Violations",
                                  "IsUSCitizen",
                                  "Occupation",
                                  "FilingStatusCode",
                                  "Fillings",
                                  "FilingCode",
                                  "LicenseDate",
                                  "State",
                                  "HadTrainingCourse",
                                  "IsMilitary",
                                  "MilitaryRank",
                                  "HadDUIDWI",
                                  "DriverCourseCompletedDate",
                                  "CanInsureOperate",
                                  "LicenseStatus",
                                  "IsGoodStudentDiscountApplicable",
                                  "MaritalStatus",
                                  "Gender",
                                  "Violation",
                                  "RelationToApplicant"
                              ],
                              "additionalProperties": true,
                              "properties": {
                                  "Type": {
                                      "title": "Type",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Principal"
                                      ]
                                  },
                                  "FirstName": {
                                      "title": "FirstName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Diane"
                                      ]
                                  },
                                  "MiddleName": {
                                      "title": "MiddleName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "LastName": {
                                      "title": "LastName",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Boyer"
                                      ]
                                  },
                                  "Suffix": {
                                      "title": "Suffix",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "DOB": {
                                      "title": "DOB",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "1962-10-24"
                                      ]
                                  },
                                  "Age": {
                                      "title": "Age",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          59
                                      ]
                                  },
                                  "LicenseNumber": {
                                      "title": "LicenseNumber",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "Violations": {
                                      "title": "Violations",
                                      "description": " ",
                                      "type": "number",
                                      "default": 0,
                                      "examples": [
                                          0
                                      ]
                                  },
                                  "IsUSCitizen": {
                                      "title": "IsUSCitizen",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          true
                                      ]
                                  },
                                  "Occupation": {
                                      "title": "Occupation",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "UN"
                                      ]
                                  },
                                  "FilingStatusCode": {
                                      "title": "FilingStatusCode",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "Fillings": {
                                      "title": "Fillings",
                                      "description": " ",
                                      "type": "object",
                                      "default": {},
                                      "required": [
                                          "Fillings",
                                          "Date",
                                          "Reason",
                                          "FilingCd",
                                          "FilingStatusCd"
                                      ],
                                      "additionalProperties": true,
                                      "properties": {
                                          "Fillings": {
                                              "title": "Fillings",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  "No"
                                              ]
                                          },
                                          "Date": {
                                              "title": "Date",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "Reason": {
                                              "title": "Reason",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "FilingCd": {
                                              "title": "FilingCd",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          },
                                          "FilingStatusCd": {
                                              "title": "FilingStatusCd",
                                              "description": " ",
                                              "type": "string",
                                              "default": "",
                                              "examples": [
                                                  ""
                                              ]
                                          }
                                      },
                                      "examples": [
                                          {
                                              "Fillings": "No",
                                              "Date": "",
                                              "Reason": "",
                                              "FilingCd": "",
                                              "FilingStatusCd": ""
                                          }
                                      ]
                                  },
                                  "FilingCode": {
                                      "title": "FilingCode",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "LicenseDate": {
                                      "title": "LicenseDate",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "1978-11-20"
                                      ]
                                  },
                                  "State": {
                                      "title": "State",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "GA"
                                      ]
                                  },
                                  "HadTrainingCourse": {
                                      "title": "HadTrainingCourse",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "IsMilitary": {
                                      "title": "IsMilitary",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "MilitaryRank": {
                                      "title": "MilitaryRank",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "HadDUIDWI": {
                                      "title": "HadDUIDWI",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "DriverCourseCompletedDate": {
                                      "title": "DriverCourseCompletedDate",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "CanInsureOperate": {
                                      "title": "CanInsureOperate",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          ""
                                      ]
                                  },
                                  "LicenseStatus": {
                                      "title": "LicenseStatus",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Valid"
                                      ]
                                  },
                                  "IsGoodStudentDiscountApplicable": {
                                      "title": "IsGoodStudentDiscountApplicable",
                                      "description": " ",
                                      "type": "boolean",
                                      "default": false,
                                      "examples": [
                                          false
                                      ]
                                  },
                                  "MaritalStatus": {
                                      "title": "MaritalStatus",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "S"
                                      ]
                                  },
                                  "Gender": {
                                      "title": "Gender",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "F"
                                      ]
                                  },
                                  "Violation": {
                                      "title": "Violation",
                                      "description": " ",
                                      "type": "array",
                                      "default": [],
                                      "additionalItems": true,
                                      "items": {},
                                      "examples": [
                                          []
                                      ],
                                      "uniqueItems": false
                                  },
                                  "RelationToApplicant": {
                                      "title": "RelationToApplicant",
                                      "description": " ",
                                      "type": "string",
                                      "default": "",
                                      "examples": [
                                          "Insured"
                                      ]
                                  }
                              },
                              "examples": [
                                  {
                                      "Type": "Principal",
                                      "FirstName": "Diane",
                                      "MiddleName": "",
                                      "LastName": "Boyer",
                                      "Suffix": "",
                                      "DOB": "1962-10-24",
                                      "Age": 59,
                                      "LicenseNumber": "",
                                      "Violations": 0,
                                      "IsUSCitizen": true,
                                      "Occupation": "UN",
                                      "FilingStatusCode": "",
                                      "Fillings": {
                                          "Fillings": "No",
                                          "Date": "",
                                          "Reason": "",
                                          "FilingCd": "",
                                          "FilingStatusCd": ""
                                      },
                                      "FilingCode": "",
                                      "LicenseDate": "1978-11-20",
                                      "State": "GA",
                                      "HadTrainingCourse": false,
                                      "IsMilitary": false,
                                      "MilitaryRank": "",
                                      "HadDUIDWI": false,
                                      "DriverCourseCompletedDate": "",
                                      "CanInsureOperate": "",
                                      "LicenseStatus": "Valid",
                                      "IsGoodStudentDiscountApplicable": false,
                                      "MaritalStatus": "S",
                                      "Gender": "F",
                                      "Violation": [],
                                      "RelationToApplicant": "Insured"
                                  }
                              ]
                          }
                      },
                      "examples": [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Driver",
                              "UnitType": "Driver",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "Type": "Principal",
                                  "FirstName": "Diane",
                                  "MiddleName": "",
                                  "LastName": "Boyer",
                                  "Suffix": "",
                                  "DOB": "1962-10-24",
                                  "Age": 59,
                                  "LicenseNumber": "",
                                  "Violations": 0,
                                  "IsUSCitizen": true,
                                  "Occupation": "UN",
                                  "FilingStatusCode": "",
                                  "Fillings": {
                                      "Fillings": "No",
                                      "Date": "",
                                      "Reason": "",
                                      "FilingCd": "",
                                      "FilingStatusCd": ""
                                  },
                                  "FilingCode": "",
                                  "LicenseDate": "1978-11-20",
                                  "State": "GA",
                                  "HadTrainingCourse": false,
                                  "IsMilitary": false,
                                  "MilitaryRank": "",
                                  "HadDUIDWI": false,
                                  "DriverCourseCompletedDate": "",
                                  "CanInsureOperate": "",
                                  "LicenseStatus": "Valid",
                                  "IsGoodStudentDiscountApplicable": false,
                                  "MaritalStatus": "S",
                                  "Gender": "F",
                                  "Violation": [],
                                  "RelationToApplicant": "Insured"
                              }
                          }
                      ]
                  },
                  "examples": [
                      [
                          {
                              "UnitId": 1,
                              "UnitNumber": "1",
                              "Name": "Driver",
                              "UnitType": "Driver",
                              "Status": "Active",
                              "Coverages": [
                                  {
                                      "Name": "Combined Single Limit",
                                      "Description": "Combined Single Limit",
                                      "Type": "Coverage",
                                      "SettlementType": "ACV",
                                      "Value": "5",
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Status": "Active"
                                  }
                              ],
                              "PremiumFactors": [
                                  {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Premium": 0,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true,
                                      "Deductible": 500,
                                      "EffectivePremium": 119,
                                      "PremiumDifference": 119,
                                      "Status": "Active",
                                      "Factor": {
                                          "Name": "PDCollNZ",
                                          "Type": "SUR",
                                          "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                          "Rate": 0,
                                          "Limit": 10000,
                                          "LimitAmount": 10000,
                                          "Deductible": 500,
                                          "Premium": 119,
                                          "EffectivePremium": 119,
                                          "IsApplicable": true,
                                          "IsSelected": true,
                                          "IsMandatory": true
                                      }
                                  }
                              ],
                              "Premium": {
                                  "BasicPremium": 12005,
                                  "Surcharge": 0,
                                  "Discount": 0,
                                  "MinPremium": 0,
                                  "EffectivePremium": 12005,
                                  "AnnualPremium": 12005,
                                  "EffectivePremiumWithFeesAndTaxes": 12405.16,
                                  "AnnualPremiumWithFeesAndTaxes": 12405.16
                              },
                              "Audit": {
                                  "CreatedBy": "nkadam",
                                  "CreatedOn": "2022-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "LastUpdatedBy": "nkadam",
                                  "LastUpdatedOn": "2022-08-18"
                              },
                              "RiskAttributes": {
                                  "Type": "Principal",
                                  "FirstName": "Diane",
                                  "MiddleName": "",
                                  "LastName": "Boyer",
                                  "Suffix": "",
                                  "DOB": "1962-10-24",
                                  "Age": 59,
                                  "LicenseNumber": "",
                                  "Violations": 0,
                                  "IsUSCitizen": true,
                                  "Occupation": "UN",
                                  "FilingStatusCode": "",
                                  "Fillings": {
                                      "Fillings": "No",
                                      "Date": "",
                                      "Reason": "",
                                      "FilingCd": "",
                                      "FilingStatusCd": ""
                                  },
                                  "FilingCode": "",
                                  "LicenseDate": "1978-11-20",
                                  "State": "GA",
                                  "HadTrainingCourse": false,
                                  "IsMilitary": false,
                                  "MilitaryRank": "",
                                  "HadDUIDWI": false,
                                  "DriverCourseCompletedDate": "",
                                  "CanInsureOperate": "",
                                  "LicenseStatus": "Valid",
                                  "IsGoodStudentDiscountApplicable": false,
                                  "MaritalStatus": "S",
                                  "Gender": "F",
                                  "Violation": [],
                                  "RelationToApplicant": "Insured"
                              }
                          }
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [
              {
                  "Vehicles": [
                      {
                          "UnitId": 1,
                          "UnitNumber": "1",
                          "Name": "Vehicle",
                          "UnitType": "Vehicle",
                          "Status": "Active",
                          "Coverages": [
                              {
                                  "Name": "Combined Single Limit",
                                  "Description": "Combined Single Limit",
                                  "Type": "Coverage",
                                  "SettlementType": "ACV",
                                  "Value": "5",
                                  "Limit": 10000,
                                  "LimitAmount": 10000,
                                  "Deductible": 500,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Status": "Active"
                              }
                          ],
                          "PremiumFactors": [
                              {
                                  "Name": "CSL",
                                  "Type": "SUR",
                                  "Description": "Combined Single Limit",
                                  "Rate": 0,
                                  "Premium": 0,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Deductible": 500,
                                  "EffectivePremium": 119,
                                  "PremiumDifference": 119,
                                  "Status": "Active",
                                  "Factor": {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "Premium": 119,
                                      "EffectivePremium": 119,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true
                                  }
                              }
                          ],
                          "Premium": {
                              "BasicPremium": 12005,
                              "Surcharge": 0,
                              "Discount": 0,
                              "MinPremium": 0,
                              "EffectivePremium": 12005,
                              "AnnualPremium": 12005,
                              "EffectivePremiumWithFeesAndTaxes": 12405.16,
                              "AnnualPremiumWithFeesAndTaxes": 12405.16
                          },
                          "AdditionalParties": [
                              {
                                  "Status": "Active",
                                  "Name": "bank of america",
                                  "ReferenceNumber": "132456",
                                  "IsPayee": true,
                                  "PartyType": "Mortgagee",
                                  "InterestType": "Mortgagee",
                                  "CreatedOn": "2018-08-18",
                                  "DeletedOn": "2022-11-30",
                                  "Address": {
                                      "Number": 1,
                                      "AddressType": "Primary",
                                      "Description": "Mailing Address",
                                      "AddressLine1": "2141 Lake Park DR SE",
                                      "AddressLine2": "Apt I",
                                      "AptSuite": "1000",
                                      "City": "Forest Park",
                                      "County": "US",
                                      "CountyCode": "COBB",
                                      "State": "GA",
                                      "PoBox": "30080",
                                      "Postalcode": "30080",
                                      "FormattedAddress": "2141 Lake Park DR SE, Smyrna GA 30080",
                                      "UnFormattedAddress": "2141LakeParkDRSESmyrnaGA30080",
                                      "AdministrationArea1": "",
                                      "AdministrationArea2": "",
                                      "Locality": "Atlanta",
                                      "Lat": "45.6654",
                                      "Long": "45.65646",
                                      "Name": "Cobb Galleria Pkwy",
                                      "Premise": "Fron",
                                      "Status": "Active",
                                      "Territory": "",
                                      "Business": "Cogitate Technology Solution",
                                      "PlaceId": "ChIJG1xIJwr99IgRNFCYy-mCBy0"
                                  },
                                  "Communications": [
                                      {
                                          "Type": "PhNo",
                                          "SubType": "Primary",
                                          "Value": "4707070096",
                                          "Status": "Active"
                                      },
                                      {
                                          "Type": "Email",
                                          "SubType": "Primary",
                                          "Value": "nkadam@cogitate.us",
                                          "Status": "Active"
                                      }
                                  ]
                              }
                          ],
                          "Audit": {
                              "CreatedBy": "nkadam",
                              "CreatedOn": "2022-08-18",
                              "DeletedOn": "2022-11-30",
                              "LastUpdatedBy": "nkadam",
                              "LastUpdatedOn": "2022-08-18"
                          },
                          "RiskAttributes": {
                              "ClassificationType": "TRUCKS, TRACTORS AND TRAILERS CLASSIFICATIONS",
                              "SecondaryUse": "",
                              "SecondaryUsePercent": "",
                              "VehicleType": "CargoVan",
                              "VIN": "2A4RR8DG6BR760259",
                              "Year": "2000",
                              "VehicleAge": "15",
                              "Make": "AlfaRomeo",
                              "Model": "Ecoride",
                              "OwnedOrLeased": "Owned",
                              "BusinessUseClass": "retail",
                              "SizeClass": "lighttrucks",
                              "GROSSCOMBWEIGHT": "MoreThan45000",
                              "PrimaryGaragingLocation": "",
                              "RADIUSCLASSTYPE": "local",
                              "VEHPRICE": "20000",
                              "PASSIVERESTR": false,
                              "VEHYEAR": "15",
                              "ANTILOCKBRAKES": false,
                              "COSTTYPE": "ACV",
                              "FARTHESTLOCCITY": "",
                              "FARTHESTLOCCOUNTY": "",
                              "FARTHESTLOCSTATE": "",
                              "FARTHESTLOC": "",
                              "ISVEHICLEUPLOADED": true,
                              "COMPDED": "500",
                              "COLLDED": "500",
                              "MPDED": "500",
                              "HASPD": "Y",
                              "HASMP": "Y",
                              "TEMPLATENAME": "Default Template",
                              "UWREFMSG": "962",
                              "GARAGELOC": "30084",
                              "HASRENTAL": "N",
                              "CSLLIMIT": "1000",
                              "LIABDED": "500",
                              "UMTYPE": "R",
                              "UMDED": "500",
                              "UMLIMIT": "75000"
                          }
                      }
                  ],
                  "Drivers": [
                      {
                          "UnitId": 1,
                          "UnitNumber": "1",
                          "Name": "Driver",
                          "UnitType": "Driver",
                          "Status": "Active",
                          "Coverages": [
                              {
                                  "Name": "Combined Single Limit",
                                  "Description": "Combined Single Limit",
                                  "Type": "Coverage",
                                  "SettlementType": "ACV",
                                  "Value": "5",
                                  "Limit": 10000,
                                  "LimitAmount": 10000,
                                  "Deductible": 500,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Status": "Active"
                              }
                          ],
                          "PremiumFactors": [
                              {
                                  "Name": "PDCollNZ",
                                  "Type": "SUR",
                                  "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                  "Rate": 0,
                                  "Premium": 0,
                                  "IsApplicable": true,
                                  "IsSelected": true,
                                  "IsMandatory": true,
                                  "Deductible": 500,
                                  "EffectivePremium": 119,
                                  "PremiumDifference": 119,
                                  "Status": "Active",
                                  "Factor": {
                                      "Name": "PDCollNZ",
                                      "Type": "SUR",
                                      "Description": "Physical Damage Rating - Collision(Non-Zone)",
                                      "Rate": 0,
                                      "Limit": 10000,
                                      "LimitAmount": 10000,
                                      "Deductible": 500,
                                      "Premium": 119,
                                      "EffectivePremium": 119,
                                      "IsApplicable": true,
                                      "IsSelected": true,
                                      "IsMandatory": true
                                  }
                              }
                          ],
                          "Premium": {
                              "BasicPremium": 12005,
                              "Surcharge": 0,
                              "Discount": 0,
                              "MinPremium": 0,
                              "EffectivePremium": 12005,
                              "AnnualPremium": 12005,
                              "EffectivePremiumWithFeesAndTaxes": 12405.16,
                              "AnnualPremiumWithFeesAndTaxes": 12405.16
                          },
                          "Audit": {
                              "CreatedBy": "nkadam",
                              "CreatedOn": "2022-08-18",
                              "DeletedOn": "2022-11-30",
                              "LastUpdatedBy": "nkadam",
                              "LastUpdatedOn": "2022-08-18"
                          },
                          "RiskAttributes": {
                              "Type": "Principal",
                              "FirstName": "Diane",
                              "MiddleName": "",
                              "LastName": "Boyer",
                              "Suffix": "",
                              "DOB": "1962-10-24",
                              "Age": 59,
                              "LicenseNumber": "",
                              "Violations": 0,
                              "IsUSCitizen": true,
                              "Occupation": "UN",
                              "FilingStatusCode": "",
                              "Fillings": {
                                  "Fillings": "No",
                                  "Date": "",
                                  "Reason": "",
                                  "FilingCd": "",
                                  "FilingStatusCd": ""
                              },
                              "FilingCode": "",
                              "LicenseDate": "1978-11-20",
                              "State": "GA",
                              "HadTrainingCourse": false,
                              "IsMilitary": false,
                              "MilitaryRank": "",
                              "HadDUIDWI": false,
                              "DriverCourseCompletedDate": "",
                              "CanInsureOperate": "",
                              "LicenseStatus": "Valid",
                              "IsGoodStudentDiscountApplicable": false,
                              "MaritalStatus": "S",
                              "Gender": "F",
                              "Violation": [],
                              "RelationToApplicant": "Insured"
                          }
                      }
                  ]
              }
          ]
      },
      "Rules": {
          "title": "Rules",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "Action",
              "MatchingRules"
          ],
          "additionalProperties": true,
          "properties": {
              "Action": {
                  "title": "Action",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "ReferToUW"
                  ]
              },
              "MatchingRules": {
                  "title": "MatchingRules",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "object",
                      "default": {},
                      "required": [
                          "Type",
                          "Description",
                          "Isfulfilled",
                          "Status",
                          "Remark",
                          "Reason"
                      ],
                      "additionalProperties": true,
                      "properties": {
                          "Type": {
                              "title": "Type",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "ReferToUW"
                              ]
                          },
                          "Description": {
                              "title": "Description",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Business structure is a Trust"
                              ]
                          },
                          "Isfulfilled": {
                              "title": "Isfulfilled",
                              "description": " ",
                              "type": "boolean",
                              "default": false,
                              "examples": [
                                  true
                              ]
                          },
                          "Status": {
                              "title": "Status",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  "Active"
                              ]
                          },
                          "Remark": {
                              "title": "Remark",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          },
                          "Reason": {
                              "title": "Reason",
                              "description": " ",
                              "type": "string",
                              "default": "",
                              "examples": [
                                  ""
                              ]
                          }
                      },
                      "examples": [{
                          "Type": "ReferToUW",
                          "Description": "Business structure is a Trust",
                          "Isfulfilled": true,
                          "Status": "Active",
                          "Remark": "",
                          "Reason": ""
                      }]
                  },
                  "examples": [
                      [{
                          "Type": "ReferToUW",
                          "Description": "Business structure is a Trust",
                          "Isfulfilled": true,
                          "Status": "Active",
                          "Remark": "",
                          "Reason": ""
                      }]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [{
              "Action": "ReferToUW",
              "MatchingRules": [{
                  "Type": "ReferToUW",
                  "Description": "Business structure is a Trust",
                  "Isfulfilled": true,
                  "Status": "Active",
                  "Remark": "",
                  "Reason": ""
              }]
          }]
      },
      "PreviousPolicies": {
          "title": "PreviousPolicies",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "IsPreviousPolicy",
              "PreviousPolicyNumber",
              "OtherCoverages",
              "IsPreviousClaims",
              "NoOfClaims",
              "TotalAmountClaimed"
          ],
          "additionalProperties": true,
          "properties": {
              "IsPreviousPolicy": {
                  "title": "IsPreviousPolicy",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              },
              "PreviousPolicyNumber": {
                  "title": "PreviousPolicyNumber",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "BCIH221023"
                  ]
              },
              "OtherCoverages": {
                  "title": "OtherCoverages",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "NA"
                  ]
              },
              "IsPreviousClaims": {
                  "title": "IsPreviousClaims",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              },
              "NoOfClaims": {
                  "title": "NoOfClaims",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              },
              "TotalAmountClaimed": {
                  "title": "TotalAmountClaimed",
                  "description": " ",
                  "type": "number",
                  "default": 0,
                  "examples": [
                      0
                  ]
              }
          },
          "examples": [{
              "IsPreviousPolicy": true,
              "PreviousPolicyNumber": "BCIH221023",
              "OtherCoverages": "NA",
              "IsPreviousClaims": true,
              "NoOfClaims": 0,
              "TotalAmountClaimed": 0
          }]
      },
      "Underwriting": {
          "title": "Underwriting",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "HaveAutoInsurance",
              "HaveSR22Fillings",
              "DriverLicenseSuspended",
              "DriverHaveTicketViolation",
              "HowLongWithCurrentInsuranceCompany",
              "AnyFaultClaim",
              "IsCarOlder"
          ],
          "additionalProperties": true,
          "properties": {
              "HaveAutoInsurance": {
                  "title": "HaveAutoInsurance",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      true
                  ]
              },
              "HaveSR22Fillings": {
                  "title": "HaveSR22Fillings",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "DriverLicenseSuspended": {
                  "title": "DriverLicenseSuspended",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "DriverHaveTicketViolation": {
                  "title": "DriverHaveTicketViolation",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              },
              "HowLongWithCurrentInsuranceCompany": {
                  "title": "HowLongWithCurrentInsuranceCompany",
                  "description": " ",
                  "type": "object",
                  "default": {},
                  "required": [
                      "Value",
                      "ValueType"
                  ],
                  "additionalProperties": true,
                  "properties": {
                      "Value": {
                          "title": "Value",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "2"
                          ]
                      },
                      "ValueType": {
                          "title": "ValueType",
                          "description": " ",
                          "type": "string",
                          "default": "",
                          "examples": [
                              "years"
                          ]
                      }
                  },
                  "examples": [{
                      "Value": "2",
                      "ValueType": "years"
                  }]
              },
              "AnyFaultClaim": {
                  "title": "AnyFaultClaim",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "No"
                  ]
              },
              "IsCarOlder": {
                  "title": "IsCarOlder",
                  "description": " ",
                  "type": "boolean",
                  "default": false,
                  "examples": [
                      false
                  ]
              }
          },
          "examples": [{
              "HaveAutoInsurance": true,
              "HaveSR22Fillings": false,
              "DriverLicenseSuspended": false,
              "DriverHaveTicketViolation": false,
              "HowLongWithCurrentInsuranceCompany": {
                  "Value": "2",
                  "ValueType": "years"
              },
              "AnyFaultClaim": "No",
              "IsCarOlder": false
          }]
      },
      "NonFunctional": {
          "title": "NonFunctional",
          "description": " ",
          "type": "object",
          "default": {},
          "required": [
              "LastSubmittedPage",
              "Milestones"
          ],
          "additionalProperties": true,
          "properties": {
              "LastSubmittedPage": {
                  "title": "LastSubmittedPage",
                  "description": " ",
                  "type": "string",
                  "default": "",
                  "examples": [
                      "/Commercial/Auto/Quote/BusinessInfo"
                  ]
              },
              "Milestones": {
                  "title": "Milestones",
                  "description": " ",
                  "type": "array",
                  "default": [],
                  "additionalItems": true,
                  "items": {
                      "title": "A",
                      "description": " ",
                      "type": "number",
                      "examples": [
                          0,
                          1,
                          2,
                          4
                      ]
                  },
                  "examples": [
                      [0, 1,
                          2,
                          4
                      ]
                  ],
                  "uniqueItems": false
              }
          },
          "examples": [{
              "LastSubmittedPage": "/Commercial/Auto/Quote/BusinessInfo",
              "Milestones": [
                  0,
                  1,
                  2,
                  4
              ]
          }]
      }
  },
  "examples": [
      {
          "id": "cd27210f-81c9-4d6e-a7d5-e0cd11431006",
          "AccountId": "Agent",
          "QuoteNumber": "ENGS1CA220009",
          "IsPolicyBind": false,
          "IsRenewed": false,
          "PolicyNumber": "SGIH3GA223885",
          "PolicyTerm": {
              "Value": 12,
              "ValueType": "Months"
          },
          "EffectiveDate": "2022-08-18",
          "ExpirationDate": "2023-08-18",
          "BindDate": "2022-08-18",
          "QuoteDate": "2022-08-18",
          "QuoteExpDate": "2022-08-18",
          "PolicyStatus": "Quote",
          "CurrentVersion": "1.0",
          "CurrentVersionEffectiveFrom": "2022-08-18",
          "RenewalTerm": 0,
          "Attributes": {
              "AppSource": "SalesForce",
              "Carrier": "ENGS",
              "Coverholder": "IH",
              "Lob": "CA",
              "State": "GA",
              "Product": "ENGS1CA",
              "RaterVersion": "2.0.0.0",
              "RenewalConfigurations": {
                  "BeforeForAgent": {
                      "Value": 30,
                      "ValueType": "Days"
                  },
                  "AfterForAgent": {
                      "Value": 30,
                      "ValueType": "Days"
                  },
                  "BeforeForUnderwriter": {
                      "Value": 60,
                      "ValueType": "Days"
                  },
                  "AfterForUnderwriter": {
                      "Value": 60,
                      "ValueType": "Days"
                  }
              },
              "QuoteValidity": {
                  "Value": 60,
                  "ValueType": "Days"
              },
              "IsTestPolicy": true
          }
      }
  ]
}
```
