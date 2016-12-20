---
title: "編譯器錯誤 CS1508 | Microsoft Docs"
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
  - "CS1508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1508"
ms.assetid: 979bc615-58ce-49f8-ba73-e6cf57c56418
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1508
在這個組件中已經使用過資源識別項 'identifier'  
  
 在編譯中，相同的識別項 \(***identifier***\) 已傳遞給兩個或多個 [\/resource](../Topic/-resource%20\(C%23%20Compiler%20Options\).md) 或 [\/linkresource](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md) 編譯器選項。  
  
 例如，下列選項會產生 CS1508：  
  
```  
/resource:anyfile.bmp,DuplicatIdent /linkresource:a.bmp,DuplicatIdent  
```