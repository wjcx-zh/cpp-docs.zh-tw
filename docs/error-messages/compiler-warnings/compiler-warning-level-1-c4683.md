---
title: 編譯器警告 （層級 1） C4683 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a157d3beb7c2efa7f1144a961973652e2ce384f7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194193"
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