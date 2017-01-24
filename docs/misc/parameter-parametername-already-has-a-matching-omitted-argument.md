---
title: "參數 &#39;&lt;參數名稱&gt;&#39; 已經有符合的省略引數 | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 參數 &#39;&lt;參數名稱&gt;&#39; 已經有符合的省略引數
程序呼叫在依位置省略某個引數之後，依名稱提供同一個引數。 以下是一個範例：  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **錯誤 ID︰**BC36566  
  
### 更正這個錯誤  
  
-   依位置提供引數，或移除省略引數的逗號。  
  
## 請參閱  
 [Passing Arguments by Position and by Name](../Topic/Passing%20Arguments%20by%20Position%20and%20by%20Name%20\(Visual%20Basic\).md)