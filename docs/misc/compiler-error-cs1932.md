---
title: "編譯器錯誤 CS1932 | Microsoft Docs"
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
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1932
無法指派 'expression' 給範圍變數  
  
 編譯器必須能夠推斷範圍變數的類型，而不論其是在 `from` 子句或 `let` 子句中所引入。 不可為 Null，因為 null 不是類型，也不可以透過不安全類型的運算式進行指派。  
  
### 更正這個錯誤  
  
-   移除無效的指派。  
  
-   將運算式明確轉換成允許的類型。  
  
## 範例  
 下列程式碼會產生 CS1932，因為無法推斷範圍變數的類型。 將值轉換成預期的類型即可修正此錯誤，如下列範例所示。  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)