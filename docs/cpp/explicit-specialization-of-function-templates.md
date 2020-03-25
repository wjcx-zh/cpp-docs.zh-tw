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
ms.openlocfilehash: c9d77cef790bdd0a65651ffb7246e685175482b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179987"
---
# <a name="explicit-specialization-of-function-templates"></a>函式樣板的明確特製化

透過函式樣板，您可以提供該類型的明確特製化 (覆寫) 函式樣板，來定義該特定類型的特殊行為。 例如：

```cpp
template<> void MySwap(double a, double b);
```

這個宣告可讓您為**double**變數定義不同的函數。 就像非樣板函式一樣，也會套用標準類型轉換（例如將**float**類型的變數升級為**double**）。

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

[函式樣板](../cpp/function-templates.md)
