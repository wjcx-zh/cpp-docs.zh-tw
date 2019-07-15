---
title: 函式樣板
ms.date: 07/15/2019
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: d430ad7650ffa47f0d6334a827b416cfb05ae6c2
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894367"
---
# <a name="function-templates"></a>函式樣板

類別樣板會根據在具現化時傳遞至類別的型別引數，定義一系列相關的類別。 函式樣板與類別樣板類似，但其定義一系列的函式。 使用函式樣板時，您可以指定一組根據相同的程式碼，但在不同類型或類別上運作的函式。 下列函式樣板會交換兩個項目：

```cpp
// function_templates1.cpp
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
int main() {
}
```

此程式碼會定義一系列交換引數值的函式。 從這個範本中，您可以產生函式，將會交換**int**並**長**類型以及使用者定義型別。 如果已正確定義類別的複製建構函式和指派運算子，則 `MySwap` 甚至會交換類別。

此外，函式樣板會讓您交換類型的物件不同，因為編譯器知道的型別  並*b*在編譯時期的參數。

雖然使用 void 指標可讓這個函式由非樣板化的函式執行，但樣板版本仍是 typesafe。 請考慮下列呼叫：

```cpp
int j = 10;
int k = 18;
CString Hello = "Hello, Windows!";
MySwap( j, k );          //OK
MySwap( j, Hello );      //error
```

因為編譯器無法產生具有不同類型之參數的 `MySwap` 函式，因此第二個 `MySwap` 呼叫會觸發編譯時間錯誤。 如果使用了 void 指標，則會正確編譯兩個函式呼叫，不過，函式在執行階段將無法正常運作。

您可以明確指定函式樣板的樣板引數。 例如：

```cpp
// function_templates2.cpp
template<class T> void f(T) {}
int main(int j) {
   f<char>(j);   // Generate the specialization f(char).
   // If not explicitly specified, f(int) would be deduced.
}
```

明確指定樣板引數時，一般會完成隱含轉換，以便將函式引數轉換為對應函式樣板參數的類型。 在上述範例中，編譯器會將轉換`j`鍵入**char**。

## <a name="see-also"></a>另請參閱

[範本](../cpp/templates-cpp.md)<br/>
[函式樣板具現化](../cpp/function-template-instantiation.md)<br/>
[明確初始化](../cpp/explicit-instantiation.md)<br/>
[函式樣板的明確特製化](../cpp/explicit-specialization-of-function-templates.md)