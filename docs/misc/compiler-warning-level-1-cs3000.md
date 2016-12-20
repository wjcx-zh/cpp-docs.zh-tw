---
title: "編譯器警告 (層級 1) CS3000 | Microsoft Docs"
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
  - "CS3000"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3000"
ms.assetid: 37cdd3dc-8481-4e29-b78c-281baeca2d64
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3000
具有變數引數的方法不符合 CLS 標準  
  
 方法中所使用的引數會公開不符合 Common Language Specifications \(CLS\) 標準的功能。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)。  
  
 下列範例會產生警告 CS3000。  
  
```  
// CS3000.cs // compile with: /target:library // CS3000 expected [assembly:System.CLSCompliant(true)] public class Test { public void AddABunchOfInts( __arglist ) {}   // CS3000 }  
```