---
title: "編譯器警告 (層級 1) C4392 | Microsoft Docs"
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
  - "C4392"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4392"
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4392
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'signature' : 內建函式的引數數目不正確，必須有 'number' 個引數  
  
 編譯器內建的函式宣告之引數數目錯誤。  結果影像可能無法正確執行。  
  
 若要修正這項警告，請更正宣告或刪除宣告，並且讓 \#include 成為適當的標頭檔。  
  
 下列範例會產生 C4392：  
  
```  
// C4392.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_stream_pd(double *dp);   // C4392  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```