---
title: "/moduleassemblyname 選項只能在建置 &#39;module&#39; 類型的目標時指定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /moduleassemblyname 選項只能在建置 &#39;module&#39; 類型的目標時指定
Visual Basic 編譯器已傳遞 `/moduleassemblyname` 編譯器選項，但 `/target` 選項設定為 `module` 以外的值。  
  
 **錯誤 ID︰**BC2030  
  
### 更正這個錯誤  
  
1.  移除 `/moduleassemblyname` 編譯器選項，或將 `/target` 選項設定為 `module`。  
  
## 請參閱  
 [\/target](../Topic/-target%20\(Visual%20Basic\).md)   
 [\/moduleassemblyname](../Topic/-moduleassemblyname.md)   
 [Visual Basic Command\-Line Compiler](../Topic/Visual%20Basic%20Command-Line%20Compiler.md)