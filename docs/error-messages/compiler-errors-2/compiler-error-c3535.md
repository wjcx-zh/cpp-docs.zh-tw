---
title: 編譯器錯誤 C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: a4bda0825e8b71eb49fe9691755d8e42fd059c06
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510093"
---
# <a name="compiler-error-c3535"></a>編譯器錯誤 C3535

無法從 ' type2 ' 推算 ' type1 ' 的類型

**`auto`** 無法從初始化運算式的類型推算關鍵字所宣告的變數類型。 例如，如果初始化運算式評估為 **`void`** （不是型別），就會發生這個錯誤。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 確定初始化運算式的類型不是 **`void`** 。

1. 確定宣告不是基本類型的指標。 如需詳細資訊，請參閱 [基本類型](../../cpp/fundamental-types-cpp.md)。

1. 確定宣告為類型的指標時，初始化運算式是指標類型。

## <a name="examples"></a>範例

下列範例會產生 C3535，因為初始化運算式會評估為 **`void`** 。

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

下列範例會產生 C3535，因為語句會將變數宣告 `x` 為推算型別的指標，但初始化運算式運算式的類型為 double。 因此，編譯器無法推算變數的類型。

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

下列範例會產生 C3535，因為變數會宣告推算 `p` 型別的指標，但初始化運算式不是指標類型。

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-cpp.md)<br/>
[基本類型](../../cpp/fundamental-types-cpp.md)
