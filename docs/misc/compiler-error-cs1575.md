---
title: "編譯器錯誤 CS1575 | Microsoft Docs"
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
  - "CS1575"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1575"
ms.assetid: 76a9c57c-8f79-482e-9ae8-c70e8f199dd7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1575
stackalloc 運算式在類型之後需要有 \[\]  
  
 要求的配置大小與 [stackalloc](../Topic/stackalloc%20\(C%23%20Reference\).md)，必須在方括號中指定。  
  
 下例會產生 CS1575：  
  
```  
// CS1575.cs // compile with: /unsafe public class MyClass { unsafe public static void Main() { int *p = stackalloc int (30);   // CS1575 // try the following line instead // int *p = stackalloc int [30]; } }  
```