---
title: 編譯器錯誤 C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: f723fcc0a3d9626f01f2059a3d9363801221bca0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216046"
---
# <a name="compiler-error-c2723"></a>編譯器錯誤 C2723

'function' : 函式定義上的 'specifier' 規範不合法

規範不能出現在類別宣告之外的函式定義。 **`virtual`** 規範只能在類別宣告內的成員函式宣告上指定。

下列範例會產生 C2723，並示範如何修正此問題：

```cpp
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```
