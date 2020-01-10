---
title: 編譯器錯誤 C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: 2c3b10ecd6808ccd864ecf877fe9f1d0e9f30a3a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748628"
---
# <a name="compiler-error-c2584"></a>編譯器錯誤 C2584

' Class '：無法存取直接基底 ' Base2 ';已經是 ' Base1 ' 的基底

`Class` 已經直接衍生自 `Base1`。 `Base2` 也衍生自 `Base1`。 `Class` 無法衍生自 `Base2`，因為這表示會再次從 `Base1` 繼承（間接），這不是合法的，因為 `Base1` 已經是直接基類。

## <a name="example"></a>範例

下列範例會產生 C2584。

```cpp
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```
