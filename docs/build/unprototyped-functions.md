---
title: 沒有原型的函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c030bd99fc185b3c52535aecb45697672ef4c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717674"
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