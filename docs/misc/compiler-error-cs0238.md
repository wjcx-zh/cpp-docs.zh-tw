---
title: "編譯器錯誤 CS0238 | Microsoft Docs"
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
  - "CS0238"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0238"
ms.assetid: 9b50c6e2-2c3f-431d-bdb7-557b0ec51626
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0238
'member' 不是 override，因此無法成為密封 \(sealed\)  
  
 [sealed](../Topic/sealed%20\(C%23%20Reference\).md) 已用於也未以 [override](../Topic/override%20\(C%23%20Reference\).md) 標記的成員。 如需詳細資訊，請參閱[繼承](../Topic/Inheritance%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0238：  
  
```  
// CS0238.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public sealed void f() // CS0238 // Try the following definition instead: // public override sealed void f() { } }  
```