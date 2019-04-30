---
title: 編譯器警告 （層級 3） C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 09b6e5b8dc984b35df7de96f5cf8610f2b0f16af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401523"
---
# <a name="compiler-warning-level-3-c4839"></a>編譯器警告 （層級 3） C4839

> 類別的非標準用法*型別*' 做為引數的 variadic 函式

類別或結構，例如傳遞給 variadic 函式`printf`必須可透過極簡方式複製。 傳遞這類物件時，編譯器只會進行位元複製，而且不會呼叫建構函式或解構函式。

這項警告是在 Visual Studio 2017 中的開始提供。

## <a name="example"></a>範例

下列範例會產生 C4839:

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

若要更正錯誤，您可以呼叫會傳回可完整複製類型的成員函式，

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

針對字串使用建置和管理`CStringW`，提供`operator LPCWSTR()`應該用來轉換`CStringW`格式字串所預期的 C 指標的物件。

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```