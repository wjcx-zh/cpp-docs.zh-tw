---
title: "編譯器錯誤 CS1621 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1621"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1621"
ms.assetid: 11b4fb94-0dd7-4484-99aa-e06eacc6a658
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1621
在匿名方法或 Lambda 運算式內不可使用 yield 陳述式  
  
 yield 陳述式不能在迭代器的匿名方法區塊中。  
  
## 範例  
 下列範例會產生 CS1621：  
  
```  
// CS1621.cs using System.Collections; delegate object MyDelegate(); class C : IEnumerable { public IEnumerator GetEnumerator() { MyDelegate d = delegate { yield return this; // CS1621 return this; }; d(); // Try this instead: // MyDelegate d = delegate { return this; }; // yield return d(); } public static void Main() { } }  
```  
  
## 請參閱  
 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)   
 [yield](../Topic/yield%20\(C%23%20Reference\).md)   
 [Lambda 運算式](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md)   
 [匿名方法](../Topic/Anonymous%20Methods%20\(C%23%20Programming%20Guide\).md)