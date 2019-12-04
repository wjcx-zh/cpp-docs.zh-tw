---
title: 編譯器錯誤 C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: c1467a3c67cccf28cc6b9bd0f987fe77b8da8988
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757874"
---
# <a name="compiler-error-c2833"></a>編譯器錯誤 C2833

' operator operator ' 不是可辨識的運算子或類型

字組 `operator` 後面必須接著您想要覆寫的運算子或您想要轉換的類型。

如需您可以在 managed 類型中定義的運算子清單，請參閱[使用者定義的運算子](../../dotnet/user-defined-operators-cpp-cli.md)。

下列範例會產生 C2833：

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
