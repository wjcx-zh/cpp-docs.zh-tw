---
title: "有引號的屬性值中不能出現運算式 | Microsoft Docs"
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
  - "bc31155"
  - "vbc31155"
helpviewer_keywords: 
  - "BC31155"
ms.assetid: ed3e618e-de94-4e4e-afaf-72b11073fb1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 有引號的屬性值中不能出現運算式
有引號的屬性值中不能出現運算式。 請嘗試移除引號。  
  
 引號內包含了 XML 常值之屬性值的內嵌運算式。  
  
 **錯誤 ID︰**BC31155  
  
### 更正這個錯誤  
  
-   請從屬性值移除分隔引號。 以下是一個範例：  
  
    ```vb#  
    ' Generates an error. Dim elem = <outer attr="<%= value %>" /> ' Does not generate an error. Dim elem = <outer attr=<%= value %> />  
    ```  
  
## 請參閱  
 [Embedded Expressions in XML](../Topic/Embedded%20Expressions%20in%20XML%20\(Visual%20Basic\).md)   
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)