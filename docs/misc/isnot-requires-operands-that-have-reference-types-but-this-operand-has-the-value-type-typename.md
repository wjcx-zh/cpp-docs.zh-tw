---
title: "&#39;IsNot&#39; 需要有參考類型的運算元，但此運算元擁有實值類型 &#39;&lt;類型名稱&gt;&#39;。 | Microsoft Docs"
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
  - "bc31419"
  - "vbc31419"
helpviewer_keywords: 
  - "BC31419"
ms.assetid: c44d2936-8c07-443a-b320-ac2bfbc1e9ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;IsNot&#39; 需要有參考類型的運算元，但此運算元擁有實值類型 &#39;&lt;類型名稱&gt;&#39;。
運算式使用 [IsNot Operator](../Topic/IsNot%20Operator%20\(Visual%20Basic\).md) 並搭配至少一個實值類型的運算元。  
  
 `IsNot` 運算子會判斷這兩個物件參考是否參考不同的物件。 它會比較參考類型的指標值，搭配實值類型使用時沒有任何意義。  
  
 **錯誤 ID︰**BC31419  
  
### 更正這個錯誤  
  
-   如果您想要比較兩個實值類型的值，請使用 `=` 或 `<>` 比較運算子。  
  
-   如果您想要比較兩個參考類型的指標，請務必使用兩個運算元的物件參考。 您可以使用參考變數，或功能類似參考變數的項目，例如 [Me](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2) 關鍵字。  
  
## 請參閱  
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [How to: Test Whether Two Objects Are the Same](../Topic/How%20to:%20Test%20Whether%20Two%20Objects%20Are%20the%20Same%20\(Visual%20Basic\).md)