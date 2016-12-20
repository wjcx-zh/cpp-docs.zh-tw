---
title: "編譯器錯誤 CS1945 | Microsoft Docs"
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
  - "CS1945"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1945"
ms.assetid: 787f61b0-4767-451c-8c78-8e456b5057eb
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1945
運算式樹狀結構不可包含匿名方法運算式。  
  
 運算式樹狀結構只能包含運算式。 匿名方法只能表示陳述式。  
  
### 更正這個錯誤  
  
1.  請不要嘗試使用陳述式來建立運算式樹狀結構。  
  
## 範例  
 下列程式碼會產生 CS1945：  
  
```  
// cs1945.cs using System; using System.Linq.Expressions; public delegate void D(); class Test { static void Main() { Expression<Func<int, Func<int, bool>>> tree = (x => delegate(int i) { return true; }); // CS1945 } }  
```  
  
## 請參閱  
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [陳述式、運算式和運算子](../Topic/Statements,%20Expressions,%20and%20Operators%20\(C%23%20Programming%20Guide\).md)