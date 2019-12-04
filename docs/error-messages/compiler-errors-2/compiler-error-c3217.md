---
title: 編譯器錯誤 C3217
ms.date: 11/04/2016
f1_keywords:
- C3217
helpviewer_keywords:
- C3217
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
ms.openlocfilehash: cb837a42841b2695941d4cd6122d186665d2d7e2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754582"
---
# <a name="compiler-error-c3217"></a>編譯器錯誤 C3217

'param'：泛型參數不可在這項宣告中受到條件約束

條件約束格式不正確；泛型類別樣板參數必須與條件約束泛型參數一致。

下列範例會產生 C3217：

```cpp
// C3217.cpp
// compile with: /clr
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T : A   // C3217
   void f();
};
```

下列範例示範可能的解決方式：

```cpp
// C3217b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T1 : A
   void f();
};
```
