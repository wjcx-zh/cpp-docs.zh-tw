---
title: 編譯器錯誤 C3733
ms.date: 11/04/2016
f1_keywords:
- C3733
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
ms.openlocfilehash: 961aa0caf31d49917f6df67305bc01d465884b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165895"
---
# <a name="compiler-error-c3733"></a>編譯器錯誤 C3733

' event '：指定 COM 事件的語法不正確;您忘了 ' __interface ' 嗎？

COM 事件使用了錯誤的語法。 若要修正此錯誤，請變更事件種類或更正語法，以符合 COM 事件規則。

下列範例會產生 C3733：

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
