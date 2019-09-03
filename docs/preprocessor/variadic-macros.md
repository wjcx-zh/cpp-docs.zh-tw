---
title: Variadic 宏
ms.date: 08/29/2019
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: 171ea797adc1e407a8b7ef0592508653f758df64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216528"
---
# <a name="variadic-macros"></a>Variadic 宏

Variadic 巨集是包含引數數目可變、類似函式的巨集。

## <a name="remarks"></a>備註

若要使用 variadic 宏, 可以將省略號指定為巨集定義中的最終型式引數, 並在定義中`__VA_ARGS__`使用取代識別碼來插入額外的引數。  `__VA_ARGS__`會由所有符合省略號的引數所取代, 包括它們之間的逗號。

C 標準指定至少必須將一個引數傳遞至省略號, 以確保宏不會解析為尾端逗號的運算式。 如果沒有任何C++引數傳遞至省略號, 傳統的 Microsoft 執行會隱藏尾端的逗號。

## <a name="example"></a>範例

```cpp
// variadic_macros.cpp
#include <stdio.h>
#define EMPTY

#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }
#define CHECK3(...) { printf(__VA_ARGS__); }
#define MACRO(s, ...) printf(s, __VA_ARGS__)

int main() {
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print

    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");

    // always invokes printf in the macro
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");

    MACRO("hello, world\n");

    MACRO("error\n", EMPTY); // would cause error C2059, except VC++
                             // suppresses the trailing comma
}
```

```Output
here are some varargs1(1)
here are some varargs2(4)
here are some varargs3(5)
hello, world
error
```

## <a name="see-also"></a>另請參閱

[巨集 (C/C++)](../preprocessor/macros-c-cpp.md)
