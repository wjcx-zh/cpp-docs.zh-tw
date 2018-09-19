---
title: 編譯器警告 （層級 1） C4391 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4391
dev_langs:
- C++
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0b3873beb635afe81cee3030a78d2b1223197a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047081"
---
# <a name="compiler-warning-level-1-c4391"></a>編譯器警告 (層級 1) C4391

'signature': 不正確的傳回型別為內建函式，必須是 'type'

編譯器內建的函式宣告有錯誤的傳回型別。 產生的映像可能無法正確執行。

若要修正這個警告，請更正宣告或刪除宣告並直接 #include 適當的標頭檔。

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