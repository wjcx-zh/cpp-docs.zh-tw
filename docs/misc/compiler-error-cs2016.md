---
title: "編譯器錯誤 CS2016 | Microsoft Docs"
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
  - "CS2016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2016"
ms.assetid: 69f77502-f726-4856-ac87-e556eeb67349
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2016
字碼頁 'codepage' 無效或是尚未安裝  
  
 無效的值傳遞到 [\/codepage](../Topic/-codepage%20\(C%23%20Compiler%20Options\).md) 編譯器選項中。  
  
 下列範例會產生 CS2016：  
  
```  
// CS2016.cs // compile with: /codepage:x // CS2016 expected class MyClass { public static void Main() { } }  
```