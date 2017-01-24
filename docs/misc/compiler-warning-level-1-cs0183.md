---
title: "編譯器警告 (層級 1) CS0183 | Microsoft Docs"
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
  - "CS0183"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0183"
ms.assetid: c8b8eb23-edae-46da-b3ae-2a00f86e56bc
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0183
指定的運算式一律為提供的 \('type'\) 類型  
  
 如果條件陳述式一律評估為 **true**，則不需要條件陳述式。 嘗試使用 **is** 運算子來評估類型時，會發生這個警告。 如果評估為實值類型，則不需要檢查。  
  
 下列範例會產生 CS0183：  
  
```  
// CS0183.cs // compile with: /W:1 using System; public class Test { public static void F(Int32 i32, String str) { if (str is Object)          // OK Console.WriteLine( "str is an object" ); else Console.WriteLine( "str is not an object" ); if (i32 is Object)   // CS0183 Console.WriteLine( "i32 is an object" ); else Console.WriteLine( "i32 is not an object" ); // never reached } public static void Main() { F(0, "CS0183"); F(120, null); } }  
```