---
title: "編譯器錯誤 CS0694 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0694
類型參數 'identifier' 與包含類型或方法的名稱相同  
  
 因為類型參數的名稱不能與包含類型參數的類型或方法名稱相同，所以您必須使用不同的類型參數名稱。  
  
## 範例  
 下列範例會產生 CS0694。  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## 範例  
 除了上述有關泛型類別的情況之外，方法也可能會發生這個錯誤：  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```