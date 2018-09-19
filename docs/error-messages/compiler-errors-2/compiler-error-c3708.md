---
title: 編譯器錯誤 C3708 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3708
dev_langs:
- C++
helpviewer_keywords:
- C3708
ms.assetid: 45e71564-9c7f-437f-98d8-a735ce162ed0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 143b386e0f1704ea8271cc93d5d7632fc84b051a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023497"
---
# <a name="compiler-error-c3708"></a>編譯器錯誤 C3708

'interface': 不當使用 'keyword';必須是相容的事件來源的成員

若要宣告為事件的介面，事件宣告必須是事件來源。

下列範例會產生 C3708:

```
// C3708.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="MyLibrary")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[ object, uuid("00000000-0000-0000-0000-000000000002") ]
__interface II {
   HRESULT func();
};

__event __interface I;   // C3708

// put the event in an event source
[ coclass, event_source(com), uuid("00000000-0000-0000-0000-000000000003") ]
struct E : II {
   __event __interface II;
};
```