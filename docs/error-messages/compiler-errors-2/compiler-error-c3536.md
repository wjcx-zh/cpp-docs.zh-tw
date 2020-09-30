---
title: 編譯器錯誤 C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: 2380a9d42525cfb662fa014b89751d6dc8b9f192
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508246"
---
# <a name="compiler-error-c3536"></a>編譯器錯誤 C3536

' symbol '：無法在初始化之前使用

指定的符號在初始化之前無法使用。 實際上，這表示不能使用變數來初始化它自己。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿將變數本身初始化。

## <a name="example"></a>範例

下列範例會產生 C3536，因為每個變數本身都會初始化。

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-cpp.md)
