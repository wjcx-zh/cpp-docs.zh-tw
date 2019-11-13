---
title: 編譯器警告（層級1） C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: 60b68906697f76d56ff6c0e13f1b4ec105ef1c25
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966120"
---
# <a name="compiler-warning-level-1-c4391"></a>編譯器警告（層級1） C4391

' signature '：內建函式的傳回類型不正確，應為 ' type '

編譯器內建的函式宣告具有錯誤的傳回類型。 產生的映射可能無法正確執行。

若要修正這個警告，請更正宣告或刪除宣告，並直接 #include 適當的標頭檔。

下列範例會產生 C4391：

```cpp
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