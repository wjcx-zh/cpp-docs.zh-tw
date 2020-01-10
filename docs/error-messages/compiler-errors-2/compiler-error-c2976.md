---
title: 編譯器錯誤 C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 76fd2363b6139bc1bc04aa4d4949a12522e31aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751790"
---
# <a name="compiler-error-c2976"></a>編譯器錯誤 C2976

' identifier '：類型引數太少

泛型或範本遺漏了一或多個實際引數。 請檢查泛型或樣板宣告，以找出正確的參數數目。

此錯誤可能是因為標準程式庫元件中C++遺漏範本引數所造成。

下列範例會產生 C2976：

```cpp
// C2976.cpp
template <class T>
struct TC {
   T t;
};
int main() {
   TC<>* t;   // C2976
   TC<int>* t2;   // OK
}
```

使用泛型時，也會發生 C2976：

```cpp
// C2976b.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC<>^ g;   // C2976
   GC<int>^ g2;   // OK
}
```
