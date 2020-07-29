---
title: 編譯器錯誤 C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2117832ffd5a90612e9745a3706f01e3b5d1b18d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197666"
---
# <a name="compiler-error-c3485"></a>編譯器錯誤 C3485

Lambda 定義不能有任何 cv 限定詞

您不能使用 **`const`** 或 **`volatile`** 限定詞做為 lambda 運算式定義的一部分。

### <a name="to-correct-this-error"></a>更正這個錯誤

- **`const`** 請 **`volatile`** 從 lambda 運算式的定義中移除或限定詞。

## <a name="example"></a>範例

下列範例會產生 C3485，因為它會使用 **`const`** 限定詞作為 lambda 運算式定義的一部分：

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
