---
title: "編譯器錯誤 CS1101 | Microsoft Docs"
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
  - "CS1101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1101"
ms.assetid: d6fc8834-eadf-4497-b442-0751895e6764
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1101
參數修飾詞 'ref' 不可與 'this' 一起使用。  
  
 當 `this` 關鍵字修改靜態方法的第一個參數時，它會通知編譯器，該方法是一個擴充方法。 擴充方法的第一個參數上不需要也不允許其他修飾詞。  
  
## 範例  
 下列範例會產生 CS1101：  
  
```  
// cs1101.cs // Compile with: /target:library public static class Extensions { // No type parameters. public static void Test(ref this int i) {} // CS1101 // Single type parameter. public static void Test<T>(ref this T t) {}// CS1101 // Multiple type parameters. public static void Test<T,U,V>(ref this U u) {}// CS1101 }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [this](../Topic/this%20\(C%23%20Reference\).md)   
 [ref](../Topic/ref%20\(C%23%20Reference\).md)