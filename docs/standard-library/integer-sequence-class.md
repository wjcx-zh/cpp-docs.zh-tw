---
title: "integer_sequence 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
dev_langs:
- C++
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e2502b627a40b40ee6942a24fdc1b8c0d16ecc31
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="integersequence-class"></a>integer_sequence 類別
表示整數序列。 可用來推算並展開作為引數傳遞給函式之 variadic 類型 (例如 std::tuple\<T...>) 中的參數封裝。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <class T, T... Vals>  
struct integer_sequence  
```  
  
#### <a name="parameters"></a>參數  
 T  
 值類型，必須是整數類型：bool、char、char16_t、char32_t、wchar_t 或代正負號或不帶正負號的整數類型。  
  
 Vals  
 非類型參數封裝，表示整數類型 T 之值的序列。  
  
## <a name="members"></a>Members  
  
|||  
|-|-|  
|`static size_t size() noexcept`|序列中的項目數。|  
|typedef T value_type|序列中每個項目的類型。 必須是整數類型。|  
  
## <a name="remarks"></a>備註  
 直接傳遞至函式的參數封裝可以是未經過任何特殊程式庫協助程式的封裝。 當參數封裝是傳遞至函式之類型的一部分，且您需要索引來存取項目時，則將它解除封裝最簡單的方式是使用 `integer_sequence` 和其相關類型別名 `make_integer_sequence`、`index_sequence`、`make_index_sequence` 和 `index_sequence_for`。  
  
## <a name="example"></a>範例  
 以下範例是以原始提案 [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html) 為基礎。 它會顯示如何使用 `integer_sequence` 從 `std::array<T,N>` 建立 `std::tuple`，以及如何使用 `integer_sequence` 取得 tuple 成員。  
  
 在 `a2t` 函式中，根據 `size_t` 整數類資料類型，`index_sequence` 是 `integer_sequence` 的別名。 `make_index_sequence` 是編譯時期的別名，會以呼叫端傳入之陣列相同的項目數，建立以零為起始的 `index_sequence`。 `a2t` 會將 `index_sequence` 以值傳遞至 `a2t_`，其中運算式 `a[I]...` 會解除封裝 `I`，然後項目會饋送至 `make_tuple`，它會使用它們做為個別引數。 例如，如果序列包含三個項目，則 `make_tuple` 稱為 make_tuple (a[0]、a[1]、a[2])。 當然，陣列項目本身可以是任何類型。  
  
 apply 函式會接受 [std::tuple](../standard-library/tuple-class.md)，並使用 `tuple_size` 協助程式類別來產生 integer_sequence。 請注意，[std::decay_t](../standard-library/decay-class.md) 是必要的，因為 [tuple_size](../standard-library/tuple-size-class-tuple.md) 不適用於參考類型。 `apply_` 函式會解除封裝 tuple 成員，並且將它們當作個別引數轉送至函式呼叫。 在此範例中，函式是會列印出值的簡單 Lambda 運算式。  
  
```  
  
#include <stddef.h>  
#include <iostream>  
#include <tuple>  
#include <utility>  
#include <array>  
#include <string>  
  
using namespace std;  
  
// Create a tuple from the array and the index_sequence  
template<typename Array, size_t... I>  
auto a2t_(const Array& a, index_sequence<I...>)  
{  
    return make_tuple(a[I]...);  
}  
  
// Create an index sequence for the array, and pass it to the  
// implementation function a2t_  
template<typename T, size_t N>  
auto a2t(const array<T, N>& a)  
{  
    return a2t_(a, make_index_sequence<N>());  
}  
  
// Call function F with the tuple members as separate arguments.   
template<typename F, typename Tuple = tuple<T...>, size_t... I>  
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)   
{  
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);  
}  
  
// Create an index_sequence for the tuple, and pass it with the   
// function object and the tuple to the implementation function apply_  
template<typename F, typename Tuple = tuple<T...>>  
decltype(auto) apply(F&& f, Tuple&& args)  
{  
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;  
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());  
}  
  
int main()  
{   
    const array<string, 3> arr { "Hello", "from", "C++14" };  
  
    //Create a tuple given a array  
    auto tup = a2t(arr);   
  
    // Extract the tuple elements  
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);  
  
    char c;  
    cin >> c;  
}  
  
```  
  
  若要為參數封裝建立 `index_sequence`，請使用 `index_sequence_for`\<T...>，這是 `make_index_sequence`\<sizeof...(T)> 的別名  
  
## <a name="requirements"></a>需求  
 標頭：<type_traits>  
  
 命名空間：std  
  
## <a name="see-also"></a>另請參閱  
 [省略符號和 Variadic 範本](../cpp/ellipses-and-variadic-templates.md)


