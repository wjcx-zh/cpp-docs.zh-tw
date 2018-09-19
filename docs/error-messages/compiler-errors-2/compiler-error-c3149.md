---
title: 編譯器錯誤 C3149 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a522bfd3ba236661f206d8d4e4b550179c06b3f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033117"
---
# <a name="compiler-error-c3149"></a>編譯器錯誤 C3149

'type': 無法使用這個類型沒有最上層的 'char'

未正確指定的宣告。

比方說，您可能已定義在全域範圍的 CLR 型別，並嘗試建立類型的變數定義的一部分。 因為不允許 CLR 類型的全域變數，編譯器會產生 C3149。

若要解決這個錯誤，宣告式函式或類型定義內的 CLR 類型的變數。

下列範例會產生 C3149:

```
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

下列範例會產生 C3149:

```
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
