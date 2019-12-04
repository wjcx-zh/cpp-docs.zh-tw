---
title: 編譯器錯誤 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: e30ed7016ca3a4d4948a08c5c09268e52c9a407d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761669"
---
# <a name="compiler-error-c3181"></a>編譯器錯誤 C3181

' type '：運算子的運算元無效

傳遞了不正確參數給[typeid](../../extensions/typeid-cpp-component-extensions.md)運算子。 參數必須是 managed 類型。

請注意，編譯器會針對對應至 common language runtime 中類型的原生類型使用別名。

下列範例會產生 C3181：

```cpp
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
