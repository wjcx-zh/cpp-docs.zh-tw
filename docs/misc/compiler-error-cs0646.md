---
title: "編譯器錯誤 CS0646 | Microsoft Docs"
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
  - "CS0646"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0646"
ms.assetid: 48ea306f-b4a0-4988-8d2b-ca9d38e9bdad
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0646
無法在包含索引子的類型上指定 DefaultMember 屬性  
  
 如果類別或其他類型指定 **System.Reflection.DefaultMemberAttribute**，則不能包含索引子。 如需詳細資訊，請參閱[屬性](../Topic/Properties%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0646：  
  
```  
// CS0646.cs // compile with: /target:library [System.Reflection.DefaultMemberAttribute("x")]   // CS0646 class MyClass { public int this[int index]   // an indexer { get { return 0; } } public int x = 0; } // OK [System.Reflection.DefaultMemberAttribute("x")] class MyClass2 { public int prop { get { return 0; } } public int x = 0; } class MyClass3 { public int this[int index]   // an indexer { get { return 0; } } public int x = 0; }  
```