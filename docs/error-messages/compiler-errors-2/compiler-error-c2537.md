---
title: 編譯器錯誤 C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 437727b334087aef496dbb0a1f3f1c8cf2b45458
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492655"
---
# <a name="compiler-error-c2537"></a>編譯器錯誤 C2537

'specifier': 不合法的連結規格

可能的原因：

1. 不支援連結指定名稱。 支援只"C"連結規範。

1. 指定一組多載函式中的多個函式的"C"連結。 這是不允許的。

下列範例會產生 C2537:

```
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```