---
title: 編譯器錯誤 C2253
ms.date: 11/04/2016
f1_keywords:
- C2253
helpviewer_keywords:
- C2253
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
ms.openlocfilehash: 89acfd8a03dc0ee2dc25e14e0b3a63ab25151cc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758849"
---
# <a name="compiler-error-c2253"></a>編譯器錯誤 C2253

' function '：純規範或抽象覆寫規範只允許用於虛擬函式

非虛擬函數會指定為純 `virtual`。

下列範例會產生 C2253：

```cpp
// C2253.cpp
// compile with: /c
class A {
public:
   void func1() = 0;   // C2253 not virtual
   virtual void func2() = 0;   // OK
};
```

下列範例會產生 C2253：

```cpp
// C2253_2.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_3 {
      int get() abstract;   // C2253
      // try the following line instead
      // virtual int get() abstract;

      void set(int i) abstract;   // C2253
      // try the following line instead
      // virtual void set(int i) abstract;
   }
};
```
