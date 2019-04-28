---
title: 編譯器錯誤 C2969
ms.date: 11/04/2016
f1_keywords:
- C2969
helpviewer_keywords:
- C2969
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
ms.openlocfilehash: 1330babe92266a6bc410084b4a46ef75f83f0b7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256798"
---
# <a name="compiler-error-c2969"></a>編譯器錯誤 C2969

語法錯誤：'symbol' : 必須是以 '}' 結尾的成員函式定義

樣板成員函式定義有不對稱的右大括弧。

下列範例會產生 C2969：

```
// C2969.cpp
// compile with: /c
class A {
   int i;
public:
   A(int i) {}
};

A anA(1);

class B {
   A a;
   B() : a(anA);   // C2969
   // try the following line instead
   // B() : a(anA) {}
};
```