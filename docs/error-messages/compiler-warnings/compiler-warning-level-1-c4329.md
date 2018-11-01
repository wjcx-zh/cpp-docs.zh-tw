---
title: 編譯器警告 (層級 1) C4329
ms.date: 11/04/2016
f1_keywords:
- C4329
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
ms.openlocfilehash: 31ea3aec2c7dd8e02a23a5c3cf6e5ac406636516
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622582"
---
# <a name="compiler-warning-level-1-c4329"></a>編譯器警告 (層級 1) C4329

列舉時會忽略 __declspec(align())

利用[對齊](../../cpp/align-cpp.md)關鍵字[__declspec](../../cpp/declspec.md)不允許修飾詞`enum`。 下列範例會產生 C4329:

```
// C4329.cpp
// compile with: /W1 /LD
enum __declspec(align(256)) TestEnum {   // C4329
   TESTVAL1,
   TESTVAL2,
   TESTVAL3
};
__declspec(align(256)) enum TestEnum1;
```