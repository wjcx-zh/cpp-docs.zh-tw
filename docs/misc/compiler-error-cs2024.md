---
title: "編譯器錯誤 CS2024 | Microsoft Docs"
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
  - "CS2023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2024"
ms.assetid: 65cf7419-a5a6-4128-88af-176dc8dba14f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2024
無效的檔案區段記憶體對齊數值 '\#'  
  
 已將無效值傳遞給 [\/filealign](../Topic/-filealign%20\(C%23%20Compiler%20Options\).md) 編譯器選項。  
  
 下列範例會產生 CS2024：  
  
```  
// CS2024.cs // compile with: /filealign:ex // CS2024 expected class MyClass { public static void Main() { } }  
```