---
title: "編譯器錯誤 CS0766 | Microsoft Docs"
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
  - "CS0766"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0766"
ms.assetid: 4574e30b-3e76-42cd-90e8-31c72126a08c
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0766
部分方法必須有 void 傳回類型。  
  
 部分方法無法傳回值。 它的傳回類型必須是 void。  
  
### 更正這個錯誤  
  
1.  指定部分方法的 void 傳回類型，或將方法轉換成一般 \(非部分\) 方法。  
  
## 範例  
 下列範例會產生 CS0766：  
  
```  
// cs0766.cs using System; public partial class C { partial int Part(); // CS0766 // Typically the implementing declaration // is contained in a separate file. partial int Part() //CS0766 { } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)