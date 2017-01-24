---
title: "&#39;MustInherit&#39; 不可針對部分類型 &#39;&lt;部分類型名稱&gt;&#39; 指定，因為它無法與針對其他部分類型指定的 &#39;NotInheritable&#39; 結合。 | Microsoft Docs"
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
  - "vbc30926"
  - "BC30926"
helpviewer_keywords: 
  - "BC30926"
ms.assetid: 59a0b5d9-f53c-4234-88f4-dfc66342f143
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustInherit&#39; 不可針對部分類型 &#39;&lt;部分類型名稱&gt;&#39; 指定，因為它無法與針對其他部分類型指定的 &#39;NotInheritable&#39; 結合。
類別是在多個部分宣告中定義，其中一個指定 `MustInherit`，另一個指定 `NotInheritable`。  
  
 當您分割數個部分宣告中的類別定義時，編譯器會將類別視為其所有部分宣告的聯集。 這不只適用於成員，同時也適用於實作、繼承和存取層級。  
  
 類別不能同時為*「抽象」*\(abstract\) 和*「密封」*\(sealed\)，亦即它不能同時要求和禁止繼承。 因此，同一類別無法同時指定 `MustInherit` 和 `NotInheritable`。  
  
 **錯誤識別碼：**BC30926  
  
### 更正這個錯誤  
  
-   決定類別應該要求繼承、禁止繼承，或兩者皆非，並移除對決策不合適的關鍵字。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)