---
title: "編譯器警告 (層級 1) C4391 | Microsoft Docs"
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
  - "C4391"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4391"
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4391
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'signature' : 內建函式的傳回型別不正確，必須是 'type'  
  
 編譯器內建的函式宣告有錯誤的傳回型別。  結果影像可能無法正確執行。  
  
 若要修正這項警告，請更正宣告或刪除宣告，並且讓 \#include 成為適當的標頭檔。  
  
 下列範例會產生 C4391：  
  
```  
// C4391.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_load_ss(float *p);   // C4391  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```