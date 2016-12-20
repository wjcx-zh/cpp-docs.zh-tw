---
title: "編譯器錯誤 CS1935 | Microsoft Docs"
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
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1935
找不到來源類型 'type' 的查詢模式實作。 找不到 'method'。 您是否遺漏 'System.Core.dll' 的參考，或 'System.linq' 的 using 指示詞?  
  
 查詢中的來源類型必須是 `IEnumerable`、`IEnumerable<T>` 或衍生類型，或是您或其他人已實作標準查詢運算子的類型。 如果來源類型是 `IEnumerable` 或 `IEnumerable<T>`，您必須加入對 system.core.dll 的參考和 System.Linq 命名空間的 `using` 指示詞，才能將標準查詢運算子擴充方法帶到範圍中。 標準查詢運算子的自訂實作必須以相同方式帶入範圍中，具有 `using` 指示詞，如有必要則還要有組件的參考。  
  
### 更正這個錯誤  
  
1.  請加入必要的 using 指示詞和專案的參考。  
  
## 範例  
 下列程式碼會產生 CS1935，因為 System.Linq 的 `using` 指示詞已標記為註解：  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## 請參閱  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)