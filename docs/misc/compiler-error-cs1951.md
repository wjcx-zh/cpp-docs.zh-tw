---
title: "編譯器錯誤 CS1951 | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1951
運算式樹狀結構 Lambda 不可包含 out 或 ref 參數。  
  
 運算式樹狀結構只會將運算式表示為資料結構。 沒有任何方法可將特定記憶體位置表示為透過傳址方式傳遞參數時的必要記憶體位置。  
  
### 更正這個錯誤  
  
1.  唯一的選項是移除委派定義中的 `ref` 修飾詞，並透過傳值方式傳入參數中。  
  
## 範例  
 下列範例會產生 CS1951：  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## 請參閱  
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)