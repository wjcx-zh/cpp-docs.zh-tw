---
title: 編譯器警告 (層級 1 和層級 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300288"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>編譯器警告 (層級 1 和層級 4) C4700

> 未初始化的區域變數 '*名稱*' 使用

區域變數*名稱*已*使用*，也就是讀取，它具有之前已經指派值。 在 C 和C++，預設不會初始化本機變數。 未初始化的變數可以包含任何值，和其用法會導致未定義的行為。 警告 C4700 幾乎一律會表示可能會造成無法預期的結果或損毀您的程式有 bug。

若要修正此問題，您可以初始化區域變數在宣告時，或將值指派給他們，再使用它們。 函式可用來初始化的變數，傳遞做為參考參數，或者當其位址被當做指標參數。

## <a name="example"></a>範例

變數 t、 u 和 v 後再進行初始化，並顯示可能會造成的廢棄項目值的類型使用時，此範例會產生 C4700。 變數 x、 y 和 z 執行不會造成警告，因為它們會在使用前先初始化：

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

這段程式碼時執行、 t、 u 和 v 的未初始化，而且 s 輸出是無法預測：

```Output
Value in s: 37816963
Value in w: 42
```
