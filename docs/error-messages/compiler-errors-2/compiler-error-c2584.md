---
title: 編譯器錯誤 C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: b61ad65555b5d5232468206f6170223c5f160a34
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556685"
---
# <a name="compiler-error-c2584"></a>編譯器錯誤 C2584

'Class': 直接基底 'Base2' 是無法存取;已經 'Base1' 的基底

`Class` 已直接衍生自`Base1`。 `Base2` 也是衍生自`Base1`。 `Class` 不能衍生自`Base2`因為這可能表示 （間接） 繼承自`Base1`再次強調，這是不合法因為`Base1`已經是直接基底類別。

## <a name="example"></a>範例

下列範例會產生 C2584。

```
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