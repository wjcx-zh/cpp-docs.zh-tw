---
title: 編譯器錯誤 C2944
ms.date: 11/04/2016
f1_keywords:
- C2944
helpviewer_keywords:
- C2944
ms.assetid: f209e668-e72f-442a-a438-8c4ff43a404a
ms.openlocfilehash: bed23b7d9117d1d1acad80f4f3d81e8b0b9d0252
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652201"
---
# <a name="compiler-error-c2944"></a>編譯器錯誤 C2944

'class' : type-class-id 重複定義為樣板的數值引數

您無法使用泛型或樣板類別取代符號作為樣板數值引數。

下列範例會產生 C2944：

```
// C2944.cpp
// compile with: /c
template<class T>
class TC { };

template <int TC<int> > struct X1 { };   // C2944

template <class T > struct X2 {};
```

使用泛型時，也會發生 C2944：

```
// C2944b.cpp
// compile with: /clr /c
generic<class T>
ref class GC {};

template <int GC<int> > struct X2 { };   // C2944
template <class T> struct X3 {};   // OK
```