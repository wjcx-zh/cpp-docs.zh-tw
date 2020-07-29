---
title: c + + 中的 constexpr lambda 運算式
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 24c70732093447649b3cfb460f63b2181efdf806
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213342"
---
# <a name="constexpr-lambda-expressions-in-c"></a>c + + 中的 constexpr lambda 運算式

**Visual Studio 2017 15.3 版和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： lambda 運算式可以在常數運算式中被宣告為 **`constexpr`** 或在常數運算式中使用的每個資料成員的初始化時，將其宣告為或用於常數運算式中。

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

如果 lambda 的結果符合函式的需求，則會隱含地 **`constexpr`** 執行此動作 **`constexpr`** ：

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

如果 lambda 是隱含或明確的 **`constexpr`** ，而且您將它轉換為函式指標，則產生的函數也會是 **`constexpr`** ：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[C + + 標準程式庫中的函式物件](../standard-library/function-objects-in-the-stl.md)<br/>
[函式呼叫](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
