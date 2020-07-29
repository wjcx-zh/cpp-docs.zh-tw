---
title: 編譯器錯誤 C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: f000287c5934a39d56342bce0f6c9ca2c69e2297
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212731"
---
# <a name="compiler-error-c2391"></a>編譯器錯誤 C2391

' identifier '： ' friend ' 不能在類型定義期間使用

宣告 **`friend`** 包含完整的類別宣告。 宣告 **`friend`** 可以指定成員函式或複雜的類型規範，而不是完整的類別宣告。

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
