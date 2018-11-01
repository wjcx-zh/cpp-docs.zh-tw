---
title: 編譯器錯誤 C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: 9e24fc28f84bfacb7478d700047c4eb1363247de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451268"
---
# <a name="compiler-error-c3246"></a>編譯器錯誤 C3246

'class': 無法繼承自 'type'，因為它已經宣告為 'sealed'

標示為 [sealed](../../windows/sealed-cpp-component-extensions.md) 的類別不能當成任何其他類別的基底類別。

下列範例會產生 C3246：

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
