---
title: "編譯器錯誤 CS0431 | Microsoft Docs"
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
  - "CS0431"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0431"
ms.assetid: 05da7ea7-f33d-48d4-948e-d64be56f91ba
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0431
不能搭配使用別名 'identifier' 與 '::'，因為別名會參考類型。 請改用 '.'。  
  
 您已搭配使用 "::" 與參考類型的別名。 若要解決這個錯誤，請使用 "." 運算子。  
  
 下列範例會產生 CS0431：  
  
```  
// CS0431.cs using A = Outer; public class Outer { public class Inner { public static void Meth() {} } } public class MyClass { public static void Main() { A::Inner.Meth();   // CS0431 A.Inner.Meth();   // OK } }  
```