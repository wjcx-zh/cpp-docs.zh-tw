---
title: "編譯器錯誤 CS0211 | Microsoft Docs"
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
  - "CS0211"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0211"
ms.assetid: 720be9a9-b0c1-4391-94e5-4c4027e83036
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0211
無法取得指定運算式的位址  
  
 您可以採用欄位、區域變數和指標間接取值的位址，但不能採用例如兩個區域變數總和的位址。 如需詳細資訊，請參閱[Unsafe 程式碼和指標](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md)。  
  
 下例會產生 CS0211：  
  
```  
// CS0211.cs // compile with: /unsafe public class MyClass { unsafe public void M() { int a = 0, b = 0; int *i = &(a + b);   // CS0211, the addition of two local variables // try the following line instead // int *i = &a; } public static void Main() { } }  
```