---
title: "無法推斷 &#39;If&#39; 運算子的第二個和第三個運算元之一般類型 | Microsoft Docs"
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
  - "vbc33106"
  - "bc33106"
helpviewer_keywords: 
  - "BC33106"
ms.assetid: 793eed88-a9f9-43e3-b657-c16795ecbbcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法推斷 &#39;If&#39; 運算子的第二個和第三個運算元之一般類型
無法推斷 'If' 運算子的第二個和第三個運算元之一般類型。 一個運算元必須要能夠擴展轉換成另一個運算元。  
  
 使用三個引數來呼叫 `If` 運算子時，在第二個與第三個引數之間必須進行擴展轉換。 例如，由於 `Integer` 與 `String` 之間沒有任一方向的擴展轉換，因此下列程式碼會造成這個錯誤。  
  
```vb#  
Dim divisor = 3  
' Not valid.  
' Console.WriteLine(If(divisor <> 0, number \ divisor, "Division by zero"))  
```  
  
 **錯誤 ID︰**BC33106  
  
### 更正這個錯誤  
  
-   如果可能的話，請在您的程式碼中提供其中一個運算元的明確轉換。  
  
-   使用不同的條件建構 \(例如 `If...Then...Else` 陳述式\)。  
  
## 請參閱  
 [If Operator](../Topic/If%20Operator%20\(Visual%20Basic\).md)   
 [If...Then...Else Statement](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)