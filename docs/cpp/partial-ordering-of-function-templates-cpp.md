---
title: 函式樣板的部分排序 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 9a3dc687f197770f7a11440699163787b1dc48ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183362"
---
# <a name="partial-ordering-of-function-templates-c"></a>函式樣板的部分排序 (C++)

提供多個符合函式呼叫之引數清單的函式樣板。 C++ 可定義函式樣板的部分排序，以指定應呼叫哪些函式。 進行部分排序是因為某些樣板會被視為等同於特製化。

編譯器會從可能相符的項目中選取最特殊的範本函式。 比方說，如果函式樣板採用型別__T__，並採用的另一個函式樣板__T\*__ 可供使用， __T\*__ 版本稱為為進一步特製化和泛型優於__T__版本時的引數是指標類型，即使兩者都是允許的相符項目。

請使用下列程序來判斷某個函式樣板是否為特製化程度較高的候選項目：

1. 考量兩個函式樣板，T1 和 T2。

1. 使用一個假設的唯一類型 X 來取代 T1 中的參數。

1. 透過 T1 中的參數清單，查看 T2 對於該參數清單來說是否為有效的範本。 忽略所有隱含轉換。

1. 以相反順序對 T1 和 T2 重複進行相同的程序。

1. 如果某個樣板是其他範本的有效樣板引數清單，但反之則不然，則該範本會被視為比其他範本的特製化程度更低。 如果使用先前步驟表單有效的引數的每個其他兩個範本，然後被視為相等的特製化，而模稜兩可的呼叫會產生當您嘗試使用它們。

1. 請使用下列規則：

   1. 特定類型的樣板特製化比採用泛型類型引數的樣板特製化程度更高。

   1. 範本僅採取__T\*__ 更具特製化，比起一個採取只__T__，因為假設輸入__X\*__ 是有效引數__T__樣板引數，但__X__不是有效的引數，如__T\*__ 樣板引數。

   1. __const T&__ 更具特製化比__T__，因為__const X__是有效的引數，如__T__樣板引數，但__X__是不是有效引數的__const T>__ 樣板引數。

   1. __const T&\*__ 更具特製化，比__T\*__，因為__const X\*__ 是有效的引數，如__T\*__ 樣板引數，但__X\*__ 不是有效的引數，如__const T&\*__ 樣板引數。

## <a name="example"></a>範例

下列範例適用於標準中所指定：

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

extern "C" int printf(const char*,...);
template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Output

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>另請參閱

[函式樣板](../cpp/function-templates.md)
