---
title: "項目名稱不能使用 &#39;xmlns&#39; 前置字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31189"
  - "bc31189"
helpviewer_keywords: 
  - "BC31189"
ms.assetid: 88716bb5-6766-4180-b2ed-1d1bee0ff7a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 項目名稱不能使用 &#39;xmlns&#39; 前置字元
使用 XML 命名空間前置字元 `xmlns` 指定了 XML 元素常值。 例如:  
  
```vb#  
Dim elem = <xmlns:ElementName>  
```  
  
 XML 1.0 規格會將 `xmlns` 識別為保留字。  
  
 **錯誤 ID︰**BC31189  
  
### 更正這個錯誤  
  
-   將 XML 命名空間前置字元變更為有效值，或移除前置字元。  
  
## 請參閱  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [Imports Statement \(XML Namespace\)](../Topic/Imports%20Statement%20\(XML%20Namespace\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)