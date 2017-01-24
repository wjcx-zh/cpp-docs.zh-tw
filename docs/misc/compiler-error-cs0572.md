---
title: "編譯器錯誤 CS0572 | Microsoft Docs"
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
  - "CS0572"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0572"
ms.assetid: ec950e95-13da-41b5-90cd-9e673d62498b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0572
'type': 不可透過運算式參考類型; 請嘗試改用 'path\_to\_type'  
  
 已嘗試透過識別項存取類別的成員，在此情況下不允許這麼做。  
  
 下列範例會產生 CS0572：  
  
```  
// CS0572.cs using System; class C { public class Inner { public static int v = 9; } } class D : C { public static void Main() { C cValue = new C(); Console.WriteLine(cValue.Inner.v);   // CS0572 // try the following line instead // Console.WriteLine(C.Inner.v); } }  
```