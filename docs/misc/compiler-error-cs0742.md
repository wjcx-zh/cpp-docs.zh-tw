---
title: "編譯器錯誤 CS0742 | Microsoft Docs"
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
  - "CS0742"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0742"
ms.assetid: 078ee7af-17e4-4572-8fee-d97e09c9002b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0742
查詢主體必須以 select 或 group 子句結尾  
  
 查詢運算式必須以無接續的 `select` 子句或 `group` 子句來終止。  
  
### 更正這個錯誤  
  
1.  將 [select 子句](../Topic/select%20clause%20\(C%23%20Reference\).md)或 [group 子句](../Topic/group%20clause%20\(C%23%20Reference\).md)加入查詢中。  
  
## 範例  
 下列程式碼會產生 CS0742：  
  
```  
// cs0742.cs using System.Linq; public class Test { public static int Main() { int[] array = { 1, 2, 3 }; var query = from num in array; // CS0742 return 1; } }  
```  
  
 如果 `group` 子句使用 [into](../Topic/into%20\(C%23%20Reference\).md) 關鍵字來將群組的結果儲存至暫時識別項，則它不能是查詢中的最後一個子句。 仍然需要 `select` 或第二個 `group` 子句。  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)