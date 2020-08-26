---
title: integer_sequence 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: 4d927be4fdd41ab75ca78a0e0e7ab0282e4fbf6a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843868"
---
# <a name="integer_sequence-class"></a>integer_sequence 類別

表示整數序列。 可以用來推算和展開 variadic 型別中的參數套件，例如 std：：元組 \<T...> ，會當做引數傳遞至函式。

## <a name="syntax"></a>語法

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>參數

*10gbase-t*\
值類型，必須是整數類型：bool、char、char16_t、char32_t、wchar_t 或代正負號或不帶正負號的整數類型。

*Vals*\
非類型參數封裝，表示整數類型 T 之值的序列。

## <a name="members"></a>成員

|名稱|描述|
|-|-|
|`static size_t size() noexcept`|序列中的項目數。|
|`typedef T value_type`|序列中每個項目的類型。 必須是整數類型。|

## <a name="remarks"></a>備註

直接傳遞至函式的參數封裝可以是未經過任何特殊程式庫協助程式的封裝。 當參數封裝是傳遞至函式之類型的一部分，且您需要索引來存取項目時，則將它解除封裝最簡單的方式是使用 `integer_sequence` 和其相關類型別名 `make_integer_sequence`、`index_sequence`、`make_index_sequence` 和 `index_sequence_for`。

## <a name="example"></a>範例

以下範例是以原始提案 [N3658](https://wg21.link/n3658) 為基礎。 它會顯示如何使用 `integer_sequence` 從 `std::array<T,N>` 建立 `std::tuple`，以及如何使用 `integer_sequence` 取得 tuple 成員。

在 `a2t` 函式中，根據 `size_t` 整數類資料類型，`index_sequence` 是 `integer_sequence` 的別名。 `make_index_sequence` 是編譯時期的別名，會以呼叫端傳入之陣列相同的項目數，建立以零為起始的 `index_sequence`。 `a2t` 會將 `index_sequence` 以值傳遞至 `a2t_`，其中運算式 `a[I]...` 會解除封裝 `I`，然後項目會饋送至 `make_tuple`，它會使用它們做為個別引數。 例如，如果序列包含三個項目，則 `make_tuple` 稱為 make_tuple (a[0]、a[1]、a[2])。 當然，陣列項目本身可以是任何類型。

Apply 函數會接受 [std：：元組](../standard-library/tuple-class.md)，並 `integer_sequence` 使用 `tuple_size` helper 類別產生。 請注意， [std：:d ecay_t](../standard-library/decay-class.md) 是必要的，因為 [tuple_size](../standard-library/tuple-size-class-tuple.md) 無法使用參考型別。 `apply_` 函式會解除封裝 tuple 成員，並且將它們當作個別引數轉送至函式呼叫。 在此範例中，函式是會列印出值的簡單 Lambda 運算式。

```cpp
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

若要建立 `index_sequence` 參數套件的，請使用 `index_sequence_for` \<T...> 它的別名作為`make_index_sequence`\<sizeof...(T)>

## <a name="requirements"></a>規格需求

標題：\<type_traits\>

命名空間：std

## <a name="see-also"></a>另請參閱

[省略號和 Variadic 範本](../cpp/ellipses-and-variadic-templates.md)
