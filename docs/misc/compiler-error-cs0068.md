---
title: "編譯器錯誤 CS0068 | Microsoft Docs"
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
  - "CS0068"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0068"
ms.assetid: 9c9ac915-e12f-4ceb-8eb0-806790f11a09
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0068
'event': 介面中的事件不能有初始設定式  
  
 介面中的事件不能有初始設定式。 如需詳細資訊，請參閱[介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0068：  
  
```  
// CS0068.cs delegate void MyDelegate(); interface I { event MyDelegate d = new MyDelegate(M.f);   // CS0068 // try the following line instead // event MyDelegate d2; } class M { event MyDelegate d = new MyDelegate(M.f); public static void f() { } public static void Main() { } }  
```