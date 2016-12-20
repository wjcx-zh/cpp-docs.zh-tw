---
title: "成員 &#39;&lt;成員名稱&gt;&#39; 與基底類型 &#39;&lt;基底類型名稱&gt;&#39; 中的成員 &#39;&lt;成員名稱&gt;&#39; 產生衝突，所以不應該宣告為 &#39;Overloads&#39; | Microsoft Docs"
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
  - "bc40021"
  - "vbc40021"
helpviewer_keywords: 
  - "BC40021"
ms.assetid: 2ec72726-ab0e-4545-9c1e-2409eb54482e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 成員 &#39;&lt;成員名稱&gt;&#39; 與基底類型 &#39;&lt;基底類型名稱&gt;&#39; 中的成員 &#39;&lt;成員名稱&gt;&#39; 產生衝突，所以不應該宣告為 &#39;Overloads&#39;
屬性或程序使用 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 關鍵字來重新宣告具有相同名稱的現有屬性或程序，但現有屬性或程序是在基底類別中。  
  
 多載可用於在同一個類別中定義屬性或程序的多個版本。 除非基底類別成員已指定[Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)，否則您無法定義基底類別成員的其他版本。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40021  
  
### 更正這個錯誤  
  
-   如果您想要定義基底類別成員的其他版本，並想要具有基底類別原始程式碼的存取權，請將 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 關鍵字加入基底類別定義中。  
  
-   如果您沒有基底類別原始程式碼的存取權，則無法多載衍生類別中的成員。 請移除 `Overloads` 關鍵字。  
  
-   如果您想要取代基底類別成員，而不是定義其他版本，請使用 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md) 關鍵字取代 `Overloads`。  
  
-   如果您想要透過衍生類別中的新成員來隱藏基底類別成員，請使用 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 關鍵字取代 `Overloads`。  
  
## 請參閱  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)