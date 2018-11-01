---
title: Variadic 巨集
ms.date: 11/04/2016
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: 0674359b8f620c2b5023ce2ef75b4e247ae765f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547442"
---
# <a name="variadic-macros"></a>Variadic 巨集

Variadic 巨集是包含引數數目可變、類似函式的巨集。

## <a name="remarks"></a>備註

若要使用 variadic 巨集，省略符號可能會指定巨集定義，並取代識別項中的最後一個型式引數為`__VA_ARGS__`可能插入額外的引數定義中使用。  `__VA_ARGS__` 取代所有符合的省略符號，包括以逗點隔開的引數。

C 標準指定必須將至少一個引數傳遞給省略符號，確保巨集不會解析成具有尾端逗號的運算式。  如果沒有傳遞引數至省略符號，Visual C++ 實作會隱藏尾端逗號。

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