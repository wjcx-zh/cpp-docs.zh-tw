---
title: "編譯器錯誤 CS0753 | Microsoft Docs"
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
  - "CS0753"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0753"
ms.assetid: 287dd9da-da74-4290-9fa1-21ef1a8150fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0753
只有方法、類別、結構或介面可以是 partial。  
  
 [partial](../Topic/partial%20\(Type\)%20\(C%23%20Reference\).md) 修飾詞只能與類別、結構、介面和方法搭配使用。  
  
### 更正這個錯誤  
  
1.  請從變數或語言建構中移除 `partial` 修飾詞。  
  
## 範例  
 下列程式碼會產生 CS0753：  
  
```  
// cs0753.cs using System; public partial class C { partial int num; // CS0753 public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)