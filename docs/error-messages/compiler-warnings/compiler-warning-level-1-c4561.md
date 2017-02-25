---
title: "編譯器警告 (層級 1) C4561 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4561"
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 1) C4561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\_\_fastcall' 與 '\/clr' 選項不符：轉換為 '\_\_stdcall'  
  
 [\_\_fastcall](../../cpp/fastcall.md) 函式呼叫慣例無法與 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項一同使用。  編譯器會忽略對 `__fastcall` 的呼叫。  若要解除這項警告，請移除對 **\_\_fastcall** 的呼叫，或不使用 **\/clr** 編譯。  
  
 下列範例會產生 C4561：  
  
```  
// C4561.cpp  
// compile with: /clr /W1 /c  
// processor: x86  
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve  
```