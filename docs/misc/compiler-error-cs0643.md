---
title: "編譯器錯誤 CS0643 | Microsoft Docs"
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
  - "CS0643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0643"
ms.assetid: beae30ff-15c2-413f-8f5c-504cdba2e57a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0643
'arg' 有重複的具名屬性引數  
  
 在使用者定義的屬性上，指定參數 `arg` 兩次。 如需詳細資訊，請參閱[屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例  
 下列範例會產生 CS0643：  
  
```  
// CS0643.cs using System; using System.Runtime.InteropServices; [AttributeUsage(AttributeTargets.Class)] public class MyAttribute : Attribute { public MyAttribute() { } public int x; } [MyAttribute(x = 5, x = 6)]   // CS0643, error setting x twice // try the following line instead // [MyAttribute(x = 5)] class MyClass { } public class MainClass { public static void Main () { } }  
```