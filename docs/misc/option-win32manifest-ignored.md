---
title: "已忽略 /win32manifest 選項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 已忽略 /win32manifest 選項
已忽略 \/win32manifest 選項。 只能在目標為組件時指定此選項。  
  
 已傳遞 `/win32manifest` 編譯器選項給 Visual Basic 編譯器，但 `/target` 選項設定為 `module`。  
  
 **錯誤 ID︰**BC2034  
  
### 更正這個錯誤  
  
1.  請移除 `/win32manifest` 編譯器選項，或將 `/target` 選項設為 `exe`、`winexe` 或 `library`。  
  
## 請參閱  
 [\/target](../Topic/-target%20\(Visual%20Basic\).md)   
 [\/win32manifest](../Topic/-win32manifest%20\(Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../Topic/Visual%20Basic%20Command-Line%20Compiler.md)