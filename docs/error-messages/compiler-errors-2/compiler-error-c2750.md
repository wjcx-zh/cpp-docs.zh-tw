---
title: 編譯器錯誤 C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 943220fae035da8d6fc861d2abae435051381e1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453738"
---
# <a name="compiler-error-c2750"></a>編譯器錯誤 C2750

'type': 無法使用 'new' 的參考類型使用 'gcnew' 代替

若要建立執行個體的 CLR 型別，這會導致要放在記憶體回收堆積上的執行個體，您必須使用[gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md)。

下列範例會產生 C2750:

```
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```