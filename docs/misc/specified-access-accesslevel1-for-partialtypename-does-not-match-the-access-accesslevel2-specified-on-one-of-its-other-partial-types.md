---
title: "&#39;&lt;部分類型名稱&gt;&#39; 的指定存取權 &#39;&lt;存取層級1&gt;&#39; 不符合它其他部分類型其中之一指定的存取權 &#39;&lt;存取層級2&gt;&#39; | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;部分類型名稱&gt;&#39; 的指定存取權 &#39;&lt;存取層級1&gt;&#39; 不符合它其他部分類型其中之一指定的存取權 &#39;&lt;存取層級2&gt;&#39;
在多個具有衝突存取層級規格的部分宣告中定義類別或結構。  
  
 當您分割數個部分宣告中類別或結構的定義時，編譯器會將類型視為其所有部分宣告的聯集。 這不只適用於成員，同時也適用於實作、繼承和存取層級。  
  
 在類別或結構定義中的存取層級不能混用。 即使是組合 `Protected Friend`，也只有當關鍵字在相同的宣告陳述式中是連續的時才被允許。  
  
 **錯誤 ID：**BC30925  
  
### 更正這個錯誤  
  
-   決定類別的存取層級應該為何，並移除所有衝突的存取層級規格。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)   
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)   
 [不在組建中：類別：物件的藍圖](http://msdn.microsoft.com/zh-tw/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)