---
title: 編譯器錯誤 C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391955"
---
# <a name="compiler-error-c2079"></a>編譯器錯誤 C2079

'identifier' 使用未定義的類別/結構/等位 'name'

指定的識別項是未定義的類別、 結構或等位。

此錯誤可能因初始化匿名等位。

下列範例會產生 C2079:

```
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

可能的解決方式：

```
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

如果您嘗試將其向前宣告是只能在範圍中之型別的堆疊上宣告物件，也會發生 C2079。

```
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

可能的解決方式：

```
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```