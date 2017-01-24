---
title: "編譯器錯誤 CS0751 | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0751
在部分類別或部分結構中必須宣告部分方法  
  
 除非[部分](../Topic/partial%20\(Method\)%20\(C%23%20Reference\).md)方法封裝在部分類別或部分結構中，否則不可以宣告此方法。  
  
### 更正這個錯誤  
  
1.  從方法中移除 `partial` 修飾詞並提供實作，或將 `partial` 修飾詞加入封入類別或結構中。  
  
## 範例  
 下列範例會產生 CS0751：  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)