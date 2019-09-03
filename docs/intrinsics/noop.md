---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 24ba85b1fbbba4491c03d5a81afae345228db3bd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217191"
---
# <a name="__noop"></a>__noop

**Microsoft 專屬**

`__noop`內建會指定應該忽略函數。 會剖析引數清單, 但不會針對引數產生任何程式碼。 其目的是要用於採用可變數目之引數的全域偵錯工具。

編譯器會在編譯`__noop`時期將內建函式轉換為0。

## <a name="example"></a>範例

下列程式碼顯示如何使用`__noop`。

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

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
