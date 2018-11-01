---
title: 編譯器警告 (層級 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: ed27e6ff63e3d5f3bab4f6d8d9639b84a5606ff2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563930"
---
# <a name="compiler-warning-level-1-c4224"></a>編譯器警告 (層級 1) C4224

使用非標準擴充： 型式參數 'identifier' 先前已定義為類型

先前已使用的識別項當做`typedef`。 這會導致 ANSI 相容性警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>範例

```
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```