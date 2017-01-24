---
title: "編譯器錯誤 CS0710 | Microsoft Docs"
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
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0710
靜態類別不能有執行個體建構函式  
  
 靜態類別無法具現化，因此不需要建構函式。 若要避免這個錯誤，請移除靜態類別所有的建構函式，或如果您真的很想要建構執行個體，請將類別變成非靜態。  
  
 下例會產生 CS0710：  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```