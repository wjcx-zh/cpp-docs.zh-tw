---
title: "編譯器錯誤 CS1940 | Microsoft Docs"
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
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1940
為來源類型 'type' 找到多個查詢模式實作。 模稜兩可的 'method' 呼叫。  
  
 已定義查詢方法的多個實作定義，編譯器無法區別哪一個最適用於查詢時，就會產生這個錯誤。 在下列範例中，兩個版本的 `Select` 都具有相同的簽章，因為它們都接受一個 `int` 作為輸入參數，而且以 `int` 作為傳回值。  
  
### 更正這個錯誤  
  
1.  請為每個方法只提供一個實作。  
  
## 範例  
 下列程式碼會產生 CS1940：  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## 請參閱  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)