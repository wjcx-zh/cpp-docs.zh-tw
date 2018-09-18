---
title: 編譯器警告 （層級 3） C4316 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4170481b95cca0d43aa03c776009a5030194a4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032922"
---
# <a name="compiler-warning-level-3-c4316"></a>編譯器警告 （層級 3） C4316

在堆積上配置的物件無法用於對齊此類型。

使用所配置的過度對齊的物件`operator new`可能沒有指定的對齊方式。 覆寫[new 運算子](../../c-runtime-library/operator-new-crt.md)並[delete 運算子](../../c-runtime-library/operator-delete-crt.md)的過度對齊類型，使其使用對齊的配置常式 — 比方說， [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)和[_aligned_free](../../c-runtime-library/reference/aligned-free.md)。 下列範例會產生 C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```