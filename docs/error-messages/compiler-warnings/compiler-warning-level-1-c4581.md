---
title: 編譯器警告 （層級 1） C4581 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4581
dev_langs:
- C++
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 586283e41fb38baae828bf5a4380ec2afe323ecb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116044"
---
# <a name="compiler-warning-level-1-c4581"></a>編譯器警告 (層級 1) C4581

被取代的行為: '"string1"' 取代 'string2'，以處理屬性

針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致此錯誤： Visual c + + 屬性的參數檢查。

在舊版中，不論是否已以引號括住接受屬性值。 如果值是列舉型別，它必須不加引號。

## <a name="example"></a>範例

下列範例會產生 C4581。

```
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```