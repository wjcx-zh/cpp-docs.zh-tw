---
title: 沒有原型的函式
ms.date: 11/04/2016
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
ms.openlocfilehash: 38207be6111dadc338593e55b683b88e0480e1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633420"
---
# <a name="unprototyped-functions"></a>沒有原型的函式

針對完全原型的函式，呼叫端會傳遞整數值以整數和浮點數的值為雙精確度。 對於只有浮點數值，整數暫存器和浮點暫存器會包含浮點值如果被呼叫端需要整數暫存器值。

```
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)