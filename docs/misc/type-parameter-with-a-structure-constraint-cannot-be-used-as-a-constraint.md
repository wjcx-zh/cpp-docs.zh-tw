---
title: "具有 &#39;Structure&#39; 條件約束的類型參數不可以當做條件約束使用 | Microsoft Docs"
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
  - "vbc32114"
  - "bc32114"
helpviewer_keywords: 
  - "BC32114"
ms.assetid: 442b2048-9dc4-4223-bcfc-4d96bf8d14de
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 具有 &#39;Structure&#39; 條件約束的類型參數不可以當做條件約束使用
具有 `Structure` 條件約束的類型參數是用作另一個類型參數的條件約束。  
  
 `Structure` 條件約束需要傳遞給其類型參數的類型引數都是實值類型。 不過，無法實作或繼承實值類型，因此使用它作為條件約束 \(即需要另一種類型參數來實作它或繼承它\) 並沒有意義。  
  
 這種狀況之唯一有意義的解釋是類型引數必須是完全相同的類型。 如果是這種狀況，泛型類型只需要一個類型參數。  
  
 下列陳述式可能會產生這個錯誤。  
  
 `Class c1(Of t1 As Structure, t2 As t1)`  
  
 傳遞給 `t2` 的類型無法實作或繼承傳遞給 `t1` 的類型，因為傳遞給 `t1` 的類型必須是實值類型。  
  
 **錯誤 ID︰**BC32114  
  
### 更正這個錯誤  
  
-   從另一個類型參數的條件約束清單中，移除限制為 `Structure` 的類型參數。  
  
-   如果這兩個類型參數都需要相同的實值類型，請定義只有一個類型參數的泛型類型。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)