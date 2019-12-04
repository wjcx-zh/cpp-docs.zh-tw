---
title: 編譯器錯誤 C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7dd47ffbd9481f69f3799a94a17a53ccdffb2a84
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745014"
---
# <a name="compiler-error-c2391"></a>編譯器錯誤 C2391

' identifier '： ' friend ' 不能在類型定義期間使用

`friend` 宣告包含完整的類別宣告。 `friend` 宣告可以指定成員函式或複雜的類型規範，而不是完整的類別宣告。

下列範例會產生 C2326：

```cpp
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```
