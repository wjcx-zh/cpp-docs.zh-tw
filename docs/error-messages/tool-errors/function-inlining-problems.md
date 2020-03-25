---
title: 函式內嵌問題
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184238"
---
# <a name="function-inlining-problems"></a>函式內嵌問題

如果您使用的是函數內嵌，您必須：

- 將內嵌函式實作為您所包含的標頭檔。

- 在標頭檔中開啟內嵌功能。

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

然後，

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

如果您使用 `#pragma inline_depth` 編譯器指示詞，請確定您的值為2或更大的集合。 值若為零，將會關閉內嵌。 也請確定您使用的是 **/Ob1**或 **/Ob2**編譯器選項。

在不同的模組上混合內嵌和非內嵌編譯選項有時可能會造成問題。 如果連結C++庫是使用開啟的函式內嵌（[/Ob1](../../build/reference/ob-inline-function-expansion.md)或[/Ob2](../../build/reference/ob-inline-function-expansion.md)）所建立，但描述函式的對應標頭檔已關閉內嵌（沒有選項），您將會收到錯誤 LNK2001。 函式不會內嵌至標頭檔中的程式碼，但是因為它們不在程式庫檔案中，所以沒有任何位址可以解析參考。

同樣地，使用函式內嵌的專案會定義 .cpp 檔案中的函式，而不是標頭檔中的函式，也會取得 LNK2019。 標頭檔會被視為適當的任何位置，但只有在 .cpp 檔案通過編譯器時，才會內嵌函式;因此，連結器在其他模組中使用時，會將函式視為無法解析的外部函數。

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

然後

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

然後

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>另請參閱

[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
