---
title: 編譯器錯誤 C2344
ms.date: 11/04/2016
f1_keywords:
- C2344
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
ms.openlocfilehash: d1ba3a0f975dbc96c9c6ca51a8dac89b5a614572
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439478"
---
# <a name="compiler-error-c2344"></a>編譯器錯誤 C2344

align(#): 使用 align 規範必須是 2 的乘冪

使用 [align](../../cpp/align-cpp.md) 關鍵字時，您傳遞的值必須是 2 的乘冪。

例如，下列程式碼會產生 C2344，因為 3 不是 2 的乘冪：

```
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```