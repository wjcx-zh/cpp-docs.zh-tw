---
title: "編譯器錯誤 CS0209 | Microsoft Docs"
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
  - "CS0209"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0209"
ms.assetid: a408a869-02db-414f-97c1-bfb1637f6155
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0209
在 fixed 陳述式中宣告的區域變數類型必須為指標類型  
  
 [fixed 陳述式](../Topic/fixed%20Statement%20\(C%23%20Reference\).md)中所宣告的變數必須是指標。 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0209：  
  
```  
// CS0209.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0209 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```