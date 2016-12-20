---
title: "參數 &#39;&lt;參數名稱&gt;&#39; 在 &#39;&lt;方法名稱&gt;&#39; 中已經有符合的省略引數 | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 參數 &#39;&lt;參數名稱&gt;&#39; 在 &#39;&lt;方法名稱&gt;&#39; 中已經有符合的省略引數
程序呼叫在依位置省略某個引數之後，依名稱提供同一個引數；例如：  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **錯誤 ID︰**BC32021  
  
### 更正這個錯誤  
  
-   依位置提供引數，或移除省略引數的逗號。  
  
## 請參閱  
 [Passing Arguments by Position and by Name](../Topic/Passing%20Arguments%20by%20Position%20and%20by%20Name%20\(Visual%20Basic\).md)