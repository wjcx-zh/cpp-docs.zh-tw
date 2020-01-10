---
title: 編譯器錯誤 C3214
ms.date: 11/04/2016
f1_keywords:
- C3214
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
ms.openlocfilehash: 4eda0abd0bbfb3bf5757e39062fa3c229f698624
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756184"
---
# <a name="compiler-error-c3214"></a>編譯器錯誤 C3214

'type': 對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，不符合條件約束 'constraint'

已針對具現化不符合泛型類別之條件約束的泛型類別指定類型。

下列範例會產生 C3214：

```cpp
// C3214.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A
ref class C {};

ref class X : public A {};

int main() {
   C<int>^ c = new C<int>;   // C3214
   C<X ^> ^ c2 = new C<X^>;   // OK
}
```
