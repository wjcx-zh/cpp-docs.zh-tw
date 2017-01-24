---
title: "編譯器錯誤 CS0239 | Microsoft Docs"
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
  - "CS0239"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0239"
ms.assetid: 2e07bbc2-03a9-44b2-b321-477ca95fff8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0239
'member': 無法覆寫繼承的成員 'inherited member'，因為其已密封  
  
 成員無法[覆寫](../Topic/override%20\(C%23%20Reference\).md)[密封](../Topic/sealed%20\(C%23%20Reference\).md)的繼承成員。 如需詳細資訊，請參閱[Checked 與 Unchecked](../Topic/Checked%20and%20Unchecked%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0239：  
  
```  
// CS0239.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public override sealed void f() { } } class MyClass3 : MyClass2 { public override void f()   // CS0239 // Try the following definition instead: // public new void f() { } }  
```