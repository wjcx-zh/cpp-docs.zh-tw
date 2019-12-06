---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: aec4df98413bf34ac1e2966d012bb905edd4775e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857927"
---
# <a name="__noop"></a>__noop

**Microsoft 專屬**

`__noop` 內建會指定應該忽略函數。 會剖析引數清單，但不會針對引數產生任何程式碼。 其目的是要用於採用可變數目之引數的全域偵錯工具。

編譯器會在編譯時期將內建函式（`__noop` 內建）轉換為0。

## <a name="example"></a>範例

下列程式碼顯示如何使用 `__noop`。

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

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
