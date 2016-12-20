---
title: "編譯器錯誤 CS0765 | Microsoft Docs"
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
  - "CS0765"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0765"
ms.assetid: adfb1f95-f7b1-4e43-83c2-42e8531eb980
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0765
在運算式樹狀結構中，不可使用只具有定義宣告或已移除條件式方法的部分方法。  
  
 雖然對移除的部分方法的呼叫是運算式，卻不是運算式樹狀結構接受的運算式。  
  
### 更正這個錯誤  
  
1.  加入部分方法的實作宣告，或移除造成編譯要排除之條件式方法的程式碼。  
  
## 範例  
 下列程式碼在兩個位置會產生 CS0765：  
  
```  
// cs0765.cs using System; using System.Collections; using System.Collections.Generic; using System.Diagnostics; using System.Linq; using System.Linq.Expressions; public delegate void dele(); public class ConClass { [Conditional("CONDITION")] public static void TestMethod() { } } public partial class PartClass : IEnumerable { List<object> list = new List<object>(); partial void Add(int x); public IEnumerator GetEnumerator() { for (int i = 0; i < list.Count; i++) yield return list[i]; } static void Main() { Expression<Func<PartClass>> testExpr1 = () => new PartClass { 1, 2 }; // CS0765 Expression<dele> testExpr2 = () => ConClass.TestMethod(); // CS0765 } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)