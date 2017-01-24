---
title: "類型參數 &#39;&lt;類型參數名稱1&gt;&#39; 必須擁有 &#39;New&#39; 條件約束或 &#39;Structure&#39; 條件約束，才能滿足類型參數 &#39;&lt;類型參數名稱2&gt;&#39; 的 &#39;New&#39; 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數 &#39;&lt;類型參數名稱1&gt;&#39; 必須擁有 &#39;New&#39; 條件約束或 &#39;Structure&#39; 條件約束，才能滿足類型參數 &#39;&lt;類型參數名稱2&gt;&#39; 的 &#39;New&#39; 條件約束
陳述式會建構泛型類型，而泛型類型傳遞不一定要滿足 `New` 條件約束的類型參數。  
  
 `New` 條件約束表示提供給該類型參數的類型引數必須公開從中建立物件之程式碼可存取的無參數建構函式。 所有實值類型都有無參數建構函式，但並非所有參考類型都有無參數建構函式。 因此，`Structure` 條件約束滿足 `New` 條件約束，但 `Class` 條件約束 \(或類別或介面名稱\) 則否。  
  
 下列陳述式可能會產生此錯誤。  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 類別 `c2` 從 `c1` 建立物件時，類型參數 `u` 未滿足類型參數 `t` 的 `New` 條件約束。  
  
 **錯誤 ID︰**BC32084  
  
### 更正這個錯誤  
  
-   如果要傳遞給泛型類型的類型參數可以滿足 `Structure` 或 `New` 條件約束，則請將適當的條件約束加入其定義中。  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   如果類型參數無法滿足 `Structure` 或 `New` 條件約束，則請不要將它傳遞給泛型類型。 您必須傳遞其他項目作為類型引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [類別 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)