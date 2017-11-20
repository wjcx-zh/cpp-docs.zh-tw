---
title: "編譯器警告 （層級 1） C4391 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4391
dev_langs: C++
helpviewer_keywords: C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 91ee6716ee5139da02319925609777ebfec08a56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4391"></a>編譯器警告 (層級 1) C4391
「 簽章': 內建函式，不正確的傳回型別必須是 'type'  
  
 編譯器內建函式宣告有錯誤的傳回型別。 產生的映像可能無法正確執行。  
  
 若要修正這個警告，請更正宣告或刪除宣告和簡單 #include 適當的標頭檔。  
  
 下列範例會產生 C4391:  
  
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