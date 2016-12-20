---
title: "傳遞至方法 &#39;&lt;泛型程序名稱&gt;&#39; 的類型引數數目不正確 | Microsoft Docs"
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
  - "bc30951"
  - "vbc30951"
helpviewer_keywords: 
  - "BC30951"
ms.assetid: 84c2f0cb-5706-4b4e-967c-0ca35a20913c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 傳遞至方法 &#39;&lt;泛型程序名稱&gt;&#39; 的類型引數數目不正確
呼叫泛型程序時所使用的類型引數數目，與所定義的類型參數數目不符。  
  
 **錯誤 ID︰**BC30951  
  
### 更正這個錯誤  
  
-   針對定義給泛型程序的每個類型參數，各提供一個類型引數。  
  
     \-或\-  
  
-   完全不使用類型引數來呼叫泛型程序，並讓編譯器嘗試推斷類型引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)