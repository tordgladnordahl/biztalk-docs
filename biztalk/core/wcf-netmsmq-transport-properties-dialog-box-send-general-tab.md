---
title: "WCF-NetMsmq Transport Properties Dialog Box, Send, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netmsmq.transport.send.general"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, properties"
  - "properties, WCF-NetMsmq adapters"
ms.assetid: 94a307bf-9eeb-44ba-badf-6f450dde6f89
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetMsmq Transport Properties Dialog Box, Send, General Tab
Use the **General** tab to configure the endpoint address, the service identity, and the SOAP **Action** header for the WCF-NetMsmq send adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. Specify the fully qualified URI with the **net.msmq** scheme for this send port. **Note:**  The current version of the WCF-NetMsmq send adapter does not allow sending messages to a remote private queue. <br /><br /> Maximum length: 255<br /><br /> Default value: net.msmq://localhost/|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Endpoint identity** property differ according to the security configuration.<br /><br /> The default value is cleared.|  
|**Action**|Specify the **SOAPAction** HTTP header field for outgoing messages. This property can also be set through the message context property **WCF.Action** in a pipeline or orchestration. You can specify this value in two different ways: the single action format and the action mapping format. If you set this property in the single action format- for example, http://contoso.com/Svc/Op1- the **SOAPAction** header for outgoing messages is always set to the value specified in this property.<br /><br /> If you set this property in the action mapping format, the outgoing **SOAPAction** header is determined by the **BTS.Operation** context property. For example, if this property is set to the following XML format and the **BTS.Operation** property is set to Op1, the WCF send adapter uses http://contoso.com/Svc/Op1 for the outgoing **SOAPAction** header.<br /><br /> \<BtsActionMapping><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /><br /><br /> \</BtsActionMapping><br /><br /> If outgoing messages comes from an orchestration port, orchestration instances dynamically set the **BTS.Operation** property with the operation name of the port. If outgoing messages are routed with content-based routing, you can set the **BTS.Operation** property in pipeline components.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
  
## See Also  
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkID=75747)   
 [How to Configure a WCF-NetMsmq Send Port](../core/how-to-configure-a-wcf-netmsmq-send-port.md)   
 [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)   
 [Configuring Dynamic Send Ports Using WCF Adapters Context Properties](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)