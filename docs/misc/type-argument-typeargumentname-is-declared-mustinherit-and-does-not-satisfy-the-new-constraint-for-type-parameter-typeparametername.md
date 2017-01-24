---
title: "類型引數 &#39;&lt;類型引數名稱&gt;&#39; 宣告為 &#39;MustInherit&#39;，無法滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;New&#39; 條件約束。 | Microsoft Docs"
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
  - "vbc32082"
  - "BC32082"
helpviewer_keywords: 
  - "BC32082"
ms.assetid: 597e5944-a61b-4858-ada5-efb80b27f26b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型引數 &#39;&lt;類型引數名稱&gt;&#39; 宣告為 &#39;MustInherit&#39;，無法滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;New&#39; 條件約束。
泛型類型和當成類型引數的 `MustInherit` 類別一起叫用，而對應的類型參數和 `New` 條件約束一起宣告。  
  
 `New` 條件約束要求在對應的類型引數中傳遞的類型必須支援建立物件。 不過，*「抽象」*\(abstract\) 類別，也就是宣告為 `MustInherit` 的類別，不會公開任何建構函式，因為您無法從它建立任何物件。  
  
 **錯誤識別碼：**BC32082  
  
### 更正這個錯誤  
  
1.  如果用於類型引數的類別不必是抽象的，則從其宣告中移除 `MustInherit` 關鍵字。  
  
2.  如果用於類型引數的類別必須是抽象的，但不必用來建構泛型類型，則在類型引數中傳遞不同的類別。  
  
3.  如果對應的類型參數不必從傳遞給它的類型中建立任何物件，則從其宣告中移除 `New` 條件約束。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)