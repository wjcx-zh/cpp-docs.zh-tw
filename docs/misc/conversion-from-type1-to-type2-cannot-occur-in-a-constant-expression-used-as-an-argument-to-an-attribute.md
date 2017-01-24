---
title: "用作為屬性之引數的常數運算式中，不可進行從 &#39;&lt;類型1&gt;&#39; 到 &#39;&lt;類型2&gt;&#39; 的轉換。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 用作為屬性之引數的常數運算式中，不可進行從 &#39;&lt;類型1&gt;&#39; 到 &#39;&lt;類型2&gt;&#39; 的轉換。
用於屬性引數的運算式評估為與對應屬性參數的資料類型不同的資料類型，而且 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 不允許屬性引數的必要類型轉換。  
  
 屬性提供所套用項目的中繼資料，而且編譯器必須可以在編譯時期建構所有中繼資料。 因此，每個屬性都必須使用在編譯時期為常數的值，因此，每個屬性引數都必須評估為編譯時期常數值。  
  
 特定類型轉換無法產生在編譯時期為常數的值。 例如，將 `String` 轉換為 `Double` 或 `Date` 取決於執行階段的地區設定。 其他轉換 \(例如衍生類型陣列到 `Object` 陣列\) 會呈現各種問題，而不允許編譯器在屬性引數上允許它們。  
  
 **錯誤 ID︰**BC30934  
  
### 更正這個錯誤  
  
-   使用評估其資料類型與對應參數相同的運算式 \(由屬性所定義\)。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Const Statement](../Topic/Const%20Statement%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)