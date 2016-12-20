---
title: "編譯器錯誤 CS0757 | Microsoft Docs"
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
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0757
部分方法不能有多重實作的宣告。  
  
 部分方法是由一個定義宣告 \(簽章\) 以及一個或零個實作宣告 \(主體\) 所組成。 同一個定義宣告不能有多個實作宣告。 部分方法可以多載，而且每個多載的版本可以有一個或零個實作宣告。  
  
### 更正這個錯誤  
  
1.  移除部分方法的所有實作宣告，只保留一個。  
  
## 範例  
 下列範例會產生 CS0757：  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)