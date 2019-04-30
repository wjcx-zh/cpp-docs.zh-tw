---
title: 編譯器錯誤 C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d920629dc0697d0f2fdd05ac5aca6118b89b88cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378852"
---
# <a name="compiler-error-c2884"></a>編譯器錯誤 C2884

'name': 由 using 宣告衝突與區域函式 'function'

您嘗試一次以上定義的函式。 第一個定義是本機的定義。 第二個是來自命名空間的`using`宣告。

下列範例會產生 C2884:

```
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```