---
title: "編譯器錯誤 CS1722 | Microsoft Docs"
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
  - "CS1722"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1722"
ms.assetid: cf698a80-e4c9-46e2-96a0-8b8b5a08fc37
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1722
基底類別 'class' 必須在任何介面的前面  
  
 指定要繼承的來源類別以及要實作的介面時，必須先指定類別名稱。  
  
## 範例  
 下列範例會產生 CS1722。  
  
```  
// CS1722.cs // compile with: /target:library public class A {} interface I {} public class MyClass : I, A {}   // CS1722 public class MyClass2 : A, I {}   // OK  
```