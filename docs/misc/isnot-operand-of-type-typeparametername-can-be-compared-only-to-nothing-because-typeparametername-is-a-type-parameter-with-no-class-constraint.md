---
title: "&#39;&lt;類型參數名稱&gt;&#39; 類型的 &#39;IsNot&#39; 運算元只能與 &#39;Nothing&#39; 比較，因為 &#39;&lt;類型參數名稱&gt;&#39; 是沒有類別條件約束的類型參數 | Microsoft Docs"
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
  - "vbc32097"
  - "bc32097"
helpviewer_keywords: 
  - "BC32097"
ms.assetid: 50283a4b-70e3-4e59-9b9b-65e7cacf5ce1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型參數名稱&gt;&#39; 類型的 &#39;IsNot&#39; 運算元只能與 &#39;Nothing&#39; 比較，因為 &#39;&lt;類型參數名稱&gt;&#39; 是沒有類別條件約束的類型參數
如果定義類型參數，但其條件約束清單中沒有 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 關鍵字或特定類別名稱，則類型參數是作為 [IsNot Operator](../Topic/IsNot%20Operator%20\(Visual%20Basic\).md) 的運算元。  
  
 `IsNot` 會比較兩個參考類型，以判斷它們是否指向記憶體中的不同物件執行個體。 除非另一個運算元是 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)，否則它無法使用不是參考類型的運算元。  
  
 **錯誤 ID︰**BC32097  
  
### 更正這個錯誤  
  
-   如果您需要提供給這個類型參數的類型引數一律是參考類型，請將 `Class` 關鍵字或特定類別名稱加入類型參數的條件約束清單中。  
  
-   如果您不需要提供給這個類型參數的類型引數一律是參考類型，請將它從 `IsNot` 運算式中移除。 您無法使用 `IsNot` 運算子來比較它與其他參考類型。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)