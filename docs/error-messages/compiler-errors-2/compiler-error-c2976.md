---
title: 編譯器錯誤 C2976
ms.date: 11/04/2016
f1_keywords:
- C2976
helpviewer_keywords:
- C2976
ms.assetid: d9bf9836-325e-4f72-a7e3-a67cf19d32e7
ms.openlocfilehash: 02771d7419c58ee4f0b6d7db46ba91fde253d9a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395361"
---
# <a name="compiler-error-c2976"></a>編譯器錯誤 C2976

'identifier': 類型引數太少

泛型或樣板遺漏一或多個實際的引數。 請檢查泛型或樣板宣告，以找出正確的參數數目。

此錯誤可能因缺少範本引數，在C++標準程式庫元件。

下列範例會產生 C2976:

```
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

使用泛型時，也會發生 C2976:

```
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