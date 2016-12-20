---
title: "編譯器錯誤 CS1952 | Microsoft Docs"
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
  - "CS1952"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1952"
ms.assetid: 8c560bf9-df93-40f5-a3d8-c66b31cde08f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1952
運算式樹狀結構 Lambda 不可包含具有變數引數的方法  
  
 不允許在編譯成運算式樹狀架構的 Lambda 運算式中使用不支援的 `__arglist` 關鍵字。  
  
### 更正這個錯誤  
  
1.  請勿使用 `__arglist`。  
  
## 範例  
 下列程式碼會產生CS1952：  
  
```  
// cs1952.cs using System; using System.Linq.Expressions; class Test { public static int M(__arglist) { return 1; } static int Main() { Expression<Func<int, int>> f = x => Test.M(__arglist(x)); // CS1952 return 1; } }  
  
```