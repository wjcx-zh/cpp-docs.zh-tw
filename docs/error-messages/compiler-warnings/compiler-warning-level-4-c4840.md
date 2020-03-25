---
title: 編譯器警告（層級4） C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185200"
---
# <a name="compiler-warning-level-4-c4840"></a>編譯器警告（層級4） C4840

> 以不可攜的方式使用類別 '*type*' 做為 variadic 函數的引數

## <a name="remarks"></a>備註

傳遞至 variadic 函數的類別或結構必須是完整可複製。 傳遞這類物件時，編譯器只會進行位元複製，而且不會呼叫建構函式或解構函式。

從 Visual Studio 2017 開始提供此警告。

## <a name="example"></a>範例

下列範例會產生 C4840，並顯示如何修正此問題：

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

針對使用 `CStringW`建立和管理的字串，提供的 `operator LPCWSTR()` 應該用來將 `CStringW` 物件轉換成格式字串所預期的 C 樣式字串指標：

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
