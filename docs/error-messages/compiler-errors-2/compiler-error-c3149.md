---
title: 編譯器錯誤 C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 8238dcec821256dad8101cd7ad59b2d85882c218
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345516"
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
