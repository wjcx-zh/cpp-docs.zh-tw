---
title: 編譯器錯誤 C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: c1a5b6edbc87e14de267cf962dc2b1a71dd6be12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200534"
---
# <a name="compiler-error-c3615"></a>編譯器錯誤 C3615

> constexpr 函數 '*function*' 無法產生常數運算式

無法在編譯時期將函數*函數*評估為 `constexpr`。 若要 `constexpr`，函數只能呼叫其他 `constexpr` 函數。

## <a name="example"></a>範例

當條件式評估作業的左運算元在 `constexpr` 內容中無效時，Visual Studio 2017 會正確地引發錯誤。 下列程式碼會在 Visual Studio 2015 中進行編譯，但不會在 Visual Studio 2017 中進行編譯。

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

若要修正此問題，請將 `array::size()` 函式宣告為 `constexpr`，或從 `f`移除 `constexpr` 辨識符號。
