---
title: 編譯器警告 （層級 3） C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402043"
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