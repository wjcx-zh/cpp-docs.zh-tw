---
title: 中的 constexpr lambda 運算式C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 9467d9e404204012df6461adacd5dc4cdbdfe71d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179571"
---
# <a name="constexpr-lambda-expressions-in-c"></a>中的 constexpr lambda 運算式C++

**Visual Studio 2017 15.3 版和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）： lambda 運算式可以宣告為**constexpr** ，或在常數運算式中允許其所捕捉或引進之每個資料成員的初始化時使用。

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

如果 lambda 的結果符合**constexpr**函數的需求，就會隱含**constexpr** ：

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

如果 lambda 是隱含或明確的**constexpr**，而且您將它轉換成函式指標，則產生的函式也會是**constexpr**：

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫的函式物件](../standard-library/function-objects-in-the-stl.md)<br/>
[函式呼叫](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
