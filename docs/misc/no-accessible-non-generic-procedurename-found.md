---
title: "找不到可存取的非泛型 &#39;&lt;程序名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 找不到可存取的非泛型 &#39;&lt;程序名稱&gt;&#39;
陳述式所呼叫的程序具有多個多載版本，但所有多載版本都是泛型，而且呼叫未提供類型引數。  
  
 如果只有一個泛型版本，而呼叫時未使用類型引數，則編譯器可以嘗試*「類型推斷」*\(type inference\)。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜類型推斷＞。 不過，如果有多個泛型版本，編譯器無法在其中選擇，除非您提供類型引數。 如果您提供一個類型引數，則必須為其中一個多載版本所定義的每個類型參數提供類型引數。  
  
 **錯誤 ID︰**BC32117  
  
### 更正這個錯誤  
  
-   呼叫具有類型引數清單的程序。  
  
## 請參閱  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)