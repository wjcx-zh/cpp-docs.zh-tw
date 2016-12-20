---
title: "編譯器錯誤 CS1675 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1675"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1675"
ms.assetid: add10021-f751-45c7-addc-0f73fa4a267c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1675
列舉不能有類型參數  
  
 若要解決這個錯誤，請從 `enum` 宣告中移除類型參數。  
  
## 範例  
 下列範例會產生 CS1675：  
  
```  
// CS1675.cs enum E<T>  // CS1675 { } class CMain { public static void Main() { } }  
```