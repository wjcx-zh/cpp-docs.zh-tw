---
title: "編譯器錯誤 CS0743 | Microsoft Docs"
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
  - "CS0743"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0743"
ms.assetid: 0dc8040a-a12f-4da6-9ed0-c0284905ee83
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0743
必須是內容關鍵字 'on'  
  
 `join` 子句的模式是 `join`...`in`...`on`...`equals`，如下列範例所示：  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### 更正這個錯誤  
  
1.  請將 `on` 關鍵字加入 `join` 子句。  
  
## 範例  
 下列程式碼會產生 CS0743：  
  
```  
// cs0743.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 x equals y // CS0743 select x; return 1; } }  
```  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)   
 [join 子句](../Topic/join%20clause%20\(C%23%20Reference\).md)