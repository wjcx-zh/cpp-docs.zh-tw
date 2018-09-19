---
title: 編譯器錯誤 C3060 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3060
dev_langs:
- C++
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c053f7b92ae12b3e99792603cf7b3c5ac9b49227
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108595"
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