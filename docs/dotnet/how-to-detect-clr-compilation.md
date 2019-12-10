---
title: 如何：偵測-clr 編譯
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 42b2952e3b63023ca26c6b1f7d0ccb8871082499
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988218"
---
# <a name="how-to-detect-clr-compilation"></a>如何：偵測 /clr 編譯

使用 `_MANAGED` 或 `_M_CEE` 宏來查看模組是否使用 **/clr**進行編譯。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../build/reference/clr-common-language-runtime-compilation.md)。

如需宏的詳細資訊，請參閱[預先定義的宏](../preprocessor/predefined-macros.md)。

## <a name="example"></a>範例

```cpp
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
