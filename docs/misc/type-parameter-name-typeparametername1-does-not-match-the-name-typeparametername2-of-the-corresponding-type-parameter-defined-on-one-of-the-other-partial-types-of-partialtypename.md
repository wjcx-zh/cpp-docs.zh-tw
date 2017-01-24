---
title: "對於 &#39;&lt;部分類型名稱&gt;&#39; 的某個其他部分類型所定義之對應類型參數的 &#39;&lt;類型參數名稱2&gt;&#39; 名稱而言，類型參數名稱 &#39;&lt;類型參數名稱1&gt;&#39; 不相符。 | Microsoft Docs"
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
  - "vbc30931"
  - "bc30931"
helpviewer_keywords: 
  - "BC30931"
ms.assetid: 01b053c3-d1b5-4e69-b908-3d5cfc73913b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 對於 &#39;&lt;部分類型名稱&gt;&#39; 的某個其他部分類型所定義之對應類型參數的 &#39;&lt;類型參數名稱2&gt;&#39; 名稱而言，類型參數名稱 &#39;&lt;類型參數名稱1&gt;&#39; 不相符。
在多個具有衝突類型參數規格的部分宣告中定義泛型類別或結構。  
  
 當您分割數個部分宣告中類別或結構的定義時，編譯器會將類型視為其所有部分宣告的聯集。 這不只適用於成員，同時也適用於實作、繼承和存取層級。  
  
 您無法針對泛型類別或結構定義中的任何類型參數指定多個名稱。  
  
 **錯誤 ID︰**BC30931  
  
### 更正這個錯誤  
  
-   決定類型參數應該要有的名稱，並在每個部分宣告中使用相同的名稱。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)   
 [不在組建中：類別：物件的藍圖](http://msdn.microsoft.com/zh-tw/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)