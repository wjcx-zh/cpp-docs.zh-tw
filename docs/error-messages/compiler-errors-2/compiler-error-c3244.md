---
title: 編譯器錯誤 C3244
ms.date: 11/04/2016
f1_keywords:
- C3244
helpviewer_keywords:
- C3244
ms.assetid: dae6c49b-5212-4206-8f61-d4010c0b9969
ms.openlocfilehash: 11de2ac8a652687d9826319f13b7c531534d5fe3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754533"
---
# <a name="compiler-error-c3244"></a>編譯器錯誤 C3244

'method': 此方法是由 'interface' 引入，而非由 'interface'

您已嘗試 [明確覆寫](../../cpp/explicit-overrides-cpp.md) 不存在於所指定介面但存在於另一個基底類別中的成員。

下列範例會產生 C3244：

```cpp
// C3244.cpp
#pragma warning(disable:4199)

__interface IX15A {
   void f();
};

__interface IX15B {
   void g();
};

class CX15 : public IX15A, public IX15B {
public:
   void IX15A::f();
   void IX15B::g();
};

void CX15::IX15A::g()   // C3244 occurs here
{
}
```
