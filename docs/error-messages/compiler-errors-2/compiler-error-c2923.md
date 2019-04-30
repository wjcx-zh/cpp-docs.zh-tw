---
title: 編譯器錯誤 C2923
ms.date: 11/04/2016
f1_keywords:
- C2923
helpviewer_keywords:
- C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
ms.openlocfilehash: 885a3a09d43d8c3c479d11e22342487d1a1958d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385728"
---
# <a name="compiler-error-c2923"></a>編譯器錯誤 C2923

'type': 對參數 'param' 而言，'identifier' 不是有效的樣板類型引數

引數清單遺漏具現化樣板或泛型所需的類型。 請檢查樣板或泛型宣告。

下列範例會產生 C2923：

```
// C2923.cpp
template <class T> struct TC {};
int x;
int main() {
   TC<x>* tc2;   // C2923
   TC<int>* tc2;   // OK
}
```

使用泛型時，也會發生 C2923：

```
// C2923b.cpp
// compile with: /clr /c
generic <class T> ref struct GC {};

int x;

int main() {
   GC<x>^ gc2;   // C2923
   GC<int>^ gc2;   // OK
}
```