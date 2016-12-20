---
title: "編譯器錯誤 CS0815 | Microsoft Docs"
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
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0815
無法指派 'expression' 給隱含類型區域變數  
  
 作為隱含類型變數之初始設定式的運算式必須具有類型。 由於匿名函式運算式、方法群組運算式和 null 常值運算式沒有類型，因此不是適當的初始設定式。 隱含類型變數無法在其宣告中使用 null 值進行初始化，不過稍後可指派 null 值給它。  
  
### 更正這個錯誤  
  
1.  為變數提供明確類型。  
  
## 範例  
 下列程式碼會產生 CS0815：  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)