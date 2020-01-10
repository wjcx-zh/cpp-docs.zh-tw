---
title: 編譯器錯誤 C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 6b487c0f94a00ec64e0c2178265c5a8c27544a51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761552"
---
# <a name="compiler-error-c3535"></a>編譯器錯誤 C3535

無法從 ' type2 ' 推算 ' type1 ' 的類型

無法從初始化運算式的類型推算 `auto` 關鍵字所宣告的變數類型。 例如，如果初始化運算式評估為 `void`，而不是型別，就會發生這個錯誤。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 請確定初始化運算式的類型不是 `void`。

1. 請確定宣告不是基本類型的指標。 如需詳細資訊，請參閱[基本類型](../../cpp/fundamental-types-cpp.md)。

1. 請確定如果宣告是類型的指標，初始化運算式就是指標類型。

## <a name="example"></a>範例

下列範例會產生 C3535，因為初始化運算式會評估為 `void`。

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>範例

下列範例會產生 C3535，因為語句會將變數 `x` 宣告為推算類型的指標，但初始化運算式運算式的類型為 double。 因此，編譯器無法推算變數的類型。

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>範例

下列範例會產生 C3535，因為變數 `p` 宣告已推算類型的指標，但初始化運算式不是指標類型。

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)<br/>
[基本類型](../../cpp/fundamental-types-cpp.md)
