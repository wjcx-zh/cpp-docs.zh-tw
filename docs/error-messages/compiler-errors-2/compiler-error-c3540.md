---
title: 編譯器錯誤 C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 897defd5643a90234c2ae3b7bb4f58904864e858
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508078"
---
# <a name="compiler-error-c3540"></a>編譯器錯誤 C3540

' type '： sizeof 無法套用至包含 ' auto ' 的類型

[Sizeof](../../cpp/sizeof-operator.md)運算子無法套用至指定的型別，因為它包含 **`auto`** 規範。

## <a name="example"></a>範例

下列範例會產生 C3540。

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-cpp.md)<br/>
[/Zc： auto (推算變數類型) ](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 運算子](../../cpp/sizeof-operator.md)
