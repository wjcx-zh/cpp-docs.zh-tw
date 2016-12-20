---
title: "無法從類型 &#39;type&#39; 選取 XML 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36807"
  - "bc36807"
helpviewer_keywords: 
  - "BC36807"
ms.assetid: 01c19899-2b44-41e9-a99c-35edfa0deaf1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從類型 &#39;type&#39; 選取 XML 項目
已針對類型不是 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument> 或 `IEnumerable(Of XElement)` 的物件，參考 XML 子項目。 如需詳細資訊，請參閱[XML Child Axis Property](../Topic/XML%20Child%20Axis%20Property%20\(Visual%20Basic\).md)。  
  
```vb#  
' Generates an error. Dim var = "sample text".<child>  
```  
  
 **錯誤 ID︰**BC36807  
  
### 更正這個錯誤  
  
-   請確定所參考屬性的物件已強類型為 <xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XDocument> 或 `IEnumerable(Of XElement)`。 以下是一個範例：  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem.<child>  
    ```  
  
## 請參閱  
 [XML Child Axis Property](../Topic/XML%20Child%20Axis%20Property%20\(Visual%20Basic\).md)   
 [XML Axis Properties](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)