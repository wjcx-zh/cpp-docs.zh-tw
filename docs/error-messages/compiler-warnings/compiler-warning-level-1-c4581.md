---
title: 編譯器警告 (層級 1) C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 9868d33538a1f56906455f2b1772b53eb3a7734d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447095"
---
# <a name="compiler-warning-level-1-c4581"></a>編譯器警告 (層級 1) C4581

被取代的行為: '"string1"' 取代 'string2'，以處理屬性

針對 Visual Studio 2005 所進行的編譯器一致性工作可能會導致此錯誤： 參數檢查視覺效果C++屬性。

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