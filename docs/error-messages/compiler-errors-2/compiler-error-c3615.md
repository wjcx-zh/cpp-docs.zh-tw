---
title: 編譯器錯誤 C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: 17a210e2a514af1ffd62bf38651c4d17bd1fe32b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230788"
---
# <a name="compiler-error-c3615"></a>編譯器錯誤 C3615

> constexpr 函數 '*function*' 無法產生常數運算式

*函數函式無法* **`constexpr`** 在編譯時期評估為。 為 **`constexpr`** ，函數只能呼叫其他函式 **`constexpr`** 。

## <a name="example"></a>範例

當條件式評估作業的左運算元在內容中無效時，Visual Studio 2017 會正確地引發錯誤 **`constexpr`** 。 下列程式碼會在 Visual Studio 2015 中進行編譯，但不會在 Visual Studio 2017 中進行編譯。

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

若要修正此問題，請將函式宣告 `array::size()` 為， **`constexpr`** 或從移除辨識 **`constexpr`** 符號 `f` 。
