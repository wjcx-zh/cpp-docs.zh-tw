---
title: "無法從類型 &#39;type&#39; 選取 XML 子系元素 | Microsoft Docs"
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
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從類型 &#39;type&#39; 選取 XML 子系元素
已針對不是屬於類型 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument> 或 `IEnumerable(Of XElement)` 的物件參考 XML 子系。 如需詳細資訊，請參閱[XML Descendant Axis Property](../Topic/XML%20Descendant%20Axis%20Property%20\(Visual%20Basic\).md)。  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **錯誤 ID︰**BC36809  
  
### 更正這個錯誤  
  
-   請確定所參考子系元素的物件已強類型為 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XDocument> 或 `IEnumerable(Of XElement)`。 以下是一個範例：  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## 請參閱  
 [XML Descendant Axis Property](../Topic/XML%20Descendant%20Axis%20Property%20\(Visual%20Basic\).md)   
 [XML Axis Properties](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)