---
title: 編譯器錯誤 C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759343"
---
# <a name="compiler-error-c2593"></a>編譯器錯誤 C2593

' operator identifier ' 不明確

為多載運算子定義了一個以上的可能運算子。

如果您在一或多個實際參數上使用明確轉換，則可能會修正此錯誤。

下列範例會產生 C2593：

```cpp
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

此錯誤可能是因為使用 `CArchive` 物件序列化浮點變數所造成。 編譯器會將 `<<` 運算子識別為不明確。 唯一 `CArchive` 可以C++序列化的基本類型是固定大小的類型 `BYTE`、`WORD`、`DWORD`和 `LONG`。 所有整數類型都必須轉換成這些類型的其中一種，才能進行序列化。 必須使用 `CArchive::Write()` 成員函式來封存浮點類型。

下列範例示範如何將浮點變數（`f`）封存到封存 `ar`：

```
ar.Write(&f, sizeof( float ));
```
