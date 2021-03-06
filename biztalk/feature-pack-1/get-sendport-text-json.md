---
title: "Get Sendport text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: bcd92a0d-3961-4bf7-bb83-dcfe03e0837d
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Sendport: text/json
## Get Sendport						
							
  Response Content Type: **text/json**				
  

  			
							
## Parameters							
							
							
							
Parameter|value  |Description  |Parameter Type|Data Type|							
---------|---------|---------|---------|---------							
**sendPortName** |(required)|Send port name|path|string|

##  Example Value
 
```
{
  "Name": "string",
  "Description": "string",
  "ApplicationName": "string",
  "IsDynamic": true,
  "IsTwoWay": true,
  "Status": "string",
  "CustomData": "string",
  "PrimaryTransport": {
    "Address": "string",
    "TransportType": "string",
    "TransportTypeData": "string",
    "SendHandler": "string",
    "RetryCount": 0,
    "RetryInterval": 0,
    "OrderedDelivery": true,
    "Schedule": {
      "ServiceWindowEnabled": true,
      "FromTime": "2017-04-23T12:05:46.017Z",
      "ToTime": "2017-04-23T12:05:46.017Z"
    }
  },
  "SecondaryTransport": {
    "Address": "string",
    "TransportType": "string",
    "TransportTypeData": "string",
    "SendHandler": "string",
    "RetryCount": 0,
    "RetryInterval": 0,
    "OrderedDelivery": true,
    "Schedule": {
      "ServiceWindowEnabled": true,
      "FromTime": "2017-04-23T12:05:46.017Z",
      "ToTime": "2017-04-23T12:05:46.017Z"
    }
  },
  "SendPipeline": "string",
  "SendPipelineData": "string",
  "ReceivePipeline": "string",
  "ReceivePipelineData": "string",
  "InboundTransforms": [
    "string"
  ],
  "OutboundTransforms": [
    "string"
  ],
  "Tracking": {
    "Body": {
      "BeforeSendPipeline": true,
      "AfterSendPipeline": true,
      "BeforeReceivePipeline": true,
      "AfterReceivePipeline": true
    },
    "Property": {
      "BeforeSendPipeline": true,
      "AfterSendPipeline": true,
      "BeforeReceivePipeline": true,
      "AfterReceivePipeline": true
    }
  },
  "EncryptionCert": {
    "CommonName": "string",
    "Thumbprint": "string"
  },
  "Filter": "string",
  "Priority": 0,
  "RouteFailedMessage": true,
  "OrderedDelivery": true,
  "StopSendingOnFailure": true
}
```

			
