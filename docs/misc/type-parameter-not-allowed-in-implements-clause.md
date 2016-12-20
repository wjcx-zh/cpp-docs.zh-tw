---
title: "&#39;Implements&#39; 子句中不允許類型參數 | Microsoft Docs"
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
  - "vbc32056"
  - "bc32056"
helpviewer_keywords: 
  - "BC32056"
ms.assetid: a62d773b-e878-4817-8638-da49849477d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; 子句中不允許類型參數
泛型類型中的 `Implements` 子句指定類型參數作為要實作的成員。  
  
 `Implements` 子句必須指定介面和成員。 它可以將類型參數傳遞給介面，但無法將它傳遞給成員，或使用它作為成員的名稱。  
  
 下列陳述式可能會產生此錯誤。  
  
```  
Class c1(Of t) Implements i1(Of t) Public Sub doSomething() Implements t End Class  
```  
  
 **錯誤 ID︰**BC32056  
  
### 更正這個錯誤  
  
-   指定介面名稱，以及 `Implements` 關鍵字後面之介面的正版成員。 您可以在適當時將類型參數傳遞給介面。  
  
    ```  
    Public Sub doSomething() Implements i1(Of t).doSomething  
    ```  
  
## 請參閱  
 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)