---
title: "編譯器錯誤 CS0242 | Microsoft Docs"
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
  - "CS0242"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0242"
ms.assetid: bc86a5a4-89c1-4de4-a874-4dd4cbf592c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0242
在 Void 指標上未定義有問題的作業  
  
 不允許遞增 void 指標。 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0242：  
  
```  
// CS0242.cs // compile with: /unsafe class TestClass { public unsafe void Test() { void * p = null; p++;   // CS0242, incrementing a void pointer not allowed } public static void Main() { } }  
```