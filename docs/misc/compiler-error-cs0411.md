---
title: "編譯器錯誤 CS0411 | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0411
方法 'method' 的類型引數不能從使用方式推斷。 請嘗試明確指定類型引數。  
  
 如果您在未明確提供類型引數的情況下呼叫泛型方法，而且編譯器無法推斷想要的類型引數，則會發生這個錯誤。 若要避免這個錯誤，請在角括弧中加入想要的類型引數。  
  
## 範例  
 下列範例會產生 CS0411：  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## 範例  
 其他可能的錯誤情況包括參數是沒有任何類型資訊的 `null` 時：  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```