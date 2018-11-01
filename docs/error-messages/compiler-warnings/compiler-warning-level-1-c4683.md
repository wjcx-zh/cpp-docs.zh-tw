---
title: 編譯器警告 (層級 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: 264753ece6cbabded21df8e6b9dbb463f811e8a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598932"
---
# <a name="compiler-warning-level-1-c4683"></a>編譯器警告 (層級 1) C4683

> '*函式*': 事件來源有 'out'-參數; 當攔截多個事件處理常式時警告

## <a name="remarks"></a>備註

如果 COM 事件來源正在接聽多個事件接收器，可能會忽略為輸出參數的值。

請注意出現記憶體流失的情況會發生在下列情況：

1. 如果方法具有輸出參數，會在內部配置，例如 BSTR *。

2. 如果事件有多個處理常式 （是多點傳送的事件）。

找出遺漏的原因是將一個以上的處理常式，來設定 out 參數，但只能由最後一個處理常式傳回至呼叫位置。

## <a name="example"></a>範例

下列範例會產生 C4683，並示範如何修正此問題：

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```