---
title: 編譯器錯誤 C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761227"
---
# <a name="compiler-error-c2993"></a>編譯器錯誤 C2993

' identifier '：非類型範本參數 ' parameter ' 的類型不合法

您不能宣告具有結構或聯集引數的範本。 使用指標來傳遞結構和等位做為樣板參數。

下列範例會產生 C2993：

```cpp
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

在 Visual Studio .NET 2003 中完成的編譯器一致性工作，也會產生此錯誤：不再允許浮點的非類型範本參數。 C++標準不允許浮點非類型範本參數。

如果它是函式樣板，請使用函式引數傳入浮點非類型樣板參數（此程式碼將在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++）中生效。 如果它是類別範本，則不容易解決。

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
