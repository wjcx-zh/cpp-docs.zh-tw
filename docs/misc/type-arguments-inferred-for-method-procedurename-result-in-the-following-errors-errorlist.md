---
title: "方法 &#39;&lt;程序名稱&gt;&#39; 的推斷類型引數，導致下列錯誤：&lt;錯誤清單&gt; | Microsoft Docs"
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
  - "bc30954"
  - "vbc30954"
helpviewer_keywords: 
  - "BC30954"
ms.assetid: 796592c4-70b7-45be-9322-db09e9095d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;程序名稱&gt;&#39; 的推斷類型引數，導致下列錯誤：&lt;錯誤清單&gt;
泛型程序是在未提供任何類型引數的情況下所呼叫，而推斷的類型引數會導致一或多個條件約束違規。  
  
 通常，當您叫用泛型類型時，會針對泛型類型所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。 如果推斷的類型無法滿足一或多個類型參數條件約束，則編譯器會產生這個錯誤。  
  
 類型參數上的*「條件約束」*\(constraint\) 會限制可傳遞給它的類型引數。 例如，可能會將類型參數限制為可實作 <xref:System.IComparable%601> 介面的類別。 如需詳細資訊，請參閱 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)中的＜條件約束＞。  
  
 **錯誤 ID︰**BC30954  
  
### 更正這個錯誤  
  
-   請將類型引數提供給泛型程序，這樣編譯器就不需要推斷它們。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)