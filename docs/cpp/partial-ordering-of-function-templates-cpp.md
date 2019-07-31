---
title: 函式樣板的部分排序 (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682431"
---
# <a name="partial-ordering-of-function-templates-c"></a>函式樣板的部分排序 (C++)

提供多個符合函式呼叫之引數清單的函式樣板。 C++ 可定義函式樣板的部分排序，以指定應呼叫哪些函式。 進行部分排序是因為某些樣板會被視為等同於特製化。

編譯器會從可能相符的項目中選取最特殊的範本函式。 例如, 如果函式樣板採用類型`T` , 而且有另一個可使用的函式範本`T*` , `T*`則會將版本視為更特殊化。 當引數為指標類型`T`時, 其偏好高於泛型版本, 即使兩者都是允許的相符專案。

請使用下列程序來判斷某個函式樣板是否為特製化程度較高的候選項目：

1. 考量兩個函式樣板，T1 和 T2。

1. 使用一個假設的唯一類型 X 來取代 T1 中的參數。

1. 透過 T1 中的參數清單，查看 T2 對於該參數清單來說是否為有效的範本。 忽略所有隱含轉換。

1. 以相反順序對 T1 和 T2 重複進行相同的程序。

1. 如果一個範本是其他範本的有效樣板引數清單, 但反之不是 true, 則該範本會被視為比其他範本更不特殊化。 如果您使用上一個步驟, 這兩個範本會形成彼此的有效引數, 則會被視為相同的特製化, 而當您嘗試使用它們時, 會將其稱為不明確的呼叫結果。

1. 請使用下列規則：

   1. 特定類型的樣板特製化比採用泛型類型引數的樣板特製化程度更高。

   1. 只採取的範本`T*`只會比一個`T`使用更具特製化, 因為假設`X*`的類型是樣板引數`T`的有效引數`X` , 但不是的有效引數`T*`樣板引數。

   1. `const T`比`T`更特殊化, 因為`const X`是樣板引數的有效自`T`變數, `const T`但`X`不是樣板引數的有效引數。

   1. `const T*`比`T*`更特殊化, 因為`const X*`是樣板引數的有效自`T*`變數, `const T*`但`X*`不是樣板引數的有效引數。

## <a name="example"></a>範例

下列範例的運作方式如標準中所指定:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

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
