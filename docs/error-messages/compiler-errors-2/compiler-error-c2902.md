---
title: 編譯器錯誤 C2902
ms.date: 11/04/2016
f1_keywords:
- C2902
helpviewer_keywords:
- C2902
ms.assetid: 89d78d0e-78e5-4c2c-a0f9-a60110e9395e
ms.openlocfilehash: 43ba7f6ddb18d86410de852ffc3e2834083f031c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735873"
---
# <a name="compiler-error-c2902"></a>編譯器錯誤 C2902

'token': 'template' 之後有未預期的語彙基元，必須是識別項

關鍵字 `template` 後面的語彙基元不是識別項。

下列範例會產生 C2902：

```cpp
// C2902.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template + 1;   // C2902
}

void f() {
   N::template X<int> x1;   // OK
}
```

使用泛型時，也會發生 C2902：

```cpp
// C2902b.cpp
// compile with: /clr /c
namespace N {
   generic<class T> ref class GC {};
}

void f() {
   N::generic + 1;   // C2902
   N::generic GC<int>^ x;
}
```
