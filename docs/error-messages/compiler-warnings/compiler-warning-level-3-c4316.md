---
title: 編譯器警告（層級3） C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 0d920cb3dc967854d1a507d06ce31fde6a670434
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198844"
---
# <a name="compiler-warning-level-3-c4316"></a>編譯器警告（層級3） C4316

在堆積上配置的物件可能不會對齊這個類型。

使用 `operator new` 配置的過度對齊物件可能沒有指定的對齊方式。 針對過度對齊的類型覆寫[operator new](../../c-runtime-library/operator-new-crt.md)和[operator delete](../../c-runtime-library/operator-delete-crt.md) ，使其使用對齊的配置常式，例如[_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)和[_aligned_free](../../c-runtime-library/reference/aligned-free.md)。 下列範例會產生 C4316：

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```
