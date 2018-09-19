---
title: 編譯器錯誤 C2164 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2164
dev_langs:
- C++
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1e997a3b260b9ec8b68a92967233269707e6888
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032155"
---
# <a name="compiler-error-c2164"></a>編譯器錯誤 C2164

'function': 未宣告的內建函式

`intrinsic` Pragma 會使用未宣告的函式 (只會發生 **/Oi**)。 或者，但不包括其標頭檔所使用的其中一個編譯器內建函式。

下列範例會產生 C2164:

```
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```