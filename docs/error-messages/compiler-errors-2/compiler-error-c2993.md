---
title: 編譯器錯誤 C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5be4836332f67f2064f60a3b058db159a18ca1e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605019"
---
# <a name="compiler-error-c2993"></a>編譯器錯誤 C2993

'identifier': 非類型範本參數 'parameter' 的類型不合法

您無法宣告結構或等位的引數的範本。 使用指標做為範本參數中傳遞結構和等位。

下列範例會產生 C2993:

```
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

在 Visual Studio.NET 2003年中已完成的編譯器一致性工作，也產生這個錯誤： 浮動點非類型樣板參數不能再使用。 C + + 標準不允許浮動點非類型範本參數。

如果是函式樣板，使用的函式引數傳入的浮動點非類型樣板參數 （此程式碼是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中的 Visual c + +）。 如果它是類別樣板，則沒有簡單的因應措施。

```
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```