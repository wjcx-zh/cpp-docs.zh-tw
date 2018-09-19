---
title: 編譯器警告 （層級 2） C4056 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4056
dev_langs:
- C++
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e069867d4aef749f9f6e42f46a34745d9e8aa62
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067503"
---
# <a name="compiler-warning-level-2-c4056"></a>編譯器警告 （層級 2） C4056

在浮點常數算術中溢位

浮點常數算術會產生超過允許的最大值的結果。

這個警告可能因常數的算術運算期間執行的編譯器最佳化。 如果它就會消失時關閉最佳化，您可以放心忽略此警告 ([/Od](../../build/reference/od-disable-debug.md))。

下列範例會產生 C4056:

```
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```