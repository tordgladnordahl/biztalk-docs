---
title: "MSBTS_ReceivePort.MgmtDbNameOverride Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb1235e3-b657-4618-a7cb-6361450f067d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceivePort.MgmtDbNameOverride Property (WMI)
Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string MgmtDbNameOverride = "";  
```  
  
## Remarks  
 This property is optional.  
  
 This property has a **Key** qualifier. Along with **Name** and **MgmtDbNameOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 123 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.