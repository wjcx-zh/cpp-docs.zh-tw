---
title: 編譯器錯誤 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: b37b28b4332b46aaaf803f58090a72c25e83f47f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587755"
---
# <a name="compiler-error-c3181"></a>編譯器錯誤 C3181

'type': 運算子的運算元無效

無效的參數傳遞給[typeid](../../windows/typeid-cpp-component-extensions.md)運算子。 參數必須是 managed 型別。

請注意，編譯器就會使用別名對應至 common language runtime 中類型的原生類型。

下列範例會產生 C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
