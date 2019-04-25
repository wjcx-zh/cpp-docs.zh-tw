---
title: 編譯器錯誤 C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: eb5ba268508922daf00adb49cf611c038db76343
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173193"
---
# <a name="compiler-error-c3246"></a>編譯器錯誤 C3246

'class': 無法繼承自 'type'，因為它已經宣告為 'sealed'

標示為 [sealed](../../extensions/sealed-cpp-component-extensions.md) 的類別不能當成任何其他類別的基底類別。

下列範例會產生 C3246：

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
