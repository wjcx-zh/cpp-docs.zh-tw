---
title: "編譯器警告 （層級 3） C4839 |Microsoft 文件"
ms.date: 10/25/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C4839
dev_langs:
- C++
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aee1e564ffd72b9b08d883c94311c2bca72b5aef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4839"></a>編譯器警告 （層級 4） C4839

> 類別使用非標準*類型*' 當做 variadic 函式的引數

在 Visual Studio 2017，類別或結構會傳遞給 variadic 函式例如`printf`必須是可完整複製。 傳遞這類物件時，編譯器只會進行位元複製，而且不會呼叫建構函式或解構函式。

## <a name="example"></a>範例

下列範例會產生 C4839:

```cpp
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

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

若要更正錯誤，您可以呼叫會傳回可完整複製類型的成員函式，

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

或者先執行靜態轉型來轉換物件，再傳遞它︰

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

建置和管理使用字串`CStringW`，提供`operator LPCWSTR()`應該用來轉換`CStringW`C 指標的格式字串所預期的物件。

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```