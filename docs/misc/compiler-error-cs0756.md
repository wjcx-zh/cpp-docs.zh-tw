---
title: "編譯器錯誤 CS0756 | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0756
部分方法不可有多重定義宣告。  
  
 部分方法的定義宣告是指定方法簽章的部分，而不是實作 \(方法主體\)。 部分方法針對每個唯一的簽章只能有一個定義宣告。 部分方法的每個多載版本必須有自己的定義宣告。  
  
### 更正這個錯誤  
  
1.  移除部分方法的所有定義宣告，只保留一個。  
  
## 範例  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## 請參閱  
 [部分類別和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)