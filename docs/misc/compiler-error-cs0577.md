---
title: "編譯器錯誤 CS0577 | Microsoft Docs"
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
  - "CS0577"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0577"
ms.assetid: 34f8f453-f016-4f2c-981a-0d61449cd74b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0577
Conditional 屬性在 'function' 上無效，因為它是建構函式、解構函式、運算子或明確介面實作  
  
 `Conditional` 無法套用至指定的方法。  
  
 例如，您無法在明確介面定義上使用某些屬性。 下列範例會產生 CS0577：  
  
```  
// CS0577.cs // compile with: /target:library interface I { void m(); } public class MyClass : I { [System.Diagnostics.Conditional("a")]   // CS0577 void I.m() {} }  
```