---
title: "編譯器警告 (層級 1) C4077 | Microsoft Docs"
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
  - "C4077"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4077"
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4077
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未知的 check\_stack 選項  
  
 搭配未知引數使用 **check\_stack** pragma 的舊格式。 此引數必須是 `+`、`-`、`(on)`、`(off)` 或空白。  
  
 編譯器會忽略 pragma，並且不會變更堆疊檢查。  
  
## 範例  
  
```  
// C4077.cpp // compile with: /W1 /LD #pragma check_stack yes // C4077 #pragma check_stack +    // Correct old form #pragma check_stack (on) // Correct new form  
```