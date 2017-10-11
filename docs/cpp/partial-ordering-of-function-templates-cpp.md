---
title: "函式樣板 （c + +） 的部分排序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: 252f80416f581ecc2c126bc44ab22c1b63c50130
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---

# <a name="partial-ordering-of-function-templates-c"></a>函式樣板的部分排序 (C++)

提供多個符合函式呼叫之引數清單的函式樣板。 C++ 可定義函式樣板的部分排序，以指定應呼叫哪些函式。 進行部分排序是因為某些樣板會被視為等同於特製化。

編譯器會從可能相符的項目中選取最特殊的範本函式。 比方說，如果函式樣板採用類型__T__，和另一個的函式樣板採用__T\* __可用， __T\* __稱為版本為多個特製化和泛型優於__T__版本每當引數是指標類型，即使兩者都是允許的相符項目。

請使用下列程序來判斷某個函式樣板是否為特製化程度較高的候選項目：

1. 考量兩個函式樣板，T1 和 T2。

2. 使用一個假設的唯一類型 X 來取代 T1 中的參數。

3. 透過 T1 中的參數清單，查看 T2 對於該參數清單來說是否為有效的範本。 忽略所有隱含轉換。

4. 以相反順序對 T1 和 T2 重複進行相同的程序。

5. 如果某個樣板是其他範本的有效樣板引數清單，但反之則不然，則該範本會被視為比其他範本的特製化程度更低。 如果使用上一個步驟表單有效的引數的每個其他兩個範本，則視為是相等的特製化，而且會產生模稜兩可的呼叫當您嘗試使用它們。

6. 請使用下列規則：

     1. 特定類型的樣板特製化比採用泛型型別引數的樣板特製化程度更高。

     2. 只接受一個範本__T\* __更具特製化比一個將只__T__，因為假設輸入__X\* __是有效引數__T__樣板引數，但__X__不是有效的引數，如__T\* __樣板引數。

     3. __const T__更具特製化比__T__，因為__const X__是有效的引數，如__T__樣板引數，但__X__不是有效的引數，如__const T__樣板引數。

     4. __const T\* __更具特製化比__T\*__，因為__const X\* __是有效的引數，如__T\*__樣板引數，但__X\* __不是有效的引數，如__const T\* __樣板引數。

## <a name="example"></a>範例

下列範例所述的標準中的運作方式：

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
  
### <a name="output"></a>輸出  
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## <a name="see-also"></a>另請參閱

[函式樣板](../cpp/function-templates.md)

