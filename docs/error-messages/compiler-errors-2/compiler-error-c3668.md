---
title: 編譯器錯誤 C3668
ms.date: 11/04/2016
f1_keywords:
- C3668
helpviewer_keywords:
- C3668
ms.assetid: 53a96698-bde4-4447-95b5-b5108291f60c
ms.openlocfilehash: 1e949a1251fcbebfd9e8fe47caf190e81b8b9f99
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758160"
---
# <a name="compiler-error-c3668"></a>編譯器錯誤 C3668

' method '：具有覆寫規範 ' override ' 的方法並未覆寫任何基類方法

函數嘗試覆寫不存在的函式。

如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3668。

```cpp
// C3668.cpp
// compile with: /c
__interface I {
   void f(int);   // virtual by default
};

class J {
public:
   void g(int);
   virtual void h(int);
};

struct R : I,J {
   virtual void f() override {}   // C3668
   virtual void f(int) override {}   // OK

   virtual void g(int) override {}   // C3668
   virtual void h(int) override {}   // OK
};
```
