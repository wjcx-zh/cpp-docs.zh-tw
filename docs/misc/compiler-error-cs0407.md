---
title: "編譯器錯誤 CS0407 | Microsoft Docs"
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
  - "CS0407"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0407"
ms.assetid: 59112fb9-4641-466e-b738-b3228539a09e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0407
'return\-type method' 的傳回類型錯誤  
  
 此方法與委派類型不相容。 引數類型相符，但傳回類型不是該委派的正確傳回類型。 若要避免這個錯誤，請使用不同的方法、變更方法的傳回類型，或變更委派的傳回類型。  
  
## 範例  
 下列範例會產生 CS0407：  
  
```  
// CS0407.cs public delegate int MyDelegate(); class C { MyDelegate d; public C() { d = new MyDelegate(F);  // OK: F returns int d = new MyDelegate(G);  // CS0407 – G doesn't return int } public int F() { return 1; } public void G() { } public static void Main() { C c1 = new C(); } }  
```