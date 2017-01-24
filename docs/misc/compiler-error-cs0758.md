---
title: "編譯器錯誤 CS0758 | Microsoft Docs"
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
  - "CS0758"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0758"
ms.assetid: 06ddd548-1311-40db-9078-8a18107b8346
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0758
兩個部分方法宣告都必須使用 params 參數，或兩者都不使用 params 參數  
  
 如果部分方法有一個部分指定 `params` 參數，則另一個部分也必須指定相同參數。  
  
### 更正這個錯誤  
  
1.  請在方法的一個部分加入 `params` 修飾詞，或在另一個部分中移除它。  
  
## 範例  
 下列程式碼會產生 CS0758：  
  
```  
using System; public partial class C { partial void Part(int i, params char[] array); partial void Part(int i, char[] array) // CS0758 { } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [params](../Topic/params%20\(C%23%20Reference\).md)