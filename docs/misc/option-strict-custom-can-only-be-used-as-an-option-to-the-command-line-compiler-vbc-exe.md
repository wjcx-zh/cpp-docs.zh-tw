---
title: "Option Strict Custom 只能當做命令列編譯器 (vbc.exe) 選項使用 | Microsoft Docs"
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
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict Custom 只能當做命令列編譯器 (vbc.exe) 選項使用
`Option Strict` 陳述式只接受 `On` 和 `Off` 作為引數；不允許 `Option Strict Custom`。  
  
 請使用 `/optionstrict:custom` 編譯器選項，以在未遵守嚴格的語意時發出警告。  
  
 **錯誤 ID︰**BC31141  
  
### 更正這個錯誤  
  
1.  從原始程式碼中移除 `Option Strict Custom`。  
  
2.  指定 `/optionstrict:custom` 選項。 如需詳細資訊，請參閱[\/optionstrict](../Topic/-optionstrict.md)。  
  
## 請參閱  
 [Option \<keyword\> Statement](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [\/optionstrict](../Topic/-optionstrict.md)