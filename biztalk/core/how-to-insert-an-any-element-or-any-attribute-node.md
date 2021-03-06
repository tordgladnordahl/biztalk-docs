---
title: "How to Insert an Any Element or Any Attribute Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cbfdc04-6c83-4639-82de-169b6f009a2e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Insert an Any Element or Any Attribute Node
BizTalk Editor supports two types of any nodes: **Any Element** and **Any Attribute**. These nodes allow you to create locations within your schema that correspond to locations within the corresponding instance messages where you do not know what elements or attributes will appear. For detailed information about how these nodes are interpreted when processing instance messages, refer directly to information about the XML Schema definition (XSD) language on the Web. For links to this information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
### To insert an Any Element node or an Any Attribute node  
  
1.  In the schema tree view, select the **Record** node into which you want to insert the **Any Element** node or the **Any Attribute** node.  
  
2.  On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Any Element** or **Any Attribute**, as appropriate.  
  
> [!IMPORTANT]
>  In this release of BizTalk Editor, setting the [Process Contents](../core/process-contents-node-property-of-all-schemas.md) property to **Lax** for **Any Element** or **Any Attribute** nodes does not work correctly. To pass validation on **Any Element** or **Any Attribute** nodes, set the property to **Skip**.  
  
> [!IMPORTANT]
>  To create a map that contains **Any Element** or **Any Attribute** nodes, you must use either the [Mass Copy](../core/mass-copy-functoid-reference.md) functoid or the [Scripting](../core/scripting-functoid-reference.md) functoid (with Inline XSLT or Inline XSLT Call Template) to perform the mapping for such nodes, or simply not map those nodes.  
  
## See Also  
 [Inserting Nodes into a Schema](../core/inserting-nodes-into-a-schema.md)