---
title: "未定義類型 &#39;&lt;類型名稱1&gt;&#39; 和 &#39;&lt;類型名稱2&gt;&#39; 的運算子 &#39;&lt;運算子名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc31080"
  - "bc31080"
helpviewer_keywords: 
  - "BC31080"
ms.assetid: d2f77450-2bf2-4b1e-b95f-dbc7878f2777
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 未定義類型 &#39;&lt;類型名稱1&gt;&#39; 和 &#39;&lt;類型名稱2&gt;&#39; 的運算子 &#39;&lt;運算子名稱&gt;&#39;
未定義類型 '\<類型名稱1\>' 和 '\<類型名稱2\>' 的運算子 '\<運算子名稱\>'。 請使用 'Is' 運算子比較兩個參考類型。  
  
 嘗試以不適用於所指定類型的方式來使用運算子。 使用 "\=" 運算子可能會導致這個錯誤，而非使用 `Is` 運算子來比較兩個物件。  
  
 **錯誤 ID︰**BC31080  
  
### 更正這個錯誤  
  
1.  請使用 `Is` 運算子比較兩個參考類型。  
  
2.  搭配使用 `Not` 運算子與 `Is` 運算子，來代表不相等。 例如:  
  
     [!code-vb[VbVbalrOOP#89](../misc/codesnippet/VisualBasic/operator-operatorname-is-not-defined-for-types-typename1-and-typename2_1.vb)]  
  
## 請參閱  
 [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md)   
 [\= Operator](../Topic/=%20Operator%20\(Visual%20Basic\).md)   
 [Not Operator](../Topic/Not%20Operator%20\(Visual%20Basic\).md)