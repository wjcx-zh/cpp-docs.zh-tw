---
title: 編譯器錯誤 C2669
ms.date: 11/04/2016
f1_keywords:
- C2669
helpviewer_keywords:
- C2669
ms.assetid: f9cb8111-bcdc-484b-a863-2c42e15a0496
ms.openlocfilehash: 7944ced947ba1d7c8b10172560ce6237a554e236
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649666"
---
# <a name="compiler-error-c2669"></a>編譯器錯誤 C2669

不允許匿名等位中成員函式

[匿名等位](../../cpp/unions.md#anonymous_unions)不能有成員函式。

## <a name="example"></a>範例

下列範例會產生 C2669:

```cpp
// C2669.cpp
struct X {
   union {
      int i;
      void f() {   // C2669, remove function
         i = 0;
      }
   };
};
```
