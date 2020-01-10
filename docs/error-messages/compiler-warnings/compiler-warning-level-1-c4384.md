---
title: 編譯器警告（層級1） C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 467f15522503d16d3b023661ee339c986f74ddec
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964892"
---
# <a name="compiler-warning-level-1-c4384"></a>編譯器警告（層級1） C4384

\#pragma ' make_public ' 只應用於全域範圍

未正確套用[make_public](../../preprocessor/make-public.md) pragma。

## <a name="example"></a>範例

下列範例會產生 C4384。

```cpp
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```