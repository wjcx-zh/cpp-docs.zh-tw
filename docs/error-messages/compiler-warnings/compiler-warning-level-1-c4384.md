---
title: 編譯器警告 (層級 1) C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 0f2666011e88dfd59eaaca154f4407bece7c963c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454677"
---
# <a name="compiler-warning-level-1-c4384"></a>編譯器警告 (層級 1) C4384

\#pragma 'make_public' 只能在全域範圍

[Make_public](../../preprocessor/make-public.md) pragma 已正確套用。

## <a name="example"></a>範例

下列範例會產生 C4384。

```
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```