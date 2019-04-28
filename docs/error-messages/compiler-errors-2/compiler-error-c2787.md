---
title: 編譯器錯誤 C2787
ms.date: 11/04/2016
f1_keywords:
- C2787
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
ms.openlocfilehash: 656fcd8a1a0429546189de8c3f01ab928c6333ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256857"
---
# <a name="compiler-error-c2787"></a>編譯器錯誤 C2787

'identifier': 沒有 GUID 已經與此物件相關聯

[__Uuidof](../../cpp/uuidof-operator.md)運算子採用的使用者定義型別附加的 GUID 或這類使用者定義類型的物件。 當引數是使用者定義型別不具有 GUID 時，就會發生此錯誤。

下列範例會產生 C2787:

```
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```