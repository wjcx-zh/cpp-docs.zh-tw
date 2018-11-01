---
title: 編譯器錯誤 C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 4356182758398fa7ed1ec6a069affa4bb99ace1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631682"
---
# <a name="compiler-error-c2341"></a>編譯器錯誤 C2341

'區段名稱': 您必須使用 #pragma data_seg、 code_seg 或先前的區段，將定義區段

[配置](../../cpp/allocate.md)陳述式是指尚未所定義的區段[code_seg](../../preprocessor/code-seg.md)， [data_seg](../../preprocessor/data-seg.md)，或[區段](../../preprocessor/section.md)pragma。

下列範例會產生 C2341:

```
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

可能的解決方式：

```
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```