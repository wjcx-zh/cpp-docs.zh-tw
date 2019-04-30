---
title: 編譯器錯誤 C2389
ms.date: 11/04/2016
f1_keywords:
- C2389
helpviewer_keywords:
- C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
ms.openlocfilehash: cb58ed0af3fda7ecbf399ac37758a688f014b826
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393645"
---
# <a name="compiler-error-c2389"></a>編譯器錯誤 C2389

'operator' : 不合法的運算元 'nullptr'

`nullptr` 不可為運算元。

下列範例會產生 C2389：

```
// C2389.cpp
// compile with: /clr
int main() {
   throw nullptr;   // C2389
}
```