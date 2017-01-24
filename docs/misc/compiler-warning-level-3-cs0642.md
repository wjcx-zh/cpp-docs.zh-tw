---
title: "編譯器警告 (層級 3) CS0642 | Microsoft Docs"
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
  - "CS0642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0642"
ms.assetid: e2df58c0-9b7e-4e50-8e31-e0134955f62c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0642
可能誤用了空白的陳述式  
  
 條件陳述式後面的分號可能會導致您的程式碼不如預期執行。  
  
 您可以使用 **\/nowarn** 編譯器選項或 `#pragmas warning` 來停用這個警告；如需詳細資訊，請參閱 [\/nowarn \(Suppress Specified Warnings\)](../Topic/-nowarn%20\(C%23%20Compiler%20Options\).md) 或 [\#pragma warning](../Topic/%23pragma%20warning%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0642：  
  
```  
// CS0642.cs // compile with: /W:3 class MyClass { public static void Main() { int i; for (i = 0; i < 10; i += 1);   // CS0642 semicolon intentional? { System.Console.WriteLine (i); } } }  
```