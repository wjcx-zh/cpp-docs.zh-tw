---
title: 編譯器錯誤 C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: b2fa2643898fed510aa7cf0f483b538ebb33b033
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760448"
---
# <a name="compiler-error-c2662"></a>編譯器錯誤 C2662

' function '：無法將 ' this ' 指標從 ' type1 ' 轉換為 ' type2 '

編譯器無法將 `this` 指標從 `type1` 轉換成 `type2`。

這個錯誤可能是因為在 `const` 物件上叫用非`const` 的成員函式所造成。  可能的解決方式：

- 從物件宣告中移除 `const`。

- 將 `const` 加入至成員函式。

下列範例會產生 C2662：

```cpp
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

使用 **/clr**進行編譯時，您無法在 `const` 或 `volatile` 合格的 managed 類型上呼叫函數。 您不能宣告 managed 類別的 const 成員函式，因此您無法在 const managed 物件上呼叫方法。

```cpp
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

下列範例會產生 C2662：

```cpp
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```
