---
title: "編譯器錯誤 CS1937 | Microsoft Docs"
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
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1937
名稱 'name' 不在 'equals' 左側的範圍內。 請考慮交換 'equals' 任一側的運算式。  
  
 `equals` 關鍵字是特殊運算子，可用於 `join` 子句來判斷兩個運算式是否相等。 左側來源序列的範圍變數會在等號左邊的範圍內，而右側來源的範圍變數只會在等號左邊的範圍內。 您可以在下列程式碼範例中使用 IntelliSense 進行試驗，以確認這項作業。  
  
### 更正這個錯誤  
  
1.  交換兩個範圍變數的位置，如下列範例中加上註解標記的一行所示：  
  
## 範例  
 下列範例會產生 CS1937：  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 左邊一般稱為「外側」，右邊一般稱為「內側」。  
  
## 請參閱  
 [join 子句](../Topic/join%20clause%20\(C%23%20Reference\).md)