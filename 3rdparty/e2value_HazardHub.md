---
id: e2valueHazardHub
title: E2Value & HazardHub
---

E2Value is an external api service by ProntoLite.It basically fetches us various details like property cost, construction type,etc.
While HazardHub typically gives us risk details like crimescore,brushzone info,earthquake details,heatsource details,constructiontype details,etc.
We have a seperate dataservices layer to access these informations in Cogitate.This dataservice needs an account information which we store in Account.xml and two seperate xslts each for e2value and hazardhub.These xslts have the transformation code along with the fields we want from the response bodies of these two APIs.In case a particular field is common , like Construction Type , then the preference is given to the response that is at later position in the Account.xml configuration.
One thing to remeber here is that all these files should be correct and provided to the infra team before setting up the account -
- Account.xml
- e2value xslt
- hazardhub xslt

Below is the sample Account setting for Account.xml-
```
<Account>
    <UserId>BNB</UserId>
    <Password>yyt@456uy@n</Password>
    <AccessKey>hdyvesjaci645bhjsk77</AccessKey>
    <Name>National Risk Solutions</Name>
    <Code>BNB</Code>
    <Environment>TEST</Environment>
    <GoogleAddressKey>AIzaSyCi9PjfqW2jLxpopznAzjxT73cMQZoVq9U</GoogleAddressKey>
    <ZillowZWSID>X1-ZWz195x76ukjd7_8jmj2</ZillowZWSID>
    <ResponseTime>45000</ResponseTime>
    <TotalRequest>1695000</TotalRequest>
    <PerDayRequest>10000</PerDayRequest>
    <Services>
      <Service>HazardHub</Service>
      <Service>E2ValueProntoLite</Service>
    </Services>
    <Status>A</Status>
    <EffectiveFrom>01/30/2020</EffectiveFrom>
    <EffectiveTo>11/30/9999</EffectiveTo>
</Account>
```
Now apart from this Account xml file, we have two seperate files as well which are basically the xslt transformation files for E2Value & HazrdHub APIs.This file is important for defining the fields we want according to our specific requirements.
Below is the sample-

```
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:ms="urn:schemas-microsoft-com:xslt"
                exclude-result-prefixes="ms"
>
  <xsl:output method="xml" omit-xml-declaration="yes" />
  <xsl:template match="/">
    <PropertyData>
      <calculatedvalue>
        <xsl:value-of select="response/Estimate/ReplacementCost/Cost"/>
      </calculatedvalue>
      <builtyear>
        <xsl:value-of select="response/Estimate/SquareFootage/YearBuilt/Value"/>
      </builtyear>
      <SqFeet>
        <xsl:value-of select="response/Estimate/SquareFootage/LivingAreaSqFt/Value"/>
      </SqFeet>
	  
	  <xsl:variable name="ConstructionType"
                    select="response/Estimate/BasicStructure/TypeOfConstruction/Value"/>
    </PropertyData>
  </xsl:template>
 </xsl:stylesheet>                
```
