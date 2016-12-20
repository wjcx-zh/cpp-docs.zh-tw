---
title: "編譯器錯誤 CS1934 | Microsoft Docs"
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
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1934
找不到來源類型 'type' 的查詢模式實作。 找不到 'method'。 請考慮明確指定範圍變數 'name' 的類型。  
  
 如果查詢運算式指定的資料來源沒有實作標準查詢運算子，就會產生這個錯誤。 產生此錯誤的一個方式是指定 `ArrayList`而不提供明確的範圍變數類型。  
  
### 更正這個錯誤  
  
1.  在下列範例中，解決方案只需指定範圍變數的類型：  
  
    ```  
    var q = from int x in list  
    ```  
  
## 範例  
 下列範例會示範產生 CS1934的一種方法：  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## 請參閱  
 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)