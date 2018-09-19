---
title: 編譯器警告 （層級 1） C4384 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4384
dev_langs:
- C++
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54d913aac76f767728bbe7b4a31d4ea1c8bbd96d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026994"
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