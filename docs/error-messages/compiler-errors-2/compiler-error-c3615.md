---
title: 編譯器錯誤 C3615 |Microsoft 文件
ms.date: 10/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3615
dev_langs:
- C++
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1ab43f8e15535614cedf43dba42fef882bf87a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3615"></a>編譯器錯誤 C3615

> constexpr 函式 '*函式*' 不能產生常數運算式

此函式*函式*不會評估為`constexpr`在編譯時間。 要`constexpr`，函式只可以呼叫其他`constexpr`函式。

## <a name="example"></a>範例

Visual Studio 2017 正確就會引發錯誤時有條件地評估運算的左運算元不是有效`constexpr`內容。 在 Visual Studio 2015，但不是在 Visual Studio 2017，會編譯下列程式碼。

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

若要修正這個問題，請宣告`array::size()`做`constexpr`或移除`constexpr`限定詞的`f`。