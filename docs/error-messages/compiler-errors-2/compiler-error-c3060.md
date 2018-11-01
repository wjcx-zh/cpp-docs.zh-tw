---
title: 編譯器錯誤 C3060
ms.date: 11/04/2016
f1_keywords:
- C3060
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
ms.openlocfilehash: c77af7fa1220aa5211d480cddf3bf0979c642ade
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515397"
---
# <a name="compiler-error-c3060"></a>編譯器錯誤 C3060

'member': Friend 函式不可使用限定名稱在類別中定義 (只可以宣告)

使用限定名稱定義了 Friend 函式，這是不允許的做法。

下列範例會產生 C3060：

```
// C3060.cpp
class A {
public:
   void func();
};

class C {
public:
   friend void A::func() { }   // C3060
   // Try the following line and the out of class definition:
   // friend void A::func();
};

// void A::func(){}
```