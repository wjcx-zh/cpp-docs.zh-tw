---
title: 編譯器警告（層級1） C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 5931516e3f4eba91c3b7a3ab4d0ca4979ce1ed84
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965929"
---
# <a name="compiler-warning-level-1-c4581"></a>編譯器警告（層級1） C4581

已取代的行為： ' "string1" ' 已取代為 ' string2 ' 以處理屬性

這項錯誤可能是因為針對 Visual Studio 2005： Visual C++屬性的參數檢查所執行的編譯器一致性工作所產生。

在先前版本中，不論屬性值是否括在引號中，都是可接受的。 如果值是列舉，則不得以引號括住。

## <a name="example"></a>範例

下列範例會產生 C4581。

```cpp
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