---
title: 編譯器錯誤 C3463
ms.date: 11/04/2016
f1_keywords:
- C3463
helpviewer_keywords:
- C3463
ms.assetid: 153efcc0-085c-4615-84ea-d22942618bdf
ms.openlocfilehash: a0c7772291085bcd872cbc1ca23b79d2fa829ad9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448668"
---
# <a name="compiler-error-c3463"></a>編譯器錯誤 C3463

'type': 屬性 'implements' 中不允許有類型

已傳遞無效的類型給 [implements](../../windows/implements-cpp.md) 屬性。 比方說，您可以將介面傳遞給 `implements`，但您無法將指標傳遞給介面。

## <a name="example"></a>範例

下列範例會產生 C3463：

```
// C3463.cpp
// compile with: /c
#include <windows.h>
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface X {};

typedef X* PX;

[ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=PX) ]   // C3463
// try the following line instead
// [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=X) ]
class CMyClass : public X {};
```