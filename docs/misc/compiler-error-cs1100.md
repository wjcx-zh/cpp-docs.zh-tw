---
title: "編譯器錯誤 CS1100 | Microsoft Docs"
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
  - "CS1100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1100"
ms.assetid: ea233371-36b6-49ae-a98c-a00ee3b79e53
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1100
成員 'name' 具有參數修飾詞 'this'，此參數修飾詞不在第一個參數上。  
  
 `this` 修飾詞只允許出現在方法的第一個參數，它會通知編譯器該方法是一個擴充方法。  
  
### 更正這個錯誤  
  
1.  請從所有方法的第一個參數以外的所有參數移除 `this` 修飾詞。  
  
## 範例  
 下列程式碼會產生 CS1100，因為 `this`  參數正在修改第二個參數：  
  
```  
// cs1100.cs static class Test { static void ExtMethod(int i, this Test c) // CS1100 { } }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)