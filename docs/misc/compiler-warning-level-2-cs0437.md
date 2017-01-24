---
title: "編譯器警告 (層級 2) CS0437 | Microsoft Docs"
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
  - "CS0437"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0437"
ms.assetid: cba5c9b6-a0bc-4f19-b1f0-c1f66436ee91
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0437
'assembly2' 中的類型 'type' 與 'fassembly1' 中匯入的命名空間 'namespace' 相衝突。 請使用 'assembly' 中定義的類型。  
  
 原始程式檔 file\_2 中的類型與 file\_1 中匯入的命名空間衝突時，會發出這個警告。 編譯器會使用原始程式檔中的類型。  
  
## 範例  
  
```  
// CS0437_a.cs // compile with: /target:library namespace Util { public class A { public void Test() { System.Console.WriteLine("CS0437_a.cs"); } } }  
```  
  
## 範例  
 下列範例會產生 CS0437。  
  
```  
// CS0437_b.cs // compile with: /reference:CS0437_a.dll /W:2 // CS0437 expected class Util { public class A { public void Test() { System.Console.WriteLine("CS0437_b.cs"); } } } public class Test { public static void Main() { Util.A x = new Util.A(); x.Test(); } }  
```