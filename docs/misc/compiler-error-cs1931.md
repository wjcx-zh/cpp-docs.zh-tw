---
title: "編譯器錯誤 CS1931 | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1931
範圍變數 'variable' 與 'variable' 的上一個宣告衝突。  
  
 範圍變數的宣告 \(就像每個其他宣告一樣\) 在變數宣告空間內必須有唯一識別項。  
  
### 更正這個錯誤  
  
1.  請提供範圍變數的唯一名稱。  
  
## 範例  
 下列程式碼會產生 CS1931，因為識別項 `x` 同時用作 `Main` 中的區域變數以及查詢運算式中的範圍變數：  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)