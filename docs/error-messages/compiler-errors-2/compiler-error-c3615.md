---
title: 編譯器錯誤 C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652214"
---
# <a name="compiler-error-c3615"></a>編譯器錯誤 C3615

> constexpr 函式 '*函式*' 無法產生常數運算式

此函式*函式*不會評估為`constexpr`在編譯時期。 要`constexpr`，函式只能呼叫其他`constexpr`函式。

## <a name="example"></a>範例

Visual Studio 2017 會正確地引發錯誤時的條件式評估作業的左運算元不是有效`constexpr`內容。 在 Visual Studio 2015，但無法在 Visual Studio 2017 中，會編譯下列程式碼。

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

若要修正此問題，請宣告`array::size()`當作`constexpr`或移除`constexpr`限定詞的`f`。