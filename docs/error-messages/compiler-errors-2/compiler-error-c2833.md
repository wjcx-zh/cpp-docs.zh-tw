---
title: 編譯器錯誤 C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: dad6a64f145c3d49d3b43044ea76a11d35827943
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408364"
---
# <a name="compiler-error-c2833"></a>編譯器錯誤 C2833

'operator operator' 不是可辨認的運算子或類型

Word`operator`後面必須是您想要覆寫的運算子或您想要轉換的類型。

如需您可以在 managed 類型中定義的運算子，請參閱[使用者定義的運算子](../../dotnet/user-defined-operators-cpp-cli.md)。

下列範例會產生 C2833:

```
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```