---
title: 編譯器錯誤 C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: c358553a36104b5c389076f5a5ce02f94f85e85a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667307"
---
# <a name="compiler-error-c2593"></a>編譯器錯誤 C2593

'運算子 identifier' 是模稜兩可

定義多個可能運算子多載的運算子。

如果您使用明確轉換一或多個實際的參數，可能會修正此錯誤。

下列範例會產生 C2593:

```
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

此錯誤可能因序列化浮點變數使用`CArchive`物件。 編譯器會識別`<<`為模稜兩可的運算子。 只有基本的 c + + 型別`CArchive`可以序列化是固定大小類型`BYTE`， `WORD`， `DWORD`，和`LONG`。 所有整數類型必須都轉換成其中一種類型，進行序列化。 浮點型別必須使用封存`CArchive::Write()`成員函式。

下列範例示範如何將浮點變數 (`f`) 來封存`ar`:

```
ar.Write(&f, sizeof( float ));
```