---
title: "編譯器錯誤 CS2007 | Microsoft Docs"
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
  - "CS2007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2007"
ms.assetid: 9be20e8e-2424-4435-9371-778fb12823c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2007
無法辨認的命令列選項: 'option'  
  
 編譯器所傳遞的字串不是[編譯器選項](../Topic/C%23%20Compiler%20Options.md)，即使它的開頭為正斜線 \(\/\) 也是一樣。  
  
 下列範例會產生 CS2007：  
  
```  
// CS2007.cs // compile with: /recur // CS2007 expected class x { public static void Main() {} }  
```