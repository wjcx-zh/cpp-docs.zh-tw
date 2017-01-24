---
title: "編譯器錯誤 CS0763 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0763
兩個部分方法宣告必須都是靜態，或者都不是靜態。  
  
 部分方法宣告不能有一部分靜態，另一部分非靜態。  
  
### 更正這個錯誤  
  
1.  將這兩部分同時設為靜態，或同時設為非靜態。  
  
## 範例  
 下列程式碼會產生 CS0763：  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [static](../Topic/static%20\(C%23%20Reference\).md)