---
title: "編譯器錯誤 CS1517 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1517"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1517"
ms.assetid: 3b0201fb-8fab-4e6a-9ad9-f04c0de89517
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1517
前置處理器運算式無效  
  
 編譯器發現無效的前置處理器運算式。  
  
 如需詳細資訊，請參閱[前置處理器指示詞](../Topic/C%23%20Preprocessor%20Directives.md)。  
  
 下列範例顯示一些有效和無效的前置處理器運算式：  
  
```  
// CS1517.cs #if symbol      // OK #endif #if !symbol     // OK #endif #if (symbol)    // OK #endif #if true        // OK #endif #if false       // OK #endif #if 1           // CS1517 #endif #if ~symbol     // CS1517 #endif #if *           // CS1517 #endif class x { public static void Main() { } }  
```