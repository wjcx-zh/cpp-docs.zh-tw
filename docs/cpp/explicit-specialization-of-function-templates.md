---
title: 函式樣板的明確特製化
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: 638b5dbca1b3c0c9b9c9c946418ea70354ff6266
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220557"
---
# <a name="explicit-specialization-of-function-templates"></a>函式樣板的明確特製化

透過函式樣板，您可以提供該類型的明確特製化 (覆寫) 函式樣板，來定義該特定類型的特殊行為。 例如：

```cpp
template<> void MySwap(double a, double b);
```

這個宣告可讓您為變數定義不同的函式 **`double`** 。 就像非樣板函式，會套用標準類型轉換（例如將類型的變數升級 **`float`** 為 **`double`** ）。

## <a name="example"></a>範例

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>另請參閱

[函數樣板](../cpp/function-templates.md)
