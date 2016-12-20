---
title: "編譯器錯誤 CS0838 | Microsoft Docs"
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
  - "CS0838"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0838"
ms.assetid: 22495e47-3331-42ef-921c-f76ff03ef1f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0838
運算式樹狀結構不可包含多維陣列初始設定式。  
  
 使用陣列初始設定式，無法初始化運算式樹狀結構中的多維陣列。  
  
### 更正這個錯誤  
  
1.  請先建立並初始化陣列，再建立運算式樹狀結構。  
  
## 範例  
 下列範例會產生 CS0838：  
  
```  
// cs0838.cs using System; using System.Linq; using System.Linq.Expressions; namespace TestNamespace { class Test { static int Main() { Expression<Func<int[,]>> expr = () => new int[2, 2] { { 1, 2 }, { 3, 4 } }; // CS0838 // try the following 2 lines instead int[,] nums = new int[2, 2] { { 1, 2 }, { 3, 4 } }; Expression<Func<int[,]>> expr2 = () => nums; return 1; } } }  
  
```  
  
## 請參閱  
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)