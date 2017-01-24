---
title: "編譯器錯誤 CS1953 | Microsoft Docs"
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
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1953
運算式樹狀架構 Lambda 不能包含方法群組。  
  
 方法呼叫需要 `()` 運算子。 沒有該運算子的方法名稱會參考到方法群組，這是具有該名稱之所有多載方法的集合。  
  
### 更正這個錯誤  
  
1.  如果您想要呼叫此方法，請加入 `()` 運算子。  
  
## 範例  
 下列範例會產生 CS1953：  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```