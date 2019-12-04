---
title: 編譯器錯誤 C2344
ms.date: 11/04/2016
f1_keywords:
- C2344
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
ms.openlocfilehash: 7aa1d5dfad67120556c9f4a1f69cf22dfca9acd2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760032"
---
# <a name="compiler-error-c2344"></a>編譯器錯誤 C2344

align(#): 使用 align 規範必須是 2 的乘冪

使用 [align](../../cpp/align-cpp.md) 關鍵字時，您傳遞的值必須是 2 的乘冪。

例如，下列程式碼會產生 C2344，因為 3 不是 2 的乘冪：

```cpp
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```
