---
title: 編譯器錯誤 C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: f462b7d26e21b9313949bb3968b5b39e81bb30b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437115"
---
# <a name="compiler-error-c2139"></a>編譯器錯誤 C2139

'type': 未定義的類別不允許做為編譯器內建類型特性 '特性' 引數

無效的引數傳遞給類型特性。

如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C2139。

```
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```