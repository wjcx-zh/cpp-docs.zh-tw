---
title: "編譯器警告 (層級 4) CS1573 | Microsoft Docs"
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
  - "CS1573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1573"
ms.assetid: 1b68cb1a-9bfd-4343-b9b6-8ce195af5e23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 4) CS1573
參數 'parameter' 在 'parameter' 的 XML 註解中沒有相符的 param 標記 \(但其他參數有\)  
  
 使用 [\/doc](../Topic/-doc%20\(C%23%20Compiler%20Options\).md) 編譯器選項時，為方法中的部分 \(而非所有\) 參數指定了註解。 您可能忘記針對這些參數輸入註解。  
  
 下列範例會產生 CS1573：  
  
```  
// CS1573.cs // compile with: /W:4 public class MyClass { /// <param name='Int1'>Used to indicate status.</param> // enter a comment for Char1? public static void MyMethod(int Int1, char Char1) { } public static void Main () { } }  
```