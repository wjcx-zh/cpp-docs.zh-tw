---
title: "編譯器錯誤 CS0711 | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0711
靜態類別不能包含解構函式  
  
 靜態類別無法具現化，因此不需要建構函式或解構函式。 若要避免這個錯誤，請移除靜態類別中的所有解構函式，或如果您真的想要建構並破壞執行個體，請將類別變成非靜態。  
  
 下列範例會產生 CS0711：  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```