---
title: 編譯器錯誤 C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 25dbb8897db45cbddaaf7f0530bcb2a8653b03cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752791"
---
# <a name="compiler-error-c3737"></a>編譯器錯誤 C3737

' delegate '：委派不能有明確的呼叫慣例

您不能指定 `delegate`的[呼叫慣例](../../cpp/calling-conventions.md)。

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
