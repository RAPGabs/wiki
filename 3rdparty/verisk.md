---
id: verisk
title: Verisk
---

VeRisk API is typically used to get vehicle informations like sizeclass,classificationtypes,driverinfo,etc using the business location address field in our DIEP2 application.We use the same plugin based hook approach for its integration with our GraphQl service.
This third party api is typically used with Commercial Auto businesses.But in  order to integrate it, we have a seperate JavaScript based code tranformation function intead of the JSONATA approach and the code for the same can be found in the pos-components package of our service.However, all the API related configurations are still maintained in the hookSchema file dumped on the blob storage.
In the hookSchema file, we just need to add the name of the integration service like for example,``AddBusinessDetails`` for veRisk.This function needs two arguments like:
- Policy Model
- Extra Parameter object from hookSchema

In return, this would provide us with the pre-populated vehicle informations mentioned above, and the the same payload is sent to the targeted GraphQl endpoint.One keynote to be observed here is that this has been used as a pre-hook since we need the Vehicle information page to be pre-filled if there's any data present on the VeRisks end , otherwise it would pass the payload as it is.


>![Business Information Page](../../static/img/docs/thirdparty/veRisk-businessinfo.png)
Business Information Page

>![Vehicle Information Page](../../static/img/docs/thirdparty/veRiskResult.png)
Vehicle Information Page