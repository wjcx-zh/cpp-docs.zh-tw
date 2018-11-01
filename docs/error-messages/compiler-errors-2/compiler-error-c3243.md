---
title: 編譯器錯誤 C3243
ms.date: 11/04/2016
f1_keywords:
- C3243
helpviewer_keywords:
- C3243
ms.assetid: 35d8ad1a-377d-47df-be9d-c55eea23340f
ms.openlocfilehash: 1fd0cdf44cb820882cdcda3728b664321f730d5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460031"
---
# <a name="compiler-error-c3243"></a>編譯器錯誤 C3243

沒有由 'interface' 引入的多載函式

您已嘗試 [明確覆寫](../../cpp/explicit-overrides-cpp.md) 不存在於所指定介面中的成員。

下列範例會產生 C3243：

```
// C3243.cpp
#pragma warning(disable:4199)
__interface IX14A {
   void g();
};

__interface IX14B {
   void f();
   void f(int);
};

class CX14 : public IX14A, public IX14B {
public:
   void IX14A::g();
   void IX14B::f();
   void IX14B::f(int);
};

void CX14::IX14A::f()   // C3243 occurs here
{
}
```