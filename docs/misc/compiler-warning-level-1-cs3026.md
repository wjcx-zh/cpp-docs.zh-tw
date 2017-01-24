---
title: "編譯器警告 (層級 1) CS3026 | Microsoft Docs"
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
  - "CS3026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3026"
ms.assetid: 6c57b2e3-3011-42db-b450-ce9e04c4b4ca
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3026
符合 CLS 標準的欄位 'field' 不可為 volatile  
  
 volatile 變數不應該符合 CLS 標準。  
  
## 範例  
 下列範例會產生 CS3026。  
  
```  
// CS3026.cs [assembly:System.CLSCompliant(true)] public class Test { public volatile int v0 =0;   // CS3026 // To resolve remove the CLS-CComplient attribute. public static void Main() { } }  
  
```