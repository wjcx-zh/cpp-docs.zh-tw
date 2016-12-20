---
title: "無法從類型 &#39;type&#39; 中選取 XML 屬性 | Microsoft Docs"
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
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從類型 &#39;type&#39; 中選取 XML 屬性
類型不是 <xref:System.Xml.Linq.XElement> 或 `IEnumerable(Of XElement)` 的物件已參考 XML 屬性。 如需詳細資訊，請參閱[XML Attribute Axis Property](../Topic/XML%20Attribute%20Axis%20Property%20\(Visual%20Basic\).md)。  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **錯誤識別碼：**BC36808  
  
### 更正這個錯誤  
  
-   請確定所參考屬性的物件已強類型為 <xref:System.Xml.Linq.XElement> 或 `IEnumerable(Of XElement)`。 以下是一個範例：  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## 請參閱  
 [XML Attribute Axis Property](../Topic/XML%20Attribute%20Axis%20Property%20\(Visual%20Basic\).md)   
 [XML Axis Properties](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)