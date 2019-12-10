---
title: 編譯器警告 (層級 3) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: c1989518c3965f8faa54a05b2925d0e37455625e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991701"
---
# <a name="compiler-warning-level-3-c4738"></a>編譯器警告 (層級 3) C4738

在記憶體中儲存 32 位元浮點結果，可能會損失效能

C4738 會警告，指派、轉換、傳遞的引數或其他作業的結果可能需要四捨五入，或操作已用盡暫存器，而且需要使用記憶體（溢出）。 這可能會導致效能降低。

若要解決此警告並避免四捨五入，請使用[/fp： fast](../../build/reference/fp-specify-floating-point-behavior.md)進行編譯，或使用 `double` 而不是 `float`。

若要解決此警告並避免暫存器用盡，請變更計算的順序，並修改內嵌的使用

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>範例

下列範例會產生 C4738：

```cpp
// C4738.cpp
// compile with: /c /fp:precise /O2 /W3
// processor: x86
#include <stdio.h>

#pragma warning(default : 4738)

float func(float f)
{
    return f;
}

int main()
{
    extern float f, f1, f2;
    double d = 0.0;

    f1 = func(d);
    f2 = (float) d;
    f = f1 + f2;   // C4738
    printf_s("%f\n", f);
}
```
