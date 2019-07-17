---
title: '&lt;utility&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: 723b077500b9b741445efcd8574fb26cd53e5fc7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246303"
---
# <a name="ltutilitygt-functions"></a>&lt;utility&gt; 函式

## <a name="asconst"></a> as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>傳回值

傳回*T*。

## <a name="declval"></a> declval

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a> Exchange

**(C++14)** 指派新值給物件，並傳回其舊值。

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>參數

*val*\
將會收到 new_val 值的物件。

*new_val*\
其值會複製或移動到 val 的物件。

### <a name="remarks"></a>備註

對於複雜類型，當可以移動建構函式時，`exchange` 可避免複製舊值，如果它是暫存的物件或已移動，則可避免複製新值，以及使用任何可用的轉換指派運算子接受任何類型做為新值。 Exchange 函式並非[std](../standard-library/algorithm-functions.md#swap) ，左邊的引數不是移動或複製到正確的引數。

### <a name="example"></a>範例

下列範例示範如何使用 `exchange`。 在真實世界中，`exchange` 最適用於複製高度耗費資源的大型物件：

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a> 向前

如果引數是右值或右值參考，有條件地將引數轉型為右值參考。 這會將引數的右值特性還原為轉送函式，以支援完美轉送。

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>參數

*型別*\
傳入值的型別*Arg*，這可能會不同的型別*Arg*。 通常由轉送函式的樣板引數所決定。

*引數*\
要轉型的引數。

### <a name="return-value"></a>傳回值

傳回右值參考*Arg*如果值傳入*Arg*原本是右值或右值參考，否則會傳回*Arg*而不需要修改它的型別。

### <a name="remarks"></a>備註

您必須指定明確的樣板引數呼叫 `forward`。

`forward` 不會轉送其引數。 相反地，如果引數原本是右值或右值參考，則透過有條件地將引數轉型為右值參考，`forward` 可讓編譯器在具備所轉送引數原始類型的知識下執行多載解析。 轉送函式的引數的明顯類型可能不同於原始類型，例如當右值做為函式的引數且繫結至參數名稱時，具有名稱會使其成為左值，與任何值確實為右值 —`forward`還原引數的右。

還原右值特性以執行多載解析的引數的原始值就所謂*完美地轉送*。 完美轉送讓樣板函式接受任何參考類型的引數，並在正確的多載解析需要時還原它的右值特性。 透過完美轉送，您可以保存右值的移動語意，避免必須為只變更其引數參考類型的函式提供多載。

## <a name="from_chars"></a> from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a> 取得

依索引位置或依類型從 `pair` 物件取得元素。

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&
    get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr const tuple_element_t<Index, pair<T1, T2>>&
    get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&&
    get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>參數

*索引*\
選擇的項目以 0 起始索引。

*T1*\
第一個配對項目的類型。

*T2*\
第二個配對項目的類型。

*提取要求*\
要從中選取的配對。

### <a name="remarks"></a>備註

範本函式各自傳回其 `pair` 引數項目的參考。

索引的多載，如果的值*索引*是函式會傳回的 0`pr.first`如果的值*的索引*為函式會傳回的 1 `pr.second`。 類型 `RI` 是傳回元素的類型。

不具有索引參數的多載，要傳回的項目是由類型引數推算。 呼叫`get<T>(Tuple)`會產生編譯器錯誤，如果*pr*包含多於或少於一個項目的 t 型別。

### <a name="example"></a>範例

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;
}
```

```Output
9 3.14
1 0.27
```

## <a name="index_sequence"></a> index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a> index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a> make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a> make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a> make_pair

樣板函式，可用來建構 `pair` 類型物件，其中元件類型是根據做為參數傳遞的資料類型自動選擇。

```cpp
template <class T, class U>
    pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>參數

*val1*\
值，初始化 `pair` 的第一個項目。

*Val2*\
值，初始化 `pair` 的第二個項目。

### <a name="return-value"></a>傳回值

建構的 pair 物件： `pair` < `T`，`U`> (`Val1`， `Val2`)。

### <a name="remarks"></a>備註

`make_pair` 會將 [reference_wrapper 類別](../standard-library/reference-wrapper-class.md)的型別物件轉換為參考型別，並將衰減陣列和函式轉換為指標。

在傳回的 `pair` 物件，`T` 的判斷方式如下:

- 如果輸入類型 `T` 是 `reference_wrapper<X>`，傳回的類型 `T` 是 `X&`。

- 否則，傳回的類型 `T` 為 `decay<T>::type`。 如果[decay 類別](../standard-library/decay-class.md)不支援，傳回的型別`T`等同於在輸入型別`T`。

傳回的類型 `U` 同樣是根據輸入類型 `U` 判斷。

其中一個優點`make_pair`已儲存的物件類型的編譯器會自動決定，而且不必明確指定。 這類不使用明確範本引數`make_pair<int, int>(1, 2)`當您使用`make_pair`因為它是詳細資訊，並新增可能導致編譯錯誤的複雜右值參考問題。 在這個範例中，正確語法是 `make_pair(1, 2)`。

`make_pair` 協助程式函式也能夠讓您傳遞兩個值給需要成對輸入參數的函式。

### <a name="example"></a>範例

如需如何使用協助程式函式 `make_pair` 宣告並初始化配對的範例，請參閱 [pair 結構](../standard-library/pair-structure.md)。

## <a name="move"></a> 移動

無條件地將它的引數轉型為右值參考，因而表示如果其類型已啟用移動，就可以移動它。

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>參數

*型別*\
傳入的引數類型推算類型*Arg*，以及參考摺疊規則。

*引數*\
要轉型的引數。 雖然的型別*Arg*指定為右值參考，會出現`move`也接受左值引數，因為左值參考可以繫結至右值參考。

### <a name="return-value"></a>傳回值

`Arg` 做為右值參考，不論它的類型是否為參考類型。

### <a name="remarks"></a>備註

樣板引數*型別*並非明確地指定，但從傳入值的類型推算*Arg*。 型別*型別*根據參考摺疊規則進一步調整。

`move` 不會移動其引數。 相反地，透過無條件地轉型其引數，這可能會是左值 — 至右值參考，它可讓編譯器後續移動，而不是複製中傳遞的值*Arg*如果其類型已啟用移動。 如果其類型不啟用移動，它會改為複製。

如果傳入的值*Arg*是左值 — 也就是它具有名稱，或可以取得自己的位址，當移動時，它會失效。 傳入的值未參照*Arg*依名稱或位址已移動之後。

## <a name="moveif"></a> move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a> 交換

交換兩個類型的項目或[pair 結構](../standard-library/pair-structure.md)物件。

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>參數

*左邊*\
型別或型別的物件`pair`。

*權限*\
型別或型別的物件`pair`。

### <a name="remarks"></a>備註

其中一個優點`swap`已儲存的物件類型的編譯器會自動決定，而且不必明確指定。 這類不使用明確範本引數`swap<int, int>(1, 2)`當您使用`swap`因為它是詳細資訊，並新增可能導致編譯錯誤的複雜右值參考問題。

## <a name="to_chars"></a> to_chars

```cpp
to_chars_result to_chars(char* first, char* last, see below value, int base = 10);
to_chars_result to_chars(char* first, char* last, float value); 
to_chars_result to_chars(char* first, char* last, double value); 
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="remarks"></a>備註

將值轉換成字元字串中，填入範圍`[first, last)`，其中`[first, last)`必須是有效的範圍。
