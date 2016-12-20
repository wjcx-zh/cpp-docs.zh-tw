---
title: "編譯器錯誤 CS1106 | Microsoft Docs"
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
  - "CS1106"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1106"
ms.assetid: 3585600a-6b2c-47aa-a418-ef049f07c107
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1106
擴充方法必須在非泛型靜態類別中定義。  
  
 擴充方法必須定義為非泛型靜態類別中的靜態方法。  
  
## 範例  
 下列範例會產生 CS1106，因為類別 `Extensions` 未定義為 `static`：  
  
```  
// cs1106.cs public class Extensions // CS1106 { public  static void Test<T>(this System.String s) {} }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [static](../Topic/static%20\(C%23%20Reference\).md)