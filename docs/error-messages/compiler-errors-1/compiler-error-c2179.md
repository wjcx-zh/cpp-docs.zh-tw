---
title: 編譯器錯誤 C2179
ms.date: 11/04/2016
f1_keywords:
- C2179
helpviewer_keywords:
- C2179
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
ms.openlocfilehash: 5b9b5382ab934f8d870e58189a447775a1e9a415
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737162"
---
# <a name="compiler-error-c2179"></a>編譯器錯誤 C2179

' type '：屬性引數不能使用類型參數

泛型型別參數會在執行時間解析。 不過，屬性參數必須在編譯時期解析。 因此，您無法使用泛型型別參數做為屬性的引數。

## <a name="example"></a>範例

下列範例會產生 C2179。

```cpp
// C2179.cpp
// compile with: /clr
using namespace System;

public ref struct Attr : Attribute {
   Attr(Type ^ a) {
      x = a;
   }

   Type ^ x;
};

ref struct G {};

generic<typename T>
public ref class Z {
public:
   Type ^ d;
   [Attr(T::typeid)]   // C2179
   // try the following line instead
   // [Attr(G::typeid)]
   T t;
};
```
