---
title: 編譯器錯誤 C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a140847b642ac2437b67aa957328c3b8fbfc592d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761565"
---
# <a name="compiler-error-c3536"></a>編譯器錯誤 C3536

' symbol '：在初始化之前無法使用

在初始化之前，無法使用指定的符號。 實際上，這表示不能使用變數來初始化它自己。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 不要以本身初始化變數。

## <a name="example"></a>範例

下列範例會產生 C3536，因為每個變數都會以自己的方式初始化。

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

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
