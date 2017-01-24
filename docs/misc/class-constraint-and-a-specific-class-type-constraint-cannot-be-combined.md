---
title: "無法合併 &#39;Class&#39; 條件約束和特定類別的類型條件約束 | Microsoft Docs"
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
  - "vbc32107"
  - "bc32107"
helpviewer_keywords: 
  - "BC32107"
ms.assetid: 218a7f0c-dd4f-4086-a52c-e8d581377e8b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法合併 &#39;Class&#39; 條件約束和特定類別的類型條件約束
條件約束清單同時包含 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 條件約束和已定義類別的名稱。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 您可以利用任意組合指定下列需求：  
  
-   類型引數必須實作一或多個介面  
  
-   類型引數最多只能繼承自一個類別  
  
-   類型引數必須公開建立程式碼可以存取的無參數建構函式 \(包含 `New` 條件約束\)  
  
 如果您未在條件約束清單中包含任何特定類別或介面，則可以指定下列其中一項以強制更一般的需求：  
  
-   類型引數必須是實值類型 \(包含 `Structure` 條件約束\)  
  
-   類型引數必須是參考類型 \(包含 `Class` 條件約束\)  
  
 您無法針對相同的類型參數同時指定 `Structure` 和 `Class`，並且無法多次指定其中一個。  
  
 **錯誤 ID︰**BC32107  
  
### 更正這個錯誤  
  
-   如果您想要以類型引數作為任何參考類型，請從條件約束清單中移除類別名稱。  
  
-   如果您想要讓類型引數繼承自指定的類別名稱，請從條件約束清單中移除 `Class` 關鍵字。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)