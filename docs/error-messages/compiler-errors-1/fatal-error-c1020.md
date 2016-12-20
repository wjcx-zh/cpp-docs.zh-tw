---
title: "嚴重錯誤 C1020 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1020"
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的 \#endif  
  
 `#endif` 指示詞沒有對應的 `#if`、`#ifdef` 或 `#ifndef` 指示詞。 每個 `#endif` 都一定要有對應的指示詞。  
  
 下列範例會產生 C1020：  
  
```  
// C1020.cpp #endif     // C1020  
```  
  
 可能的解決方式：  
  
```  
// C1020b.cpp // compile with: /c #if 1 #endif  
```