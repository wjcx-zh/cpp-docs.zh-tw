---
title: "沒有可存取的 &#39;&lt;泛型程序名稱&gt;&#39; 接受此類型引數數目 | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有可存取的 &#39;&lt;泛型程序名稱&gt;&#39; 接受此類型引數數目
陳述式會呼叫泛型程序，該程序具有多個多載版本，但沒有任何多載版本定義與呼叫中提供之類型引數數目相同數目的類型參數。  
  
 如果只有一個泛型版本，而呼叫時不需要類型引數，而且編譯器可以嘗試*類型推斷*。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜類型推斷＞。 不過，如果有多個泛型版本，編譯器無法在其中選擇，除非您提供類型引數。 如果您提供一個類型引數，則必須為其中一個多載版本所定義的每個類型參數提供類型引數。  
  
 **錯誤 ID︰**BC32118  
  
### 更正這個錯誤  
  
-   請決定您要呼叫哪個多載版本，然後提供適當數目的類型引數。  
  
## 請參閱  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)