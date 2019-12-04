---
title: 編譯器錯誤 C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: ea158d8dada013f6b90d0fbe1e7502665c1c24da
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757718"
---
# <a name="compiler-error-c2079"></a>編譯器錯誤 C2079

' identifier ' 使用了未定義的類別/結構/聯集 ' name '

指定的識別碼是未定義的類別、結構或等位。

這個錯誤可能是因為初始化匿名等位所造成。

下列範例會產生 C2079：

```cpp
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

可能的解決方案：

```cpp
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

如果您嘗試在型別的堆疊上宣告一個物件，而該類型的轉送宣告只在範圍內，也可能會發生 C2079。

```cpp
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

可能的解決方案：

```cpp
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
