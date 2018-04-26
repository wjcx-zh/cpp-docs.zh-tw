---
title: '&lt;tuple&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
dev_langs:
- C++
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
caps.latest.revision: 13
manager: ghogen
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: cd58624affd15174730802f938ffb1cb72772c9b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="lttuplegt-functions"></a>&lt;tuple&gt; 函式

||||
|-|-|-|
|[get](#get)|[make_tuple](#make_tuple)|[tie](#tie)|

## <a name="get"></a> get

從 `tuple` 物件取得項目，依索引或 ( C++14) 依類型。

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>參數

`Index` 要取得之項目的索引。

`Types` Tuple，按宣告順序中宣告的類型序列。

`T` 要取得之項目的類型。

`Tuple` Std:: tuple，其中包含任何數目的元素。

### <a name="remarks"></a>備註

範本函式傳回位於索引 `Index`的值參考，或 `T` 物件中的類型 `tuple` 。

如果 Tuple 不是包含剛剛好一個類型 T 的元素，呼叫 `get<T>(Tuple)` 就會產生編譯器錯誤。

### <a name="example"></a>範例

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_tuple"></a>  make_tuple

從元素值製作 `tuple`。

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>參數

`TN` Nth 函式參數的型別。

`tN` Nth 函式參數的值。

### <a name="remarks"></a>備註

樣板函式會傳回 `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)`，其中當對應類型 `Ti` 為 `cv` `reference_wrapper<X>` 時，每個類型 `Vi` 都是 `X&`，否則為 `Ti`。

`make_tuple` 的其中一個優點是，編譯器會自動決定所儲存物件的類型，不需要明確指定。 當您使用 `make_tuple<int, int>(1, 2)` 時不要使用明確樣板引數 (例如 `make_tuple`)，因為它具有不必要的詳細資訊，並新增可能導致編譯錯誤的複雜右值參考問題。

### <a name="example"></a>範例

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="tie"></a>  將繫結

從元素參考製作 `tuple`。

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>參數

`TN` Tuple 第 n 個項目的基底類型。

### <a name="remarks"></a>備註

此範本函式會傳回 `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)`。

### <a name="example"></a>範例

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>另請參閱

[\<tuple>](../standard-library/tuple.md)<br/>
