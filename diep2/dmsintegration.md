---
id: dmsIntegration
title: DMS Integration
---

DMS stands for Document Management System. All DIEP implementations are integrated with Cogitate DMS. Documents are pushed to DMS at different stages during the policy life cycle.
APIs allow applications to integrate with DMS. In POS application following APIs are used to integrate with DMS.

## 1) GetPolicyDocList

This endpoint is used to pull all documents for a particular policy.
<h3>Request</h3>
<table>
<tr>
<td>METHOD</td>
<td></td>
<td>GET</td>
</tr>
<tr>
<td colspan="3">Header</td>
</tr>
<tr>
<td>AUTHORIZATION</td>
<td>STRING</td>
<td>Specify basic Authorization in this format. Basic *Authorization Code* </td>
</tr>
<tr>
<td colspan="3">Query Parameters</td>
</tr>
<tr>
<td>carrierCode</td>
<td>STRING</td>
<td>Carrier Code of Policy</td>
</tr>
<tr>
<td>coverholderCode</td>
<td>STRING</td>
<td>Coverholder Code of Policy</td>
</tr>
<tr>
<td>lobCode</td>
<td>STRING</td>
<td>LOB Code of Policy</td>
</tr>
<tr>
<td>stateCode</td>
<td>STRING</td>
<td>State Code of Policy</td>
</tr>
<tr>
<td>referenceNumber</td>
<td>STRING</td>
<td>Reference Number of Policy. Can be quote number or policy number</td>
</tr>
</table>

**Sample Request**

https://uat.cogitate.us/DIEP2.DMS.API/api/GetPolicyDocList?carrierCode=ENGS&coverholderCode=MS&lobCode=CA&stateCode=IL&referenceNumber=QENGS220136&cloudBlobContainer=dms

**Sample Response**
```jsx
[
  {
    "CarrierCode": "ENGS",
    "CoverholderCode": "MS",
    "Lob": "CA",
    "State": "IL",
    "PolicyNumber": "ENGS1IL220215",
    "TransactionType": "Policy",
    "TransactionCount": "0",
    "PEffective": null,
    "TransactionDate": "2022-09-30",
    "EffectiveDate": null,
    "PolicyInfoId": "QENGS220136",
    "FileName": null,
    "DocumentType": "test_2022-10-22T10:20:46.560Z",
    "AgentId": null,
    "AgencyId": null,
    "AgencyName": null,
    "FormattedAddress": null,
    "InsuredName": null,
    "CreatedDateTime": null,
    "UserName": null,
    "BlobUri": "ENGSMS/CA/IL/QENGS220136/",
    "PolicyUri": null,
    "Uri": "https://uatdiep2.azure-api.net/dms/ENGSMS/CA/IL/QENGS220136/DigitalEdge Evolution 2.0.pptx",
    "ApplicationStatus": null,
    "AnnualPremium": null,
    "EffectivePremium": null,
    "RaterVersion": null,
    "InsuredEmailId": null,
    "EmailBody": null,
    "AppVersion": null,
    "MetaData": [],
    "File": null,
    "FileDataStream": null
  },
  {
    "CarrierCode": "ENGS",
    "CoverholderCode": "MS",
    "Lob": "CA",
    "State": "IL",
    "PolicyNumber": "ENGS1IL220215",
    "TransactionType": "Policy",
    "TransactionCount": "0",
    "PEffective": null,
    "TransactionDate": "2022-09-30",
    "EffectiveDate": null,
    "PolicyInfoId": "QENGS220136",
    "FileName": null,
    "DocumentType": "Check_2022-10-22T10:21:27.257Z",
    "AgentId": null,
    "AgencyId": null,
    "AgencyName": null,
    "FormattedAddress": null,
    "InsuredName": null,
    "CreatedDateTime": null,
    "UserName": null,
    "BlobUri": "ENGSMS/CA/IL/QENGS220136/",
    "PolicyUri": null,
    "Uri": "https://uatdiep2.azure-api.net/dms/ENGSMS/CA/IL/QENGS220136/Standard Estimation & Pricing.xlsx",
    "ApplicationStatus": null,
    "AnnualPremium": null,
    "EffectivePremium": null,
    "RaterVersion": null,
    "InsuredEmailId": null,
    "EmailBody": null,
    "AppVersion": null,
    "MetaData": [],
    "File": null,
    "FileDataStream": null
  }
]
```

