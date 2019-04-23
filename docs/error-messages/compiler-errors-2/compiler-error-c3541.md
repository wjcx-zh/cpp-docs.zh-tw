---
title: 編譯器錯誤 C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 03361fa3e8d4ecb9647d354dd402a9f2b0865eb6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037681"
---
# <a name="compiler-error-c3541"></a>編譯器錯誤 C3541

'type': typeid 無法套用至包含 'auto' 的類型

[Typeid](../../extensions/typeid-cpp-component-extensions.md)運算子不能套用至指定的類型，因為它包含`auto`規範。

## <a name="example"></a>範例

下列範例會產生 C3541。

```
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

[auto 關鍵字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (推算變數類型)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)