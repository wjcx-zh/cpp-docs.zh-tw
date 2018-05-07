---
title: 編譯器警告 （層級 1 和層級 4） C4700 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4700
dev_langs:
- C++
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 876ae98fb2fdea5a9d8bdaecb93b8c229213d329
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>編譯器警告 (層級 1 和層級 4) C4700

> 未初始化的區域變數 '*名稱*' 使用

本機變數*名稱*已*用*，亦即，讀取之前它有, 已指派的值。 在 C 和 c + + 中，預設不會初始化本機變數。 未初始化的變數可以包含任何值，並使用會導致未定義的行為。 警告 C4700 幾乎都表示一個錯誤，可能會造成無法預期的結果或損毀您的程式。

若要修正此問題，您可以初始化本機變數宣告時, 或在使用前，將值指派給他們。 函式可以用來初始化的變數，會傳遞做為參考參數，或當其位址被當做指標參數。

## <a name="example"></a>範例

此範例會產生 C4700，當變數 t、 u 和 v 可用後再進行初始化，並顯示可能造成記憶體回收值的種類。 變數 x、 y 和 z 執行不會導致警告，因為它們會使用前進行初始化：

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

這段程式碼時執行、 t、 u 和 v 的初始化，而且 s 輸出，則無法預測：

```Output
Value in s: 37816963
Value in w: 42
```
