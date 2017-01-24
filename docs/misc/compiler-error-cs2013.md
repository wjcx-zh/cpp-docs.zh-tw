---
title: "編譯器錯誤 CS2013 | Microsoft Docs"
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
  - "CS2013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2013"
ms.assetid: 8a57b4c8-02fc-4f73-b489-121ff468c17d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2013
映像基底編號 'value' 無效  
  
 已將無效值 \(非數字\) 傳遞給 [\/baseaddress](../Topic/-baseaddress%20\(C%23%20Compiler%20Options\).md) 編譯器選項。  
  
 下列範例會產生 CS2013：  
  
```  
// CS2013.cs // compile with: /target:library /baseaddress:x // CS2013 expected class MyClass { }  
```