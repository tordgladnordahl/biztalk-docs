---
title: "Child Delimiter Type (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Child Delimiter Type property [Flat File schemas]"
ms.assetid: 2ac3248a-e2d8-4fd6-b10e-feecb7428dc0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Child Delimiter Type (Node Property of Flat File Schemas)
Use the **Child Delimiter Type** property to configure, on a per-record basis, how an alternative child delimiter string will be expressed in the [Child Delimiter](../core/child-delimiter-node-property-of-flat-file-schemas.md) property and in the underlying XSD representation, or whether the default child delimiter string will be used.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
  
|Drop-down list choice|Description|  
|----------------------------|-----------------|  
|**Character**|Specifies that you will provide a child delimiter string as characters in the **Child Delimiter** property, which will be formatted as characters in the XSD representation of the schema.|  
|**Hexadecimal**|Specifies that you will provide the hexadecimal value ("0xNNNN") of a child delimiter string in the **Child Delimiter** property, which will be formatted as a hexadecimal value in the XSD representation of the schema.|  
|**Default Child Delimiter**|Specifies that the delimiter specified using the [Default Child Delimiter](../core/default-child-delimiter-node-property-of-flat-file-schemas.md) property will be used.|  
|**None**|Removes the corresponding annotation in the XSD representation of the schema, if any, specifying that there is no child delimiter for this **Record** node. If more than one child node is specified in the schema, this setting will result in a warning during compilation.|  
  
## Default Value  
 **None**, resulting in no annotation being added to the XSD representation of the schema.  
  
## XSD Persistence  
 As the value of the **child_delimiter_type** (="char", "hex", or "default") attribute of the **element/annotation/appinfo/recordInfo** annotation element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you have:  
  
-   Selected a **Record** node (including a root **Record** node) in BizTalk Editor  
  
-   Set the **Structure** property of the selected **Record** node to **Delimited**  
  
-   Configured the **Flat File Extension** option for the **Schema Editor Extensions** property of the **Schema** node  
  
 If you configure this property with a value of **Character** or **Hexadecimal**, then you can configure the **Child Delimiter** property in one of these two formats.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)