---
title: "&#39;NotOverridable&#39; 不能指定於不覆寫其他方法的方法 | Microsoft Docs"
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
  - "vbc31088"
  - "bc31088"
helpviewer_keywords: 
  - "BC31088"
ms.assetid: 0241197c-51fa-48b8-9a2a-4205d25641d3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NotOverridable&#39; 不能指定於不覆寫其他方法的方法
根據預設，屬性和方法是 `NotOverridable``NotOverridable` 修飾詞只能用於覆寫另一個屬性或方法的方法上。  
  
 **錯誤 ID︰**BC31088  
  
### 更正這個錯誤  
  
-   從不覆寫另一個成員的屬性和方法中，移除 `NotOverridable` 修飾詞。  
  
## 請參閱  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)   
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)