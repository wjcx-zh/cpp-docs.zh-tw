---
title: "無法從委派 &#39;&lt;委派名稱&gt;&#39; 推斷方法 &#39;&lt;程序名稱&gt;&#39; 的類型引數 | Microsoft Docs"
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
  - "vbc30952"
  - "bc30952"
helpviewer_keywords: 
  - "BC30952"
ms.assetid: 5eb804ce-2e93-4668-b655-7fe00815e552
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法從委派 &#39;&lt;委派名稱&gt;&#39; 推斷方法 &#39;&lt;程序名稱&gt;&#39; 的類型引數
指派陳述式使用 `AddressOf` 將泛型程序的位址指派給委派，但未將任何類型引數提供給泛型程序。  
  
 通常，當您叫用泛型類型時，會針對泛型類型所定義的每個類型參數提供類型引數。 如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。 如果內容未提供足夠的資訊讓編譯器推斷類型，則會產生錯誤。  
  
 **錯誤 ID︰**BC30952  
  
### 更正這個錯誤  
  
-   在 `AddressOf` 運算式中指定泛型程序的類型引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)