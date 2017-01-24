---
title: "編譯器警告 (層級 3) CS1718 | Microsoft Docs"
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
  - "CS1718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1718"
ms.assetid: 7c1c11fd-4f91-482d-b8f7-efe2a361634e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS1718
對同一個變數進行比較; 您是否想要比較別的東西?  
  
 如果您想要與其他項目相比較，您應該只要更正陳述式。  
  
 但另一種可能性是您在測試為 true 或 false，並使用陳述式例如 `if (a == a) (true)` 或 `if (a < a) (false)` 進行。 最好只使用 `if (true)` 或 `if (false)`。 不這麼做的原因有兩個：  
  
-   它比較簡單：只說您心中所指的永遠比較清楚。  
  
-   有助於避免混淆：C\# 2.0 的一項新功能是可為 Null 的實值類型，類似於 T\-SQL \(SQL Server 所使用的程式設計語言\) 中的 `null` 值。 熟悉 T\-SQL 的開發人員可能會擔心可為 Null 的類型對例如 `if (a == a)` 的運算式有什麼影響，因為在 T\-SQL 中使用三元邏輯。 如果您使用 `true` 或 `false`，即可避免可能的混淆。  
  
## 範例  
 下列程式碼會產生警告 CS1718：  
  
```  
// CS1718.cs using System; public class Tester { public static void Main() { int i = 0; if (i == i) { // CS1718.cs //if (true) { i++; } } }  
```