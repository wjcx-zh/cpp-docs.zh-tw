---
title: 編譯器警告 (層級 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 24a3ca8b35266e93f298314f45015b7a480e2af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563783"
---
# <a name="compiler-warning-level-1-c4561"></a>編譯器警告 (層級 1) C4561

'__fastcall' 不具有 '/ /clr' 選項： 將轉換成 '\__stdcall'

[__Fastcall](../../cpp/fastcall.md)函式呼叫慣例不能搭配[/clr](../../build/reference/clr-common-language-runtime-compilation.md)編譯器選項。 編譯器會忽略呼叫`__fastcall`。 若要修正這個警告，移除對 **__fastcall**或編譯而不要 **/clr**。

下列範例會產生 C4561:

```
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```