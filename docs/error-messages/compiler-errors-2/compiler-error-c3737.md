---
title: 編譯器錯誤 C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 6b61904fac09145ba749138a730603fcfdbb862d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223378"
---
# <a name="compiler-error-c3737"></a>編譯器錯誤 C3737

' delegate '：委派不能有明確的呼叫慣例

您不能指定的[呼叫慣例](../../cpp/calling-conventions.md) **`delegate`** 。

## <a name="example"></a>範例

下列範例會產生 C3737：

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
