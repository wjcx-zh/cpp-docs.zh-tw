---
title: 編譯器錯誤 C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 2d6179657462325a30de0c4548becff4b4cf86c9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508071"
---
# <a name="compiler-error-c3541"></a>編譯器錯誤 C3541

' type '： typeid 無法套用至包含 ' auto ' 的類型

[Typeid](../../extensions/typeid-cpp-component-extensions.md)運算子無法套用至指定的型別，因為它包含 **`auto`** 規範。

## <a name="example"></a>範例

下列範例會產生 C3541。

```cpp
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-cpp.md)<br/>
[/Zc： auto (推算變數類型) ](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)
