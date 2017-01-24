---
title: "編譯器錯誤 CS0254 | Microsoft Docs"
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
  - "CS0254"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0254"
ms.assetid: 85b2ab1e-0011-4f1d-9181-76b9c9f3d914
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0254
fixed 陳述式指派運算子的右邊不能是 cast 運算式  
  
 [fixed](../Topic/fixed%20Statement%20\(C%23%20Reference\).md) 運算式的右邊不能使用 cast。 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0254：  
  
```  
// CS0254.cs // compile with: /unsafe class Point { public uint x, y; } class FixedTest { unsafe static void SquarePtrParam (int* p) { *p *= *p; } unsafe public static void Main() { Point pt = new Point(); pt.x = 5; pt.y = 6; fixed (int* p = (int*)&pt.x)   // CS0254 // try the following line instead // fixed (uint* p = &pt.x) { SquarePtrParam ((int*)p); } } }  
```