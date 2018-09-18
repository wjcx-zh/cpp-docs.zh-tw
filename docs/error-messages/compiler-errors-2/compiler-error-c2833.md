---
title: 編譯器錯誤 C2833 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53360c1eaf81ad407589fbdb125d9e6fe017708e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070167"
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