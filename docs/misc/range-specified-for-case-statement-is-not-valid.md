---
title: "&#39;Case&#39; 陳述式的指定範圍無效 | Microsoft Docs"
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
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; 陳述式的指定範圍無效
為 `Case` 陳述式指定的範圍無效。  
  
 當您比較相同的運算式與數個不同的值時，可以使用 `Select...Case` 陳述式來代替 `If...Then...Else` 陳述式。 雖然 `If` 和 `ElseIf` 陳述式可以評估每個陳述式中的不同運算式，但是 `Select` 陳述式只會評估單一運算式一次，然後使用它來進行每次比較。 每個 `Case` 陳述式都可以包含多個值、某範圍的值，或值與比較運算子的組合。  
  
 **錯誤 ID︰**BC40052  
  
### 更正這個錯誤  
  
-   修改範圍，使其包括所有值，或使用 `Case Else` 陳述式來捕捉未定義的值。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)   
 [Decision Structures](../Topic/Decision%20Structures%20\(Visual%20Basic\).md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)