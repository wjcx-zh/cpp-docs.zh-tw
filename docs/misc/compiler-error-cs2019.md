---
title: "編譯器錯誤 CS2019 | Microsoft Docs"
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
  - "CS2019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2019"
ms.assetid: eafd2531-8b3a-499c-9e12-a605a011396f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2019
\/target: 的目標類型無效。必須指定 'exe'、'winexe'、'library' 或 'module'。  
  
 已使用 [\/target](../Topic/-target%20\(C%23%20Compiler%20Options\).md) 編譯器選項，但傳遞的參數無效。 若要解決此錯誤，請使用適合您輸出檔之 **\/target** 選項的形式重新編譯程式。  
  
 下列範例會產生 CS2017：  
  
```  
// CS2019.cs // compile with: /target:libra // CS2019 expected class MyClass { }  
```