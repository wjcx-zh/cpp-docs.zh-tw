---
title: 編譯器錯誤 C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 74a114245e350f174c05e5009775545bd42faf5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486641"
---
# <a name="compiler-error-c3535"></a>編譯器錯誤 C3535

無法推算類型 'type1' 從 'type2'

所宣告變數的型別`auto`無法從初始化運算式的類型推算關鍵字。 比方說，這個錯誤發生於初始化運算式評估為`void`，這不是型別。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 確定初始化運算式的型別不是`void`。

1. 請確定宣告不是基本類型的指標。 如需詳細資訊，請參閱 <<c0> [ 基本類型](../../cpp/fundamental-types-cpp.md)。

1. 請確定如果的宣告類型的指標，初始化運算式會是指標類型。

## <a name="example"></a>範例

下列範例會產生 C3535，因為初始化運算式評估為`void`。

```
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

下列範例會產生 C3535，因為陳述式會宣告變數`x`推算的類型，但在初始設定式類型的指標運算式是雙精度浮點。 因此，編譯器無法推斷變數的類型。

```
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>範例

下列範例會產生 C3535，因為變數`p`宣告指標推算的類型，但初始化運算式不是指標類型。

```
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)<br/>
[基本類型](../../cpp/fundamental-types-cpp.md)