---
title: 編譯器警告（層級2） C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 20e7c2693c14c0ea05cc6f07f8dad4ce76c1ef5e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052198"
---
# <a name="compiler-warning-level-2-c4056"></a>編譯器警告（層級2） C4056

浮點常數算術中溢位

浮點常數算術會產生超過最大可允許值的結果。

這項警告可能是在常數算術期間執行編譯器優化所造成。 如果您關閉優化（[/od](../../build/reference/od-disable-debug.md)），可以放心地忽略此警告。

下列範例會產生 C4056：

```cpp
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```