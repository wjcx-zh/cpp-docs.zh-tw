---
title: "&#39;TryCast&#39; 運算元必須是具有類別條件約束的類型參數，但 &#39;&lt;類型參數名稱&gt;&#39; 沒有類別條件約束 | Microsoft Docs"
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
  - "BC30793"
  - "vbc30793"
helpviewer_keywords: 
  - "BC30793"
ms.assetid: a38a1da9-4413-4a69-a2ce-0b6d51c2c4ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TryCast&#39; 運算元必須是具有類別條件約束的類型參數，但 &#39;&lt;類型參數名稱&gt;&#39; 沒有類別條件約束
[TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md) 運算子是與不保證為參考類型的類型參數運算元搭配使用。  
  
 `TryCast` 僅操作於參考類型 \(例如類別或介面\)。 將類型參數傳遞為 `TryCast` 的引數時，必須將該類型參數限制為參考類型。 做法是在類型參數的條件約束清單中包括下列一個或多個項目：  
  
-   一個或多個介面名稱 \(類型引數必須實作所有介面\)  
  
-   最多一個類別名稱 \(類型引數必須繼承自它\)  
  
-   [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md) 條件約束 \(類型引數必須公開建立程式碼可以存取的無參數建構函式，因此它必須是類別\)  
  
-   [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 條件約束 \(類型引數必須是參考類型\)  
  
 **錯誤 ID︰**BC30793  
  
### 更正這個錯誤  
  
-   如果您需要將這個類型參數傳遞給 `TryCast`，請使用上述清單中的一個或多個條件約束來限制它。  
  
-   如果您無法要求類型參數僅接受參考類型，則無法搭配使用它與 `TryCast`。 您可以改為使用 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)