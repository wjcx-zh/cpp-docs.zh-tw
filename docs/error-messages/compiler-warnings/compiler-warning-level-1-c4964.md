---
title: 編譯器警告 (層級 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 7852340bc056e126238a2d9c7493887ef3caf93e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174488"
---
# <a name="compiler-warning-level-1-c4964"></a>編譯器警告 (層級 1) C4964

未指定優化選項;將不會收集設定檔資訊

已指定[/gl](../../build/reference/gl-whole-program-optimization.md)和[/ltcg](../../build/reference/ltcg-link-time-code-generation.md) ，但未要求優化，因此不會產生 .pgc 檔案，因此不會有任何特性指引優化。

如果您想要在執行應用程式時產生 .pgc 檔案，請指定其中一個[/o](../../build/reference/o-options-optimize-code.md)編譯器選項。

下列範例會產生 C4964：

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```
