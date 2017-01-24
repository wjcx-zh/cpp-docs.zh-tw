---
title: "編譯器錯誤 CS2020 | Microsoft Docs"
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
  - "CS2020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2020"
ms.assetid: b2db7a05-5965-4a9b-86c3-0c4792b29a6c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2020
只有第一組輸入檔可以建置 'module' 以外的目標  
  
 在多重輸出編譯中，第一個輸出檔必須以 [\/target:exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md)、[\/target:winexe](../Topic/-target:winexe%20\(C%23%20Compiler%20Options\).md) 或 [\/target:library](../Topic/-target:library%20\(C%23%20Compiler%20Options\).md) 建置。 任何後續的輸出檔則必須以 [\/target: module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) 建置。