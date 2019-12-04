---
title: 編譯器錯誤 C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: a708e711fd086d31ecd5e8cc9c35679571af48c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739567"
---
# <a name="compiler-error-c2788"></a>編譯器錯誤 C2788

' identifier '：一個以上與此物件相關聯的 GUID

[__Uuidof](../../cpp/uuidof-operator.md)運算子會使用已附加 GUID 的使用者自訂類型，或此類使用者定義類型的物件。 當引數為具有多個 Guid 的物件時，就會發生此錯誤。

下列範例會產生 C2788：

```cpp
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```
