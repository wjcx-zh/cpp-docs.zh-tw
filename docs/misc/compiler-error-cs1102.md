---
title: "編譯器錯誤 CS1102 | Microsoft Docs"
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
  - "CS1102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1102"
ms.assetid: 7de798d4-1b4b-4842-ae43-9bc83e6dc9a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1102
參數修飾詞 'out' 不可與 'this' 一起使用。  
  
 當 `this` 關鍵字修改靜態方法的第一個參數時，它會通知編譯器，該方法是一個擴充方法。 擴充方法的第一個參數上不需要也不允許其他修飾詞。  
  
### 更正這個錯誤  
  
1.  請從第一個參數移除未經授權的修飾詞。  
  
## 範例  
 下列範例會產生 CS1102：  
  
```  
// cs1102.cs // Compile with: /target:library. public static class Extensions { // No type parameters. public static void Test(this out int i) {} // CS1102 //Single type parameter public static void Test<T>(this out T t) {}// CS1102 //Multiple type parameters public static void Test<T,U,V>(this out U u) {}// CS1102 }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [this](../Topic/this%20\(C%23%20Reference\).md)   
 [out](../Topic/out%20\(C%23%20Reference\).md)