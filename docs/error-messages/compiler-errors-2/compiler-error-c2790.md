---
title: 編譯器錯誤 C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: e377c18b5c0774a466dc535f2a1fba3411bd15b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530243"
---
# <a name="compiler-error-c2790"></a>編譯器錯誤 C2790

'super': 此關鍵字僅適用於類別成員函式主體內

如果使用者試著使用關鍵字出現下列錯誤訊息[super](../../cpp/super.md)成員函式的內容之外。

下列範例會產生 C2790:

```
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```