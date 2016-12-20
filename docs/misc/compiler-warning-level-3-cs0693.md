---
title: "編譯器警告 (層級 3) CS0693 | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0693
類型參數 'type parameter' 與外部類型 'type' 的類型參數名稱相同  
  
 當您有泛型成員 \(例如泛型類別內的方法\) 時，會發生這個錯誤。 因為方法的類型參數不一定與類別的類型參數相同，所以您無法讓它們具有相同名稱。 如需詳細資訊，請參閱[泛型方法](../Topic/Generic%20Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 若要避免這種情況，請對其中一個類型參數使用不同的名稱。  
  
## 範例  
 下列範例會產生 CS0693。  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```