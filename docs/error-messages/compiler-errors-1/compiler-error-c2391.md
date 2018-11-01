---
title: 編譯器錯誤 C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7683ad1580454bd7edb1fc08e5bd110a3e5c36c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491483"
---
# <a name="compiler-error-c2391"></a>編譯器錯誤 C2391

'identifier': 'friend' 不能在類型定義

`friend`宣告包含完整的類別宣告。 A`friend`宣告可以指定一個成員函式或複雜的類型規範，但不是完整的類別宣告。

下列範例會產生 C2326：

```
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