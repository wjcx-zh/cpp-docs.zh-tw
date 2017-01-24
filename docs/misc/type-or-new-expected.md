---
title: "必須是類型或 &#39;New&#39; | Microsoft Docs"
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
  - "vbc32092"
  - "bc32092"
helpviewer_keywords: 
  - "BC32092"
ms.assetid: b3041c1d-837c-4d58-bbb4-5c46f227b66d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是類型或 &#39;New&#39;
泛型類型宣告中的類型參數引入了具有 `As` 關鍵字的條件約束清單，但未指定有效的條件約束。  
  
 類型參數的條件約束必須是有效的類別或介面，或是關鍵字 `Class`、`Structure` 或 `New` 之一。 如果指定的條件約束無效或沒有指定任何條件約束，則編譯器會產生這個錯誤。  
  
 **錯誤 ID︰**BC32092  
  
### 更正這個錯誤  
  
1.  決定要如何限制類型參數，並在條件約束清單中指定適當的條件約束。  
  
2.  如果您希望類型參數受到類別或介面的條件約束，請確定該條件約束的拼字正確無誤。  
  
3.  記得使用逗號來分隔單一類型參數的多個條件約束，並使用大括號 \(`{ }`\) 來括住條件約束清單。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [類別 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)