---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: e12855127e417472eb88c951b71881240b808013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214200"
---
# <a name="__noop"></a>__noop

**Microsoft 特定的**

內建 **`__noop`** 會指定應該忽略函數。 會剖析引數清單，但不會針對引數產生任何程式碼。 其目的是要用於採用可變數目之引數的全域偵錯工具。

**`__noop`** 編譯器會在編譯時期將內建函式轉換為0。

## <a name="example"></a>範例

下列程式碼顯示如何使用 **`__noop`** 。

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
