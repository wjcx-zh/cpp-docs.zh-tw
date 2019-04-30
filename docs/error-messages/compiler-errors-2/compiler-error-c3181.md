---
title: 編譯器錯誤 C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382390"
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
