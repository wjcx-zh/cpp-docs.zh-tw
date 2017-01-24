---
title: "編譯器錯誤 CS0210 | Microsoft Docs"
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
  - "CS0210"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0210"
ms.assetid: 9f2ec1b8-6ca4-4147-b004-e3b43e7e8754
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0210
在 fixed 或 using 陳述式宣告中，必須提供初始設定式。  
  
 您必須宣告並初始化 [fixed 陳述式](../Topic/fixed%20Statement%20\(C%23%20Reference\).md)中的變數。 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0210：  
  
```  
// CS0210a.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0210 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```  
  
 下列範例也會產生 CS0210，因為 [using 陳述式](../Topic/using%20Statement%20\(C%23%20Reference\).md)沒有初始設定式。  
  
```  
// CS0210b.cs using System.IO; class Test { static void Main() { using (StreamWriter w) // CS0210 // Try this line instead: // using (StreamWriter w = new StreamWriter("TestFile.txt")) { w.WriteLine("Hello there"); } } }  
```