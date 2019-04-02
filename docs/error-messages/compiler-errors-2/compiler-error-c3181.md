---
title: 編譯器錯誤 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781805"
---
# <a name="compiler-error-c3181"></a>編譯器錯誤 C3181

'type': 運算子的運算元無效

無效的參數傳遞給[typeid](../../extensions/typeid-cpp-component-extensions.md)運算子。 參數必須是 managed 型別。

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
