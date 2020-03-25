---
title: 編譯器警告 (層級 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: f86cf8f6d894d6efaa1b49977634956dc1979a98
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175425"
---
# <a name="compiler-warning-level-1-c4683"></a>編譯器警告 (層級 1) C4683

> '*function*'：事件來源具有 ' out'-參數;在連結多個事件處理常式時，請小心

## <a name="remarks"></a>備註

如果有一個以上的事件接收正在接聽 COM 事件來源，可能會忽略 out 參數的值。

請注意，在下列情況中會發生記憶體流失：

1. 如果方法具有內部配置的 out 參數，例如 BSTR *。

2. 如果事件有一個以上的處理常式（是多播事件）。

遺漏的原因是，out 參數會由一個以上的處理常式所設定，但只會由最後一個處理常式傳回給呼叫位置。

## <a name="example"></a>範例

下列範例會產生 C4683，並顯示如何修正此問題：

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
