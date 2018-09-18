---
title: 編譯器錯誤 C3733 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3733
dev_langs:
- C++
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b8aa8d3d952f84b9fee0c00b5cfcb7c5e5c45d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051302"
---
# <a name="compiler-error-c3733"></a>編譯器錯誤 C3733

'event': 不適當的語法指定 COM 事件;您是否忘記 '__interface'？

錯誤的語法用於 COM 事件。 若要修正這個錯誤，變更的事件類型或修正語法以符合 COM 事件規則。

下列範例會產生 C3733:

```
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[coclass, event_source(com), // change 'com' to 'native' to resolve
uuid("00000000-0000-0000-0000-000000000001")]
class A
{
   __event void func();   // C3733
};

int main()
{
}
```