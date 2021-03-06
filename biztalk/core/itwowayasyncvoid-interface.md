---
title: "ITwoWayAsyncVoid Interface | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d453d7ec-d49c-401d-b21f-0ffb28220fd1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ITwoWayAsyncVoid Interface
The **ITwoWayAsyncVoid** interface is used for the WCF one-way receive locations that do not support a transaction protocol, excluding the WCF-NetMsmq adapter. The WCF adapters asynchronously process messages incoming through this interface.  
  
> [!WARNING]
>  This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.  
  
## Interface Declaration  
  
```  
[ServiceContract(Namespace = http://www.microsoft.com/biztalk/2006/r2/wcf-adapter")]  
public interface ITwoWayAsyncVoid  
```  
  
## Public Methods  
  
|Method|Description|  
|------------|-----------------|  
|[ITwoWayAsyncVoid.BeginTwoWayMethod Method](../core/itwowayasyncvoid-begintwowaymethod-method.md)|Asynchronously processes messages incoming through the WCF one-way receive locations that do not support a transaction protocol, excluding the WCF-NetMsmq adapter.|  
|[ITwoWayAsyncVoid.EndTwoWayMethod Method](../core/itwowayasyncvoid-endtwowaymethod-method.md)|\<End> method corresponding to **BeginTwoWayMethod** for the asynchronous operation implementation.|  
|[ITwoWayAsyncVoid.BizTalkSubmit Method](../core/itwowayasyncvoid-biztalksubmit-method.md)|Causes the runtime to create WSDL operations in the metadata. This method should never get invoked|