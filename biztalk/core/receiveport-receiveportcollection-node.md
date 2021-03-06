---
title: "ReceivePort (ReceivePortCollection Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ReceivePort node [binding file]"
ms.assetid: 30ae9cef-4e0f-42ca-ac45-fe1fabdfc7c5
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ReceivePort (ReceivePortCollection Node)
The ReceivePort node of the ReceivePortCollection node of a binding file contains specific information about a receive port that is exported with the binding file.  
  
## Nodes in the ReceivePort node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the receive port.|Not required|Default value: empty|  
|IsTwoWay|Attribute|xs:boolean|Specifies whether the receive port is one way or is request-response (two way).|Required|Default value: none<br /><br /> Possible values are documented in [MSBTS_SendPort.IsTwoWay Property (WMI)](../core/msbts-sendport-istwoway-property-wmi.md)|  
|BindingOption|Attribute|xs:int|Specifies the type of binding for the orchestration port.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.BindingType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.bindingtype.aspx) enumeration.|  
|Description|Element|xs:string|Specifies a description for the receive port.|Required|Default value: empty|  
|[ReceiveLocations](../core/receivelocations-receiveport-node.md)|Record|ArrayOfReceiveLocation (ComplexType)|Container node for the receive locations associated with this receive port.|Not required.|Default value: none|  
|[TransmitPipeline (ReceivePort Node)](../core/transmitpipeline-receiveport-node.md)|Record|PipelineRef (ComplexType)|Specifies the send pipeline associated with the receive port if the receive port is a two way receive port.|Not required|Default value: none|  
|SendPipelineData|Element|xs:string|Specifies the custom configuration specific to this instance of the usage of the pipeline.|Not required|Default value: empty.|  
|Authentication|Element|xs:int|Specifies an enumeration value indicating whether authentication is needed at this receive port.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.AuthenticationType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.authenticationtype.aspx) enumeration.|  
|Tracking|Element|xs:int|Specifies the level of document tracking for the receive port|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.TrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.trackingtypes.aspx) enumeration.|  
|[Transforms (ReceivePort Node)](../core/transforms-receiveport-node.md)|Record|ArrayOfTransform (ComplexType)|Specifies the collection of inbound transforms of a one way receive port.|Not required|Default value: none|  
|[OutboundTransforms](../core/outboundtransforms-receiveport-node.md)|Record|ArrayOfTransform (ComplexType)|Specifies the collection of outbound transforms to apply to documents on a two-way receive port|Not required|Default value: none|  
|RouteFailedMessage|Element|xs:boolean|Specifies whether or not failed messages are routed to failed message subscribers.|Required|Default value: none<br /><br /> Possible values are documented in [MSBTS_SendPort.RouteFailedMessage Property (WMI)](../core/msbts-sendport-routefailedmessage-property-wmi.md)|  
|ApplicationName|Element|xs:string|Specifies the name of the application associated with the receive port.|Required|Default value: empty<br /><br /> Possible values are documented in [ISSOMapping Interface (COM)](../core/issomapping-interface-com.md)|