<h3>Response</h3>
<table>
<tr>
<td>Uri</td>
<td>STRING</td>
<td>Link to download file</td>
</tr>
<tr>
<td>CarrierCode</td>
<td>STRING</td>
<td>Carrier Code set metadata of the file</td>
</tr>
<tr>
<td>CoverholderCode</td>
<td>STRING</td>
<td>Coverholder Code set metadata of the file</td>
</tr>
<tr>
<td>Lob</td>
<td>STRING</td>
<td>Lob set metadata of the file</td>
</tr>
<tr>
<td>State</td>
<td>STRING</td>
<td>State set metadata of the file</td>
</tr>
<tr>
<td>PolicyNumber</td>
<td>STRING</td>
<td>PolicyNumber set metadata of the file</td>
</tr>
<tr>
<td>TransactionType</td>
<td>STRING</td>
<td>Transaction Type set metadata of the file</td>
</tr>
<tr>
<td>TransactionCount</td>
<td>STRING</td>
<td>Transaction Count set metadata of the file</td>
</tr>
<tr>
<td>PEffective</td>
<td>STRING</td>
<td>PEffective set metadata of the file</td>
</tr>
<tr>
<td>TransactionDate</td>
<td>STRING</td>
<td>Transaction Date set metadata of the file</td>
</tr>
<tr>
<td>EffectiveDate</td>
<td>STRING</td>
<td>Effective Date set metadata of the file</td>
</tr>
<tr>
<td>PolicyInfoId</td>
<td>STRING</td>
<td>PolicyInfoId set metadata of the file</td>
</tr>
<tr>
<td>FileName</td>
<td>STRING</td>
<td>FileName set metadata of the file</td>
</tr>
<tr>
<td>DocumentType</td>
<td>STRING</td>
<td>DocumentType set metadata of the file</td>
</tr>
<tr>
<td>AgentId</td>
<td>STRING</td>
<td>AgentId set metadata of the file</td>
</tr>
<tr>
<td>AgencyId</td>
<td>STRING</td>
<td>AgencyId set metadata of the file</td>
</tr>
<tr>
<td>FormattedAddress</td>
<td>STRING</td>
<td>FormattedAddress set metadata of the file</td>
</tr>
<tr>
<td>InsuredName</td>
<td>STRING</td>
<td>InsuredName set metadata of the file</td>
</tr>
<tr>
<td>CreatedDateTime</td>
<td>STRING</td>
<td>CreatedDateTime set metadata of the file</td>
</tr>
<tr>
<td>UserName</td>
<td>STRING</td>
<td>UserName set metadata of the file</td>
</tr>
<tr>
<td>BlobUri</td>
<td>STRING</td>
<td>BlobUri of the file</td>
</tr>
<tr>
<td>PolicyUri</td>
<td>STRING</td>
<td>PolicyUri of the file</td>
</tr>
<tr>
<td>ApplicationStatus</td>
<td>STRING</td>
<td>ApplicationStatus set metadata of the file</td>
</tr>
<tr>
<td>AnnualPremium</td>
<td>STRING</td>
<td>AnnualPremium set metadata of the file</td>
</tr>
<tr>
<td>EffectivePremium</td>
<td>STRING</td>
<td>EffectivePremium set metadata of the file</td>
</tr>
<tr>
<td>RaterVersion</td>
<td>STRING</td>
<td>RaterVersion set metadata of the file</td>
</tr>
<tr>
<td>InsuredEmailId</td>
<td>STRING</td>
<td>InsuredEmailId set metadata of the file</td>
</tr>
<tr>
<td>EmailBody</td>
<td>STRING</td>
<td>EmailBody set metadata of the file</td>
</tr>
<tr>
<td>AppVersion</td>
<td>STRING</td>
<td>AppVersion set metadata of the file</td>
</tr>
<tr>
<td>coverholderCode</td>
<td>STRING</td>
<td>Carrier Code set metadata of the file</td>
</tr>
<tr>
<td>MetaData</td>
<td>STRING</td>
<td>MetaData of the file</td>
</tr>
<tr>
<td>File</td>
<td>STRING</td>
<td>File</td>
</tr>
<tr>
<td>FileDataStream</td>
<td>STRING</td>
<td>File Stream</td>
</tr>
</table>

## 2) CreateDocument

API helps in moving document to dms. 

<h3>Request</h3>
<table>
<tr>
<td>METHOD</td>
<td></td>
<td>POST</td>
</tr>
<tr>
<td colspan="3">Header</td>
</tr>
<tr>
<td>AUTHORIZATION</td>
<td>STRING</td>
<td>Specify basic Authorization in this format. Basic *Authorization Code* </td>
</tr>
<tr>
<td colspan="3">BODY</td>
</tr>
<tr>
<td>PolicyInfoId</td>
<td>STRING</td>
<td>PolicyInfoId of Policy</td>
</tr>
<tr>
<td>PolicyNumber</td>
<td>STRING</td>
<td>PolicyNumber of Policy</td>
</tr>
<tr>
<td>DocumentType</td>
<td>STRING</td>
<td>Type of Policy</td>
</tr>
<tr>
<td>CarrierCode</td>
<td>STRING</td>
<td>Carrier Code of Policy</td>
</tr>
<tr>
<td>CoverholderCode</td>
<td>STRING</td>
<td>Coverholder Code of Policy</td>
</tr>
<tr>
<td>Lob</td>
<td>STRING</td>
<td>Lob Code of Policy</td>
</tr>
<tr>
<td>State</td>
<td>STRING</td>
<td>State Code of Policy</td>
</tr>
<tr>
<td>TransactionCount</td>
<td>STRING</td>
<td>TransactionCount of Policy</td>
</tr>
<tr>
<td>TransactionType</td>
<td>STRING</td>
<td>TransactionType Code of Policy</td>
</tr>
<tr>
<td>TransactionDate</td>
<td>STRING</td>
<td>TransactionDate of Policy</td>
</tr>
<tr>
<td>Filename</td>
<td>STRING</td>
<td>File Object</td>
</tr>
<tr>
<td>Applicationstatus</td>
<td>STRING</td>
<td>Applicationstatus of Policy</td>
</tr>
</table>

<h3>Response</h3>

Response is a boolean response in case of success. Otherwise it will return 500 status code.

**Sample Request**

```jsx
{
  "PolicyInfoId": "QENGS220135",
  "PolicyNumber": "ENGS1IL220214",
  "DocumentType": "ff_2022-10-22T11:01:00.907Z",
  "CarrierCode": "ENGS",
  "CoverholderCode": "MS",
  "Lob": "CA",
  "State": "IL",
  "TransactionCount": "0",
  "TransactionType": "Policy",
  "TransactionDate": "2022-09-30",
  "Filename": "DigitalEdge Evolution 2.0.pptx",
  "Applicationstatus": "Policy In Force-Bind"
}
```

***Sample Response***
```jsx
true
```

