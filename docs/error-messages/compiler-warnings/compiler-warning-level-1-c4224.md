---
title: 編譯器警告 (層級 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: c58b003e43e74886c65d41e9abd6e49d15825653
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220089"
---
# <a name="compiler-warning-level-1-c4224"></a>編譯器警告 (層級 1) C4224

使用非標準的擴充：先前已將正式參數 ' identifier ' 定義為類型

識別碼先前是用來做為 **`typedef`** 。 這會導致在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下出現警告。

## <a name="example"></a>範例

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```
