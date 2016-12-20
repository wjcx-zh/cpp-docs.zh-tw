---
title: "編譯器錯誤 CS0529 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0529"
ms.assetid: 61de8086-f991-455c-b009-bb8cd05f34bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0529
繼承的介面 'interface1' 造成 'interface2' 介面階層架構中出現循環  
  
 [介面](../Topic/interface%20\(C%23%20Reference\).md)的繼承清單包含本身的直接或間接參考。 介面無法繼承自本身。  
  
 下列範例會產生 CS0529：  
  
```  
// CS0529.cs namespace x { public interface a { } public interface b : a, c { } public interface c : b   // CS0529, b inherits from c { } }  
```