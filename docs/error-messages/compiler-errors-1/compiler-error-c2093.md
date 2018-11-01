---
title: 編譯器錯誤 C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511146"
---
# <a name="compiler-error-c2093"></a>編譯器錯誤 C2093

'variable1': 不可以使用 自動變數的 '變數 2' 的位址初始化

進行編譯時[/Za](../../build/reference/za-ze-disable-language-extensions.md)，程式會嘗試自動變數的位址做為初始設定式。

下列範例會產生 C2093:

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```