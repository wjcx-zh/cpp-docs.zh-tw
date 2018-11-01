---
title: 編譯器錯誤 C2157
ms.date: 11/04/2016
f1_keywords:
- C2157
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
ms.openlocfilehash: 1338a0f0ceb1a42ed84fe74e4ed9a2d774979075
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450943"
---
# <a name="compiler-error-c2157"></a>編譯器錯誤 C2157

'function': 在 pragma 清單中使用之前必須先宣告

未宣告函式名稱，便在 [alloc_text](../../preprocessor/alloc-text.md) pragma 的函式清單中參考此名稱。

下列範例會產生 C2157：

```
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```