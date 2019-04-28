---
title: 編譯器警告 （層級 4） C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a757004659c1a9d2ce858cfae5ddfbc6c024d782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360004"
---
# <a name="compiler-warning-level-4-c4840"></a>編譯器警告 （層級 4） C4840

> 非可移植的類別的用法*型別*' 做為引數的 variadic 函式

## <a name="remarks"></a>備註

類別或結構傳遞給 variadic 函式必須是可完整複製。 傳遞這類物件時，編譯器只會進行位元複製，而且不會呼叫建構函式或解構函式。

這項警告是在 Visual Studio 2017 中的開始提供。

## <a name="example"></a>範例

下列範例會產生 C4840，並示範如何修正此問題：

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

針對字串使用建置和管理`CStringW`，提供`operator LPCWSTR()`應該用來轉換`CStringW`格式字串所預期的 C 樣式字串指標的物件：

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```