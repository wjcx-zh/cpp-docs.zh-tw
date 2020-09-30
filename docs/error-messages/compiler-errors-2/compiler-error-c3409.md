---
title: 編譯器錯誤 C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: d3800998ded1758ab1de92af689d9d4613c2c61e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502330"
---
# <a name="compiler-error-c3409"></a>編譯器錯誤 C3409

> 不允許空白的屬性區塊

## <a name="remarks"></a>備註

編譯器將方括弧解釋為 [屬性](../../windows/attributes/attributes-alphabetical-reference.md) 區塊，但找不到任何屬性。

當您使用方括弧作為 lambda 運算式定義的一部分時，編譯器可能會產生此錯誤。 當編譯器無法判斷方括弧是否為 lambda 運算式或屬性區塊定義的一部分時，就會發生這個錯誤。 如需 lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 如果方括弧是屬性區塊的一部分：

   1. 提供屬性區塊中的一或多個屬性。

   1. 移除屬性區塊。

1. 如果方括弧是 lambda 運算式的一部分，請確定 lambda 運算式遵循有效的語法規則。

   如需 lambda 運算式語法的詳細資訊，請參閱 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。

## <a name="examples"></a>範例

下列範例會產生 C3409。

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

下列範例會產生 C3409，因為 lambda 運算式使用 **`mutable`** 規格，但未提供參數清單。 編譯器無法判斷方括弧是否為 lambda 運算式或屬性區塊定義的一部分。

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>另請參閱

[屬性](../../windows/attributes/attributes-alphabetical-reference.md)<br/>
[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)
