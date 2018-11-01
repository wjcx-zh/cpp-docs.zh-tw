---
title: 編譯器錯誤 C3189
ms.date: 11/04/2016
f1_keywords:
- C3189
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
ms.openlocfilehash: fe9dc38748fd667734c5d80f1284348184fed450
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456975"
---
# <a name="compiler-error-c3189"></a>編譯器錯誤 C3189

' typeid\<抽象宣告子的類型 >': 已不再支援此語法，請使用:: typeid 改為

過時形式[typeid](../../windows/typeid-cpp-component-extensions.md)已使用，使用新的表單。

下列範例會產生 C3189:

```
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```