---
title: "&#39;&lt;參數名稱&gt;&#39; 已經宣告為此方法的類型參數 | Microsoft Docs"
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
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;參數名稱&gt;&#39; 已經宣告為此方法的類型參數
泛型程序使用了與類型參數相同的名稱來定義一般參數或區域變數。  
  
 程序的每個參數 \(包括泛型程序的每個類型參數\) 都必須具有與所有其他參數不同的名稱。 由於程序參數會當做區域變數使用，因此程序內宣告的所有區域變數也必須具有與所有參數和類型參數不同的名稱。  
  
 **錯誤 ID︰**BC32089  
  
### 更正這個錯誤  
  
-   變更一般參數或區域變數的名稱。  
  
## 請參閱  
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Parameter List](../Topic/Parameter%20List%20\(Visual%20Basic\).md)