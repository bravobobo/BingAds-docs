---
title: Date Data Object - Campaign Management
ms.service: bing-ads-campaign-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Represents a date.
---
# Date Data Object - Campaign Management
Represents a date.

## Syntax
```xml
<xs:complexType name="Date" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:sequence>
    <xs:element name="Day" type="xs:int" />
    <xs:element name="Month" type="xs:int" />
    <xs:element name="Year" type="xs:int" />
  </xs:sequence>
</xs:complexType>
```

## <a name="elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="day"></a>Day|Specifies the day of the month.<br/><br/>**Add:** Required<br/>**Update:** Required|**int**|
|<a name="month"></a>Month|Specifies the month.<br/><br/>**Add:** Required<br/>**Update:** Required|**int**|
|<a name="year"></a>Year|Specifies the year.<br/><br/>**Add:** Required<br/>**Update:** Required|**int**|

## Requirements
Service: [CampaignManagementService.svc v12](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v12/CampaignManagementService.svc)  
Namespace: https\://bingads.microsoft.com/CampaignManagement/v12  

## Used By
[AdGroup](adgroup.md)  
[Experiment](experiment.md)  
[Schedule](schedule.md)  
