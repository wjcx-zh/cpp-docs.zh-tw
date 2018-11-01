---
title: 編譯器錯誤 C3644
ms.date: 11/04/2016
f1_keywords:
- C3644
helpviewer_keywords:
- C3644
ms.assetid: 2e3f6c41-3ec5-4a01-82bc-f11b61ebe68e
ms.openlocfilehash: 6d147d6a5955208bbca1ccf9a2f2bcfe3f485b4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428024"
---
# <a name="compiler-error-c3644"></a>編譯器錯誤 C3644

'function': 無法編譯產生 managed 程式碼的函式

函式中的某些關鍵字將導致編譯成原生函式。

下列範例會產生 C3644:

```
// C3644.cpp
// compile with: /clr
// processor: x86

void __clrcall Func2(int i) {
   __asm {}   // C3644
}
```