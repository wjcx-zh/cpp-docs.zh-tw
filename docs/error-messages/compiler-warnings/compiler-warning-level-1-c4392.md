---
title: 編譯器警告 （層級 1） C4392 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4392
dev_langs:
- C++
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b64159737b9423f3d9ea55489eb28c20a2162d14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281254"
---
# <a name="compiler-warning-level-1-c4392"></a>編譯器警告 (層級 1) C4392
「 簽章': 內建函式的引數數目不正確，必須是 'number' 引數  
  
 編譯器內建函式宣告具有引數數目錯誤。 產生的映像可能無法正確執行。  
  
 若要修正這個警告，請更正宣告或刪除宣告和簡單 #include 適當的標頭檔。  
  
 下列範例會產生 C4392:  
  
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