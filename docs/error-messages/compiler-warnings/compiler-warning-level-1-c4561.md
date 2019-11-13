---
title: 編譯器警告（層級1） C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: b0fd27142f0404a53fa2fee87fb2309e2f54d2c2
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965971"
---
# <a name="compiler-warning-level-1-c4561"></a>編譯器警告（層級1） C4561

' __fastcall ' 與 '/clr ' 選項不相容：轉換成 '\__stdcall '

[__Fastcall](../../cpp/fastcall.md)函式呼叫慣例不能與[/clr](../../build/reference/clr-common-language-runtime-compilation.md)編譯器選項一起使用。 編譯器會忽略 `__fastcall`的呼叫。 若要修正這個警告，請移除不含 **/clr**的 **__fastcall**或編譯呼叫。

下列範例會產生 C4561：

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```