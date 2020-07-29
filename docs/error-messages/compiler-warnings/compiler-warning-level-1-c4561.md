---
title: 編譯器警告 (層級 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: fe8ae1f8ef8180f2d3c5ba9ae2401b9447b22527
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230632"
---
# <a name="compiler-warning-level-1-c4561"></a>編譯器警告 (層級 1) C4561

' __fastcall ' 與 '/clr ' 選項不相容：轉換成 ' \_ _stdcall '

[__Fastcall](../../cpp/fastcall.md)函式呼叫慣例不能與[/clr](../../build/reference/clr-common-language-runtime-compilation.md)編譯器選項一起使用。 編譯器會忽略對的呼叫 **`__fastcall`** 。 若要修正這個警告，請在 **`__fastcall`** 不含 **/clr**的情況下移除或編譯的呼叫。

下列範例會產生 C4561：

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
