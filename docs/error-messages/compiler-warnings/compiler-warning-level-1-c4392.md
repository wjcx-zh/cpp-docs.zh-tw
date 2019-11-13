---
title: 編譯器警告（層級1） C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: b19080f4a86267a48618a5f40d7576c07c96c18a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966111"
---
# <a name="compiler-warning-level-1-c4392"></a>編譯器警告（層級1） C4392

' signature '：內建函式的引數數目不正確，應為 ' number ' 個引數

編譯器內建的函式宣告有錯誤的引數數目。 產生的映射可能無法正確執行。

若要修正這個警告，請更正宣告或刪除宣告，並直接 #include 適當的標頭檔。

下列範例會產生 C4392：

```cpp
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