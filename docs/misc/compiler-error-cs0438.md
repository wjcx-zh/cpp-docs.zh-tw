---
title: "編譯器錯誤 CS0438 | Microsoft Docs"
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
  - "CS0438"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0438"
ms.assetid: 92c91ecb-8d6a-4850-84eb-c095c3c957f1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0438
'module\_1' 中的類型 'type' 與 'module\_2' 中的命名空間 'namespace' 衝突。  
  
 當原始程式檔中的一個類型與另一個原始程式檔中的一個命名空間衝突時，就會發生這個錯誤。 當其中一個或兩者來自加入的模組時，通常會發生這種情況。 若要解決，請重新命名造成衝突的類型或命名空間。  
  
 下列範例會產生 CS0438：  
  
 先編譯這個檔案：  
  
```  
// CS0438_1.cs // compile with: /target:module public class Util { public class A { } }  
```  
  
 然後，編譯這個檔案：  
  
```  
// CS0438_2.cs // compile with: /target:module namespace Util { public class A { } }  
```  
  
 再編譯這個檔案：  
  
```  
// CS0438_3.cs // compile with: /addmodule:CS0438_1.netmodule /addmodule:CS0438_2.netmodule using System; public class Test { public static void Main() { Console.WriteLine(typeof(Util.A));   // CS0438 } }  
  
```