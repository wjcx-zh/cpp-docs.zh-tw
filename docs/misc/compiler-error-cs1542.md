---
title: "編譯器錯誤 CS1542 | Microsoft Docs"
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
  - "CS1542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1542"
ms.assetid: d7f60aa2-6645-472c-ac12-fa57a09fbd87
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1542
無法將 'dll' 加入至此組件，因為本身已經是組件；請使用 '\/R' 選項代替  
  
 使用 [\/addmodule](../Topic/-addmodule%20\(C%23%20Compiler%20Options\).md) 編譯器選項所參考的檔案，並未使用 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) 建置；請使用 [\/reference](../Topic/-reference%20\(C%23%20Compiler%20Options\).md) 在此編譯中參考該檔案。