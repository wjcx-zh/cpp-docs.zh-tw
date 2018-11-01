---
title: 編譯器錯誤 C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: bc07a99f12ed0e447427990969e54f7f3d3d3b7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635380"
---
# <a name="compiler-error-c2723"></a>編譯器錯誤 C2723

'function' : 函式定義上的 'specifier' 規範不合法

規範不能出現在類別宣告之外的函式定義。 只可以在類別宣告中的成員函式宣告上指定 `virtual` 規範。

下列範例會產生 C2723，並示範如何修正此問題：

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```