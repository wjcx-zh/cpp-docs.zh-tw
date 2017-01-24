---
title: "編譯器錯誤 CS1105 | Microsoft Docs"
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
  - "CS1105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1105"
ms.assetid: fcbd91ad-a76a-4b22-868d-16824fa96f85
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1105
擴充方法必須為靜態。  
  
 擴充方法必須宣告為非泛型靜態類別中的靜態方法。  
  
## 範例  
 下列範例會產生 CS1105，因為 `Test` 不是靜態的：  
  
```  
// cs1105.cs // Compile with: /target:library public class Extensions { // Single type parameter. public void Test<T>(this System.String s) {} //CS1105 }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [static](../Topic/static%20\(C%23%20Reference\).md)