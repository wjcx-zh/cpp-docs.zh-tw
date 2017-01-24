---
title: "編譯器錯誤 CS0825 | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0825
內容關鍵字 'var' 只能出現在區域變數宣告中。  
  
 使用 `var` 關鍵字的隱含類型只能套用至本機方法範圍的變數。  
  
### 更正這個錯誤  
  
1.  如果變數屬於類別範圍，請指定明確的類型。  否則，請將它移至將使用它的方法內。  
  
## 範例  
 因為在類別欄位上使用 `var`，所以下列程式碼會產生 CS0825：  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## 請參閱  
 [隱含類型區域變數](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)