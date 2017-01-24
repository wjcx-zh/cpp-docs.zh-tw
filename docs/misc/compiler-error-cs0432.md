---
title: "編譯器錯誤 CS0432 | Microsoft Docs"
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
  - "CS0432"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0432"
ms.assetid: 39b63146-ecb2-4b7a-b3cb-f68fff5069f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0432
找不到別名 'identifier'  
  
 當您在非別名的識別項右側使用 "::" 時，會發生這個錯誤。 若要解決這個錯誤，請改用 "."。  
  
 下列範例會產生 CS0432：  
  
```  
// CS0432.cs namespace A { public class B { public static void Meth() { } } } public class Test { public static void Main() { A::B.Meth();   // CS0432 // To resolve, use the following line instead: // A.B.Meth(); } }  
```