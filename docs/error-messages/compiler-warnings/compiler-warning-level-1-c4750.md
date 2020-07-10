---
title: 編譯器警告 (層級 1) C4750
description: 描述有關可能的堆疊溢位的 MSVC 編譯器警告 C4750。
ms.date: 07/08/2020
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 9a22bdda407b02b8723b7198d62289d39f62792d
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180964"
---
# <a name="compiler-warning-level-1-c4750"></a>編譯器警告 (層級 1) C4750

> '*identifier*'： _alloca ( # A1 內嵌到迴圈中的函式

## <a name="remarks"></a>備註

'*Identifier*' 函式會強制函式 [`_alloca`](../../c-runtime-library/reference/alloca.md) 在迴圈中內嵌展開，這可能會在執行迴圈時造成堆疊溢位。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請確定 '*identifier*' 函式未以規範修改 [`__forceinline`](../../cpp/inline-functions-cpp.md) 。

1. 請確定 '*identifier*' 函式不包含 [`_alloca`](../../c-runtime-library/reference/alloca.md) 包含在迴圈中的函式。

1. 請勿指定 [`/O1`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 、 [`/O2`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 、 [`/Ox`](../../build/reference/ox-full-optimization.md) 或 [`/Og`](../../build/reference/og-global-optimizations.md) 編譯參數。

1. 將函 [`_alloca`](../../c-runtime-library/reference/alloca.md) 式放在會攔截堆疊溢位的[try-except 語句](../../cpp/try-except-statement.md)中。

## <a name="example"></a>範例

下列程式碼範例會呼叫迴圈中的 `MyFunction` ，而 `MyFunction` 會呼叫 `_alloca` 函式。 `__forceinline` 修飾詞會造成 `_alloca` 函式的內嵌展開。

```cpp
// c4750.cpp
// compile with: /O2 /W1 /c
#include <intrin.h>

char * volatile newstr;

__forceinline void myFunction(void) // C4750 warning
{
// The _alloca function does not require a __try/__except
// block because the example uses compiler option /c.
    newstr = (char * volatile) _alloca(1000);
}

int main(void)
{
    for (int i=0; i<50000; i++)
       myFunction();
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[_alloca](../../c-runtime-library/reference/alloca.md)
