---
title: "編譯器錯誤 CS0506 | Microsoft Docs"
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
  - "CS0506"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0506"
ms.assetid: 1286957c-2505-4b5f-ade0-154ad5f09dc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0506
'function1': 無法覆寫繼承的成員 'function2'，因為其未標記為 "virtual"、"abstract" 或 "override"  
  
 已覆寫的方法未明確地標記為 **virtual**, **abstract** 或 `override`。  
  
 下列範例會產生 CS0506：  
  
```  
// CS0506.cs namespace MyNameSpace { abstract public class ClassX { public int i = 0; public int f() { return 0; } // Try the following definition for f() instead: // abstract public int f(); } public class ClassY : ClassX { public override int f()   // CS0506 { return 0; } public static int Main() { return 0; } } }  
```