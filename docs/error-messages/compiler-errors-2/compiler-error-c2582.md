---
title: 編譯器錯誤 C2582
ms.date: 11/04/2016
f1_keywords:
- C2582
helpviewer_keywords:
- C2582
ms.assetid: ee1b9378-8bcd-4792-b87e-6d7a466d29ed
ms.openlocfilehash: 102682e64602d06b2ee5449ac5b71852cfa33af3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748667"
---
# <a name="compiler-error-c2582"></a>編譯器錯誤 C2582

' function ' 函式無法在 ' type ' 中使用

嘗試指派給沒有指派運算子的物件。

下列範例會產生 C2582：

```cpp
// C2582.cpp
// compile with: /clr
using namespace System;

struct N {};
ref struct O {};
ref struct R {
   property O prop;   // C2582
   property O ^ prop2;   // OK
};

int main() {
   String ^ st1 = gcnew String("");
   ^st1 = gcnew String("");   // C2582
   st1 = "xxx";   // OK
}
```
