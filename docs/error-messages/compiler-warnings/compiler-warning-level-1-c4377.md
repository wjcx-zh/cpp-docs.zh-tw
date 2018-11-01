---
title: 編譯器警告 (層級 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: d8c89967e0dc900e098ca03d22932451f26a6a0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531011"
---
# <a name="compiler-warning-level-1-c4377"></a>編譯器警告 (層級 1) C4377

原生型別是私用的預設值;-d1PrivateNativeTypes 已被取代

在舊版中，組件中的原生型別是公用的預設值，而且內部且未記載的編譯器選項 (**/d1PrivateNativeTypes**) 用來使其私用。

所有類型，原生和 CLR，現在是私用預設會在組件，因此 **/d1PrivateNativeTypes**不再需要。

## <a name="example"></a>範例

下列範例會產生 C4377。

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```