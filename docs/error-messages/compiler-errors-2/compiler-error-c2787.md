---
title: 編譯器錯誤 C2787
ms.date: 11/04/2016
f1_keywords:
- C2787
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
ms.openlocfilehash: 00f2097dc556055f0becf1d81d784c9126c66f63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739593"
---
# <a name="compiler-error-c2787"></a>編譯器錯誤 C2787

' identifier '：沒有與此物件相關聯的 GUID

[__Uuidof](../../cpp/uuidof-operator.md)運算子會使用已附加 GUID 的使用者自訂類型，或此類使用者定義類型的物件。 當引數是沒有 GUID 的使用者定義型別時，就會發生這個錯誤。

下列範例會產生 C2787：

```cpp
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```
