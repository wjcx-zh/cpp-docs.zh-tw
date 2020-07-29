---
title: 編譯器錯誤 C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: a6ffcb13d04f3c7c5ac62e147a2b6b2b305e11e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218165"
---
# <a name="compiler-error-c2833"></a>編譯器錯誤 C2833

> ' operator *operator-name*' 不是可辨識的運算子或類型

這個字 **`operator`** 後面必須加上您想要覆寫的*運算子名稱*，或您想要轉換的類型。

如需您可以在 managed 類型中定義的運算子清單，請參閱[使用者定義的運算子](../../dotnet/user-defined-operators-cpp-cli.md)。

下列範例會產生 C2833：

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
