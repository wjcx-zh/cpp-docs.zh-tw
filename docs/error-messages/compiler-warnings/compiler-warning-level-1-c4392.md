---
title: 編譯器警告 (層級 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: 1dc0c546509b17132358f432f6a781035a314a72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472198"
---
# <a name="compiler-warning-level-1-c4392"></a>編譯器警告 (層級 1) C4392

'signature': 不正確的內建函數的引數的數目必須是 'number' 引數

編譯器內建的函式宣告具有引數數目錯誤。 產生的映像可能無法正確執行。

若要修正這個警告，請更正宣告或刪除宣告並直接 #include 適當的標頭檔。

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