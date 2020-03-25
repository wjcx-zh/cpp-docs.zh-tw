---
title: 編譯器警告 (層級 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: 99d60bc08a077ae1637b80eac6775c8fa2571a1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163594"
---
# <a name="compiler-warning-level-1-c4167"></a>編譯器警告 (層級 1) C4167

函式：僅供用為內建函式

**#pragma 函式** 嘗試強制編譯器對必須用於內建形式的函式使用傳統呼叫。 忽略 pragma。

若要避免這個警告，請移除 **#pragma 函式**。

## <a name="example"></a>範例

```cpp
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```
