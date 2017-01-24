---
title: "編譯器錯誤 C3641 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3641"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3641"
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3641
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 對以 \/clr:pure 或 \/clr:safe 編譯的函式無效的呼叫慣例 'calling\_convention'  
  
 只有 [\_\_clrcall](../../cpp/clrcall.md) 呼叫慣例允許配合 [\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) 使用。  
  
 下列範例會產生 C3641：  
  
```  
// C3641.cpp  
// compile with: /clr:pure /c  
void __cdecl f() {}   // C3641  
```