---
title: 編譯器錯誤 C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 263eb03b7a9f45458f8d8b586adc6f1cfc5805be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745976"
---
# <a name="compiler-error-c3149"></a>編譯器錯誤 C3149

' type '：無法在沒有最上層 ' char ' 的情況下使用此類型

未正確指定宣告。

例如，您可能已在全域範圍中定義 CLR 類型，並嘗試建立該類型的變數做為定義的一部分。 因為不允許 CLR 類型的全域變數，所以編譯器會產生 C3149。

若要解決這個錯誤，請在函式或類型定義內宣告 CLR 類型的變數。

下列範例會產生 C3149：

```cpp
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

下列範例會產生 C3149：

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
